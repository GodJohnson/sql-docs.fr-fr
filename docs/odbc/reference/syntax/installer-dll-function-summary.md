---
title: Récapitulatif des fonctions DLL de programme d’installation | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecb486f51caa97c715d54885c34575a60bfdfb83
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723327"
---
# <a name="installer-dll-function-summary"></a>Récapitulatif des fonctions de la DLL d’installation
Le tableau suivant décrit les fonctions dans le programme d’installation DLL. Pour plus d’informations sur la syntaxe et la sémantique pour chaque fonction, consultez [référence d’API de DLL de programme d’installation](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Tâche|Nom de la fonction|Fonction|  
|----------|-------------------|-------------|  
|L’installation d’ODBC|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Charge la DLL d’installation spécifiques au pilote.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Retourne une liste des pilotes installés.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Ajoute un pilote aux informations système.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Retourne le répertoire cible pour le Gestionnaire de pilotes.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Retourne des informations d’erreur ou d’état pour les fonctions du programme d’installation.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Ajoute un traducteur d’informations sur le système.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Permet à une bibliothèque du programme d’installation de pilote ou de convertisseur pour signaler des erreurs.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Supprime un pilote à partir des informations système.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Supprime les composants principaux ODBC à partir des informations système.|  
||[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Supprime le traducteur à partir des informations système.|  
|Configuration des sources de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Appelle la DLL d’installation spécifiques au pilote.|  
||[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Affiche une boîte de dialogue pour ajouter une source de données.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Récupère le mode de configuration qui indique où l’entrée de fichier Odbc.ini répertoriant les valeurs de la source de données est dans les informations système.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Écrit une valeur dans les informations système.|  
||[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Affiche une boîte de dialogue pour sélectionner un traducteur.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Affiche une boîte de dialogue pour configurer les pilotes et les sources de données.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Lit les informations à partir de sources de données de fichier.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Supprime la source de données par défaut.|  
||[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Supprime une source de données.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Définit le mode de configuration qui indique où l’entrée de fichier Odbc.ini répertoriant les valeurs de la source de données est dans les informations système.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Vérifie la longueur et la validité du nom de source de données.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Ajoute une source de données.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Écrit les informations dans le fichier DSN.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Obtient une valeur à partir des informations système.|
