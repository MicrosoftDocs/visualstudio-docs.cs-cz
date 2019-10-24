---
title: Funkce rozhraní API modulu plug-in správy zdrojových kódů | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57e451ebb4693e7742208ab6a375fa7d50563a17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719900"
---
# <a name="source-control-plug-in-api-functions"></a>Funkce modulu plug-in správy zdrojového kódu v rozhraní API
Rozhraní API modulu plug-in správy zdrojových kódů poskytuje následující funkce, které musí být implementovány modulem plug-in správy zdrojových kódů v souladu s tímto rozhraním API. Signatury každé funkce a sémantiky přidružené k bitovým příznakům a dalším parametrům jsou podrobněji popsány v tomto odkazu.

## <a name="initialization-and-housekeeping-functions"></a>Inicializační a údržbu funkce

|Funkce|Popis|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zavře projekt.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Vyzve uživatele k zadání pokročilých možností pro daný příkaz.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Vrátí verzi modulu plug-in správy zdrojových kódů.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializuje modul plug-in správy zdrojových kódů. Je volána jednou pro každou instanci modulu plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Otevře projekt.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Obecná funkce používaná k nastavení široké škály možností. Každá možnost začíná na `SCC_OPT_xxx` a má svou vlastní definovanou sadu hodnot.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Volá se jednou, když je potřeba odpojit modul plug-in správy zdrojových kódů.|

## <a name="core-source-control-functions"></a>Základní funkce správy zdrojového kódu

|Funkce|Popis|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Přidá pole souborů určené plně kvalifikovanými názvy cest do systému správy zdrojového kódu.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umožňuje uživateli vyhledat soubory, které jsou již v systému správy zdrojů, a poté tyto soubory zpřístupnit v rámci aktuálního projektu.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Kontroluje v poli souborů.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Rezervuje pole souborů.|
|[SccDiff](../extensibility/sccdiff-function.md)|Zobrazuje rozdíly mezi souborem místního uživatele zadaným pomocí plně kvalifikovaného názvu cesty a verze v rámci správy zdrojového kódu.|
|[SccGet](../extensibility/sccget-function.md)|Načte kopii sady souborů určenou jen pro čtení.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Kontroluje stav souborů, o kterých volající požadoval (prostřednictvím `SccQueryInfo`).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Způsobí, že modul plug-in správy zdrojových kódů vyzve uživatele k zadání cesty projektu, která má smysl pro modul plug-in.|
|[SccHistory](../extensibility/scchistory-function.md)|Zobrazuje historii pole plně kvalifikovaných místních názvů souborů.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Prověřuje seznam souborů pro jejich aktuální stav. Kromě toho používá funkci `pfnPopulate` k upozorňování volajícího, když soubor neodpovídá kritériím pro `nCommand`.|
|[SccProperties](../extensibility/sccproperties-function.md)|Zobrazuje vlastnosti plně kvalifikovaného souboru.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Prověřuje seznam plně kvalifikovaných souborů pro jejich aktuální stav.|
|[SccRemove](../extensibility/sccremove-function.md)|Odebere pole plně kvalifikovaných souborů ze systému správy zdrojů.|
|[SccRename](../extensibility/sccrename-function.md)|Přejmenuje daný soubor na nový název v systému správy zdrojového kódu.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Přistupuje k celé škále funkcí systému správy zdrojového kódu.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Vrátí rezervaci pole souborů.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkce, které podporují další možnosti (verze 1,2 rozhraní API modulu plug-in správy zdrojového kódu)
 Tato skupina funkcí definuje další funkce zahrnuté ve verzi 1,2 rozhraní API modulu plug-in správy zdrojového kódu. Poskytují přístup k pokročilejším funkcím a možnostem správy zdrojového kódu.

|Funkce|Popis|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Spustí dávkovou operaci.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Vytvoří dílčí projekt se zadaným názvem v rámci existujícího nadřazeného projektu.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Zobrazuje rozdíly mezi adresářem místního uživatele, který je určený plně kvalifikovaným názvem cesty a umístěním databáze správy zdrojového kódu.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Prověřuje seznam plně kvalifikovaných adresářů pro jejich aktuální stav.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Ukončí operaci Batch.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Vrátí nadřazenou cestu daného projektu (projekt musí existovat).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Kontroluje, zda je povoleno více rezervací souboru.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Ověří, jestli modul plug-in vytvoří MSSCCPRJ. Soubory SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkce, které podporují pokročilou funkci (verze 1,3 rozhraní API modulu plug-in správy zdrojového kódu)
 Tato skupina funkcí definuje další funkce zahrnuté ve verzi 1,3 rozhraní API modulu plug-in správy zdrojového kódu. Poskytují přístup k pokročilejším funkcím a možnostem správy zdrojového kódu.

|Funkce|Popis|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Přidá do aktuálního projektu seznam souborů ze správy zdrojového kódu.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Načte seznam souborů ze správy zdrojového kódu bez uživatelského rozhraní.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Načte seznam souborů ve správě zdrojového kódu, které se liší od místních souborů.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Načte příznaky, které určují rozšířené možnosti podporované modulem plug-in správy zdrojových kódů.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Načte možnosti specifické pro uživatele.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Prověřuje seznam adresářů a souborů v projektu nebo projektech, které jsou pod správou zdrojových kódů. Každý nalezený adresář a název souboru se předává funkci zpětného volání.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Kontroluje změny názvů provedené v seznamu souborů. Každý název souboru je předán funkci zpětného volání s jeho stavem změny.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SCC. h

 (Dodává se ve složce prostředí SDK Common includes ve výchozím nastavení: *[jednotka]* \Program Files\VSIP 8.0 \ EnvSDK\common\inc; také ve složce VSIP s ukázkou MSSCCI *[jednotka]* \Program Files\VSIP 8.0 \ MSSCCI).

## <a name="see-also"></a>Viz také:
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)