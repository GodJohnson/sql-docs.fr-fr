---
title: ALTER PARTITION FUNCTION (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER PARTITION FUNCTION
- ALTER_PARTITION_FUNCTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- splitting partitions [SQL Server]
- partitioned tables [SQL Server], splitting
- ALTER PARTITION FUNCTION statement
- merging partitions [SQL Server]
- partitioned indexes [SQL Server], merging
- partitioned indexes [SQL Server], splitting
- modifying partition functions
- partition functions [SQL Server], modifying
- partitioned tables [SQL Server], merging
ms.assetid: 70866dac-0a8f-4235-8108-51547949ada4
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5969f9487a55437febfba9f6deec7fb1e0df5f02
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-partition-function-transact-sql"></a>ALTER PARTITION FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Modifie une fonction de partition en divisant ou en fusionnant ses valeurs limites. En exécutant ALTER PARTITION FUNCTION, vous pouvez diviser une partition d'une table ou d'un index utilisant la fonction de partition en deux partitions, ou fusionner deux partitions dans une seule.  
  
> [!CAUTION]  
>  Une même fonction de partition peut être utilisée par plusieurs tables ou index. Ils sont alors tous affectés par ALTER PARTITION FUNCTION en une seule transaction.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER PARTITION FUNCTION partition_function_name()  
{   
    SPLIT RANGE ( boundary_value )  
  | MERGE RANGE ( boundary_value )   
} [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *partition_function_name*  
 Est le nom de la fonction de partition à modifier.  
  
 SPLIT RANGE ( *boundary_value* )  
 Ajoute une partition à la fonction de partition. *boundary_value* détermine la plage de la nouvelle partition et doivent être différents des plages limites existantes de la fonction de partition. En fonction de *boundary_value*, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] divise l’une des plages existantes en deux. De ces deux que celui dans lequel le nouveau *boundary_value* réside est considéré comme la nouvelle partition.  
  
 Pour conserver la nouvelle partition, un groupe de fichiers doit être en ligne et être marqué par le schéma de partition qui utilise la fonction de partition comme étant le prochain utilisé (NEXT USED). Les groupes de fichiers sont alloués aux partitions dans une instruction CREATE PARTITION SCHEME. Si une instruction CREATE PARTITION SCHEME alloue plus de groupes de fichiers qu'il n'en faut (il y a alors moins de partitions créées dans l'instruction CREATE PARTITION FUNCTION qu'il n'y a de groupes de fichiers pour les accueillir), certains groupes de fichiers ne sont pas affectés, et l'un d'entre eux est marqué NEXT USED par le schéma de partition. C'est ce groupe de fichiers qui accueillera la nouvelle partition. Si aucun groupe de fichiers n'est marqué NEXT USED par le schéma de partition, vous devez utiliser ALTER PARTITION SCHEME pour ajouter un groupe de fichiers, ou en désigner un existant, afin d'accueillir la nouvelle partition. Un groupe de fichiers contenant déjà des partitions peut être désigné pour accueillir des partitions supplémentaires. Étant donné qu'une fonction de partition peut participer à plusieurs schémas de partition, tous les schémas de partition utilisant la fonction de partition à laquelle vous ajoutez des partitions doivent contenir un groupe de fichiers NEXT USED. À défaut, ALTER PARTITION FUNCTION échoue et génère une erreur indiquant le ou les schémas de partition qui sont dépourvus d'un groupe de fichiers NEXT USED.  
  
 Si vous créez toutes les partitions dans le même groupe de fichiers, celui-ci est initialement et automatiquement affecté comme le groupe de fichiers NEXT USED. Toutefois, après une opération de fractionnement, il n'y a plus de groupe de fichiers NEXT USED désigné. Vous devez affecter explicitement le groupe de fichiers comme groupe de fichiers NEXT USED à l'aide de ALTER PARTITION SCHEME, sinon toute opération de fractionnement ultérieure échoue.  
  
> [!NOTE]  
>  Limitations de l’index columnstore : seules les partitions vides peuvent être fractionnées lorsqu’il existe un index columnstore sur la table. Vous devez supprimer ou désactiver l’index columnstore avant d’effectuer cette opération.  
  
 FUSIONNER [plage ( *boundary_value*)]  
 Supprime une partition et fusionne les valeurs qui existent dans la partition dans l'une des partitions restantes. PLAGE (*boundary_value*) doit être une valeur limite existante, dans laquelle les valeurs de la partition supprimée sont fusionnées. Le groupe de fichiers qui contenait initialement *boundary_value* le schéma de partition est supprimé, sauf si elle est utilisée par une partition restante, ou est marqué avec la propriété NEXT USED. La partition fusionnée réside dans le groupe de fichiers qui ne contenait pas initialement *boundary_value*. *boundary_value* est une expression constante qui peut référencer des variables (y compris les variables de type défini par l’utilisateur) ou des fonctions (y compris les fonctions définies par l’utilisateur). Elle ne peut pas faire référence à une expression [!INCLUDE[tsql](../../includes/tsql-md.md)]. *boundary_value* doit soit correspondre ou être implicitement convertible en type de données de la colonne de partitionnement correspondante et ne peut pas être tronquée pendant une conversion implicite d’une manière que la taille et l’échelle de la valeur ne correspond pas à celles de son *input_parameter_type*.  
  
> [!NOTE]  
>  Limitations de l’index columnstore : Impossible de fusionner deux partitions non vides contenant un index columnstore. Vous devez supprimer ou désactiver l’index columnstore avant d’effectuer cette opération.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Conservez toujours les partitions vides aux deux extrémités de la plage de partition pour vous assurer que le fractionnement de la partition (avant de charger de nouvelles données) et la fusion de la partition (après déchargement des données précédentes) n'entraînent aucun déplacement de données. Évitez de fractionner ou fusionner des partitions remplies. Cela peut être très inefficace, car la génération peut parfois prendre quatre fois plus de temps et provoquer également un verrouillage grave.  
  
## <a name="limitations-and-restrictions"></a>Limitations et restrictions  
 ALTER PARTITION FUNCTION repartitionne les tables et les index qui utilisent la fonction en une opération atomique unique. Toutefois, cette opération se produit hors ligne et, selon l'étendue du repartitionnement, elle peut s'avérer gourmande en ressources.  
  
 L'utilisation de ALTER PARTITION FUNCTION doit uniquement viser à diviser une partition en deux, ou à fusionner deux partitions dans une seule. Pour modifier la façon dont une table est partitionnée (par exemple, de 10 partitions à 5), vous pouvez utiliser l'une des options indiquées ci-dessous. La consommation en ressources de ces options peut varier en fonction de la configuration de votre système.  
  
-   Créez une nouvelle table partitionnée avec la fonction de partition de votre choix, puis insérez les données de l'ancienne table dans la nouvelle à l'aide de l'instruction INSERT INTO...SELECT FROM.  
  
-   Créez un index cluster partitionné sur un segment.  
  
    > [!NOTE]  
    >  La suppression d'un index cluster partitionné engendre un segment partitionné.  
  
-   Supprimez et reconstruisez un index partitionné existant à l'aide de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX avec la clause DROP EXISTING = ON.  
  
-   Exécutez une séquence d'instructions ALTER PARTITION FUNCTION.  
  
 Tous les groupes de fichiers concernés par l'instruction ALTER PARITITION FUNCTION doivent être en ligne.  
  
 ALTER PARTITION FUNCTION échoue s'il existe un index cluster désactivé dans une table qui utilise la fonction de partition.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'assure pas la prise en charge de la réplication lors de la modification d'une fonction de partition. Les modifications apportées à une fonction de partition dans la base de données de publication doivent être appliquées manuellement dans la base de données d'abonnement.  
  
## <a name="permissions"></a>Permissions  
 L'instruction ALTER PARTITION FUNCTION peut être exécutée avec les autorisations suivantes :  
  
-   Autorisation ALTER ANY DATASPACE. Cette autorisation est attribuée par défaut aux membres du rôle de serveur fixe **sysadmin** et des rôles de base de données fixes **db_owner** et **db_ddladmin** .  
  
-   Autorisation CONTROL ou ALTER sur la base de données dans laquelle la fonction de partition a été créée.  
  
-   Autorisation CONTROL SERVER ou ALTER ANY DATABASE sur le serveur de la base de données dans laquelle la fonction de partition a été créée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-splitting-a-partition-of-a-partitioned-table-or-index-into-two-partitions"></a>A. Fractionnement d'une partition de table ou d'index partitionné en deux partitions  
 L'exemple suivant crée une fonction de partition pour partitionner une table ou un index en quatre partitions. `ALTER PARTITION FUNCTION` fractionne l'une des partitions en deux pour créer au total cinq partitions.  
  
```tsql  
IF EXISTS (SELECT * FROM sys.partition_functions  
    WHERE name = 'myRangePF1')  
DROP PARTITION FUNCTION myRangePF1;  
GO  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
GO  
--Split the partition between boundary_values 100 and 1000  
--to create two partitions between boundary_values 100 and 500  
--and between boundary_values 500 and 1000.  
ALTER PARTITION FUNCTION myRangePF1 ()  
SPLIT RANGE (500);  
```  
  
### <a name="b-merging-two-partitions-of-a-partitioned-table-into-one-partition"></a>B. Fusion de deux partitions d'une table partitionnée en une seule partition  
 L'exemple suivant crée une fonction de partition (identique à celle de l'exemple précédent), puis fusionne deux des partitions en une seule partition, pour un total de trois partitions.  
  
```tsql  
IF EXISTS (SELECT * FROM sys.partition_functions  
    WHERE name = 'myRangePF1')  
DROP PARTITION FUNCTION myRangePF1;  
GO  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
GO  
--Merge the partitions between boundary_values 1 and 100  
--and between boundary_values 100 and 1000 to create one partition  
--between boundary_values 1 and 1000.  
ALTER PARTITION FUNCTION myRangePF1 ()  
MERGE RANGE (100);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et index partitionnés](../../relational-databases/partitions/partitioned-tables-and-indexes.md)   
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [Sys.partition_functions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [Sys.partition_parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)   
 [Sys.partition_range_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [Sys.partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  