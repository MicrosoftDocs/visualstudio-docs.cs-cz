---
title: Funkce rozhraní API modulu plug-in správy zdrojového kódu | Microsoft Docs
description: Seznamte se s funkcemi, které poskytuje rozhraní API modulu plug-in správy zdrojového kódu, které musí modul plug-in správy zdrojového kódu implementovat.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4f93ddff78aa151218d0b46d017e4631d9489e44
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899599"
---
# <a name="source-control-plug-in-api-functions"></a>Funkce modulu plug-in správy zdrojového kódu v rozhraní API
Rozhraní API modulu plug-in správy zdrojového kódu poskytuje následující funkce, které musí modul plug-in správy zdrojového kódu implementovat v souladu s tímto rozhraním API. Podpisy jednotlivých funkcí a sémantiku přidruženou k bitům a dalším parametrům jsou podrobně popsány v tomto odkazu.

## <a name="initialization-and-housekeeping-functions"></a>Funkce inicializace a správy

|Funkce|Description|
|--------------|-----------------|
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zavře projekt.|
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Vyzve uživatele k zadání rozšířených možností pro daný příkaz.|
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Vrátí verzi modulu plug-in správy zdrojového kódu.|
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializuje modul plug-in správy zdrojového kódu. Volá se jednou pro každou instanci modulu plug-in.|
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Otevře projekt.|
|[SccSetOption](../extensibility/sccsetoption-function.md)|Obecná funkce, která slouží k nastavení široké škály možností. Každá možnost začíná na a `SCC_OPT_xxx` má vlastní definovanou sadu hodnot.|
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Volá se jednou, když je potřeba zrušit připojení modulu plug-in správy zdrojového kódu.|

## <a name="core-source-control-functions"></a>Základní funkce správy zdrojového kódu

|Funkce|Description|
|--------------|-----------------|
|[SccAdd](../extensibility/sccadd-function.md)|Přidá do systému správy zdrojového kódu pole souborů určené plně kvalifikovanými názvy cest.|
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umožňuje uživateli vyhledat soubory, které už jsou v systému správy zdrojového kódu, a potom je nastavit jako součást aktuálního projektu.|
|[SccCheckin](../extensibility/scccheckin-function.md)|Kontroluje pole souborů.|
|[SccCheckout](../extensibility/scccheckout-function.md)|Zkontroluje pole souborů.|
|[SccDiff](../extensibility/sccdiff-function.md)|Ukazuje rozdíly mezi souborem místního uživatele určeným plně kvalifikovaným názvem cesty a verzí ve správy zdrojového kódu.|
|[SccGet](../extensibility/sccget-function.md)|Načte kopii sady souborů jen pro čtení.|
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Zkontroluje stav souborů, na které se volající dotaz (přes `SccQueryInfo` ).|
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Způsobí, že modul plug-in správy zdrojového kódu vyzve uživatele k zadání cesty projektu, která má smysl pro modul plug-in.|
|[SccHistory](../extensibility/scchistory-function.md)|Zobrazuje historii pro pole plně kvalifikovaných místních názvů souborů.|
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Zkontroluje aktuální stav souborů v seznamu. Kromě toho používá funkci k oznámení volajícímu v případě, že soubor neodpovídá `pfnPopulate` kritériím pro `nCommand` .|
|[SccProperties](../extensibility/sccproperties-function.md)|Zobrazí vlastnosti plně kvalifikovaného souboru.|
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Zkontroluje seznam plně kvalifikovaných souborů a zkontroluje jejich aktuální stav.|
|[SccRemove](../extensibility/sccremove-function.md)|Odebere pole plně kvalifikovaných souborů ze systému správy zdrojového kódu.|
|[SccRename](../extensibility/sccrename-function.md)|Přejmenuje daný soubor na nový název v systému správy zdrojového kódu.|
|[SccRunScc](../extensibility/sccrunscc-function.md)|Přistupuje k celé řadě funkcí systému správy zdrojového kódu.|
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Vrátí zpět pokladnu pole souborů.|

## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkce, které podporují další funkce (verze 1.2 rozhraní API modulu plug-in správy zdrojového kódu)
 Tato skupina funkcí definuje další funkce, které jsou součástí rozhraní API modulu plug-in správy zdrojového kódu verze 1.2. Poskytují přístup k pokročilejším funkcím a možnostem správy zdrojového kódu.

|Funkce|Description|
|--------------|-----------------|
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Spustí dávkovou operaci.|
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Vytvoří podprojekt s daným názvem v rámci existujícího nadřazeného projektu.|
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Ukazuje rozdíly mezi adresářem místního uživatele určeným plně kvalifikovaným názvem cesty a umístěním databáze správy zdrojového kódu.|
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Zkontroluje seznam plně kvalifikovaných adresářů a zkontroluje jejich aktuální stav.|
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Ukončí dávkovou operaci.|
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Vrátí nadřazenou cestu daného projektu (projekt musí existovat).|
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Kontroluje, zda je pro soubor povoleno vícenásobné zaškrtnutí.|
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Zkontroluje, jestli modul plug-in vytvoří MSSCCPRJ. Soubory SCC.|

## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkce, které podporují pokročilé funkce (verze 1.3 rozhraní API modulu plug-in správy zdrojového kódu)
 Tato skupina funkcí definuje další funkce, které jsou součástí rozhraní API modulu plug-in správy zdrojového kódu verze 1.3. Poskytují přístup k pokročilejším funkcím a možnostem správy zdrojového kódu.

|Funkce|Description|
|--------------|-----------------|
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Přidá seznam souborů ze správy zdrojového kódu do aktuálního projektu.|
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Načte seznam souborů ze správy zdrojového kódu bez uživatelského rozhraní.|
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Načte seznam souborů ve zdrojovém kódu, které se liší od místních souborů.|
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Načte příznaky, které určují rozšířené možnosti podporované plug-inem správy zdrojového kódu.|
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Načte možnosti specifické pro uživatele.|
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Prozkoumá seznam adresářů a souborů v projektu nebo projektech, které jsou ve zdrojovém kódu. Každý nalezený název adresáře a souboru se předá funkci zpětného volání.|
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Kontroluje změny názvů provedené v seznamu souborů. Každý název souboru je předán funkci zpětného volání s jeho stavem změny.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SCC. h

 (Dodává se ve složce prostředí SDK Common includes ve výchozím nastavení: *[jednotka]* \Program Files\VSIP 8.0 \ EnvSDK\common\inc; také ve složce VSIP s ukázkou MSSCCI *[jednotka]* \Program Files\VSIP 8.0 \ MSSCCI).

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)
