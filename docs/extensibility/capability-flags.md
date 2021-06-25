---
title: Příznaky schopností | Microsoft Docs
description: Přečtěte si o SCC_CAP_xxx, které označují možnosti modulu plug-in správy zdrojového kódu a příznaky SCC_EXCAP_xxx, které označují rozšířené možnosti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, capability flags
ms.assetid: a3f6071c-eac8-4bcd-8ffd-8d0a2d24a252
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3fdb660fd4e7c595f522686280f8bec6c0acae81
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905095"
---
# <a name="capability-flags"></a>Příznaky schopností
Příznaky SCC_CAP_ *xxx* jsou bitové příznaky, které slouží k označení možností modulu plug-in správy zdrojového kódu. Příznaky SCC_EXCAP_ *xxx* jsou přírůstkové příznaky, které označují rozšířené možnosti a přechádují se na celočíselné hodnoty.

|Kód schopností|Hodnota|Popis|
|---------------------|-----------|-----------------|
|`SCC_CAP_REMOVE`|0x00000001L|Podporuje [SccRemove a](../extensibility/sccremove-function.md) příkaz .|
|`SCC_CAP_RENAME`|0x00000002L|Podporuje [SccRename a](../extensibility/sccrename-function.md) příkaz .|
|`SCC_CAP_DIFF`|0x00000004L|Podporuje [SccDiff](../extensibility/sccdiff-function.md) a příkaz .|
|`SCC_CAP_HISTORY`|0x00000008L|Podporuje [SccHistory a](../extensibility/scchistory-function.md) příkaz .|
|`SCC_CAP_PROPERTIES`|0x00000010L|Podporuje [SccProperties](../extensibility/sccproperties-function.md) a příkaz .|
|`SCC_CAP_RUNSCC`|0x00000020L|Podporuje [SccRunScc a](../extensibility/sccrunscc-function.md) příkaz .|
|`SCC_CAP_GETCOMMANDOPTIONS`|0x00000040L|Podporuje [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) a příkaz .|
|`SCC_CAP_QUERYINFO`|0x00000080L|Podporuje [SccQueryInfo a](../extensibility/sccqueryinfo-function.md) příkaz .|
|`SCC_CAP_GETEVENTS`|0x00000100L|Podporuje [SccGetEvents](../extensibility/sccgetevents-function.md) a příkaz .|
|`SCC_CAP_GETPROJPATH`|0x00000200L|Podporuje [SccGetProjPath a](../extensibility/sccgetprojpath-function.md) příkaz .|
|`SCC_CAP_ADDFROMSCC`|0x00000400L|Podporuje [SccAddFromScc](../extensibility/sccaddfromscc-function.md) a příkaz .|
|`SCC_CAP_COMMENTCHECKOUT`|0x00000800L|Podporuje komentář k pokladně.|
|`SCC_CAP_COMMENTCHECKIN`|0x00001000L|Podporuje komentář ke kontrole.|
|`SCC_CAP_COMMENTADD`|0x00002000L|Podporuje komentář na Přidat.|
|`SCC_CAP_COMMENTREMOVE`|0x00004000L|Podporuje komentář u odebrat.|
|`SCC_CAP_TEXTOUT`|0x00008000L|Zapisuje text do výstupní funkce integrovaného vývojového prostředí (IDE).|
|`SCC_CAP_ADD_STORELATEST`|0x00200000L|Podporuje ukládání souborů bez rozdílů.|
|`SCC_CAP_HISTORY_MULTFILE`|0x00400000L|Podporuje historii více souborů.|
|`SCC_CAP_IGNORECASE`|0x00800000L|Podporuje porovnání souborů bez rozlišení velkých a malých písmen.|
|`SCC_CAP_IGNORESPACE`|0x01000000L|Podporuje porovnání souborů, které ignoruje prázdné znaky.|
|`SCC_CAP_POPULATELIST`|0x02000000L|Podporuje hledání dalších souborů.|
|`SCC_CAP_COMMENTPROJECT`|0x04000000L|Podporuje komentáře k vytvoření projektu.|
|`SCC_CAP_DIFFALWAYS`|0x10000000L|Podporuje rozdíl ve všech stavech, pokud je pod kontrolou.|
|`SCC_CAP_GET_NOUI`|0x20000000L|Modul plug-in nepodporuje uživatelské rozhraní pro Get, ale integrované vývojové prostředí může stále volat [SccGet.](../extensibility/sccget-function.md)|
|`SCC_CAP_REENTRANT`|0x40000000L|Modul plug-in je reentrant a bezpečný pro vlákno. Ve verzi 1.0 se předpokládá, že žádné moduly plug-in nejsou reentrant a bezpečné pro přístup z více vláken. Pokud modul plug-in 1.1 nastaví tento bit, hostitel může souběžně otevřít více projektů.|

