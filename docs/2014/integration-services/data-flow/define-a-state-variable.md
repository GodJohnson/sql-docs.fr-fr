---
title: Définir une variable d’état | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 45d66152-883a-49a7-a877-2e8ab45f8f79
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3d80c4dc4d304dfb6b3043475026e0e5e34c2e57
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072563"
---
# <a name="define-a-state-variable"></a>Définir une variable d’état
  Cette procédure explique comment définir une variable de package dans laquelle l'état de capture de données modifiées est stocké.  
  
 La variable d'état de capture de données modifiées est chargée, initialisée et mise à jour par la tâche de contrôle de capture de données modifiées et est utilisée par le composant de flux de données de la source CDC pour déterminer la plage de traitement actuelle des enregistrements de modification. La variable d'état de capture de données modifiées peut être définie sur n'importe quel conteneur commun à la tache de contrôle de capture de données modifiées et à la source CDC. La définition peut être effectuée au niveau du package mais également sur d'autres conteneurs, tel qu'un conteneur de boucles.  
  
 Il est déconseillé de modifier manuellement la valeur d'une variable d'état de capture de données modifiées. Toutefois, cela peut être utile pour comprendre son contenu.  
  
 Le tableau suivant fournit une description globale des composants de la valeur de variable d'état de capture de données modifiées.  
  
|Composant|Description|  
|---------------|-----------------|  
|`<state-name>`|Il s'agit du nom de l'état de capture de données modifiées actuel.|  
|`CS`|Cela marque le point de départ de la plage de traitement actuelle (début actuel).|  
|`<cs-lsn>`|Il s'agit du dernier numéro séquentiel dans le journal (NSE) traité dans l'exécution de capture de données modifiées précédente.|  
|`CE`|Cela marque le point d'arrivée de la plage de traitement actuelle (fin actuelle). La présence du composant CE dans l'état de capture de données modifiées indique qu'un package de capture de données modifiées est actuellement en cours de traitement ou qu'un package de capture de données modifiées a échoué avant la fin du traitement complet de sa plage de traitement de capture de données modifiées.|  
|`<ce-lsn>`|Il s'agit du dernier numéro séquentiel dans le journal à traiter dans l'exécution de capture de données modifiées actuelle. On part du principe que le dernier numéro de séquence à traiter correspond au maximum (0xFFF…).|  
|`IR`|Cela marque la plage de traitement initiale.|  
|`<ir-start>`|Il s'agit d'un numéro séquentiel dans le journal d'un changement juste avant le début de la charge initiale.|  
|`<ir-end>`|Il s'agit d'un numéro séquentiel dans le journal d'un changement juste après la fin de la charge initiale.|  
|`TS`|Cela marque l'horodateur pour la dernière mise à jour de l'état de capture de données modifiées.|  
|**\<timestamp>**|Il s'agit d'une représentation décimale de la propriété de 64 bits, System.DateTime.UtcNow.|  
|`ER`|Ce message apparaît lorsque la dernière opération a échoué et il inclut une brève description de la cause de l'erreur. Si ce composant est présent, il apparaît toujours en dernier.|  
|`<short-error-text>`|Il s'agit de la brève description de l'erreur.|  
  
 Les numéros séquentiels dans le journal et les numéros de séquence sont tous encodés sous forme de chaîne hexadécimale comportant jusqu'à 20 chiffres représentant la valeur du numéro séquentiel dans le journal de Binary(10).  
  
 Le tableau suivant décrit les valeurs possibles d'état de capture de données modifiées.  
  
