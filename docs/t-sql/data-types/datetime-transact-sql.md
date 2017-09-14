---
title: DateTime (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetime_TSQL
- datetime
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- date and time [SQL Server], datetime
- dates [SQL Server], data types
- datetime data type [SQL Server]
- data types [SQL Server], date and time
ms.assetid: 9bd1cc5b-227b-4032-95d6-7581ddcc9924
caps.latest.revision: 64
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ae40eaacd6fd441ce0bdbadd3af02b7b189704a2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="datetime-transact-sql"></a>datetime (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Définit une date qui est associée à une heure de la journée avec des fractions de seconde qui se présente au format 24 heures.
  
> [!NOTE]  
>  Utilisez le **temps**, **date**, **datetime2** et **datetimeoffset** des types de données pour les nouvelles tâches. Ces types s'alignent sur la norme SQL. Ils sont plus portables. **temps**, **datetime2** et **datetimeoffset** offrent une meilleure précision à la seconde. **DateTimeOffset** fournit la prise en charge de fuseau horaire pour les applications globalement déployées.  
  
## <a name="datetime-description"></a>Description de datetime  
  
|Propriété|Valeur|  
|---|---|
|Syntaxe|**datetime**|  
|Utilisation|DÉCLARER @MyDatetime **datetime**<br /><br /> CRÉER une TABLE Table1 (Column1 **datetime** )|  
|Formats de littéraux de chaîne par défaut<br /><br /> (utilisé pour le client de bas niveau)|Non applicable|  
|Plage de dates|Du 1er janvier 1753 au 31 décembre 9999|  
|Plage temporelle|00:00:00 à 23:59:59.997|  
|Plage de décalages de fuseau horaire|Aucune|  
|Plages d'éléments|AAAA comprend quatre chiffres, entre 1753 et 9999, qui représentent une année.<br /><br /> MM est deux chiffres, entre 01 et 12, qui représentent un mois dans l’année spécifiée.<br /><br /> DD est à deux chiffres, entre 01 et 31 selon le mois, qui représentent un jour du mois spécifié.<br /><br /> hh comprend deux chiffres, entre 00 et 23, qui représentent l'heure.<br /><br /> mm comprend deux chiffres, entre 00 et 59, qui représentent la minute.<br /><br /> ss comprend deux chiffres, entre 00 et 59, qui représentent la seconde.<br /><br /> n* comprend entre zéro et trois chiffres, entre 0 et 999, qui représentent les fractions de seconde.|  
|Longueur de caractère|19 positions au minimum et 23 au maximum|  
|Taille de stockage|8 octets|  
|Analyse de précision|Arrondi aux incréments de ,000, ,003 ou ,007 secondes|  
|Valeur par défaut|1900-01-01 00:00:00|  
|Calendrier|Grégorien (N'inclut pas la plage complète des années.)|  
|Précision à la fraction de seconde définie par l'utilisateur|Non|  
|Prise en charge et conservation du décalage de fuseau horaire|Non|  
|Prise en charge de l'heure d'été|Non|  
  
## <a name="supported-string-literal-formats-for-datetime"></a>Formats de littéraux de chaîne pris en charge pour datetime  
Les tableaux suivants répertorient les formats de littéraux de chaîne pris en charge pour **datetime**. Sauf pour ODBC, **datetime** littéraux de chaîne sont des guillemets simples ('), par exemple, 'string_literaL'. Si l’environnement n’est pas **us_english**, les littéraux de chaîne doivent être au format N 'string_literaL'.
  
|Numérique| Description|  
|---|---|
|Formats de date :<br /><br /> [0]4/15/[19]96 -- (mja)<br /><br /> [0]4-15-[19]96 -- (mja)<br /><br /> [0]4.15.[19]96 -- (mja)<br /><br /> [0]4/[19]96/15 -- (maj)<br /><br /> 15/[0]4/[19]96 -- (jma)<br /><br /> 15/[19]96/[0]4 -- (jam)<br /><br /> [19]96/15/[0]4 -- (ajm)<br /><br /> [19]96/[0]4/15 -- (amj)<br /><br /> Formats d'heure :<br /><br /> 14:30<br /><br /> 14:30[:20:999]<br /><br /> 14:30[:20.9]<br /><br /> 4am<br /><br /> 16:00|Vous pouvez spécifier les données de date à l'aide d'un mois spécifié sous forme numérique. Par exemple, 5/20/97 correspond au vingtième jour du mois de mai 1997. Lorsque vous utilisez un format de date numérique, spécifiez l'année, le mois et le jour dans une chaîne qui utilise des barres obliques (/), des traits d'union (-) ou des points (.) comme séparateurs. Cette chaîne doit apparaître sous la forme suivante :<br /><br /> *nombre séparateur nombre séparateur nombre [time] [time]*<br /><br /> <br /><br /> Lorsque la langue a la valeur **us_english**, l’ordre par défaut pour la date est jma. Vous pouvez modifier l’ordre de date à l’aide de la [SET DATEFORMAT](../../t-sql/statements/set-dateformat-transact-sql.md) instruction.<br /><br /> Le paramètre de SET DATEFORMAT détermine l'interprétation des valeurs de date. Si l'ordre ne correspond pas au paramètre, les valeurs ne sont pas interprétées comme des dates (car elles sont hors limites) ou elles sont mal interprétées. Par exemple, 12/10/08 peut être interprété comme 6 dates différentes, selon le paramétrage de DATEFORMAT. Une année en quatre parties est interprétée comme l'année.|  
  
|Alphabétique| Description|  
|---|---|
|Avr[il] [15][,] 1996<br /><br /> Avr[il] 15[,] [19]96<br /><br /> Avr[il] 1996 [15]<br /><br /> [15] Avr[il][,] 1996<br /><br /> 15 Avr[il][,][19]96<br /><br /> 15 [19]96 avr[il]<br /><br /> [15] 1996 avr[il]<br /><br /> 1996 AvR[IL] [15]<br /><br /> 1996 [15] AVR[IL]|Vous pouvez spécifier des données de date avec un mois spécifié comme nom complet du mois. Par exemple, Avril ou l'abréviation Avr spécifiée dans la langue actuelle ; les virgules sont facultatives et la mise en majuscules est ignorée.<br /><br /> Instructions relatives à l'utilisation des formats de date alphabétiques :<br /><br /> (1) Mettez les données de date et d’heure entre des guillemets simples ('). Pour les langues autres que l'anglais, utilisez N'<br /><br /> (2) les caractères placés entre crochets sont facultatifs.<br /><br /> (3) si vous spécifiez uniquement les deux derniers chiffres de l’année, les valeurs inférieures que les deux derniers chiffres de la valeur de la [configurer l’année à deux chiffres cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md) option de configuration sont au même siècle que l’année de coupure. Les valeurs supérieures ou égales à la valeur de cette option sont au siècle qui précède l’année de coupure. Par exemple, si **année de coupure à deux chiffres** a pour valeur 2050 (valeur par défaut), 25 est interprété comme 2025 et 50 est interprété comme 1950. Pour éviter toute ambiguïté, représentez les années à l'aide de quatre chiffres.<br /><br /> (4) si le jour est manquant, le premier jour du mois est fourni.<br /><br /> <br /><br /> Le paramètre de session SET DATEFORMAT n'est pas appliqué lorsque vous précisez le mois sous forme alphabétique.|  
  
|ISO 8601| Description|  
|---|---|
|AAAA-MM-JJThh:mm:ss[.mmm]<br /><br /> AAAAMMJJ[ hh:mm:ss [.mmm]]|Exemples :<br /><br /> (1) 2004-05-23T14:25:10<br /><br /> (2) 2004-05-23T14:25:10.487<br /><br /> <br /><br /> Pour respecter le format ISO 8601, vous devez spécifier chaque élément dans ce format. Cela inclut également la **T**, le signe deux-points ( :) et le point (.) qui sont affichés dans le format.<br /><br /> Les crochets indiquent que le composant fractions de seconde est facultatif. Le composant heure s'exprime au format 24 heures.<br /><br /> Le T indique le début de la partie heure de la **datetime** valeur.<br /><br /> Le format ISO 8601 présente un avantage de taille puisqu'il s'agit d'une norme internationale avec une spécification claire. En outre, ce format n’est pas affecté par les paramètres SET DATEFORMAT ou [SET LANGUAGE](../../t-sql/statements/set-language-transact-sql.md) paramètre.|  
  
|Non séparé| Description|  
|---|---|
|AAAAMMJJ hh:mm:ss [.mmm]||  
  
|ODBC| Description|  
|---|---|
|{ ts '1998-05-02 01:23:56.123' }<br /><br /> { d '1990-10-02' }<br /><br /> { t '13:33:41' }|L'API ODBC définit des séquences d'échappement pour représenter les valeurs de date et d'heure, ce qu'ODBC appelle des données horodateur. Ce format d’horodatage ODBC est également pris en charge par la définition de langage OLE DB (DBGUID-SQL) pris en charge par le [!INCLUDE[msCoName](../../includes/msconame-md.md)] fournisseur OLE DB pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les applications qui utilisent les API basées sur ADO, OLE DB et ODBC peuvent utiliser ce format d'horodateur ODBC pour représenter les dates et les heures.<br /><br /> Les séquences d’échappement ODBC timestamp sont au format : { *type_littéral* '*valeur_constante*'} :<br /><br /> <br /><br /> - *type_littéral* Spécifie le type de la séquence d’échappement. Type horodateur a trois *literal_type* spécificateurs :<br />(1) d = date uniquement<br />(2) t = heure uniquement<br />(3) ts = horodateur (heure + date)<br /><br /> <br /><br /> -'*valeur_constante*» est la valeur de la séquence d’échappement. *valeur_constante* doit respecter les formats suivants pour chaque *type_littéral*.<br />d : aaaa-mm-jj.<br />t : hh : mm : [.fff]<br />TS : aaaa-mm-jj hh : mm : [.fff]|  
  
## <a name="rounding-of-datetime-fractional-second-precision"></a>Arrondi de la précision à la fraction de seconde datetime  
**DateTime** sont arrondies à des incréments d’extension.000,.003 ou.007 secondes, comme indiqué dans le tableau suivant.
  
|Valeur spécifiée par l'utilisateur|Valeur stockée système|  
|---|---|
|01/01/98 23:59:59.999|1998-01-02 00:00:00.000|  
|01/01/98 23:59:59.995<br /><br /> 01/01/98 23:59:59.996<br /><br /> 01/01/98 23:59:59.997<br /><br /> 01/01/98 23:59:59.998|1998-01-01 23:59:59.997|  
|01/01/98 23:59:59.992<br /><br /> 01/01/98 23:59:59.993<br /><br /> 01/01/98 23:59:59.994|1998-01-01 23:59:59.993|  
|01/01/98 23:59:59.990<br /><br /> 01/01/98 23:59:59.991|1998-01-01 23:59:59.990|  
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformité ANSI et ISO 8601  
**DateTime** n’est pas ANSI ou ISO 8601 compatible.
  
##  <a name="_datetime"></a>Conversion des données de Date et heure  
Lorsque vous effectuez une conversion vers des types de données date et heure, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejette toutes les valeurs qu'il ne peut identifier comme dates ou heures. Pour plus d’informations sur l’utilisation des fonctions CAST et CONVERT avec des données de date et d’heure, consultez [CAST et CONVERT &#40; Transact-SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-other-date-and-time-types-to-the-datetime-data-type"></a>Conversion d’autres Types de Date et heure pour le Type de données datetime 
Cette section décrit ce qui se produit lorsque les autres types de données de date et d’heure sont converties à le **datetime** type de données.  
  
Lorsque la conversion est de **date**, jour, mois et année sont copiés. Le composant heure est défini sur 00:00:00.000. Le code suivant montre les résultats de la conversion d'une valeur `date` en valeur `datetime`.  
  
```sql
DECLARE @date date = '12-21-16';  
DECLARE @datetime datetime = @date;  
  
SELECT @datetime AS '@datetime', @date AS '@date';  
  
--Result  
--@datetime               @date  
------------------------- ----------  
--2016-12-21 00:00:00.000 2016-12-21  
```  
  
Lorsque la conversion est de **Time (n)**, le composant heure est copié et le composant date est défini sur ' 1900-01-01 ». Lorsque la précision de fraction de la **Time (n)** valeur est supérieure à trois chiffres, la valeur sera tronquée pour s’ajuster. L'exemple suivant montre les résultats de la conversion d'une valeur `time(4)` en valeur `datetime`.  
  
```sql
DECLARE @time time(4) = '12:10:05.1237';  
DECLARE @datetime datetime = @time;  
  
SELECT @datetime AS '@datetime', @time AS '@time';  
  
--Result  
--@datetime               @time  
------------------------- -------------  
--1900-01-01 12:10:05.123 12:10:05.1237  
```  
  
Lorsque la conversion est de **smalldatetime**, les heures et minutes sont copiées. Les secondes et fractions de seconde sont définies sur 0. Le code suivant montre les résultats de la conversion d'une valeur `smalldatetime` en valeur `datetime`.  
  
```sql
DECLARE @smalldatetime smalldatetime = '12-01-16 12:32';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @datetime AS '@datetime', @smalldatetime AS '@smalldatetime';  
  
--Result  
--@datetime               @smalldatetime  
------------------------- -----------------------  
--2016-12-01 12:32:00.000 2016-12-01 12:32:00  
```  
  
Lorsque la conversion est de **DateTimeOffset (n)**, les composants de date et d’heure sont copiées. Le fuseau horaire est tronqué. Lorsque la précision de fraction de la **DateTimeOffset (n)** valeur est supérieure à trois chiffres, la valeur sera tronquée. L'exemple suivant montre les résultats de la conversion d'une valeur `datetimeoffset(4)` en valeur `datetime`.  
  
```sql
DECLARE @datetimeoffset datetimeoffset(4) = '1968-10-23 12:45:37.1234 +10:0';  
DECLARE @datetime datetime = @datetimeoffset;  
  
SELECT @datetime AS '@datetime', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@datetime               @datetimeoffset  
------------------------- ------------------------------  
--1968-10-23 12:45:37.123 1968-10-23 12:45:37.1237 +01:0   
```  
  
Lorsque la conversion est de **datetime2**, la date et l’heure sont copiées. Lorsque la précision de fraction de la **datetime2** valeur est supérieure à trois chiffres, la valeur sera tronquée. L'exemple suivant montre les résultats de la conversion d'une valeur `datetime2(4)` en valeur `datetime`.  
  
```sql
DECLARE @datetime2 datetime2(4) = '1968-10-23 12:45:37.1237';  
DECLARE @datetime datetime = @datetime2;  
  
SELECT @datetime AS '@datetime', @datetime2 AS '@datetime2';  
  
--Result  
--@datetime               @datetime2  
------------------------- ------------------------  
--1968-10-23 12:45:37.123 1968-10-23 12:45:37.1237  
```  
  
## <a name="examples"></a>Exemples  
L’exemple suivant compare les résultats de la conversion d’une chaîne en chaque **date** et **temps** type de données.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|Type de données|Sortie|  
|---|---|
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