## <a name="capability-bits-added-in-version-12"></a>Bity schopností přidané ve verzi 1.2

|Kód schopností|Hodnota|Popis|
|---------------------|-----------|-----------------|
|`SCC_CAP_CREATESUBPROJECT`|0x00010000L|Podporuje [SccCreateSubProject](../extensibility/scccreatesubproject-function.md).|
|`SCC_CAP_GETPARENTPROJECT`|0x00020000L|Podporuje [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).|
|`SCC_CAP_BATCH`|0x00040000L|Podporuje [SccBeginBatch](../extensibility/sccbeginbatch-function.md) a [SccEndBatch.](../extensibility/sccendbatch-function.md)|
|`SCC_CAP_DIRECTORYSTATUS`|0x00080000L|Podporuje [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md).|
|`SCC_CAP_DIRECTORYDIFF`|0x00100000L|Podporuje [SccDirDiff](../extensibility/sccdirdiff-function.md).|
|`SCC_CAP_MULTICHECKOUT`|0x08000000L|Podporuje více checkoutů pro soubor a [SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md).|
|`SCC_CAP_SCCFILE`|0x80000000L|Podporuje soubor *MSSCCPRJ.SCC* (v závislosti na přepsání uživatelem nebo správcem) a [soubor SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md).|

## <a name="capability-bits-added-in-version-13"></a>Bity schopností přidané ve verzi 1.3
 Tyto příznaky se předá funkci [SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md) po jednom, aby určila, jestli je funkce podporovaná.

|Kód rozšířených schopností|Hodnota|Popis|
|------------------------------|-----------|-----------------|
|`SCC_EXCAP_CHECKOUT_LOCALVER`|1|Podporuje `SCC_CHECKOUT_LOCALVER` možnost pro pokladny.|
|`SCC_EXCAP_BACKGROUND_GET`|2|Podporuje [SccBackgroundGet](../extensibility/sccbackgroundget-function.md).|
|`SCC_EXCAP_ENUM_CHANGED_FILES`|3|Podporuje [SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md).|
|`SCC_EXCAP_POPULATELIST_DIR`|4|Podporuje hledání dalších adresářů.|
|`SCC_EXCAP_QUERYCHANGES`|5|Podporuje vytváření výčtu změn souborů.|
|`SCC_EXCAP_ADD_FILES_FROM_SCC`|6|Podporuje [SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md).|
|`SCC_EXCAP_GET_USER_OPTIONS`|7|Podporuje [SccGetUserOption.](../extensibility/sccgetuseroption-function.md)|
|`SCC_EXCAP_THREADSAFE_QUERY_INFO`|8|Podporuje volání SccQueryInfo ve více vláknech.|
|`SCC_EXCAP_REMOVE_DIR`|9|Podporuje funkci SccRemoveDir.|
|`SCC_EXCAP_DELETE_CHECKEDOUT`|10|Může odstranit soubory s rezervování.|
|`SCC_EXCAP_RENAME_CHECKEDOUT`|11|Může přejmenovat soubory s rezervování.|

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
