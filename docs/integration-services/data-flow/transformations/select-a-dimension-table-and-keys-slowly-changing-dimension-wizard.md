---
title: Sélectionner une table et des clés de dimension (Assistant Dimension à variation lente) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c23e4973ce31027291542aefe183ecbd5e464583
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47791787"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Sélectionner une table et des clés de dimension (Assistant Dimension à variation lente)
  Utilisez la page **Sélectionner une table et des clés de dimension** pour sélectionner une table de dimension à charger. Mappez les colonnes du flux de données avec les colonnes qui vont être chargées.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Options  
 **Connection manager**  
 Sélectionnez un gestionnaire de connexions OLE DB existant dans la liste ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions OLE DB.  
  
> [!NOTE]  
>  L’Assistant Dimension à variation lente prend en charge les gestionnaires de connexions OLE DB et prend uniquement en charge les connexions à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Nouveau**  
 Utilisez la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** pour sélectionner un gestionnaire de connexions existant ou cliquez sur **Nouvelle** pour créer une nouvelle connexion OLE DB.  
  
 **Table ou vue**  
 Sélectionnez une table ou une vue dans la liste.  
  
 **Colonnes d'entrée**  
 Sélectionnez dans la liste les colonnes d'entrée auxquelles vous voulez appliquer le mappage.  
  
 **Colonnes de dimension**  
 Affiche toutes les colonnes de dimension disponibles.  
  
 **Type de clé**  
 Sélectionnez la colonne de dimension qui sera la clé d'entreprise. Vous devez avoir une clé d'entreprise.  
  
## <a name="see-also"></a> Voir aussi  
 [Configurer les sorties à l'aide de l'Assistant Dimension à variation lente](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
