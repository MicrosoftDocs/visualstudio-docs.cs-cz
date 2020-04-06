---
title: Funkce rozhraní API pro slučovací modul správy dat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce685729dda8750d772e244398b736cff4951b72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699925"
---
# <a name="source-control-plug-in-api-functions"></a>Funkce modulu plug-in správy zdrojového kódu v rozhraní API
Rozhraní plug-in správy zdrojového kódu poskytuje následující funkce, které musí být implementovány modulem plug-in správy zdrojového kódu v souladu s tímto rozhraním API. Podpisy každé funkce a sémantiku spojenou s bitovými příznaky a dalšími parametry jsou podrobně popsány v tomto odkazu.

## <a name="initialization-and-housekeeping-functions"></a>Inicializační a úklidové funkce

|Funkce|Popis|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zavře projekt.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Zobrazí uživateli výzvu k zadání rozšířených možností pro daný příkaz.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Vrátí verzi modulu plug-in správy zdrojového kódu.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializuje modul plug-in modul pro řízení zdrojového kódu. Je volána jednou pro každou instanci modulu plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Otevře projekt.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Obecná funkce používaná k nastavení široké škály možností. Každá možnost `SCC_OPT_xxx` začíná a má vlastní definovanou sadu hodnot.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Volána jednou, když je třeba odpojit modul plug-in správy zdrojového kódu.|

## <a name="core-source-control-functions"></a>Základní funkce správy zdrojového kódu

|Funkce|Popis|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Přidá do systému správy zdrojového kódu pole souborů určených plně kvalifikovanými názvy cest.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umožňuje uživateli procházet soubory, které jsou již v systému správy zdrojového kódu a potom tyto soubory součástí aktuálního projektu.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Vrátí se změnami v poli souborů.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Rezervuje pole souborů.|
|[SccDiff](../extensibility/sccdiff-function.md)|Zobrazuje rozdíly mezi souborem místního uživatele určeným plně kvalifikovaným názvem cesty a verzí pod správu zdrojového kódu.|
|[SccGet](../extensibility/sccget-function.md)|Načte kopii sady souborů jen pro čtení.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Zkontroluje stav souborů, na které se `SccQueryInfo`volající ptal (prostřednictvím).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Způsobí, že modul plug-in správy zdrojového kódu vyzve uživatele k cestě projektu, která má smysl pro modul plug-in.|
|[SccHistory](../extensibility/scchistory-function.md)|Zobrazuje historii pole plně kvalifikovaných názvů místních souborů.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Zkontroluje seznam souborů pro jejich aktuální stav. Kromě toho používá `pfnPopulate` funkci upozornit volajícího, pokud soubor neodpovídá `nCommand`kritériím pro .|
|[SccProperties](../extensibility/sccproperties-function.md)|Zobrazuje vlastnosti plně kvalifikovaného souboru.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Zkontroluje seznam plně kvalifikovaných souborů pro jejich aktuální stav.|
|[SccRemove](../extensibility/sccremove-function.md)|Odebere pole plně kvalifikovaných souborů ze systému správy zdrojového kódu.|
|[SccRename](../extensibility/sccrename-function.md)|Přejmenuje daný soubor na nový název v systému správy zdrojového kódu.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Přistupuje k celé řadě funkcí systému správy zdrojového kódu.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Vrácení pokladny pole souborů.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkce, které podporují další funkce (verze 1.2 rozhraní plug-in správy zdrojového kódu)
 Tato skupina funkcí definuje další funkce obsažené ve verzi 1.2 rozhraní plug-in správy zdrojového kódu. Poskytují přístup k pokročilejším funkcím a funkcím správy zdrojového kódu.

|Funkce|Popis|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Spustí dávkovou operaci.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Vytvoří dílčí projekt s daným názvem pod existujícím nadřazeným projektem.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Zobrazuje rozdíly mezi adresářem místního uživatele určeným plně kvalifikovaným názvem cesty a umístěním databáze správy zdrojového kódu.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Zkontroluje seznam plně kvalifikovaných adresářů pro jejich aktuální stav.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Ukončí dávkovou operaci.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Vrátí nadřazenou cestu daného projektu (projekt musí existovat).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Zkontroluje, zda je povoleno více povýběrů v souboru.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Zkontroluje, zda modul plug-in vytvoří MSSCCPRJ. SCC soubory.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkce, které podporují pokročilé funkce (verze 1.3 rozhraní plug-in source control)
 Tato skupina funkcí definuje další funkce obsažené ve verzi 1.3 rozhraní plug-in správy zdrojového kódu. Poskytují přístup k pokročilejším funkcím a funkcím správy zdrojového kódu.

|Funkce|Popis|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Přidá seznam souborů ze správy zdrojového kódu do aktuálního projektu.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Načte seznam souborů ze správy zdrojového kódu bez uživatelského rozhraní.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Načte seznam souborů ve zdrojovém ovládacím prvku, které se liší od místních souborů.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Načte příznaky, které určují rozšířené možnosti podporované modulem plug-in správy zdrojového kódu.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Načte možnosti specifické pro uživatele.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Zkontroluje seznam adresářů a souborů v projektu nebo projekty, které jsou pod smytem zdrojového kódu. Každý nalezený adresář a název souboru je předán funkci zpětného volání.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Zkontroluje změny názvu provedené v seznamu souborů. Každý název souboru je předán funkci zpětného volání s jeho stavem změny.|

## <a name="requirements"></a>Požadavky
 Záhlaví: scc.h

 (Součástí sady Environment SDK common obsahuje složku , ve výchozím nastavení *[jednotka]* \Program Files\VSIP 8.0\EnvSDK\common\inc; také dodávané ve složce VSIP s ukázkou MSSCCI, *[jednotka]* \Program Files\VSIP 8.0\MSSCCI).

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)
