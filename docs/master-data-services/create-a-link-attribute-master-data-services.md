---
title: "Créer un attribut de lien (Master Data Services) | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], creating link attributes
- creating link attributes [Master Data Services]
ms.assetid: e6658e9c-5b08-4b8d-b556-17ec2dd041d2
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1b5c1a0c51283b981daf0df5e65740892fb830c2
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-link-attribute-master-data-services"></a>Créer un attribut de lien (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], créez un attribut de lien lorsque vous souhaitez que les utilisateurs entrent un lien hypertexte comme valeur d'attribut, tel que http://www.contoso.com.  
  
> [!NOTE]  
>  Quand les utilisateurs entrent une valeur pour un attribut de lien, la chaîne doit commencer par **http://** , sinon une erreur est affichée.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Une entité doit exister pour créer l'attribut qui lui est destiné. Pour plus d’informations, consultez [Créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
## <a name="attribute-information"></a>Informations sur les attributs  
 Pour chaque attribut créé, une ligne comportant sept colonnes est ajoutée à la grille. Le tableau suivant décrit ces colonnes.  
  
|Colonne|Description|  
|------------|-----------------|  
|État|État de l’attribut.<br /><br /> Lorsque vous cliquez sur Enregistrer, la ![icône de mise à jour d’état](../master-data-services/media/mds-statusicon-updating.png "icône de mise à jour d’état") image s’affiche, indiquant que l’attribut est mise à jour.<br /><br /> S’il existe des erreurs lors de la création ou modification d’un attribut, le ![icône de statut d’erreur](../master-data-services/media/mds-statusicon-error.png "icône de statut d’erreur") image s’affiche.<br /><br /> Dans le cas contraire, l’état est OK et la ![icône pour l’état OK](../master-data-services/media/mds-statusicon-ok.png "icône pour l’état OK") image s’affiche.|  
|Nom|Nom de l'attribut.|  
|Nom complet|Nom de l’attribut.|  
|Description|Description de l’attribut.|  
|Largeur d’affichage en pixels|Largeur de l’attribut.|  
|Types et propriétés|Informations sur le type et le type de données de l’attribut.|  
|Activer le suivi des modifications|Spécifie si le suivi des modifications est activé sur l’attribut et indique le numéro du groupe entre parenthèses.|  
  
 Quand vous cliquez sur un attribut, les informations suivantes s’affichent.  
  
-   **Créé par**: nom de l’utilisateur qui a créé l’attribut.  
  
-   **Le**: date et heure de création de l’attribut.  
  
-   **Mis à jour par**: nom du dernier utilisateur qui a mis à jour l’attribut.  
  
-   **Le**: date et heure de la dernière mise à jour de l’attribut.  
  
### <a name="to-create-a-link-attribute"></a>Pour créer un attribut de lien  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Gérer le modèle** , sélectionnez un modèle dans la grille et cliquez sur **Entités**.  
  
3.  Dans la page **Gérer l’entité** , sélectionnez la ligne de l’entité pour laquelle vous souhaitez créer un attribut.  
  
4.  Cliquez sur **Attributs**.  
  
5.  Dans la page **Gérer les attributs** , effectuez l’une des opérations suivantes, puis cliquez sur **Ajouter**.  
  
    -   Si l’attribut concerne les membres feuille, sélectionnez **Feuille** dans la zone de liste **Types de membre** .  
  
    -   Si l’attribut concerne les membres consolidés, sélectionnez **Consolidé** dans la zone de liste **Types de membre** .  
  
    -   Si l’attribut concerne les collections, sélectionnez **Collection** dans la zone de liste **Types de membre** .  
  
6.  Dans la zone **Nom** , tapez un nom pour l'attribut. Pour obtenir la liste des mots qui ne doivent pas être utilisés comme noms d’attributs, consultez [Mots réservés &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
7.  Si vous le souhaitez, tapez le nom complet et une description de l’attribut dans le champ **Description** .  
  
8.  Dans la zone **Largeur d'affichage en pixels** , tapez la largeur de la colonne d'attribut à afficher dans la grille **Explorateur** .  
  
9. Dans la liste **Type d’attribut** , sélectionnez **Forme libre**.  
  
10. Dans la liste **Type de données** , sélectionnez **Lien**.  
  
11. Dans la zone **Longueur** , tapez le nombre maximal de caractères autorisé.  
  
12. Sélectionnez éventuellement **Activer le suivi des modifications** pour effectuer le suivi des modifications apportées aux groupes d'attributs. Pour plus d’informations, consultez [Ajouter des attributs à un groupe de suivi des modifications &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).  
  
13. Cliquez sur **Enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [Modifier un nom d’attribut et Type de données &#40; Master Data Services &#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [Créer un attribut basé sur un domaine &#40; Master Data Services &#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [Créer un attribut de fichier &#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  