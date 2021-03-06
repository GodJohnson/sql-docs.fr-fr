---
title: sp_syscollector_create_collector_type (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collector_type
- sp_syscollector_create_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_create_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 568e9119-b9b0-4284-9cef-3878c691de5f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 24e9f4aa4cf1ab8694947411f5565250c6544d92
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51659108"
---
# <a name="spsyscollectorcreatecollectortype-transact-sql"></a>sp_syscollector_create_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un type de collecteur pour le collecteur de données. Un type de collecteur est un wrapper logique autour du [!INCLUDE[ssIS](../../includes/ssis-md.md)] les packages qui fournissent le mécanisme de collecte de données et les télécharger dans l’entrepôt de données de gestion.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syscollector_create_collector_type   
    [ [@collector_type_uid = ] 'collector_type_uid' OUTPUT ]  
    , [ @name = ] 'name'  
    , [ [ @parameter_schema = ] 'parameter_schema' ]  
    , [ [ @parameter_formatter = ] 'parameter_formatter' ]  
    , [ @collection_package_id = ] 'collection_package_id'  
    , [ @upload_package_id = ] 'upload_package_id'  
```  
  
## <a name="arguments"></a>Arguments  
 [ @collector_type_uid =] '*collector_type_uid*'  
 Est le GUID pour le type de collecteur. *collector_type_uid* est **uniqueidentifier** et si sa valeur est NULL, il sera automatiquement créée et retournée en tant que sortie.  
  
 [ @name =] '*nom*'  
 Nom du type de collecteur. *nom* est **sysname** et doit être spécifié.  
  
 [ @parameter_schema =] '*parameter_schema*'  
 Schéma XML pour ce type de collecteur. *parameter_schema* est **xml** avec NULL comme valeur par défaut.  
  
 [ @parameter_formatter =] '*parameter_formatter*'  
 Modèle à utiliser pour transformer le XML utilisé dans la page de propriétés du jeu d'éléments de collecte. *parameter_formatter* est **xml** avec NULL comme valeur par défaut.  
  
 [@collection_package_id =] *collection_package_id*  
 Identificateur unique local qui pointe vers le package de collection [!INCLUDE[ssIS](../../includes/ssis-md.md)] utilisé par le jeu d'éléments de collecte. *collection_package_id* est **uniqueidentifer** et est obligatoire.  
  
 [@upload_package_id =] *upload_package_id*  
 Identificateur unique local qui pointe vers le package de téléchargement [!INCLUDE[ssIS](../../includes/ssis-md.md)] utilisé par le jeu d'éléments de collecte. *upload_package_id* est **uniqueidentifier** et est obligatoire.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="permissions"></a>Permissions  
 Requiert l'appartenance au rôle de base de données fixe dc_admin (avec autorisation EXECUTE) pour exécuter cette procédure.  
  
## <a name="example"></a>Exemple  
 Cela crée le type collecteur Requête T-SQL générique.  
  
```  
EXEC sp_syscollector_create_collector_type  
@collector_type_uid = '302E93D1-3424-4be7-AA8E-84813ECF2419',  
@name = 'Generic T-SQL Query Collector Type',  
@parameter_schema = '<?xml version="1.0" encoding="utf-8"?>  
  <xs:schema xmlns:xs="https://www.w3.org/2001/XMLSchema" targetNamespace="DataCollectorType">  
    <xs:element name="TSQLQueryCollector">  
      <xs:complexType>  
        <xs:sequence>  
          <xs:element name="Query" minOccurs="1" maxOccurs="unbounded">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element name="Value" type="xs:string" />  
                <xs:element name="OutputTable" type="xs:string" />  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
          <xs:element name="Databases" minOccurs="0" maxOccurs="1">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element name="Database" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
              </xs:sequence>  
              <xs:attribute name="UseSystemDatabases" type="xs:boolean" use="optional" />  
              <xs:attribute name="UseUserDatabases" type="xs:boolean" use="optional" />  
            </xs:complexType>  
          </xs:element>  
        </xs:sequence>  
      </xs:complexType>  
    </xs:element>  
  </xs:schema>',  
@collection_package_id = '292B1476-0F46-4490-A9B7-6DB724DE3C0B',  
@upload_package_id = '6EB73801-39CF-489C-B682-497350C939F0';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
