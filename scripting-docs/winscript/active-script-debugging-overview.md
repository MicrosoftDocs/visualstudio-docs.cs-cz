---
title: Přehled ladění aktivních skriptů | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0181ee305c99a1d0af1d3e1e965c6ac8fe16f375
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835664"
---
# <a name="active-script-debugging-overview"></a>Přehled ladění aktivních skriptů
Rozhraní ladění aktivního skriptu umožňují jazykově neutrální a nezávislé ladění a podporují širokou škálu vývojových prostředí.  
  
 ![Hostitelský proces skriptu](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Obrázek 1  
  
 Jazykově neutrální ladicí prostředí může podporovat libovolný programovací jazyk nebo kombinaci programovacích jazyků, aniž by bylo nutné znát konkrétní znalosti těchto jazyků. Ladicí prostředí podporuje také rozjezd a zarážky mezi jazyky. (Tento přehled se zaměřuje hlavně na jazykovou skriptovací jazyky, jako je například VBScript a [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] .)  
  
 Hostitelský ladicí program lze automaticky použít u libovolného aktivního skriptovacího hostitele, jako je například Internet Explorer nebo vlastní hostitel. Hostitel řídí, co ladicí program prezentuje uživateli, ze struktury stromu dokumentu až po obsah a barvy syntaxe dokumentů ladění. To umožňuje, aby byl laděný zdrojový kód zobrazen v kontextu hostitelského dokumentu. Například Internet Explorer může zobrazit skript na stránce HTML.  
  
 V níže uvedených částech jsou popsány všechny klíčové komponenty v aktivním ladění a jejich přidružených rozhraních. Než však budete pokračovat, je třeba definovat několik konceptů aktivního ladění v klíči:  
  
 **Hostitelská aplikace**  
 Aplikace, která je hostitelem skriptovacích strojů a poskytuje skriptovatelných sady objektů (neboli "objektového modelu").  
  
 **jazykový modul**  
 Komponenta, která poskytuje analýzy, spouštění a ladění abstrakcí pro určitý jazyk.  
  
 **rozhraní IDE pro ladicí program**  
 Aplikace, která poskytuje rozhraní pro ladění, prostřednictvím komunikace s hostitelskou aplikací a jazykovými moduly.  
  
 **Správce ladění počítače** Komponenta, která udržuje registr laděných aplikačních procesů.  
  
 **Správce ladění procesů**  
 Komponenta, která udržuje strom laděných dokumentů pro konkrétní aplikaci, sleduje spuštěné vlákna a tak dále.  
  
 **kontext dokumentu**  
 Kontext dokumentu je abstrakce představující konkrétní rozsah ve zdrojovém kódu hostitelského dokumentu.  
  
 **kontext kódu**  
 Kontext kódu představuje konkrétní umístění v kódu běžícím na jazykovém modulu ("ukazatel virtuální instrukce".)  
  
 **kontext výrazu**  
 Konkrétní kontext (například blok zásobníku), ve kterém mohou být výrazy vyhodnoceny modulem jazyka.  
  
 **procházení objektů**  
 Strukturovaný, nezávislá reprezentace objektu názvu, typu, hodnoty a dílčích objektů vhodná pro implementaci uživatelského rozhraní kukátko.  
  
 Níže je uveden přehled všech klíčových aktivních komponent ladění a odpovídajících, přidružených rozhraní následovaných podrobnostmi o těchto rozhraních.  
  
## <a name="language-engine"></a>Jazykový modul  
 Jazykový modul poskytuje:  
  
- Analýza jazyka a provádění.  
  
- Podpora ladění (zarážky a tak dále).  
  
- Vyhodnocení výrazu.  
  
- Barevné zvýrazňování syntaxe.  
  
- Procházení objektu.  
  
- Výčet a analýza zásobníku  
  
  Níže jsou uvedená rozhraní, která skriptovací modul potřebuje k zajištění ladění, vyhodnocení výrazu a procházení objektů. Tato rozhraní používá hostitelská aplikace k mapování mezi kontextem dokumentu a kontexty kódu stroje a také pomocí uživatelského rozhraní ladicího programu k vyhodnocení výrazu, výčtu zásobníku a procházení objektů.  
  
  [IActiveScriptDebug – rozhraní](../winscript/reference/iactivescriptdebug-interface.md)  
  Poskytuje barevné zvýrazňování syntaxe a výčet kontextu kódu.  
  
  [IActiveScriptErrorDebug – rozhraní](../winscript/reference/iactivescripterrordebug-interface.md)  
  Vrátí kontexty dokumentu a bloky zásobníku pro chyby.  
  
  [IActiveScriptSiteDebug – rozhraní](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Hostitel poskytl propojení z skriptovacího stroje k ladicímu programu.  
  
  [IDebugCodeContext – rozhraní](../winscript/reference/idebugcodecontext-interface.md)  
  Poskytuje virtuální "ukazatel" instrukcí ve vlákně.  
  
  [IEnumDebugCodeContexts – rozhraní](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Vytvoří výčet kontextů kódu, které odpovídají kontextu dokumentu.  
  
  [IDebugStackFrame – rozhraní](../winscript/reference/idebugstackframe-interface.md)  
  Představuje logický rámec zásobníku v zásobníku vláken.  
  
  [IDebugExpressionContext – rozhraní](../winscript/reference/idebugexpressioncontext-interface.md)  
  Poskytuje kontext, ve kterém lze výrazy vyhodnotit.  
  
  [IDebugStackFrameSniffer – rozhraní](../winscript/reference/idebugstackframesniffer-interface.md)  
  Poskytuje způsob zobrazení výčtu logických rámců zásobníku.  
  
  [IDebugExpression – rozhraní](../winscript/reference/idebugexpression-interface.md)  
  Představuje asynchronní vyhodnocený výraz.  
  
  [IDebugSyncOperation – rozhraní](../winscript/reference/idebugsyncoperation-interface.md)  
  Umožňuje skriptovacímu stroji abstrakci operace, kterou je třeba provést, když jsou vnořeny v určitém blokovaném vlákně.  
  
  [IDebugAsyncOperation – rozhraní](../winscript/reference/idebugasyncoperation-interface.md)  
  Poskytuje asynchronní přístup k synchronní operaci ladění.  
  
  [IDebugAsyncOperationCallBack – rozhraní](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Poskytuje události stavu související se průběhem `IDebugAsyncOperation` hodnocení rozhraní.  
  
  [IEnumDebugExpressionContexts – rozhraní](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Vytvoří výčet kolekce `IDebugExpressionContexts` objektů.  
  
  [IProvideExpressionContexts – rozhraní](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Poskytuje způsob, jak vytvořit výčet kontextů výrazů známých určitou komponentou.  
  
  [IDebugFormatter – rozhraní](../winscript/reference/idebugformatter-interface.md)  
  Umožňuje jazyku nebo rozhraní IDE přizpůsobit převod mezi hodnotami VARIANT nebo typy a řetězci VARTYPE.  
  
  [IDebugStackFrameSnifferEx – rozhraní](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Vytvoří výčet logických rámců zásobníku pro PDM.  
  
## <a name="hosts"></a>Hostitelé  
 Hostitel:  
  
- Hostuje jazykové moduly.  
  
- Poskytuje objektový model (sadu objektů, které lze skriptovat).  
  
- Definuje strom dokumentů, které lze ladit a jejich obsah.  
  
- Uspořádá skripty do virtuálních aplikací.  
  
  Existují dva druhy hostitelů:  
  
- Hostitel Dumb podporuje jenom základní aktivní skriptovací rozhraní. Nemá žádnou kontrolu nad strukturou dokumentu ani organizacemi. To je určeno výhradně skripty poskytovanými pro jazykové moduly.  
  
- Inteligentní hostitel podporuje větší sadu rozhraní, která umožňuje definovat strom dokumentů, obsah dokumentů a barevné zvýrazňování syntaxe. Existuje sada pomocných rozhraní, která jsou popsaná v následující podčásti, což je mnohem snazší, aby hostitel byl inteligentním hostitelem.  
  
### <a name="smart-host-helper-interfaces"></a>Pomocná rozhraní pro inteligentní hostitele  
 `IDebugDocumentHelper`Metody poskytují výrazně zjednodušenou sadu rozhraní, kterou může hostitel použít k získání výhod inteligentního hostování bez nutnosti zajistit úplnou složitost (a sílu) úplných hostitelských rozhraní.  
  
 Hostitel není potřebný k použití těchto rozhraní. Použití těchto rozhraní se však může vyhnout implementaci nebo použití několika složitějších rozhraní.  
  
 [IDebugDocumentHelper – rozhraní](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implementováno pomocí PDM a poskytuje implementace pro mnoho rozhraní nezbytných pro inteligentní hostování.  
  
 [IDebugDocumentHost – rozhraní](../winscript/reference/idebugdocumenthost-interface.md)  
 Implementovaná (volitelně) hostitel k vystavení funkcí specifických pro hostitele, jako je například Obarvení syntaxe, do ladicího programu.  
  
 Další informace najdete v tématu [implementace pomocných rozhraní inteligentního hostitele](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Úplná rozhraní pro inteligentní hostování  
 Níže je uvedená úplná sada rozhraní, kterou musí inteligentní hostitel implementovat nebo použít, pokud nepoužívají rozhraní pomocníka.  
  
 Rozhraní implementovaná hostitelem:  
  
 [IDebugDocumentInfo – rozhraní](../winscript/reference/idebugdocumentinfo-interface.md)  
 Poskytuje informace o dokumentu, který může nebo nemusí být vytvořen.  
  
 [IDebugDocumentProvider – rozhraní](../winscript/reference/idebugdocumentprovider-interface.md)  
 Poskytuje způsob vytváření instancí dokumentu na vyžádání.  
  
 [IDebugDocument – rozhraní](../winscript/reference/idebugdocument-interface.md)  
 Základní rozhraní pro všechny dokumenty ladění.  
  
 [IDebugDocumentText – rozhraní](../winscript/reference/idebugdocumenttext-interface.md)  
 Poskytuje přístup k verzi dokumentu ladění pouze pro text.  
  
 [IDebugDocumentTextAuthor – rozhraní](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Umožňuje úpravy verze dokumentu ladění pouze pro text.  
  
 [IDebugDocumentContext – rozhraní](../winscript/reference/idebugdocumentcontext-interface.md)  
 Poskytuje abstraktní znázornění části laděného dokumentu.  
  
 Rozhraní implementovaná nástrojem PDM jménem hostitele:  
  
 [IDebugApplicationNode – rozhraní](../winscript/reference/idebugapplicationnode-interface.md)  
 Rozšiřuje funkčnost `IDebugDocumentProvider` rozhraní tím, že poskytuje kontext v rámci stromu projektu.  
  
## <a name="debugger-ide"></a>Rozhraní IDE pro ladicí program  
 Rozhraní IDE je uživatelské rozhraní pro ladění nezávislé na jazyce. Tato služba poskytuje:  
  
- Prohlížeče a editory dokumentů.  
  
- Správa zarážek  
  
- Vyhodnocení výrazu a okna kukátka.  
  
- Procházení rámce zásobníku.  
  
- Procházení objektu/třídy.  
  
- Procházení struktury virtuální aplikace  
  
  Rozhraní implementovaná ladicím programem:  
  
  [IApplicationDebugger – rozhraní](../winscript/reference/iapplicationdebugger-interface.md)  
  Primární rozhraní vystavené relací IDE ladicího programu.  
  
  [IApplicationDebuggerUI – rozhraní](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Poskytuje lepší kontrolu nad uživatelským rozhraním (UI) ladicího programu pro externí komponentu.  
  
  [IDebugExpressionCallBack – rozhraní](../winscript/reference/idebugexpressioncallback-interface.md)  
  Poskytuje události stavu pro `IDebugExpression` průběh vyhodnocení.  
  
  [IDebugDocumentTextEvents – rozhraní](../winscript/reference/idebugdocumenttextevents-interface.md)  
  Poskytuje události indikující změny přidruženého textového dokumentu.  
  
  [IDebugApplicationNodeEvents – rozhraní](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Poskytuje rozhraní události pro `IDebugApplicationNode` rozhraní.  
  
### <a name="machine-debug-manager"></a>Správce ladění počítače  
 Správce ladění počítače poskytuje propojení bod mezi virtuálními aplikacemi a ladicími programy tím, že uchovává a vytváří výčet seznamů aktivních virtuálních aplikací.  
  
 [IDebugSessionProvider – rozhraní](../winscript/reference/idebugsessionprovider-interface.md)  
 Vytvoří ladicí relaci pro spuštěnou aplikaci.  
  
 [IMachineDebugManager – rozhraní](../winscript/reference/imachinedebugmanager-interface.md)  
 Primární rozhraní pro správce ladění počítače.  
  
 [IMachineDebugManagerCookie – rozhraní](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Podobně jako `IMachineDebugManager` rozhraní, ale toto rozhraní podporuje soubory cookie ladění.  
  
 [IMachineDebugManagerEvents – rozhraní](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Signalizuje změny v seznamu běžící aplikace udržované správcem ladění počítače.  
  
 [IEnumRemoteDebugApplications – rozhraní](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Vytvoří výčet spuštěných aplikací v počítači.  
  
### <a name="process-debug-manager"></a>Správce ladění procesu  
 PDM provádí následující akce:  
  
- Synchronizuje ladění více jazykových modulů.  
  
- Udržuje strom laděných dokumentů.  
  
- Sloučí rámce zásobníku.  
  
- Koordinuje zarážky a rozkrokování napříč jazykovými moduly.  
  
- Sleduje vlákna.  
  
- Udržuje podproces ladicího programu pro asynchronní zpracování.  
  
- Komunikuje se správcem ladění počítače a rozhraním IDE ladicího programu.  
  
  Níže jsou uvedena rozhraní poskytovaná správcem ladění procesu.  
  
  [IProcessDebugManager – rozhraní](../winscript/reference/iprocessdebugmanager-interface.md)  
  Primární rozhraní pro správce ladění procesu. Toto rozhraní může vytvořit, přidat nebo odebrat virtuální aplikaci z procesu.  
  
  [IRemoteDebugApplication – rozhraní](../winscript/reference/iremotedebugapplication-interface.md)  
  Představuje běžící aplikaci.  
  
  [IDebugApplication – rozhraní](../winscript/reference/idebugapplication-interface.md)  
  Zpřístupňuje nevzdáleně metody ladění, které se použijí pro jazykové moduly a hostitele.  
  
  [IRemoteDebugApplicationThread – rozhraní](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Představuje vlákno provádění v rámci konkrétní aplikace.  
  
  [IDebugApplicationThread – rozhraní](../winscript/reference/idebugapplicationthread-interface.md)  
  Umožňuje jazykovým modulům a hostitelům poskytovat synchronizaci vláken a uchovávat informace o stavu ladění specifických pro vlákno.  
  
  [IEnumRemoteDebugApplicationThreads – rozhraní](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Vytvoří výčet spuštěných vláken v aplikaci.  
  
  [IDebugThreadCall – rozhraní](../winscript/reference/idebugthreadcall-interface.md)  
  Odesílá zařazování volání.  
  
  [IDebugApplicationNode – rozhraní](../winscript/reference/idebugapplicationnode-interface.md)  
  Udržuje pozici pro dokument v hierarchii.  
  
  [IEnumDebugApplicationNodes – rozhraní](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Vytvoří výčet podřízených uzlů uzlu přidruženého k aplikaci.  
  
  [IEnumDebugStackFrames – rozhraní](../winscript/reference/ienumdebugstackframes-interface.md)  
  Vytvoří výčet rámců zásobníku odpovídajících vláknu, které jsou sloučeny z modulů.  
  
  [IDebugCookie – rozhraní](../winscript/reference/idebugcookie-interface.md)  
  Povolí nastavení souboru cookie pro ladění v ladicích nástrojích skriptů.  
  
  [IDebugHelper – rozhraní](../winscript/reference/idebughelper-interface.md)  
  Slouží jako továrna pro prohlížeče objektů a jednoduché spojovací body pro skriptovací stroje.  
  
  [ISimpleConnectionPoint – rozhraní](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Poskytuje jednoduchý způsob, jak popsat a vytvořit výčet událostí vyvolaných v určitém bodu připojení pro skriptovací stroje.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní ladicího programu aktivních skriptů](../winscript/reference/active-script-debugger-interfaces.md)
