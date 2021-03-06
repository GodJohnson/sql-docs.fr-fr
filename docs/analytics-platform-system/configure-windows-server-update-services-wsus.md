---
title: Configurer WSUS - Analytique Platform System | Microsoft Docs
description: Ces instructions vous guident dans les étapes d’utilisation de l’Assistant de Configuration de Windows Server Update Services (WSUS) pour configurer WSUS pour l’Analytique Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0b79db4806f22c7d25af4f292fedddb46b40d1e7
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696938"
---
# <a name="configure-windows-server-update-services-wsus-in-analytics-platform-system"></a>Configurer Windows Server Update Services (WSUS) dans le système de plateforme d’Analytique
Ces instructions vous guident dans les étapes d’utilisation de l’Assistant de Configuration de Windows Server Update Services (WSUS) pour configurer WSUS pour l’Analytique Platform System. Vous devez configurer WSUS avant de pouvoir appliquer des mises à jour logicielles à l’appliance. WSUS est déjà installé sur l’ordinateur virtuel VMM de l’appliance.  
  
Pour plus d’informations sur la configuration de WSUS, consultez le [Guide d’Installation pas à pas WSUS](https://go.microsoft.com/fwlink/?LinkId=202417) sur le site Web WSUS. Après la configuration de WSUS, consultez [télécharger et appliquer les mises à jour Microsoft &#40;Analytique Platform System&#41; ](download-and-apply-microsoft-updates.md) pour lancer une mise à jour.  
  
> [!WARNING]  
> Si vous rencontrez des erreurs au cours de ce processus de configuration, arrêtez et contactez le support technique pour obtenir une assistance. Ne pas ignorer les erreurs ou continuer dans le processus après réception des erreurs.  
  
## <a name="before-you-begin"></a>Avant de commencer  
Pour configurer WSUS, vous devez :  
  
-   Avoir les informations de connexion du compte administrateur Analytique Platform System appliance domaine.  
  
-   Disposer d’une connexion de système de plateforme d’Analytique avec les autorisations d’accès à la **Console d’administration** et afficher des informations d’état appliance.  
  
-   Connaître l’adresse IP du serveur WSUS en amont, si vous envisagez de synchroniser les mises à jour à partir d’un serveur WSUS en amont au lieu de la synchronisation des mises à jour directement à partir de Microsoft Update. Assurez-vous que votre serveur WSUS en amont est configuré pour autoriser les connexions anonymes et prend en charge SSL.  
  
-   Connaître l’adresse IP du serveur proxy si votre appliance utilisera un serveur proxy pour accéder au serveur en amont ou les Microsoft Update.  
  
-   Dans la plupart des cas, WSUS doit accéder aux serveurs en dehors de l’appliance. Pour prendre en charge ce scénario d’utilisation du système de plateforme Analytique DNS peut être configuré pour prendre en charge d’un redirecteur de nom externe qui autorise les hôtes de système de plateforme d’Analytique et les Machines virtuelles (VM) à utiliser les serveurs DNS externes pour résoudre les noms en dehors de la appliance. Pour plus d’informations, consultez [utiliser un redirecteur DNS pour résoudre les noms DNS Non-Appliance &#40;Analytique Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md).  
  
## <a name="to-configure-windows-server-update-services-wsus"></a>Pour configurer Windows Server Update Services (WSUS)  
  
1.  Connectez-vous à la **Console d’administration**. Sur le **Appliance état** onglet, vérifiez que le **Cluster** et **réseau** colonnes indiquent vert (ou **NA**) pour tous les nœuds. Vérifiez les indicateurs d’état pour tous les nœuds sur le **Appliance état**.  
  
    -   Il est possible de poursuivre vert ou indicateurs de NA.  
  
    -   Évaluer les erreurs d’avertissement (jaune) non critiques. Dans certains cas des messages d’avertissement ne bloquent pas les mises à jour. S’il existe une erreur de volume de disque non critiques qui n’est pas sur le lecteur C:\, vous pouvez passer à l’étape suivante avant de résoudre l’erreur de volume de disque.  
  
    -   La plupart des indicateurs rouges doivent être résolues avant de continuer. S’il existe des défaillances de disque, utilisez le **alertes de la Console Administrateur** page pour vérifier que la défaillance ne dépasse pas un disque au sein de chaque serveur ou une baie de stockage SAN. En cas de défaillance de disque ne plusieurs au sein de chaque serveur ou de la baie de SAN, vous pouvez passer à l’étape suivante avant de corriger les défaillances de disque. Veillez à contacter le support Microsoft pour résoudre les défaillances de disque dès que possible.  
  
2.  Connectez-vous à la machine virtuelle VMM en tant qu’administrateur de domaine de l’appliance.  
  
3.  Lancer l’Assistant de configuration.  
  
    #### <a name="to-launch-the-configuration-wizard"></a>Pour lancer l’Assistant de configuration  
  
    1.  Dans le **tableau de bord Gestionnaire de serveur**, dans le **outils** menu, cliquez sur **Windows Server Update Services**.  
  
    2.  Dans le volet gauche de la **les Services de mise à jour** fenêtre, cliquez pour développer le serveur de nœud de gestion d’ordinateurs virtuels (***appliance_domain *-VMM**), puis cliquez sur **Options**.  
  
    3.  Dans le **Options** volet, cliquez sur **Assistant Configuration du serveur WSUS** pour lancer l’Assistant de configuration.  
  
        ![Menu Tableau de bord Gestionnaire de serveur](./media/configure-windows-server-update-services-wsus/WSUS_Wiz0.png "WSUS_Wiz0")  
  
    4.  Si c’est la première fois que vous avez exécuté l’Assistant WSUS, vous pouvez être invité à configurer un répertoire pour stocker les mises à jour. `C:\wsus` est un emplacement approprié ; Toutefois, vous pouvez fournir un autre chemin d’accès.  
  
        ![Chemin d’accès WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz1.png "WSUS_Wiz1")  
  
    5.  Examinez le **avant de commencer** liste des éléments à effectuer avant de terminer l’Assistant.  
  
        ![WSUS avant de commencer](./media/configure-windows-server-update-services-wsus/WSUS_Wiz2.png "WSUS_Wiz2")  
  
    6.  Sur le **participer au programme d’amélioration du produit de mise à jour Microsoft** page, sélectionnez **Oui, je souhaite participer au programme d’amélioration du produit de mise à jour Microsoft**, puis cliquez sur **suivant**.  
  
        ![Programme d’amélioration de WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz3.png "WSUS_Wiz3")  
  
    Vous devriez maintenant voir le **choisir le serveur en amont** page. La capture d’écran suivante est le point de départ de l’Assistant de configuration.  
  
    ![WSUS-synchronisation du serveur en amont](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
4.  Choisissez le serveur en amont.  
  
    Sur le **choisir le serveur en amont** page de l’Assistant de configuration de WSUS, vous allez sélectionner comment WSUS sur le nœud de gestion de l’ordinateur virtuel doit se connecter à un serveur en amont pour obtenir des mises à jour logicielles. Vos deux choix sont pour synchroniser le serveur en amont avec [Microsoft Update](https://go.microsoft.com/fwlink/?LinkId=133349) ou de synchroniser les mises à jour avec un autre serveur Windows Server Update Services.  
  
    #### <a name="to-update-by-using-microsoft-update"></a>Pour mettre à jour à l’aide de Microsoft Update  
  
    1.  Si vous choisissez de synchroniser avec Microsoft Update, vous n’avez pas besoin d’apporter des modifications à la **choisir le serveur en amont** page. Cliquer sur **Suivant**.  
  
        ![WSUS-synchronisation du serveur en amont](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
    #### <a name="to-update-from-another-wsus-server"></a>Pour mettre à jour à partir d’un autre serveur WSUS  
  
    1.  Si vous choisissez d’effectuer une synchronisation avec une source autre que Microsoft Update (un serveur en amont), spécifiez le serveur (entrez l’adresse IP) et le port sur lequel ce serveur communiquera avec le serveur en amont.  
  
        ![WSUS-synchronisation du serveur en amont à partir de WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4b.png "WSUS_Wiz4b")  
  
    2.  Pour utiliser Secure Sockets Layer (SSL), sélectionnez le **utiliser SSL lors de la synchronisation des informations de mise à jour** case à cocher. Dans ce cas, les serveurs utiliseront le port 443 pour la synchronisation.  
  
        ![WSUS-synchronisation du serveur en amont à partir de WSUS SSL](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4c.png "WSUS_Wiz4c")  
  
    3.  S’il s’agit d’un serveur réplica, sélectionnez le **il s’agit d’un réplica du serveur en amont** case à cocher. Il est possible de sélectionner les deux **utiliser SSL lors de la synchronisation des informations de mise à jour** et **il s’agit d’un réplica du serveur en amont**.  
  
        ![Réplica de serveur en amont de WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4d.png "WSUS_Wiz4d")  
  
    4.  À ce stade, vous avez terminé avec la configuration du serveur en amont. Cliquez sur **suivant**, ou sélectionnez **spécifier le serveur proxy** dans le volet de navigation gauche.  
  
5.  Spécifiez le serveur proxy.  
  
    Si ce serveur nécessite un serveur proxy pour accéder à Microsoft Update ou un autre serveur en amont, vous pouvez configurer les paramètres du serveur proxy ici ; Sinon, cliquez sur **suivant**.  
  
    ![Proxy WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5a.png "WSUS_Wiz5a")  
  
    #### <a name="to-configure-proxy-server-settings"></a>Pour configurer les paramètres du serveur proxy  
  
    1.  Sur le **spécifier le serveur Proxy** page de l’Assistant de configuration, sélectionnez le **utiliser un serveur proxy lors de la synchronisation** case à cocher, puis tapez l’adresse IP du serveur proxy (non pas par nom) et le numéro de port (port 80 par par défaut) dans les zones correspondantes.  
  
    2.  Si vous souhaitez vous connecter au serveur proxy à l’aide des informations d’identification de l’utilisateur spécifique, sélectionnez le **utiliser les informations d’identification de l’utilisateur pour se connecter au serveur proxy** case à cocher, puis tapez le nom d’utilisateur, le domaine et le mot de passe de l’utilisateur dans le correspondantes zones. Si vous souhaitez activer l’authentification de base pour l’utilisateur qui se connecte au serveur proxy, activez la **autoriser l’authentification de base (mot de passe est envoyé en texte clair)** case à cocher.  
  
        ![Informations d’identification du Proxy WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5b.png "WSUS_Wiz5b")  
  
    3.  À ce stade, vous avez terminé avec la configuration du serveur proxy. Cliquez sur **suivant** pour accéder à la page suivante, où vous pouvez commencer à configurer le processus de synchronisation.  
  
6.  Commencer à se connecter.  
  
    ![Proxy WSUS commencent à se connecter](./media/configure-windows-server-update-services-wsus/WSUS_Wiz6.png "WSUS_Wiz6")  
  
    Cliquez sur **commencent à se connecter**.  
  
    Une fois la connexion a réussi, cliquez sur **suivant** pour accéder à la page suivante, dans laquelle vous pouvez choisir les langues.  
  
7.  Choisir les langues.  
  
    Sélectionnez **télécharger les mises à jour dans ces langues uniquement**.  
  
    Sélectionnez **anglais**, puis cliquez sur **suivant**.  
  
    ![Choisir les langues](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseLanguages.png "SQL_Server_PDW_WSUSChooseLanguages")  
  
8.  Choisissez les produits.  
  
    > [!NOTE]  
    > Si vous utilisez un serveur en amont, vous n’êtes peut-être pas en mesure de choisir les produits. Si cette option n’est pas disponible, ignorez cette étape.  
  
    Désélectionnez toutes les mises à jour sélectionnées.  
  
    Sélectionnez **Windows Server 2012 R2**, et **System Center 2012 R2 - Virtual Machine Manager**, puis cliquez sur **suivant**.  
  
9. Sélectionner les classifications.  
  
    > [!NOTE]  
    > Si vous utilisez un serveur en amont, vous n’êtes peut-être pas en mesure de choisir les Classifications.  Si cette option n’est pas disponible, ignorez cette étape.  
  
    Désélectionnez toutes les mises à jour précédemment sélectionnés.  
  
    Sélectionnez **mises à jour critiques** et **mises à jour de sécurité** pour les mises à jour qui seront synchronisées pour l’appliance Analytique Platform System, puis cliquez sur **suivant**.  
  
    ![Sélectionner les classifications](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseClassifications.png "SQL_Server_PDW_WSUSChooseClassifications")  
  
10. Configurez la planification de synchronisation.  
  
    Sélectionnez **synchroniser manuellement**, puis cliquez sur **suivant**.  
  
    ![Planification de la synchronisation](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSyncSchedule.png "SQL_Server_PDW_WSUSSyncSchedule")  
  
11. Commencer la synchronisation initiale.  
  
    Sélectionnez **commencer la synchronisation initiale**, puis cliquez sur **suivant**.  
  
12. Terminer.  
  
    Cliquez sur **Terminer**.  
  
## <a name="bkmk_WSUSGroup"></a>Regrouper les serveurs de l’Appliance dans WSUS  
Après avoir configuré les WSUS d’Analytique Platform System, l’étape suivante consiste à regrouper les serveurs de l’appliance. En ajoutant tous les serveurs de l’appliance à un groupe, WSUS sera en mesure d’appliquer des mises à jour logicielles sur tous les serveurs dans l’appliance.  
  
> [!NOTE]  
> Le système WSUS est conçu pour exécuter de façon asynchrone. Création de l’activité ne produit pas toujours une mise à jour immédiatement. Par conséquent, vous devrez peut-être attendre un certain temps, jusqu'à ce que les ordinateurs seront visibles dans les boîtes de dialogue WSUS. En cours d’exécution le `setup.exe /action=ReportMicrosoftUpdateClientStatus /DomainAdminPassword="<password>"` commande décrite à la fin de la rubrique [télécharger et appliquer les mises à jour Microsoft &#40;Analytique Platform System&#41; ](download-and-apply-microsoft-updates.md) peut aider à actualiser les boîtes de dialogue.  
  
#### <a name="to-group-the-appliance-servers"></a>Pour regrouper les serveurs de l’appliance  
  
1.  Ouvrez la console WSUS, cliquez sur **tous les ordinateurs** puis cliquez sur **ajouter l’ordinateur groupe**.  
  
    ![Ajouter un groupe d’ordinateurs. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSAddComputerGroup.png "SQL_Server_PDW_WSUSAddComputerGroup")  
  
2.  Entrez le nom « APS » pour le groupe d’ordinateurs, puis cliquez sur **ajouter**.  
  
    ![Entrez un nom pour votre nouveau groupe d’ordinateurs. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSpecifyGroupName.png "SQL_Server_PDW_WSUSSpecifyGroupName")  
  
3.  Cliquez sur **tous les ordinateurs** , modifiez l’état dans le **état** menu déroulant à **n’importe quel**, puis cliquez sur **Actualiser**. Vous devrez peut-être développer **tous les ordinateurs** en cliquant sur le contrôle d’arborescence à gauche pour voir le nouveau groupe que vous venez d’ajouter.  
  
    ![Modifiez un état, puis cliquez sur Actualiser. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusToAny.png "SQL_Server_PDW_WSUSChangeStatusToAny")  
  
4.  Sélectionnez tous les ordinateurs qui font partie de l’appliance, avec le bouton droit, puis cliquez sur **modifier l’appartenance**.  
  
    ![Modifier l’appartenance de tous les ordinateurs PDW. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeMembership.png "SQL_Server_PDW_WSUSChangeMembership")  
  
5.  Sélectionnez le nouveau groupe d’ordinateurs que vous avez créé en cliquant sur la case à cocher, puis sur **OK**.  
  
    ![L’appartenance au groupe d’ordinateurs ensemble](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSetComputerGroupMembership.png "SQL_Server_PDW_WSUSSetComputerGroupMembership")  
  
6.  Sélectionnez le groupe d’ordinateurs, modifiez son **état** à **n’importe quel**, puis cliquez sur **Actualiser**. Tous les ordinateurs doivent maintenant être affectés à ce groupe et répertoriés dans le volet droit. Il est généralement possible de continuer en cas d’avertissements, tels qu’affichent les nœuds **ce nœud n’a pas indiqué son état encore**.  
  
    ![Modifiez un état, puis cliquez sur Actualiser. ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusAnyRefresh.png "SQL_Server_PDW_WSUSChangeStatusAnyRefresh")  
  