|État|Description|  
|-----------|-----------------|  
|(INITIAL)|Il s'agit de l'état initial avant l'exécution d'un package sur le groupe CDC actuel. Il s'agit également de l'état correspondant à une capture de données modifiées vide.|  
|ILSTART (charge initiale démarrée)|Il s'agit de l'état au démarrage du package de charge initiale, après l'appel de l'opération `MarkInitialLoadStart` à la tâche de contrôle CDC.|  
|ILEND (fin de la charge initiale)|C’est l’état lorsque le package de charge initiale se termine avec succès, une fois que le `MarkInitialLoadEnd` appel d’opération pour la tâche de contrôle de capture de données modifiées.|  
|ILUPDATE (mise à jour de la charge initiale)|Il s'agit de l'état lors des exécutions du package de mise à jour à flux progressif, suivant la charge initiale, alors que le traitement de la plage initiale est encore en cours. Il s’agit d’après le `GetProcessingRange` appel d’opération pour la tâche de contrôle de capture de données modifiées.<br /><br /> Si vous utilisez la colonne __$reprocessing, elle contient la valeur 1 pour indiquer que le package peut retraiter des lignes qui sont déjà au niveau de la cible.|  
|TFEND (fin de la mise à jour à flux progressif)|Il s'agit de l'état attendu pour une exécution CDC normale. Il indique que l'exécution précédente a réussi et qu'une nouvelle exécution avec une nouvelle plage de traitement peut démarrer.|  
|TFSTART|C’est l’état sur une exécution non initiale du package de mise à jour de flux progressif, après le `GetProcessingRange` appel d’opération pour la tâche de contrôle de capture de données modifiées.<br /><br /> Cela indique qu’une exécution CDC normale a démarré mais n’est pas terminée ou n'a pas encore terminée correctement (`MarkProcessedRange`).|  
|TFREDO (Retraitement des mises à jour à flux progressif)|Il s'agit de l'état d'un `GetProcessingRange` qui se produit après TFSTART. Il indique que l'exécution précédente ne s'est pas terminée avec succès.<br /><br /> Si vous utilisez la colonne __$reprocessing, elle contient la valeur 1 pour indiquer que le package peut retraiter des lignes qui sont déjà au niveau de la cible.|  
|ERROR|Le groupe CDC est dans un état ERROR.|  
  
 Voici des exemples de valeurs de variable d'état de capture de données modifiées.  
  
-   ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/  
  
-   ILSTART/IR/0x0000162B158700000000//TS/2011-08-07T17:10:43.0031645/  
  
-   TFEND/CS/0x0000025B000001BC0003/TS/2011-07-17T12:05:58.1001145/  
  
-   TFSTART/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:43.9344900/  
  
-   TFREDO/CS/0x0000030D000000AE0003/CE/0x0000159D1E0F01000000/TS/2011-08-09T05:30:59.5544900/  
  
### <a name="to-define-a-cdc-state-variable"></a>Pour définir une variable d'état de capture de données modifiées  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] contenant le flux de données de capture de données modifiées dans lequel vous devez définir la variable.  
  
2.  Cliquez sur l'onglet **Explorateur de package** , puis ajoutez une nouvelle variable.  
  
3.  Attribuez à la variable un nom que vous pouvez identifier en tant que variable d'état.  
  
4.  Attribuez à la variable le type de données **Chaîne** .  
  
 N'attribuez pas une valeur à la variable dans le cadre de sa définition. La valeur doit être définie par la tâche de contrôle de capture de données modifiées.  
  
 Si vous envisagez d'utiliser la tâche de contrôle de capture de données modifiées avec **Permanence d'état automatique**, la variable d'état de capture de données modifiées sera lue dans la table d'état de la base de données que vous spécifiez et sera remise à jour dans cette même table lorsque sa valeur sera modifiée. Pour plus d'informations sur la table d'état, consultez [CDC Control Task](../control-flow/cdc-control-task.md)et [CDC Control Task Editor](../cdc-control-task-editor.md).  
  
 Si vous n'utilisez pas la tâche de contrôle de capture de données modifiées avec Permanence d'état automatique, vous devez charger la valeur de la variable depuis le stockage permanent dans lequel sa valeur a été enregistrée lors la dernière exécution du package, puis la réécrire dans le stockage permanent une fois le traitement de la plage de traitement actuelle terminé.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâche de contrôle CDC](../control-flow/cdc-control-task.md)   
 [Éditeur de tâche de contrôle CDC](../cdc-control-task-editor.md)  
  
  
