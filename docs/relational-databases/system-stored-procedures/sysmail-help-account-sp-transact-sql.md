---
title: sysmail_help_account_sp (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_help_account_sp_TSQL
- sysmail_help_account_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_help_account_sp
ms.assetid: 87c7c39c-8e05-4e68-9272-45f908809c3b
caps.latest.revision: "48"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b586334d1b725922ec38b3ed63e6cfc8eb0847a7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailhelpaccountsp-transact-sql"></a>sysmail_help_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie les informations (à l'exception des mots de passe) relatifs aux comptes de messagerie de base de données.  
  
||  
|-|  
|**S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu’à [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_account_sp [ [ @account_id = ] account_id | [ @account_name = ] 'account_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@account_id**  =] *account_id*  
 ID du compte pour lequel les informations seront répertoriées. *account_id* est **int**, avec NULL comme valeur par défaut.  
  
 [  **@account_name**  =] **'***account_name***'**  
 Nom du compte pour lequel les informations seront répertoriées. *account_name* est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne un jeu de résultats contenant les colonnes répertoriées ci-après.  
  
||||  
|-|-|-|  
|Nom de colonne|Type de données| Description|  
|**account_id**|**int**|Identificateur du compte.|  
|**nom**|**sysname**|Nom du compte|  
|**Description**|**nvarchar (256)**|Description du compte.|  
|**email_address**|**nvarchar (128)**|Adresse électronique à partir de laquelle les messages sont envoyés.|  
|**nom_complet**|**nvarchar (128)**|Nom d'affichage du compte|  
|**replyto_address**|**nvarchar (128)**|L’adresse où les réponses aux messages de ce compte sont envoyés.|  
|**type de serveur**|**sysname**|Type de serveur de messagerie pour le compte.|  
|**nom du serveur**|**sysname**|Nom du serveur de messagerie pour le compte.|  
|**port**|**int**|Numéro de port utilisé par le serveur de messagerie.|  
|**nom d’utilisateur**|**nvarchar (128)**|Nom d'utilisateur à utiliser pour se connecter au serveur de messagerie, si ce serveur utilise l'authentification. Lorsque **nom d’utilisateur** est NULL, la messagerie de base de données n’utilise pas l’authentification pour ce compte.|  
|**use_default_credentials**|**bit**|Spécifie si le courrier électronique doit être envoyé au serveur SMTP en utilisant les informations d'identification du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. **use_default_credentials** est de type bit, sans valeur par défaut. Lorsque ce paramètre est 1, la messagerie de base de données utilise les informations d’identification de le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] service. Lorsque ce paramètre est 0, la messagerie de base de données utilise le  **@username**  et  **@password**  pour l’authentification sur le serveur SMTP. Si  **@username**  et  **@password**  ont la valeur NULL, alors que la messagerie de base de données utilise l’authentification anonyme. Consultez administrateur SMTP avant de spécifier ce paramètre.|  
|**enable_ssl**|**bit**|Spécifie si la messagerie de base de données chiffre les communications à l'aide de la technologie SSL (Secure Sockets Layer). Utilisez cette option si SSL est obligatoire sur votre serveur SMTP. **enable_ssl** est de type bit, sans valeur par défaut. 1 indique que la messagerie de base de données chiffre les communications au moyen de SSL tandis que la valeur 0 indique qu'elle envoie le courrier sans le chiffrement SSL.|  
  
## <a name="remarks"></a>Notes  
 Lorsqu’aucun *account_id* ou *account_name* est fourni, **sysmail_help_account** répertorie des informations sur tous les comptes de messagerie de base de données dans l’instance de Microsoft SQL Server.  
  
 La procédure stockée **sysmail_help_account_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 **A. Liste des informations pour tous les comptes**  
  
 L'exemple suivant illustre comment répertorier les informations relatives à tous les comptes de l'instance.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp ;  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- --------------------------------------- ------------------------- -------------------------------- --------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
149         Audit Account                Account for audit e-mail.               audit@Adventure-Works.com Automated Mailer (Audit)         NULL            SMTP       smtp.Adventure-Works.com  25          NULL 0                          0        
```  
  
 **B. Liste des informations pour un compte spécifique**  
  
 L'exemple suivant illustre comment répertorier les informations relatives au compte nommé `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_help_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
```  
account_id  name                         description                             email_address             display_name                     replyto_address servertype servername                port        username use_default_credentials enable_ssl  
----------- ---------------------------- ------------------------------------------------------ ------------------------- ---------------- ---------- ------------------------- ----------- -------- ----------------------- ----------  
148         AdventureWorks Administrator Mail account for administrative e-mail. dba@Adventure-Works.com   AdventureWorks Automated Mailer  NULL            SMTP       smtp.Adventure-Works.com  25          NULL     0                       0       
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Messagerie de base de données stockée procédures &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  