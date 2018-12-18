---
title: Zdroj modulu Plug-in API funkce ovládacího prvku | Dokumentace Microsoftu
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
- source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5dcb07c3c49b132cdf12c1a4973af3ebf04dfa74
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796776"
---
# <a name="source-control-plug-in-api-functions"></a>Funkce modulu plug-in správy zdrojového kódu v rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozhraní API modulu Plug-in zdroje ovládacího prvku poskytuje následující funkce, které musí být implementované v souladu se toto rozhraní API modulu plug-in správy zdrojového kódu. Podpisy jednotlivých funkcí a sémantika přidružené bitové příznaky a další parametry jsou podrobně popsané v této referenční dokumentaci.  
  
## <a name="initialization-and-housekeeping-functions"></a>Inicializace a údržbu funkce  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|Zavření projektu.|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|Vyzve uživatele k rozšířené možnosti pro daný příkaz.|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|Vrátí verzi objektu správy zdrojového kódu modulu plug-in.|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|Inicializuje modul plug-in správy zdrojového kódu. Se volá jednou pro každou instanci modulu plug-in.|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|Otevře se projekt.|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|Obecná funkce lze nastavit celou řadu možností. Jednotlivé možnosti začíná `SCC_OPT_xxx` a má vlastní definované sady hodnot.|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|Volá se, až když plug-in správy zdrojových kódů musí být odpojen.|  
  
## <a name="core-source-control-functions"></a>Základní funkce ovládacího prvku zdroje  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|Přidá pole soubory určené názvy plně kvalifikovanou cestu k systému správy zdrojového kódu.|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|Umožňuje uživateli procházet soubory, které jsou již v systému správy zdrojového kódu a pak proveďte tyto soubory součástí aktuálního projektu.|  
|[SccCheckin](../extensibility/scccheckin-function.md)|Pole souborů se změnami.|  
|[SccCheckout](../extensibility/scccheckout-function.md)|Rezervuje soubory pole.|  
|[SccDiff](../extensibility/sccdiff-function.md)|Jsou uvedeny rozdíly mezi místní uživatel soubor určený parametrem na plně kvalifikovaný název cesty a verze pod správou zdrojových kódů.|  
|[SccGet](../extensibility/sccget-function.md)|Načte kopii sady souborů jen pro čtení.|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|Kontroluje stav soubory, které volající požádal o (prostřednictvím `SccQueryInfo`).|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|Způsobí, že plug-in požádat uživatele o cestu k projektu, který má smysl v modulu plug-in správy zdrojových kódů.|  
|[SccHistory](../extensibility/scchistory-function.md)|Zobrazí historii pole názvů plně kvalifikovaný místního souboru.|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|Zkontroluje seznam souborů pro jejich aktuální stav. Kromě toho používá `pfnPopulate` funkce oznámit volajícímu, soubor neodpovídá kritériím pro `nCommand`.|  
|[SccProperties](../extensibility/sccproperties-function.md)|Zobrazí vlastnosti úplný soubor.|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|Zkontroluje seznam plně kvalifikovaných souborů pro jejich aktuální stav.|  
|[SccRemove](../extensibility/sccremove-function.md)|Pole plně kvalifikovaný souborů, které odebere ze systému správy zdrojového kódu.|  
|[SccRename](../extensibility/sccrename-function.md)|Daný soubor přejmenuje na nový název v systému správy zdrojového kódu.|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|Přistupuje k plný rozsah funkcí systému správy zdrojového kódu.|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|Zruší rezervaci pole souborů.|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>Funkce, které podporují další možnosti (rozhraní API modulu Plug-in zdroje ovládacího prvku verze 1.2)  
 Tato skupina funkce definuje další funkce, které jsou zahrnuté ve verzi 1.2 rozhraní API modulu Plug-in zdroje ovládacího prvku. Poskytují přístup k rozšířené funkce správy zdrojového kódu a možnosti.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|Spustí dávkovou operaci.|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|Vytvoří dílčí projekt s daným názvem v existujícím projektu nadřazené.|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|Jsou uvedeny rozdíly mezi určené plně kvalifikovanou cestu název a umístění databáze správy zdrojového adresáře místního uživatele.|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|Zkontroluje seznam plně kvalifikovaných adresářů pro jejich aktuální stav.|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|Ukončí operaci služby batch.|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|Vrátí nadřazený cestu daného projektu (musí existovat projektu).|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|Kontroluje, zda je povoleno více rezervace souboru.|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|Kontroluje, zda modul plug-in se vytvoří MSSCCPRJ. Soubory SCC.|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>Funkce, které podporují pokročilé možnosti (rozhraní API modulu Plug-in zdroje ovládacího prvku verze 1.3)  
 Tato skupina funkce definuje další funkce, která je součástí verze 1.3 rozhraní API modulu Plug-in zdroje ovládacího prvku. Poskytují přístup k rozšířené funkce správy zdrojového kódu a možnosti.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|Seznam souborů ze správy zdrojového kódu přidá do aktuálního projektu.|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|Načte seznam souborů ze správy zdrojového kódu bez uživatelského rozhraní.|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|Načte seznam souborů ve správě zdrojového kódu, které se liší od místních souborů.|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|Získá příznaky určující rozšířené možnosti podporuje modul plug-in správy zdrojového kódu.|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|Načte možnosti specifické pro uživatele.|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|Zkontroluje seznam adresářů a souborů v projektu nebo v projektech, které jsou pod správou zdrojových kódů. Každý název adresáře a souboru nalezena je předán funkci zpětného volání.|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|Prozkoumá název změny provedené v seznamu souborů. Každý název souboru je předán funkci zpětného volání s jeho změna stavu.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: scc.h  
  
 (Zadaná v sadě SDK prostředí společná zahrnují složku, ve výchozím nastavení *[jednotka]* \Program Files\VSIP 8.0\EnvSDK\common\inc; rovněž dodán v programu VSIP složky s ukázkou MSSCCI *[jednotka]* \Program Files\VSIP 8.0\MSSCCI).  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek moduly plug-in zdrojového kódu](../extensibility/source-control-plug-ins.md)   
 [Vytvoření modulu plug-in správy zdrojového kódu](../extensibility/internals/creating-a-source-control-plug-in.md)

