---
title: Příznaky schopností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 831a52818cfc5c7b75c01a9551b70cd26b95dbcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184521"
---
# <a name="capability-flags"></a>Příznaky funkcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Příznaky SCC_CAP_*xxx* jsou bitové příznaky používané k označení schopností modulu plug-in správy zdrojového kódu. Příznaky SCC_EXCAP_*xxx* jsou přírůstkové příznaky, které označují rozšířené možnosti a jsou přeloženy na celočíselné hodnoty.  
  
|Kód možnosti|Hodnota|Popis|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_REMOVE`|0x00000001L|Podporuje [SccRemove](../extensibility/sccremove-function.md) a příkaz.|  
|`SCC_CAP_RENAME`|0x00000002L|Podporuje [SccRename](../extensibility/sccrename-function.md) a příkaz.|  
|`SCC_CAP_DIFF`|0x00000004L|Podporuje [SccDiff](../extensibility/sccdiff-function.md) a příkaz.|  
|`SCC_CAP_HISTORY`|0x00000008L|Podporuje [SccHistory](../extensibility/scchistory-function.md) a příkaz.|  
|`SCC_CAP_PROPERTIES`|0x00000010L|Podporuje [SccProperties](../extensibility/sccproperties-function.md) a příkaz.|  
|`SCC_CAP_RUNSCC`|0x00000020L|Podporuje [SccRunScc](../extensibility/sccrunscc-function.md) a příkaz.|  
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Podporuje [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a příkaz.|  
|`SCC_CAP_QUERYINFO`|0x00000080L|Podporuje [SccQueryInfo](../extensibility/sccqueryinfo-function.md) a příkaz.|  
|`SCC_CAP_GETEVENTS`|0x00000100L|Podporuje [SccGetEvents](../extensibility/sccgetevents-function.md) a příkaz.|  
|`SCC_CAP_GETPROJPATH`|0x00000200L|Podporuje [SccGetProjPath](../extensibility/sccgetprojpath-function.md) a příkaz.|  
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Podporuje [SccAddFromScc](../extensibility/sccaddfromscc-function.md) a příkaz.|  
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Podporuje komentář při rezervaci.|  
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Podporuje komentář při vrácení se změnami.|  
|`SCC_CAP_COMMENTADD`|0x00002000L|Podporuje komentář při přidání.|  
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Při odebrání podporuje komentář.|  
|`SCC_CAP_TEXTOUT`|0x00008000L|Zapíše text do výstupní funkce poskytnuté rozhraním IDE.|  
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Podporuje ukládání souborů bez rozdílových rozdílů.|  
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Podporuje více historie souborů.|  
|`SCC_CAP_IGNORECASE`|0x00800000L|Podporuje porovnání souborů bez rozlišení velkých a malých písmen.|  
|`SCC_CAP_IGNORESPACE`|0x01000000L|Podporuje porovnání souborů, které ignoruje prázdné znaky.|  
|`SCC_CAP_POPULATELIST`|0x02000000L|Podporuje hledání dalších souborů.|  
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Podporuje komentáře k vytvoření projektu.|  
|`SCC_CAP_DIFFALWAYS`|0x10000000L|V případě řízení podporuje rozdíl ve všech stavech.|  
|`SCC_CAP_GET_NOUI`|0x20000000L|Modul plug-in nepodporuje uživatelské rozhraní pro Get, ale prostředí IDE přesto může volat [SccGet](../extensibility/sccget-function.md).|  
|`SCC_CAP_REENTRANT`|0x40000000L|Modul plug-in je nově zavedený a je bezpečný pro přístup z více vláken. Ve verzi 1,0 se nepředpokládalo, že žádné moduly plug-in se předávají a jsou bezpečné pro přístup z více vláken. Pokud tento bit nastaví modul plug-in 1,1, může hostitel současně otevřít více projektů.|  
  
## <a name="capability-bits-added-in-version-12"></a>Služba Capability bitů byla přidána ve verzi 1,2.  
  
|Kód možnosti|Hodnota|Popis|  
|---------------------|-----------|-----------------|  
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Podporuje [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|  
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Podporuje [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|  
|`SCC_CAP_BATCH`|0x00040000L|Podporuje rozhraní [SccBeginBatch](../extensibility/sccbeginbatch-function.md) a [SccEndBatch](../extensibility/sccendbatch-function.md).|  
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Podporuje [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|  
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Podporuje [SccDirDiff](../extensibility/sccdirdiff-function.md).|  
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Podporuje více rezervací pro soubor a [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|  
|`SCC_CAP_SCCFILE`|0x80000000L|Podporuje MSSCCPRJ. Soubor SCC (podléhající přepsání uživatele/správce) a [SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|  
  
## <a name="capability-bits-added-in-version-13"></a>Služba Capability bitů byla přidána ve verzi 1,3.  
 Tyto příznaky jsou předány postupně do funkce [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) , aby bylo možné zjistit, zda je funkce podporovaná.  
  
|Rozšířený kód možnosti|Hodnota|Popis|  
|------------------------------|-----------|-----------------|  
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Podporuje `SCC_CHECKOUT_LOCALVER` možnost rezervace.|  
|`SCC_EXCAP_BACKGROUND_GET`|2|Podporuje [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|  
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Podporuje [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|  
|`SCC_EXCAP_POPULATELIST_DIR`|4|Podporuje hledání nadbytečných adresářů.|  
|`SCC_EXCAP_QUERYCHANGES`|5|Podporuje výčet změn souborů.|  
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Podporuje [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|  
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Podporuje [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|  
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Podporuje volání SccQueryInfo ve více vláknech.|  
|`SCC_EXCAP_REMOVE_DIR`|9|Podporuje funkci SccRemoveDir.|  
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Může odstranit rezervované soubory.|  
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Může přejmenovat soubory, které se rezervovaly.|  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
