---
title: sp_addpublication_snapshot (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_addpublication_snapshot_TSQL
- sp_addpublication_snapshot
helpviewer_keywords:
- sp_addpublication_snapshot
ms.assetid: 192b6214-df6e-44a3-bdd4-9d933a981619
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b7a56fad97e7716cce4cc52858b6af2b24a6e09a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731057"
---
# <a name="spaddpublicationsnapshot-transact-sql"></a>sp_addpublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Crée l'Agent d'instantané pour la publication spécifiée. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
> [!IMPORTANT]  
>  Lors de la configuration d'un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées en texte brut au serveur de distribution. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addpublication_snapshot [ @publication= ] 'publication'  
    [ , [ @frequency_type= ] frequency_type ]  
    [ , [ @frequency_interval= ] frequency_interval ]  
    [ , [ @frequency_subday= ] frequency_subday ]  
    [ , [ @frequency_subday_interval= ] frequency_subday_interval ]  
    [ , [ @frequency_relative_interval= ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor= ] frequency_recurrence_factor ]  
    [ , [ @active_start_date= ] active_start_date ]  
    [ , [ @active_end_date= ] active_end_date ]  
    [ , [ @active_start_time_of_day= ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day= ] active_end_time_of_day ]  
    [ , [ @snapshot_job_name = ] 'snapshot_agent_name' ]  
    [ , [ @publisher_security_mode = ] publisher_security_mode ]  
    [ , [ @publisher_login = ] 'publisher_login' ]  
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]  
    [ , [ @job_password = ] 'job_password' ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'***publication***'**  
 Nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@frequency_type=**] *frequency_type*  
 Fréquence à laquelle l'Agent d'instantané est exécuté. *frequency_type* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Une seule fois.|  
|**4** (valeur par défaut)|Tous les jours.|  
|**8**|Toutes les semaines.|  
|**16**|Tous les mois.|  
|**32**|Tous les mois, en fonction de l'intervalle de fréquence.|  
|**64**|Au démarrage de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**128**|Exécution pendant une période d'inactivité de l'ordinateur.|  
  
 [  **@frequency_interval=**] *frequency_interval*  
 Est la valeur à appliquer à la fréquence définie par *frequency_type*. *frequency_interval* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur de frequency_type|Effet sur frequency_interval|  
