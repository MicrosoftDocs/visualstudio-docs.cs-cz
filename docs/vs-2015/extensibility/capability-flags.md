---
title: Příznaky funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fd526abb5580b6eb3899df9ee76baacd91e56d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785284"
---
# <a name="capability-flags"></a>Příznaky funkcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SCC_CAP_*xxx* příznaky jsou bitové příznaky, které slouží k označení funkce modulu plug-in správy zdrojového kódu. SCC_EXCAP_*xxx* příznaky jsou přírůstkové příznaky, které označují rozšířené možnosti a vyřešit celočíselné hodnoty.  
  
|Kód funkce|Hodnota|Popis|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Podporuje [sccremove –](../extensibility/sccremove-function.md) a příkazů.|  
|`SCC_CAP_RENAME`|0x00000002L|Podporuje [sccrename –](../extensibility/sccrename-function.md) a příkazů.|  
|`SCC_CAP_DIFF`|0x00000004L|Podporuje [sccdiff –](../extensibility/sccdiff-function.md) a příkazů.|  
|`SCC_CAP_HISTORY`|0x00000008L|Podporuje [scchistory –](../extensibility/scchistory-function.md) a příkazů.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Podporuje [sccproperties –](../extensibility/sccproperties-function.md) a příkazů.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Podporuje [sccrunscc –](../extensibility/sccrunscc-function.md) a příkazů.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Podporuje [sccgetcommandoptions –](../extensibility/sccgetcommandoptions-function.md) a příkazů.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Podporuje [sccqueryinfo –](../extensibility/sccqueryinfo-function.md) a příkazů.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Podporuje [sccgetevents –](../extensibility/sccgetevents-function.md) a příkazů.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Podporuje [sccgetprojpath –](../extensibility/sccgetprojpath-function.md) a příkazů.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Podporuje [sccaddfromscc –](../extensibility/sccaddfromscc-function.md) a příkazů.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Podporuje komentář při rezervaci.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Podporuje komentář vrácení se změnami.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Podporuje komentář na Přidat.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Podporuje komentář na odebrat.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Zapíše text do funkce výstupní poskytované rozhraní IDE.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Podporuje ukládání souborů bez rozdíly.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Podporuje více historie souborů.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Podporuje porovnání velká a malá písmena souboru.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Podporuje souboru porovnání, které ignoruje prázdné znaky.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Podporuje hledání dalších souborů.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Podporuje komentáře k vytvoření projektu.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Podporuje rozdíl v všechny stavy Pokud pod kontrolou.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Modul plug-in nepodporuje uživatelského rozhraní pro Get, ale může stále volat IDE [sccget –](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Modul plug-in je vícenásobné a bezpečné pro vlákna. Ve verzi 1.0 žádné moduly plug-in se předpokládá, že se vícenásobné a bezpečné pro vlákna. Pokud 1.1 modul plug-in nastaví tento bit, hostitel může otevřít více projektů současně.|  
  
## <a name="capability-bits-added-in-version-12"></a>Funkce Bits přidáno ve verzi 1.2  
  
|Kód funkce|Hodnota|Popis|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Podporuje [scccreatesubproject –](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Podporuje [sccgetparentprojectpath –](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Podporuje [sccbeginbatch –](../extensibility/sccbeginbatch-function.md) a [sccendbatch –](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Podporuje [sccdirqueryinfo –](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Podporuje [sccdirdiff –](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Podporuje více rezervace souboru a [sccismulticheckoutenabled –](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Podporuje MSSCCPRJ. Soubor SCC (v souladu s přepsáním uživatele/správce) a [sccwillcreatesccfile –](../extensibility/sccwillcreatesccfile-function.md).|  
  
## <a name="capability-bits-added-in-version-13"></a>Služba Bits funkce byly přidány ve verzi 1.3  
 Tyto příznaky jsou předány jednotlivě na [sccgetextendedcapabilities –](../extensibility/sccgetextendedcapabilities-function.md) funkce k určení, zda je funkce podporována.  
  
|Rozšířené funkce kódu|Hodnota|Popis|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Podporuje `SCC_CHECKOUT_LOCALVER` možnost pro rezervace.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Podporuje [sccbackgroundget –](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Podporuje [sccenumchangedfiles –](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Podporuje hledání další adresáře.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Podporuje vytváření výčtu změn souborů.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Podporuje [sccaddfilesfromscc –](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Podporuje [sccgetuseroption –](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Podporuje volání sccqueryinfo – ve více vláknech.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Podporuje funkci SccRemoveDir.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Můžete odstranit rezervovaných souborů.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Můžete přejmenovat rezervovaných souborů.|  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)

