---
title: Utiliser des vues de gestion dynamique (DMV) dans Analysis Services | Microsoft Docs
ms.date: 09/25/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d59601d0706b65186ed5f260128c3c44a134d60e
ms.sourcegitcommit: 110e5e09ab3f301c530c3f6363013239febf0ce5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2018
ms.locfileid: "48906399"
---
# <a name="dynamic-management-views-dmvs"></a>Vues de gestion dynamique 

[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

Vues de gestion dynamique Analysis Services (DMV) sont des requêtes qui retournent des informations sur les objets de modèle, les opérations de serveur et l’intégrité du serveur. La requête, basée sur SQL, est une interface vers *ensembles de lignes de schéma*. Ensembles de lignes de schéma sont on tables qui contiennent des informations sur les objets Analysis Services et l’état du serveur, y compris le schéma de base de données, les sessions actives, les connexions, les commandes et les travaux qui s’exécutent sur le serveur.

Les requêtes DMV sont une alternative à l'exécution des commandes Discover XML/A. Pour la plupart des administrateurs, écrire une requête DMV est plus simple, car la syntaxe est basée sur SQL. En outre, le résultat est retourné dans un format de table qui est plus facile à lire et à copier. 
  
La plupart des DMV les requêtes utilisent un **sélectionnez** instruction et le **$System** schéma avec un ensemble de lignes de schéma XML/A, par exemple :  
  
```  
SELECT * FROM $System.<schemaRowset>  
```  
  
 Requêtes DMV retournent des informations sur l’état de serveur et l’objet au moment où la requête est exécutée. Pour surveiller les opérations en temps réel, utilisez plutôt le suivi. Pour plus d’informations en temps réel de surveillance à l’aide de traces, consultez [utilisez SQL Server Profiler pour surveiller Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
## <a name="query-syntax"></a>syntaxe de requête

Le moteur d'interrogation des vues DMV est l'analyseur d'exploration de données. La syntaxe de requête DMV repose sur l’instruction SELECT &#40;DMX&#41; instruction. Bien que la syntaxe de requête DMV soit basée sur une instruction SQL SELECT, elle ne prend pas en charge la syntaxe complète d'une instruction SELECT. Notez que JOIN, GROUP BY, LIKE, CAST et CONVERT ne sont pas pris en charge.  
  
```  
SELECT [DISTINCT] [TOP <n>] <select list>  
FROM $System.<schemaRowset>  
[WHERE <condition expression>]  
[ORDER BY <expression>[DESC|ASC]]  
```  
  
L'exemple suivant pour DISCOVER_CALC_DEPENDENCY illustre l'utilisation de la clause WHERE pour la fourniture d'un paramètre à la requête :  
  
```  
SELECT * FROM $System.DISCOVER_CALC_DEPENDENCY  
WHERE OBJECT_TYPE = 'ACTIVE_RELATIONSHIP'  
```  
  
Pour les ensembles de lignes de schéma qui comportent des restrictions, la requête doit inclure la fonction SYSTEMRESTRICTSCHEMA. L’exemple suivant retourne des métadonnées CSDL sur 1103 modèles tabulaires au niveau de compatibilité. Notez que CATALOG_NAME respecte la casse :  
  
```  
Select * from SYSTEMRESTRICTSCHEMA ($System.Discover_csdl_metadata, [CATALOG_NAME] = 'Adventure Works DW')  
```  

## <a name="examples-and-scenarios"></a>Exemples et scénarios

Une requête DMV peut vous aider à répondre à des questions sur les sessions et les connexions actives, ainsi que sur les objets qui consomment le plus d'UC ou de mémoire à un moment précis. Exemple :
  
 `Select * from $System.discover_object_activity`  
Cette requête rend sur l’activité de l’objet depuis le dernier démarrage de service. 
  
 `Select * from $System.discover_object_memory_usage`  
Cette requête rend la consommation de mémoire par objet.  
  
 `Select * from $System.discover_sessions`  
Cette requête rend compte des sessions actives, y compris la durée et l’utilisateur de la session.  
  
 `Select * from $System.discover_locks`   
Cette requête retourne un instantané des verrous utilisés à un moment précis dans le temps.  


## <a name="tools-and-permissions"></a>Outils et autorisations

Vous pouvez utiliser toute application cliente qui prend en charge les requêtes MDX ou DMX. Dans la plupart des cas, il est préférable d’utiliser SQL Server Management Studio. Vous devez disposer des autorisations d’administrateur de serveur sur l’instance à interroger une vue DMV.  
  
 **Pour exécuter une requête DMV à partir de SQL Server Management Studio**

1. Se connecter au serveur et de l’objet de modèle que vous souhaitez interroger. 
2. Cliquez sur l’objet serveur ou base de données > **nouvelle requête** > **MDX**.
3. Tapez votre requête, puis cliquez sur **Execute**, ou appuyez sur F5.
  
## <a name="schema-rowsets"></a>Ensembles de lignes de schéma

Tous les ensembles de lignes de schéma n'ont pas d'interface DMV. Pour retourner la liste de tous les ensembles de lignes de schéma qui peuvent être interrogés à l'aide d'une vue de gestion dynamique, exécutez la requête suivante.  
 
```  
SELECT * FROM $System.DBSchema_Tables   
WHERE TABLE_TYPE = 'SCHEMA'   
ORDER BY TABLE_NAME ASC  
```  
  
Si une vue DMV n’est pas disponible pour un ensemble de lignes donné, le serveur retourne erreur : `The <schemarowset> request type was not recognized by the server.` toutes les autres erreurs indiquent des problèmes avec la syntaxe.  

Ensembles de lignes de schéma sont décrites dans les deux protocoles de SQL Server Analysis Services :   

[[MS-SSAS-T] : protocole tabulaire de SQL Server Analysis Services](https://msdn.microsoft.com/library/mt719260) -décrit les ensembles de lignes de schéma pour les modèles tabulaires aux niveaux de compatibilité 1200 et supérieur.

[[MS-SSAS] : SQL Server Analysis Services protocole](https://msdn.microsoft.com/library/ee320606) -décrit les ensembles de lignes de schéma pour les modèles multidimensionnels et les modèles tabulaires aux niveaux de compatibilité 1100 et 1103.

### <a name="rowsets-described-in-the-ms-ssas-t-sql-server-analysis-services-tabular-protocol"></a>Ensembles de lignes décrites dans le [MS-SSAS-T] : protocole tabulaire de SQL Server Analysis Services

|Ensemble de lignes  |Description  |
|---------|---------|
|[TMSCHEMA_ANNOTATIONS](https://msdn.microsoft.com/library/mt704370)|Fournit des informations sur les objets Annotation dans le modèle.|
|[TMSCHEMA_ATTRIBUTE_HIERARCHIES](https://msdn.microsoft.com/library/mt704362)     |   Fournit des informations sur les objets AttributeHierarchy pour une colonne.      |
|[TMSCHEMA_COLUMNS](https://msdn.microsoft.com/library/mt704373)    |  Fournit des informations sur les objets de colonne dans chaque table.       |
|[TMSCHEMA_COLUMN_PERMISSIONS](https://msdn.microsoft.com/library/mt842440)|Fournit des informations sur les objets ColumnPermission dans chaque autorisation de table.|
|[TMSCHEMA_CULTURES](https://msdn.microsoft.com/library/mt719125)|Fournit des informations sur les objets de Culture dans le modèle.|
|[TMSCHEMA_DATA_SOURCES](https://msdn.microsoft.com/library/mt719191)   |   Fournit des informations sur les objets de source de données dans le modèle.      |
|[TMSCHEMA_DETAIL_ROWS_DEFINITIONS](https://msdn.microsoft.com/library/mt825017)|Fournit des informations sur les objets DetailRowsDefinition dans le modèle.|
|[TMSCHEMA_EXPRESSIONS](https://msdn.microsoft.com/library/mt825015)|Fournit des informations sur les objets d’Expression dans le modèle.|
|[TMSCHEMA_EXTENDED_PROPERTIES](https://msdn.microsoft.com/library/mt842451)|Fournit des informations sur les objets ExtendedProperty dans le modèle.|
|[TMSCHEMA_HIERARCHIES](https://msdn.microsoft.com/library/mt719136)    |    Fournit des informations sur les objets de hiérarchie dans chaque table.     |
|[TMSCHEMA_KPIS](https://msdn.microsoft.com/library/mt719002)     |    Fournit des informations sur les objets de l’indicateur de performance clé dans le modèle.     |
|[TMSCHEMA_LEVELS](https://msdn.microsoft.com/library/mt719038)     |   Fournit des informations sur les objets au niveau de chaque hiérarchie.      |
|[TMSCHEMA_LINGUISTIC_METADATA](https://msdn.microsoft.com/library/mt719169)|Fournit des informations sur les synonymes pour les objets dans le modèle pour une culture particulière|
|[TMSCHEMA_MEASURES](https://msdn.microsoft.com/library/mt719218)     |    Fournit des informations sur les objets de mesure dans chaque table.     |
|[TMSCHEMA_MODEL](https://msdn.microsoft.com/library/mt719042)    |  Spécifie un objet de modèle dans la base de données.       |
|[TMSCHEMA_OBJECT_TRANSLATIONS](https://msdn.microsoft.com/library/mt719119)|Fournit des informations sur les traductions de différents objets pour une culture.|
|[TMSCHEMA_PARTITIONS](https://msdn.microsoft.com/library/mt704375)     |     Fournit des informations sur les objets de Partition dans chaque table.    |
|[TMSCHEMA_PERSPECTIVE_COLUMNS](https://msdn.microsoft.com/library/mt719164)     |   Fournit des informations sur les objets PerspectiveColumn dans chaque objet PerspectiveTable.      |
|[TMSCHEMA_PERSPECTIVE_HIERARCHIES](https://msdn.microsoft.com/library/mt719104)     |  Fournit des informations sur les objets PerspectiveHierarchy dans chaque objet PerspectiveTable.       |
|[TMSCHEMA_PERSPECTIVE_MEASURES](https://msdn.microsoft.com/library/mt719135)     |    Fournit des informations sur les objets PerspectiveMeasure dans chaque objet PerspectiveTable.     |
|[TMSCHEMA_PERSPECTIVE_TABLES](https://msdn.microsoft.com/library/mt719272)     |    Fournit des informations sur les objets de Table dans une perspective.     |
|[TMSCHEMA_PERSPECTIVES](https://msdn.microsoft.com/library/mt704340)     |     Fournit des informations sur les objets de Perspective dans le modèle.    |
|[TMSCHEMA_RELATIONSHIPS](https://msdn.microsoft.com/library/mt704355)     |    Fournit des informations sur les objets de relation dans le modèle.     |
|[TMSCHEMA_ROLE_MEMBERSHIPS](https://msdn.microsoft.com/library/mt704584)     |  Fournit des informations sur les objets RoleMembership dans chaque rôle.      |
|[TMSCHEMA_ROLES](https://msdn.microsoft.com/library/mt719267)    |   Fournit des informations sur les objets de rôle dans le modèle.      |
|[TMSCHEMA_TABLE_PERMISSIONS](https://msdn.microsoft.com/library/mt704347)    |    Fournit des informations sur les objets TablePermission dans chaque rôle.     |
|[TMSCHEMA_TABLES](https://msdn.microsoft.com/library/mt719250)     |   Fournit des informations sur les objets de Table dans le modèle.      |
|[TMSCHEMA_VARIATIONS](https://msdn.microsoft.com/library/mt825008)|Fournit des informations sur les objets Variation dans chaque colonne.|

### <a name="rowsets-described-in-the-ms-ssas-sql-server-analysis-services-protocol"></a>Ensembles de lignes décrit dans [MS-SSAS] : protocole de SQL Server Analysis Services

|Ensemble de lignes|Description|  
|------------|-----------------|  
|[DBSCHEMA_CATALOGS](https://msdn.microsoft.com/library/ee302115)|Décrit les catalogues qui sont accessibles sur le serveur.|  
|[DBSCHEMA_COLUMNS](https://msdn.microsoft.com/library/ee301789)|Retourne une ligne pour chaque mesure, chaque attribut de dimension de cube et chaque colonne d’ensemble de lignes de schéma, exposées en tant que colonne.|  
|[DBSCHEMA_PROVIDER_TYPES](https://msdn.microsoft.com/library/ee301696)|Identifie les types de données (base) pris en charge par le serveur.|  
|[DBSCHEMA_TABLES](https://msdn.microsoft.com/library/ee320843)|Retourne les dimensions, les groupes de mesures ou les ensembles de lignes de schéma exposé en tant que tables.|  
|[DISCOVER_CALC_DEPENDENCY](https://msdn.microsoft.com/library/hh770226)| Retourne des informations sur la dépendance de calcul pour un objet qui est spécifié dans une base de données tabulaire ou dans une requête DAX qui est exécutée sur une base de données tabulaire. |  
|[DISCOVER_COMMAND_OBJECTS](https://msdn.microsoft.com/library/ee320662)|Fournit des informations sur l'activité et l'utilisation des ressources des objets actuellement utilisés par la commande référencée.|  
|[DISCOVER_COMMANDS](https://msdn.microsoft.com/library/ee320715)|Fournit des informations sur l'activité et l'utilisation des ressources des dernières commandes exécutées ou des commandes en cours d'exécution sur les connexions ouvertes sur le serveur.|  
|[DISCOVER_CONNECTIONS](https://msdn.microsoft.com/library/ee301889)|Fournit des informations sur l'activité et l'utilisation des ressources des connexions actuellement ouvertes sur le serveur.|  
|[DISCOVER_CSDL_METADATA](https://msdn.microsoft.com/library/gg587670)|Retourne des informations sur les métadonnées de base de données pour les bases de données en mémoire.|  
|[DISCOVER_DATASOURCES](https://msdn.microsoft.com/library/ee320285)|Retourne une liste des sources de données qui sont disponibles sur le serveur.|
|[DISCOVER_DB_CONNECTIONS](https://msdn.microsoft.com/library/ee320467)|Fournit des informations sur l'activité et l'utilisation des ressources des connexions actuellement ouvertes du serveur à une base de données.|  
|[DISCOVER_DIMENSION_STAT](https://msdn.microsoft.com/library/ee320284)|Retourne des statistiques sur la dimension spécifiée.|  
|[DISCOVER_ENUMERATORS](https://msdn.microsoft.com/library/ee302012)|Retourne une liste des noms, types de données et valeurs d'énumération d'énumérateurs pris en charge par le fournisseur XMLA pour une source de données spécifique.|  
|[DISCOVER_INSTANCES](https://msdn.microsoft.com/library/ee320541)|Décrit les instances sur le serveur.|  
|[DISCOVER_JOBS](https://msdn.microsoft.com/library/ee320363)|Fournit des informations sur les travaux actifs exécutés sur le serveur. Un travail fait une partie d'une commande qui exécute une tâche spécifique pour le compte de la commande.|  
|[DISCOVER_KEYWORDS &AMP;#40;XMLA&AMP;#41;](https://msdn.microsoft.com/library/ee301719)|Retourne des informations sur les mots clés réservés par le serveur XMLA.|  
|[DISCOVER_LITERALS](https://msdn.microsoft.com/library/ee301320)|Retourne des informations sur les littéraux pris en charge par le serveur.|  
|[DISCOVER_LOCATIONS](https://msdn.microsoft.com/library/ee302024)|Retourne des informations sur le contenu d'un fichier de sauvegarde. |
|[DISCOVER_LOCKS](https://msdn.microsoft.com/library/ee320398)|Fournit des informations sur les verrous actuellement en place sur le serveur.|  
|[DISCOVER_MASTER_KEY](https://msdn.microsoft.com/library/ee301825)|Retourne la clé de chiffrement principale du serveur.|
|[DISCOVER_MEMORYGRANT](https://msdn.microsoft.com/library/ee320945)|Retourne la liste des allocations de quotas de mémoire interne qui sont prises par les travaux en cours d'exécution sur le serveur.|  
|[DISCOVER_MEMORYUSAGE](https://msdn.microsoft.com/library/ee320910)|Retourne les statistiques DISCOVER_MEMORYUSAGE pour plusieurs objets alloués par le serveur.|  
|[DISCOVER_OBJECT_ACTIVITY](https://msdn.microsoft.com/library/ee320661)|Fournit l'utilisation des ressources par objet depuis le démarrage du service.|  
|[DISCOVER_OBJECT_MEMORY_USAGE](https://msdn.microsoft.com/library/ee320910)|Retourne les statistiques DISCOVER_MEMORYUSAGE pour plusieurs objets alloués par le serveur.|  
|[DISCOVER_PARTITION_DIMENSION_STAT](https://msdn.microsoft.com/library/ee320268)|Retourne des statistiques sur la dimension associée à une partition.|  
|[DISCOVER_PARTITION_STAT](https://msdn.microsoft.com/library/ee320483)|Retourne des statistiques sur les agrégations dans une partition particulière.|  
|[DISCOVER_PERFORMANCE_COUNTERS](https://msdn.microsoft.com/library/ee320809)|Retourne la valeur d'un ou de plusieurs compteurs de performance spécifiés. |  
|[DISCOVER_PROPERTIES](https://msdn.microsoft.com/library/ee320589)|Retourne une liste d’informations et des valeurs sur les propriétés qui sont prises en charge par le serveur pour la source de données spécifié.|  
|[DISCOVER_RING_BUFFERS](https://msdn.microsoft.com/library/mt719204)|Retourne des informations sur les tampons en anneau XEvent actuels sur le serveur.|
|[DISCOVER_SCHEMA_ROWSETS](https://msdn.microsoft.com/library/ee320478)|Retourne les noms, restrictions, description et autres informations pour toutes les demandes de découverte.|  
|[DISCOVER_SESSIONS](https://msdn.microsoft.com/library/ee301962)|Fournit des informations sur l'activité et l'utilisation des ressources des sessions actuellement ouvertes sur le serveur.|  
|[DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS](https://msdn.microsoft.com/library/ee320710)|Retourne des informations sur les segments de colonne utilisé pour stocker des données pour les tables en mémoire.|  
|[DISCOVER_STORAGE_TABLE_COLUMNS](https://msdn.microsoft.com/library/ee302101)|Contient des informations sur les colonnes utilisées pour représenter les colonnes d’une table en mémoire.|  
|[DISCOVER_STORAGE_TABLES](https://msdn.microsoft.com/library/ee302014)|Retourne des statistiques sur les tables en mémoire disponibles sur le serveur.|  
|[DISCOVER_TRACE_COLUMNS]()||  
|[DISCOVER_TRACE_DEFINITION_PROVIDERINFO](https://msdn.microsoft.com/library/ee301342)|Contient l’ensemble de lignes de schéma DISCOVER_TRACE_COLUMNS.|  
|[DISCOVER_TRACE_EVENT_CATEGORIES](https://msdn.microsoft.com/library/ee320442)|Contient l’ensemble de lignes de schéma DISCOVER_TRACE_EVENT_CATEGORIES.|  
|[DISCOVER_TRACES](https://msdn.microsoft.com/library/ee301643)|Contient l’ensemble de lignes du schéma DISCOVER_TRACES.|  
|[DISCOVER_TRANSACTIONS](https://msdn.microsoft.com/library/ee301363)|Retourne l'ensemble actuel des transactions en attente sur le système.|  
|[DISCOVER_XEVENT_TRACE_DEFINITION](https://msdn.microsoft.com/library/mt704568)|Fournit des informations sur les traces XEvent qui sont actuellement actives sur le serveur.|  
|[DISCOVER_XEVENT_PACKAGES](https://msdn.microsoft.com/library/mt704569)|Fournit des informations sur les packages de XEvent qui sont décrites sur le serveur.|
|[DISCOVER_XEVENT_OBJECTS](https://msdn.microsoft.com/library/mt704543)|Fournit des informations sur les objets de XEvent qui sont décrites sur le serveur.|
|[DISCOVER_XEVENT_OBJECT_COLUMNS](https://msdn.microsoft.com/library/mt719352)|Fournit des informations sur le schéma des objets de XEvent qui sont décrites sur le serveur.|
|[DISCOVER_XEVENT_SESSIONS](https://msdn.microsoft.com/library/mt704397)|Fournit des informations sur les sessions XEvent actives sur le serveur.|
|[DISCOVER_XEVENT_SESSION_TARGETS](https://msdn.microsoft.com/library/mt704564)|Fournit des informations sur les cibles en cours de la session XEvent sur le serveur.|
|[DISCOVER_XML_METADATA](https://msdn.microsoft.com/library/ee301560)|Retourne un ensemble de lignes avec une seule ligne et une colonne. |
|[DMSCHEMA_MINING_COLUMNS](https://msdn.microsoft.com/library/ee301664)|Décrit les colonnes de tous les modèles d’exploration de données décrites qui sont déployés sur le serveur.|  
|[DMSCHEMA_MINING_FUNCTIONS](https://msdn.microsoft.com/library/ee320415)|Décrit les fonctions d’exploration de données qui sont pris en charge par les algorithmes d’exploration de données qui sont disponibles sur un serveur qui exécute Analysis Services.|  
|[DMSCHEMA_MINING_MODEL_CONTENT](https://msdn.microsoft.com/library/ee302124)|Permet à l’application cliente pour parcourir le contenu d’un modèle d’exploration de données d’apprentissage.|  
|[DMSCHEMA_MINING_MODEL_CONTENT_PMML](https://msdn.microsoft.com/library/ee320692)|Retourne la structure XML du modèle d'exploration de données. Le format de la chaîne XML respecte la norme PMML 2.1.|  
|[DMSCHEMA_MINING_MODEL_XML](https://msdn.microsoft.com/library/ee301916)|Retourne la structure XML du modèle d'exploration de données. Le format de la chaîne XML respecte la norme PMML 2.1.|  
|[DMSCHEMA_MINING_MODELS](https://msdn.microsoft.com/library/ee320603)|Énumère les modèles d'exploration de données déployés sur le serveur.|  
|[DMSCHEMA_MINING_SERVICE_PARAMETERS](https://msdn.microsoft.com/library/ee320378)|Fournit la liste des paramètres pouvant être utilisés pour configurer le comportement de chaque algorithme d'exploration de données installé sur le serveur.|  
|[DMSCHEMA_MINING_SERVICES](https://msdn.microsoft.com/library/ee320487)|Fournit des informations sur chaque algorithme d’exploration de données qui prend en charge par le serveur.|  
|[DMSCHEMA_MINING_STRUCTURE_COLUMNS](https://msdn.microsoft.com/library/ee320277)|Décrit les colonnes de toutes les structures d'exploration de données qui sont déployées sur le serveur.|  
|[DMSCHEMA_MINING_STRUCTURES](https://msdn.microsoft.com/library/ee320704)|Fournit des informations sur les structures d'exploration de données contenues dans le catalogue actuel.|  
|[MDSCHEMA_ACTIONS](https://msdn.microsoft.com/library/ee320890)|Décrit les actions qui peuvent être disponibles à l’application cliente.|
|[MDSCHEMA_CUBES](https://msdn.microsoft.com/library/ee301304)|Décrit la structure des cubes d'une base de données. Les perspectives sont également retournés dans ce schéma.|
|[MDSCHEMA_DIMENSIONS](https://msdn.microsoft.com/library/ee301366)|Décrit les dimensions dans une base de données.|  
|[MDSCHEMA_FUNCTIONS](https://msdn.microsoft.com/library/mt719467)|Retourne des informations sur les fonctions qui sont actuellement disponibles pour une utilisation dans les langues DAX et MDX.|
|[MDSCHEMA_HIERARCHIES](https://msdn.microsoft.com/library/ee320250)|Décrit chaque hiérarchie dans une dimension particulière.|  
|[MDSCHEMA_INPUT_DATASOURCES](https://msdn.microsoft.com/library/ee301386)|Décrit les objets de source de données décrites dans la base de données.|  
|[MDSCHEMA_KPIS](https://msdn.microsoft.com/library/ee320406)|Décrit les indicateurs de performance clés au sein d’une base de données.|  
|[MDSCHEMA_LEVELS](https://msdn.microsoft.com/library/ee320746)|Décrit chaque niveau dans une hiérarchie particulière.|  
|[MDSCHEMA_MEASUREGROUP_DIMENSIONS](https://msdn.microsoft.com/library/ee320977)|Énumère les dimensions des groupes de mesures.|  
|[MDSCHEMA_MEASUREGROUPS](https://msdn.microsoft.com/library/ee320601)|Décrit les groupes de mesures d'une base de données.|  
|[MDSCHEMA_MEASURES](https://msdn.microsoft.com/library/ee301871)|Décrit chaque mesure.|  
|[MDSCHEMA_MEMBERS](https://msdn.microsoft.com/library/ee320960)|Décrit les membres d'une base de données.|  
|[MDSCHEMA_PROPERTIES](https://msdn.microsoft.com/library/ee320393)|Décrit les propriétés des membres et les propriétés de cellule.|  
|[MDSCHEMA_SETS](https://msdn.microsoft.com/library/ee301356)|Décrit les ensembles actuellement décrits dans une base de données, y compris les jeux d’étendue de session.|  

> [!NOTE]
> STOCKAGES DMV n’ont pas d’un ensemble de lignes de schéma décrit dans le protocole.