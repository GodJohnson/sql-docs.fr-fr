---
title: Créer un InfoSource pour les données de transaction | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 35a8af1e63172dd678a85a612a09d922759373fb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658447"
---
# <a name="create-infosource-for-transaction-data"></a>Créer un InfoSource pour les données de transaction
  Utilisez la boîte de dialogue **Créer un InfoSource pour les données de transaction** pour créer un InfoSource pour les données de transaction dans le système SAP Netweaver BW.  
  
 Vous pouvez ouvrir la boîte de dialogue **Créer un InfoSource pour les données de transaction** depuis la page **Gestionnaire de connexions** de **l’Éditeur de destination SAP BW**. Pour en savoir plus sur la destination SAP BW, consultez [Destination SAP BW](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la boîte de dialogue Créer un InfoSource pour les données de transaction**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la destination SAP BW.  
  
3.  Dans l' **Éditeur de destination SAP BW**, cliquez sur **Gestionnaire de connexions** pour ouvrir la page **Gestionnaire de connexions** de l'éditeur.  
  
4.  Dans la page **Gestionnaire de connexions** , dans la zone de groupe **Créer des objets SAP BW** , sélectionnez **InfoSource**, puis cliquez sur **Créer**.  
  
5.  Dans la boîte de dialogue **Créer un InfoSource** , sélectionnez **Données de transaction**, puis cliquez sur **OK**.  
  
## <a name="general-options"></a>Options générales  
 **Nom de l'InfoSource**  
 Entrez un nom pour le nouvel InfoSource.  
  
 **Description courte**  
 Entrez une brève description pour le nouvel InfoSource.  
  
 **Description longue**  
 Entrez une longue description pour le nouvel InfoSource.  
  
 **Système source**  
 Sélectionnez le système source associé à InfoSource.  
  
 **Enregistrer et activer**  
 Enregistrez et activez le nouvel InfoSource.  
  
## <a name="infosource-transfer-structure-options"></a>Options de structure de transfert d'InfoSource  
 La structure de transfert d'InfoSource vous permet associer les colonnes de flux de données à des InfoSources.  
  
 **PipelineElement**  
 Affiche la colonne dans la sortie du flux de données qui est connectée à la destination SAP BW.  
  
 **PipelineDataType**  
 Affiche le type de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de la colonne du flux de données.  
  
 **Iobject - Rechercher**  
 Associez un InfoObject existant à la colonne de flux de données dans la ligne actuelle. Pour effectuer cette association, cliquez sur **Rechercher**, puis utilisez la boîte de dialogue **Rechercher un InfoObject** pour sélectionner l’InfoObject existant. Pour plus d’informations sur cette boîte de dialogue, consultez [Rechercher un InfoObject](../../integration-services/data-flow/look-up-infoobject.md).  
  
 Après avoir sélectionné un InfoObject existant, le composant remplit les colonnes **InfoObject** et **Type** avec les valeurs sélectionnées.  
  
 **Iobject - Nouveau**  
 Créez un nouvel InfoObject et associez-le à la colonne de flux de données de la ligne actuelle. Pour créer l’InfoObject, cliquez sur **Nouveau**, puis utilisez la boîte de dialogue **Créer un nouvel InfoObject** pour créer l’InfoObject. Pour plus d'informations sur cette boîte de dialogue, consultez [Create New InfoObject](../../integration-services/data-flow/create-new-infoobject.md).  
  
 Après avoir créé un InfoObject, le composant remplit les colonnes **InfoObject** et **Type** avec les nouvelles valeurs.  
  
 **Iobject - Supprimer**  
 Supprimez l'association entre l'InfoObject et la colonne de flux de données de la ligne actuelle. Pour supprimer cette association, cliquez sur **Supprimer**.  
  
 **InfoObject**  
 Affiche le nom de l'InfoObject qui est associé à la colonne de flux de données.  
  
 **Type**  
 Affiche le type de l'InfoObject qui est associé à la colonne de flux de données. Le tableau suivant répertorie les valeurs possibles pour le type.  
  
|Valeur|Description|  
|-----------|-----------------|  
|CHA|Caractéristiques|  
|UNI|Unités|  
|KYF|Chiffres clés|  
|TIM|Caractéristiques de temps|  
  
 **Champ d'unité**  
 Spécifiez les unités que l'InfoObject va utiliser.  
  
## <a name="see-also"></a> Voir aussi  
 [Créer un InfoSource](../../integration-services/data-flow/create-infosource.md)   
 [Aide (F1) sur Microsoft Connector pour SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
