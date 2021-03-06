---
title: L’appel de Java à partir de SQL | Microsoft Docs
description: Découvrez comment appeler des classes Java à partir de procédures stockées SQL Server à l’aide de l’extension de langage dans SQL Server 2019 de programmation de Java.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 08af5a18b827c783515ecd3b4ba4a802c3472f93
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715041"
---
# <a name="how-to-call-java-from-sql-server-2019"></a>L’appel de Java à partir de SQL Server 2019

Lorsque vous utilisez le [extension de langage Java](extension-java.md), le [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) système, procédure stockée est l’interface utilisée pour appeler le runtime Java. Autorisations sur la base de données s’appliquent à l’exécution de code Java.

Cet article explique les détails d’implémentation des méthodes qui s’exécutent sur SQL Server et les classes Java. Une fois que vous êtes familiarisé avec ces détails, passez en revue la [exemple Java](java-first-sample.md) l’étape suivante.

## <a name="basic-principles"></a>Principes de base

* Des classes Java personnalisées compilées doivent exister dans les fichiers .class ou les fichiers .jar dans votre chemin de classe Java. Le [les paramètre CLASSPATH](#set-classpath) fournit le chemin d’accès aux fichiers Java compilés. 

* La méthode de Java que vous appelez doit être fournie dans le paramètre « script » sur la procédure stockée.

* Si la classe appartient à un package, le « packageName » doit être fourni.

* « params » est utilisé pour transmettre des paramètres à une classe Java. Appel d’une méthode qui requiert des arguments n'est pas pris en charge, ce qui rend les paramètres de la seule façon de passer des valeurs d’argument à votre méthode. 

> [!Note]
> Cette note reformule prises en charge et non pris en charge des opérations spécifiques à Java dans CTP 2.0.
> * Sur la procédure stockée, les paramètres d’entrée sont pris en charge. Paramètres de sortie ne sont pas.
> * Diffusion en continu à l’aide du paramètre sp_execute_external_script **@r_rowsPerRead** n’est pas pris en charge.
> * Partitionnement à l’aide de **@input_data_1_partition_by_columns** n’est pas pris en charge.
> * Parallèle à l’aide de traitement  **@parallel= 1** est pris en charge.

## <a name="call-spexecuteexternalscript"></a>Appel sp_execute_external_script

Le [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) système, procédure stockée est l’interface utilisée pour appeler le runtime Java. L’exemple suivant montre un sp_execute_external_script à l’aide de l’extension de Java et les paramètres pour spécifier le chemin d’accès, le script et votre code personnalisé.

```sql
DECLARE @myClassPath nvarchar(30)
DECLARE @param1 int

SET @myClassPath = N'/<my path>/program.jar'
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>.<methodName>'
, @input_data_1 = N'<Input Query>
, @params = N'@CLASSPATH nvarchar(30), @param1 INT'
, @CLASSPATH = @myClassPath
, @param1 = @param1
```

<a name="set-classpath"></a>

## <a name="set-classpath"></a>Définir le chemin de classe

Une fois que vous avez compilé votre classe Java ou les classes et placé l’ou les fichiers .class ou les fichiers .jar dans votre chemin de classe Java, vous avez deux options pour fournir le chemin de classe pour l’extension de SQL Server Java :

**Option 1 : Passer en tant que paramètre**

Une approche permettant de spécifier un chemin d’accès au code compilé consiste en définissant le chemin de classe comme paramètre d’entrée à la procédure de sp_execute_external_script. Le [exemple Java](java-first-sample.md#call-method) illustre cette technique. Si vous choisissez cette approche et que vous disposez de plusieurs chemins, veillez à utiliser le séparateur de chemin d’accès est valide pour le système d’exploitation sous-jacent :

* Sur Linux, séparez les chemins d’accès dans l’instruction CLASSPATH par le signe deux-points « : ».
* Sur Windows, séparez les chemins d’accès dans le chemin de classe par un point-virgule « ; »

**Option 2 : Inscrire une variable système**

Tout comme vous avez créé une variable système pour les exécutables JDK, vous pouvez créer une variable système pour les chemins de code. Pour ce faire, créé une variable d’environnement appelée « CLASSPATH »

## <a name="class-requirements"></a>Spécifications de la classe

Dans l’ordre pour SQL Server de communiquer avec le runtime Java, vous devez implémenter des variables statiques spécifiques dans votre classe. SQL Server peut alors exécuter une méthode dans les données de classe et d’exchange Java à l’aide de l’extension du langage Java.

> [!Note]
> Prévoyez les détails d’implémentation pour modifier dans les CTP à venir que nous travaillons à améliorer l’expérience pour les développeurs.

## <a name="method-requirements"></a>Spécifications des méthodes
Pour passer des arguments, utilisez le **@param** paramètre dans sp_execute_external_script. La méthode elle-même ne peut pas avoir d’arguments. Le type de retour doit être void.  

```java
public static void test()  {}
```

## <a name="data-inputs"></a>Entrées de données 

Cette section explique comment transmettre des données à partir d’une requête de SQL Server à l’aide de Java **InputDataSet** dans sp_execute_external_script.

Pour chaque colonne d’entrée, qu'exécute un push de votre requête SQL pour Java, vous devez déclarer un tableau.

### <a name="inputdatacol"></a>inputDataCol

Dans la version actuelle de l’extension de Java, le **inputDataColN** variable est requise, où *N* est le numéro de colonne. 

```java
public static <type>[] inputDataColN = new <type>[1]
```

Ces tableaux doivent être initialisés (la taille du tableau doit être supérieur à 0 et ne doit pas nécessairement refléter la longueur réelle de la colonne).

Exemple : `public static int[] inputDataCol1 = new int[1];`

Ces variables tableau contiendra des données d’entrée à partir d’une requête SQL server avant l’exécution du programme Java que vous appelez.

### <a name="inputnullmap"></a>inputNullMap

Mappage de valeur NULL est utilisé par l’extension de savoir quelles valeurs sont null. Cette variable sera remplie avec des informations sur les valeurs null par SQL Server avant l’exécution de la fonction de l’utilisateur.

L’utilisateur doit uniquement initialiser cette variable (et la taille du tableau doit être supérieure à 0).

```java
public static boolean[][] inputNullMap = new boolean[1][1];
```

## <a name="data-outputs"></a>Sorties de données 

Cette section décrit **OutputDataSet**, les jeux de données de sortie retournées à partir de Java, que vous pouvez envoyer à et conserver dans SQL Server.

> [!Note]
> Dans les paramètres de sortie [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) ne sont pas pris en charge dans cette version.

### <a name="outputdatacoln"></a>outputDataColN

Semblable à **inputDataSet**, pour chaque colonne de sortie que votre programme Java envoie à SQL Server, vous devez déclarer une variable tableau. Tous les **outputDataCol** tableaux doivent avoir la même longueur. Vous devez vous assurer que cela est initialisée au moment où que l’exécution de la classe terminée.

```java
public static <type>[] outputDataColN = new <type>[]
```

### <a name="numberofoutputcols"></a>numberofOutputCols

Définissez cette variable sur le nombre de colonnes de données de sortie que vous prévoyez d’avoir des lorsque la fonction de l’utilisateur termine son exécution.

```java
public static short numberofOutputCols = <expected number of output columns>;
```

### <a name="outputnullmap"></a>outputNullMap

Mappage de valeur NULL est utilisé par l’extension pour indiquer les valeurs sont null. Nous avons besoin de cela dans la mesure où les types primitifs ne prennent en charge null. Actuellement, nous exigeons également que la carte null pour les types de chaîne, même si les chaînes peuvent être null. Les valeurs NULL sont indiquées par « true ».

Cette NullMap doit être rempli avec le nombre attendu de colonnes et lignes que vous retournez à SQL Server.

```java
public static boolean[][] outputNullMap
```

## <a name="next-steps"></a>Étapes suivantes

+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Types de données Java et SQL Server](java-sql-datatypes.md)
+ [Extension de langage Java dans SQL Server](extension-java.md)
