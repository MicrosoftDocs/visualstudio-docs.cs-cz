---
title: Funkce modulu Plug-in rozhraní API ovládacího prvku zdroje | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a834c4352ea2444c2669a57f760ed373999b07dd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144366"
---
# <a name="source-control-plug-in-api-functions"></a>Funkce modulu Plug-in rozhraní API ovládacího prvku zdroje
Rozhraní API ovládacího prvku Plug-in Zdroj poskytuje následující funkce, které musí být implementované v souladu s toto rozhraní API modulu plug-in zdrojového kódu. Podpisy jednotlivé funkce a sémantiky přidružené bitové příznaky a další parametry jsou podrobně popsané v této referenci.  
  
## <a name="initialization-and-housekeeping-functions"></a>Inicializace a Housekeeping funkce  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zavře projektu.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Vyzve uživatele k rozšířené možnosti pro daný příkaz.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Vrátí verzi zdrojového kódu modulu plug-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializuje modul plug-in zdrojového kódu. Volá se jednou pro každou instanci modulu plug-in.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Otevře se projektu.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Obecné funkce, používá se k nastavení širokou škálu možností. Každá možnost začíná `SCC_OPT_xxx` a má svou vlastní definované sady hodnot.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Volá se poté, kdy modul plug-in správy zdroje musí být odpojené.|  
  
## <a name="core-source-control-functions"></a>Funkce základní zdroj ovládacího prvku  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Přidá pole soubory zadané názvy plně kvalifikovanou cestu do správy zdrojového kódu.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umožňuje uživatelům procházet soubory, které jsou již v systému správy zdrojů a pak proveďte tyto soubory součástí aktuálního projektu.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Kontroluje v matici souborů.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Zkontrolujte pole souborů.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Jsou uvedeny rozdíly mezi místní uživatele soubor určený touto plně kvalifikovanou cestu název a verze ve správě zdrojového kódu.|  
|[SccGet](../extensibility/sccget-function.md)|Načte kopii sady souborů jen pro čtení.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Kontroluje stav souborů, které volající požádal o (prostřednictvím `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Způsobí, že modul plug-in pro vyzvání uživatele pro cestu k projektu, který má smysl v modulu plug-in zdrojového kódu.|  
|[SccHistory](../extensibility/scchistory-function.md)|Zobrazí historii pole názvů plně kvalifikovaný místního souboru.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Prozkoumá seznam souborů pro jejich aktuální stav. Kromě toho používá `pfnPopulate` funkce, které oznámí souboru neodpovídá kritériím pro volající `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Zobrazuje vlastnosti plně kvalifikovaný souboru.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Prozkoumá seznam plně kvalifikovaný souborů pro jejich aktuální stav.|  
|[SccRemove](../extensibility/sccremove-function.md)|Odebere pole plně kvalifikovaný soubory ze správy zdrojového kódu.|  
|[SccRename](../extensibility/sccrename-function.md)|Daný soubor přejmenuje na nový název v systému správy zdrojů.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Přístup k plný rozsah funkcí správy zdrojového kódu.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Vrátí zpět rezervaci pole souborů.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkce, které podporují další schopnosti (verze 1.2 rozhraní API modulu Plug-in řízení zdroje)  
 Tato skupina funkcí definuje další funkce, které jsou součástí verze 1.2 rozhraní API ovládacího prvku Plug-in zdroje. Poskytuje přístup k dalších pokročilých funkcí správy zdrojového kódu a možnosti.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Spustí dávkovou operaci.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Vytvoří dílčí projekt s daným názvem. v části existující nadřazený projekt.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Jsou uvedeny rozdíly mezi místní uživatele adresář zadaný název plně kvalifikovanou cestu a zdrojovým umístěním databáze ovládacího prvku.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Prozkoumá seznam plně kvalifikovaný adresářů pro jejich aktuální stav.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Ukončí dávkové operace.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Vrátí nadřazená cesta daného projektu (musí existovat projekt).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Kontroluje, zda je povoleno více rezervace na soubor.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Kontroluje, zda modul plug-in vytvoří MSSCCPRJ. SCC soubory.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkce, které podporují pokročilé schopnosti (verze 1.3 rozhraní API modulu Plug-in řízení zdroje)  
 Tato skupina funkcí definuje další funkce, které jsou součástí 1.3 verzi rozhraní API ovládacího prvku Plug-in zdroje. Poskytuje přístup k dalších pokročilých funkcí správy zdrojového kódu a možnosti.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Seznam souborů, od správy zdrojového kódu se přidá do aktuálního projektu.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Načte seznam souborů, od správy zdrojového kódu bez uživatelského rozhraní.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Načte seznam souborů ve správě zdrojového kódu, které se liší od místních souborů.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Načte příznaky, které určují rozšířené možnosti, které podporuje modul plug-in zdrojového kódu.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Načte možnosti specifické pro uživatele.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Prozkoumá seznam adresářů a souborů v projektu nebo projektů, které jsou v části Správa zdrojového kódu. Každý název adresáře a souboru nalezen předaný funkci zpětného volání.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Prozkoumá název změny provedené v seznamu souborů. Každý název souboru je předaný funkci zpětného volání s jeho změnu stavu.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: scc.h  
  
 (Zadaný v sadě SDK prostředí běžné zahrnuje složku, ve výchozím nastavení *[jednotka]* \Program Files\VSIP 8.0\EnvSDK\common\inc; také zadaný ve složce VSIP s ukázkou MSSCCI *[jednotka]* \Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in programu zdroj ovládacího prvku](../extensibility/source-control-plug-ins.md)   
 [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)