|------------------------------|-----------------------------------|  
|**1**|*frequency_interval* n’est pas utilisé.|  
|**4** (valeur par défaut)|Chaque *frequency_interval* jours, avec une valeur par défaut de tous les jours.|  
|**8**|*frequency_interval* prend une ou plusieurs des opérations suivantes (combinées avec un [ &#124; (opération de bits OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md) opérateur logique) :<br /><br /> **1** = dimanche&#124;<br /><br /> **2** = lundi&#124;<br /><br /> **4** = mardi&#124;<br /><br /> **8** = mercredi&#124;<br /><br /> **16** = jeudi&#124;<br /><br /> **32** = vendredi&#124;<br /><br /> **64** = samedi|  
|**16**|Sur le *frequency_interval* jour du mois.|  
|**32**|*frequency_interval* est une des opérations suivantes :<br /><br /> **1** = dimanche&#124;<br /><br /> **2** = lundi&#124;<br /><br /> **3** = mardi&#124;<br /><br /> **4** = mercredi&#124;<br /><br /> **5** = jeudi&#124;<br /><br /> **6** = vendredi&#124;<br /><br /> **7** = samedi&#124;<br /><br /> **8** = jour&#124;<br /><br /> **9** = jour de semaine&#124;<br /><br /> **10** = jour de week-end|  
|**64**|*frequency_interval* n’est pas utilisé.|  
|**128**|*frequency_interval* n’est pas utilisé.|  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Unité de *freq_subday_interval*. *frequency_subday* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|Seconde|  
|**4** (valeur par défaut)|Minute|  
|**8**|Heure|  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Intervalle de *frequency_subday*. *frequency_subday_interval* est **int**, avec une valeur 5 par défaut, ce qui signifie que toutes les 5 minutes.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Date d'exécution de l'Agent d'instantané. *frequency_relative_interval* est **int**, avec 1 comme valeur par défaut.  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Facteur de récurrence utilisé par *frequency_type*. *frequency_recurrence_factor* est **int**, avec 0 comme valeur par défaut.  
  
 [  **@active_start_date=**] *active_start_date*  
 Date à laquelle l’Agent d'instantané est planifié pour la première fois, au format AAAAMMJJ. *active_start_date* est **int**, avec 0 comme valeur par défaut.  
  
 [  **@active_end_date=**] *active_end_date*  
 Date à laquelle l’Agent d'instantané cesse d'être planifié, au format AAAAMMJJ. *active_end_date* est **int**, avec 99991231 par défaut, ce qui signifie que le 31 décembre 9999.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Heure à laquelle l’Agent d'instantané est planifié pour la première fois, au format HHMMSS. *active_start_time_of_day* est **int**, avec 0 comme valeur par défaut.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Heure à laquelle l’Agent d'instantané cesse d'être planifié, au format HHMMSS. *active_end_time_of_day* est **int**, avec 235959 par défaut, qui correspond à 11:59:59 P.M. comme sur une horloge de 24 heures.  
  
 [  **@snapshot_job_name =** ] **'***snapshot_agent_name***'**  
 Nom d'un travail existant de l'Agent d'instantané si un travail existant est en cours d'utilisation. *snapshot_agent_name* est **nvarchar (100)** avec une valeur par défaut NULL. Ce paramètre est réservé à un usage interne et ne doit pas être spécifié lors de la création d'une nouvelle publication. Si *snapshot_agent_name* est spécifié, puis *job_login* et *job_password* doit être NULL.  
  
 [ **@publisher_security_mode**=] *publisher_security_mode*  
 Mode de sécurité utilisé par l'agent lors de la connexion au serveur de publication. *publisher_security_mode* est **smallint**, avec 1 comme valeur par défaut. **0** spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, et **1** Spécifie l’authentification Windows. La valeur **0** doit être spécifié pour les non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [ **@publisher_login**=] **'***publisher_login***'**  
 Connexion au serveur de publication. *publisher_login* est **sysname**, avec NULL comme valeur par défaut. *publisher_login* doit être spécifié lorsque *publisher_security_mode* est **0**. Si *publisher_login* a la valeur NULL et *publisher_security_mode* est **1**, le compte spécifié dans *job_login* sera utilisé lorsque connexion au serveur de publication.  
  
 [ **@publisher_password**=] **'***publisher_password***'**  
 Mot de passe utilisé lors de la connexion au serveur de publication. *publisher_password* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  Ne stockez pas les informations d'authentification dans des fichiers de script. Pour améliorer la sécurité, nous vous recommandons de fournir les noms de connexion et les mots de passe au moment de l'exécution.  
  
 [ **@job_login**=] **'***job_login***'**  
 Est la connexion pour le compte sous lequel l’agent s’exécute. Sur Azure SQL Database Managed Instance, utilisez un compte SQL Server. *job_login* est **nvarchar (257)**, avec NULL comme valeur par défaut. Ce compte est toujours utilisé pour les connexions d’agent au serveur de distribution. Vous devez fournir ce paramètre lorsque vous créez un nouveau travail d'Agent d'instantané.  
  
> [!NOTE]  
>  Pour les non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication, il doit être la même connexion que celui spécifiée dans [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md).  
  
 [ **@job_password**=] **'***job_password***'**  
 Mot de passe du compte Windows sous lequel l'Agent s'exécute. *job_password* est **sysname**, sans valeur par défaut. Vous devez fournir ce paramètre lorsque vous créez un nouveau travail d'Agent d'instantané.  
  
> [!IMPORTANT]  
>  Ne stockez pas les informations d'authentification dans des fichiers de script. Pour améliorer la sécurité, nous vous recommandons de fournir les noms de connexion et les mots de passe au moment de l'exécution.  
  
 [ **@publisher**=] **'***publisher***'**  
 Spécifie un serveur de publication non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé lors de la création d’un Agent d’instantané à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addpublication_snapshot** est utilisé dans la réplication de capture instantanée, la réplication transactionnelle et la réplication de fusion.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-snapsh_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addpublication_snapshot**.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Créer et appliquer un instantané](../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_startpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-startpublication-snapshot-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
