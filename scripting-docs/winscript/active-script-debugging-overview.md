---
title: Přehled ladění aktivních skriptů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8624c1405931edefe2e1e53e579ad28a7b238f1
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220219"
---
# <a name="active-script-debugging-overview"></a>Přehled ladění aktivních skriptů
Rozhraními aktivního ladění skriptu povolit ladění jazykově neutrální, nezávislá na hostitele a podporují širokou škálu vývojových prostředích.  
  
 ![Skript hostitelský proces](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Obrázek 1  
  
 Ladění prostředí neutrální jazyk podporuje libovolný programovací jazyk nebo směs programovacích jazyků, aniž by bylo specifické znalosti některý z těchto jazyků. Ladicí prostředí podporuje také krokování mezi jazyky a zarážky. (Tento přehled se zaměřují hlavně na podporu skriptovacích jazyků, jako jsou VBScript a [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].)  
  
 Ladicí program nezávislá na hostitele je možné automaticky s jakýmkoli hostitelem aktivní skriptování, jako je například Internet Explorer nebo vlastního hostitele. Hostitel řídí, co ladicí program se uživateli zobrazí, z strukturu stromu dokumentu k obsahu a barevné zvýrazňování syntaxe dokumentů ladění. To umožňuje ladění zdrojový kód zobrazený v kontextu hostitelský dokument. Například Internet Exploreru můžete zobrazit skript na stránce HTML.  
  
 V podčásti níže jsou popsány každý klíčovou součástí aktivního ladění a jeho přidružené rozhraní. Nicméně než budete pokračovat, musí být definován několik klíčových konceptů aktivního ladění:  
  
 **Hostitelské aplikace**  
 Aplikace, který je hostitelem skriptu strojům a poskytuje skriptovatelný sadu objektů (nebo "object model").  
  
 **modul jazyka**  
 Komponenta, která poskytuje analýzu, spuštění a ladění abstrakce pro konkrétní jazyk.  
  
 **ladicí program integrovaného vývojového prostředí**  
 Aplikace, která poskytuje ladění uživatelského rozhraní tím, že komunikuje s hostiteli aplikace a jazyk moduly.  
  
 **Správce ladění počítač** komponenty, která udržuje registr laditelné aplikace zpracovává.  
  
 **Správce ladění procesu**  
 Komponenta, která udržuje stromu laditelné dokumenty pro konkrétní aplikaci, sleduje běžící vlákna a tak dále.  
  
 **Kontext dokumentu**  
 Kontext dokumentu je abstrakcí představující konkrétní rozsah ve zdrojovém kódu hostitelský dokument.  
  
 **Kontext kódu**  
 Kontext kódu představuje určité místo v spuštěním kódu modulu jazyka ("virtuální instrukce ukazatel".)  
  
 **místní výraz**  
 Konkrétním kontextu (například rámec zásobníku) ve kterém může být výrazy vyhodnoceny pomocí modulu jazyka.  
  
 **procházení objektů**  
 Strukturovaná, nezávislým na jazyku reprezentace objektu název, typ, hodnotu a dílčí objekty, které jsou vhodné pro implementaci "okna kukátka" uživatelské rozhraní.  
  
 Níže je uveden přehled jednotlivých klíčových komponent aktivního ladění a odpovídající, přidružené rozhraní, za nímž následuje podrobnosti o těchto rozhraní.  
  
## <a name="language-engine"></a>Modul jazyka  
 Modul jazyka poskytuje:  
  
- Jazyk parsování a spuštění.  
  
- Podpora ladění (zarážky a tak dále).  
  
- Vyhodnocení výrazu.  
  
- Barevné zvýrazňování syntaxe.  
  
- Objekt, procházení.  
  
- Výčet zásobníku a analýzu.  
  
  V následující tabulce jsou rozhraní, která skriptovací stroj musí podporovat poskytnout, ladění, vyhodnocení výrazu a procházení objektů. Tato rozhraní jsou používány hostitelskou aplikaci mapování mezi jeho kontext dokumentu a kontexty kód stroje, také pomocí ladicího programu uživatelského rozhraní provést vyhodnocení výrazu zásobníku výčtu a objekt procházení.  
  
  [IActiveScriptDebug – rozhraní](../winscript/reference/iactivescriptdebug-interface.md)  
  Poskytuje kontext výčtu syntaxe barevné zvýrazňování a kódu.  
  
  [IActiveScriptErrorDebug – rozhraní](../winscript/reference/iactivescripterrordebug-interface.md)  
  Vrátí dokumentu kontextů a rámce zásobníku pro chyby.  
  
  [IActiveScriptSiteDebug – rozhraní](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Hostitel zadaný odkaz z skriptovací stroj do ladicího programu.  
  
  [IDebugCodeContext – rozhraní](../winscript/reference/idebugcodecontext-interface.md)  
  Poskytuje virtuální "ukazatele na instrukci" ve vlákně.  
  
  [IEnumDebugCodeContexts – rozhraní](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Vytvoří výčet kontexty kódu, které odpovídají kontextu dokumentu.  
  
  [IDebugStackFrame – rozhraní](../winscript/reference/idebugstackframe-interface.md)  
  Představuje rámec zásobníku logického zásobníku vlákna.  
  
  [IDebugExpressionContext – rozhraní](../winscript/reference/idebugexpressioncontext-interface.md)  
  Poskytuje kontext, ve kterém můžete vyhodnotit výrazy.  
  
  [IDebugStackFrameSniffer – rozhraní](../winscript/reference/idebugstackframesniffer-interface.md)  
  Poskytuje způsob, jak vytvořit výčet logického zásobníku.  
  
  [IDebugExpression – rozhraní](../winscript/reference/idebugexpression-interface.md)  
  Představuje asynchronně vyhodnocený výraz.  
  
  [IDebugSyncOperation – rozhraní](../winscript/reference/idebugsyncoperation-interface.md)  
  Povoluje skriptovací stroj abstraktní operace, kterou je potřeba provést v průběhu vnořené v konkrétní vlákno blokované.  
  
  [IDebugAsyncOperation – rozhraní](../winscript/reference/idebugasyncoperation-interface.md)  
  Poskytuje asynchronní přístup k ladění synchronní operace.  
  
  [IDebugAsyncOperationCallBack – rozhraní](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Poskytuje stav události související s průběh `IDebugAsyncOperation` rozhraní hodnocení.  
  
  [IEnumDebugExpressionContexts – rozhraní](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Vytvoří výčet kolekce `IDebugExpressionContexts` objekty.  
  
  [IProvideExpressionContexts – rozhraní](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Poskytuje způsob, jak vytvořit výčet výraz kontexty známé určitá komponenta.  
  
  [IDebugFormatter – rozhraní](../winscript/reference/idebugformatter-interface.md)  
  Umožňuje jazyk nebo integrované vývojové prostředí přizpůsobit převod mezi hodnotami VARIANT nebo VARTYPE typy a řetězci.  
  
  [IDebugStackFrameSnifferEx – rozhraní](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Vytváří výčet rámců logického zásobníku pro PDM.  
  
## <a name="hosts"></a>Hostitelé  
 Hostitel:  
  
- Hostuje moduly jazyka.  
  
- Poskytuje objektový model (sadu objektů, které mohou být skripty).  
  
- Definuje strom dokumentů, které lze ladit a jejich obsah.  
  
- Slouží k uspořádání skripty do virtuální aplikace.  
  
  Existují dva typy hostitelů:  
  
- Vlečný hostitel podporuje pouze základní aktivní skriptování rozhraní. Nemá žádnou kontrolu nad tím strukturu dokumentu nebo organizace; Toto je určeno zcela skripty pro moduly jazyka.  
  
- Inteligentního hostitele podporuje větší sadu rozhraní, které umožňuje definovat stromu dokumentu, obsah dokumentu a barevné zvýrazňování syntaxe. Je sada rozhraní pomocné rutiny, je popsáno v následující podčásti, které bylo mnohem snazší pro hostitele inteligentního hostitele.  
  
### <a name="smart-host-helper-interfaces"></a>Smart-host pomocných rozhraní  
 `IDebugDocumentHelper` Metody poskytují výrazně zjednodušeným sadu rozhraní, můžete získat výhody smart hostování bez zpracování úplné složitost (a napájení) úplné hostitele rozhraní hostitele.  
  
 Hostitel není potřeba samozřejmě použití těchto rozhraní. Ale pomocí těchto rozhraní se můžete vyhnout implementace nebo s počtem složitější rozhraní.  
  
 [IDebugDocumentHelper – rozhraní](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implementováno komponentou PDM a poskytuje implementaci pro mnoho rozhraní nutná pro inteligentní hostování.  
  
 [IDebugDocumentHost – rozhraní](../winscript/reference/idebugdocumenthost-interface.md)  
 (Volitelně) implementované hostitele ke zveřejnění funkce specifické pro hostitele, třeba barevné zvýrazňování, ladicí program syntaxe.  
  
 Další informace najdete v tématu [implementace pomocných rozhraní ke inteligentního hostitele](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Rozhraní úplné Smart hostitele  
 Níže je kompletní sadu rozhraní, která smart hostitel musí implementovat nebo použijte, pokud nepoužívá rozhraní pomocné rutiny.  
  
 Rozhraní implementovaná hostitele:  
  
 [IDebugDocumentInfo – rozhraní](../winscript/reference/idebugdocumentinfo-interface.md)  
 Obsahuje informace o dokumentu, který může nebo nemusí být vytvořena.  
  
 [IDebugDocumentProvider – rozhraní](../winscript/reference/idebugdocumentprovider-interface.md)  
 Poskytuje prostředky pro vytvoření instance dokumentu na vyžádání.  
  
 [IDebugDocument – rozhraní](../winscript/reference/idebugdocument-interface.md)  
 Základní rozhraní pro všechny dokumenty ladění.  
  
 [IDebugDocumentText – rozhraní](../winscript/reference/idebugdocumenttext-interface.md)  
 Poskytuje přístup k verzi dokumentu ladění prostého textu.  
  
 [IDebugDocumentTextAuthor – rozhraní](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Povolí úpravy jen textovou verzi dokumentu ladění.  
  
 [IDebugDocumentContext – rozhraní](../winscript/reference/idebugdocumentcontext-interface.md)  
 Poskytuje abstraktní reprezentace část dokumentu, který se právě ladí.  
  
 Rozhraní je implementováno komponentou PDM jménem hostitele:  
  
 [IDebugApplicationNode – rozhraní](../winscript/reference/idebugapplicationnode-interface.md)  
 Rozšiřuje funkce `IDebugDocumentProvider` rozhraní tím, že poskytuje kontext v rámci stromu projektu.  
  
## <a name="debugger-ide"></a>Ladicí program integrovaného vývojového prostředí  
 Rozhraní IDE je nezávislým na jazyku ladění uživatelského rozhraní. Poskytuje:  
  
- Prohlížeče dokumentů/editory.  
  
- Správa zarážku.  
  
- Výraz vyhodnocování a sledování systému windows.  
  
- Stack – procházení snímků.  
  
- Objekt nebo třída procházení.  
  
- Procházení struktury virtuální aplikace.  
  
  Rozhraní implementovaná pomocí ladicího programu:  
  
  [IApplicationDebugger – rozhraní](../winscript/reference/iapplicationdebugger-interface.md)  
  Primární rozhraní vystavené IDE relace ladicího programu.  
  
  [IApplicationDebuggerUI – rozhraní](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Externí komponenta dává větší kontrolu nad uživatelského rozhraní (UI) ladicího programu.  
  
  [IDebugExpressionCallBack – rozhraní](../winscript/reference/idebugexpressioncallback-interface.md)  
  Poskytuje stav události pro `IDebugExpression` probíhá vyhodnocení.  
  
  [IDebugDocumentTextEvents – rozhraní](../winscript/reference/idebugdocumenttextevents-interface.md)  
  Poskytuje události, které naznačují změny přidružené textový dokument.  
  
  [IDebugApplicationNodeEvents – rozhraní](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Poskytuje rozhraní události pro `IDebugApplicationNode` rozhraní.  
  
### <a name="machine-debug-manager"></a>Správce ladění počítače  
 Správce ladění počítač bodu propojení mezi virtuální a ladicí programy zajišťuje údržbu a vytváření výčtů seznam aktivních virtuálních aplikací.  
  
 [IDebugSessionProvider – rozhraní](../winscript/reference/idebugsessionprovider-interface.md)  
 Vytvoří relaci ladění pro běžící aplikaci.  
  
 [IMachineDebugManager – rozhraní](../winscript/reference/imachinedebugmanager-interface.md)  
 Primární rozhraní pro ladění machine manager.  
  
 [IMachineDebugManagerCookie – rozhraní](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Podobně jako `IMachineDebugManager` rozhraní, ale toto rozhraní podporuje ladění souborů cookie.  
  
 [IMachineDebugManagerEvents – rozhraní](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Signály změny ve spuštěném seznam aplikací, které spravuje správce počítače ladění.  
  
 [IEnumRemoteDebugApplications – rozhraní](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Vytvoří výčet spouštění aplikací v počítači.  
  
### <a name="process-debug-manager"></a>Správce ladění procesu  
 PDM provede následující akce:  
  
- Synchronizuje ladění více modulů jazyka.  
  
- Udržuje stromu laditelné dokumentů.  
  
- Sloučení rámců zásobníku.  
  
- Souřadnice zarážky a krokování napříč moduly jazyka.  
  
- Sleduje vlákna.  
  
- Udržuje vlákno ladicího programu pro asynchronní zpracování.  
  
- Komunikuje se službou machine manager ladění a ladicí program integrovaného vývojového prostředí.  
  
  Následující části jsou rozhraní poskytovaných službou Správce ladění procesu.  
  
  [IProcessDebugManager – rozhraní](../winscript/reference/iprocessdebugmanager-interface.md)  
  Primární rozhraní pro správce ladění procesu. Toto rozhraní můžete vytvořit, přidat nebo odebrat virtuální aplikace z procesu.  
  
  [IRemoteDebugApplication – rozhraní](../winscript/reference/iremotedebugapplication-interface.md)  
  Představuje běžící aplikaci.  
  
  [IDebugApplication – rozhraní](../winscript/reference/idebugapplication-interface.md)  
  Poskytuje metody ladění bez podpory vzdáleného přístupu pro použití modulů jazyka a hostitele.  
  
  [IRemoteDebugApplicationThread – rozhraní](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Představuje vlákno provádění v rámci konkrétní aplikace.  
  
  [IDebugApplicationThread – rozhraní](../winscript/reference/idebugapplicationthread-interface.md)  
  Umožňuje jazykové moduly a hostitelům zajistit synchronizaci vláken a udržovat informace specifické pro vlákno, stav ladění.  
  
  [IEnumRemoteDebugApplicationThreads – rozhraní](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Vytvoří výčet spuštěných vláken v aplikaci.  
  
  [IDebugThreadCall – rozhraní](../winscript/reference/idebugthreadcall-interface.md)  
  Odešle zařadit volání.  
  
  [IDebugApplicationNode – rozhraní](../winscript/reference/idebugapplicationnode-interface.md)  
  Udržuje na umístění dokumentu v hierarchii.  
  
  [IEnumDebugApplicationNodes – rozhraní](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Vytvoří výčet podřízené uzly uzlu přidružené k aplikaci.  
  
  [IEnumDebugStackFrames – rozhraní](../winscript/reference/ienumdebugstackframes-interface.md)  
  Vytváří výčet rámců zásobníku odpovídající vlákno sloučeno z motorů.  
  
  [IDebugCookie – rozhraní](../winscript/reference/idebugcookie-interface.md)  
  Umožňuje ladění souborů cookie v ladicích programů skriptů.  
  
  [IDebugHelper – rozhraní](../winscript/reference/idebughelper-interface.md)  
  Slouží jako objekt pro vytváření pro objekt prohlížeče a jednoduché spojovací body pro skriptovací stroje.  
  
  [ISimpleConnectionPoint – rozhraní](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Poskytuje jednoduchý způsob pro popisující a výčet události vyvolané na bod připojení pro skriptovací stroje.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní ladicího programu aktivních skriptů](../winscript/reference/active-script-debugger-interfaces.md)
