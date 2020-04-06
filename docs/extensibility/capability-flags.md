---
title: Vlajky schopností | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9660cbe5a18e82974858fa4d923a38fc73e773f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739865"
---
# <a name="capability-flags"></a>Příznaky schopností
Příznaky SCC_CAP_*xxx* jsou bitové příznaky používané k označení možností modulu plug-in správy zdrojového kódu. SCC_EXCAP_*xxx* příznaky jsou přírůstkové příznaky, které označují rozšířené možnosti a přeložit na celé hodnoty.

|Kód schopností|Hodnota|Popis|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Podporuje [Příkaz SccRemove](../extensibility/sccremove-function.md) a command.|
|`SCC_CAP_RENAME`|0x00000002L|Podporuje [SccRename](../extensibility/sccrename-function.md) a příkaz.|
|`SCC_CAP_DIFF`|0x00000004L|Podporuje [příkaz SccDiff](../extensibility/sccdiff-function.md) a command.|
|`SCC_CAP_HISTORY`|0x00000008L|Podporuje [SccHistory](../extensibility/scchistory-function.md) a příkaz.|
|`SCC_CAP_PROPERTIES`|0x00000010L|Podporuje [SccProperties](../extensibility/sccproperties-function.md) a příkaz.|
|`SCC_CAP_RUNSCC`|0x00000020L|Podporuje [Příkaz SccRunScc](../extensibility/sccrunscc-function.md) a příkaz.|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Podporuje [Příkaz SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a příkaz.|
|`SCC_CAP_QUERYINFO`|0x00000080L|Podporuje [příkaz SccQueryInfo](../extensibility/sccqueryinfo-function.md) a příkaz.|
|`SCC_CAP_GETEVENTS`|0x00000100L|Podporuje [SccGetEvents](../extensibility/sccgetevents-function.md) a příkaz.|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Podporuje [SccGetProjPath](../extensibility/sccgetprojpath-function.md) a příkaz.|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Podporuje [příkaz SccAddFromScc](../extensibility/sccaddfromscc-function.md) a command.|
|`SCC_CAP_COMMENTCHECKOUT`|0x0000800L|Podporuje komentář k pokladně.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Podporuje komentář k vrácení se změnami.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Podporuje komentář k Přidat.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Podporuje komentář k Remove.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Zapisuje text do výstupní funkce poskytované ide.|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Podporuje ukládání souborů bez delt.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Podporuje více historie souborů.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Podporuje porovnání souborů bez rozlišování velkých a malých písmen.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Podporuje porovnání souborů, které ignoruje prázdné znaky.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Podporuje hledání dalších souborů.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Podporuje komentáře k vytvoření projektu.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Podporuje rozdíl ve všech stavech, pokud je pod kontrolou.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Modul plug-in nepodporuje ui pro get, ale IDE může stále volat [SccGet](../extensibility/sccget-function.md).|
|`SCC_CAP_REENTRANT`|0x40000000L|Modul plug-in je reentrant a bezpečné pro přístup z více vláken. Ve verzi 1.0 se nepředpokládalo, že žádné moduly plug-in budou reentrant a bezpečné pro přístup z více vláken. Pokud modul plug-in 1.1 nastaví tento bit, hostitel může otevřít více projektů paralelně.|

## <a name="capability-bits-added-in-version-12"></a>Bity schopností přidané ve verzi 1.2

|Kód schopností|Hodnota|Popis|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Podporuje [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Podporuje [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Podporuje [SccBeginBatch](../extensibility/sccbeginbatch-function.md) a [SccEndBatch](../extensibility/sccendbatch-function.md).|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Podporuje [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Podporuje [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Podporuje více políček na soubor a [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Podporuje soubor *MSSCCPRJ.SCC* (podléhá přepsání uživatelem/správcem) a [soubor SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bity schopností přidané ve verzi 1.3
 Tyto příznaky jsou předávány jeden po druhém [sccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) funkce k určení, zda je podporována funkce.

|Kód rozšířené schopnosti|Hodnota|Popis|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Podporuje `SCC_CHECKOUT_LOCALVER` možnost pro pokladny.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Podporuje [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Podporuje [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Podporuje hledání dalších adresářů.|
|`SCC_EXCAP_QUERYCHANGES`|5|Podporuje výčet změn souborů.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Podporuje [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Podporuje [SccGetUserOption](../extensibility/sccgetuseroption-function.md).|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Podporuje volání SccQueryInfo ve více vláknech.|
|`SCC_EXCAP_REMOVE_DIR`|9|Podporuje funkci SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Může odstranit zasazené soubory.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Můžete přejmenovat zasazené soubory.|

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
