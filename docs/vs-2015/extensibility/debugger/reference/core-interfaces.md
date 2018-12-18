---
title: Základní rozhraní | Dokumentace Microsoftu
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
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ea9a80bf469d0555b07d48ca48b158027c90abb7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764803"
---
# <a name="core-interfaces"></a>Základní rozhraní
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Následující rozhraní jsou základní rozhraní pro rozšíření ladicího programu s použitím [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)].  
  
## <a name="discussion"></a>Diskuse  
 Tato rozhraní primárně slouží k vytvoření ladicího stroje (DE). Seřazené zde podle kategorií:  
  
- [Zarážky](#Breakpoints)  
  
- [Kontexty](#Contexts)  
  
- [Jádro serveru](#CoreServer)  
  
- [Ladicí stroje](#DebugEngines)  
  
- [Dokumenty](#Documents)  
  
- [Události](#Events)  
  
- [Výrazy](#Expressions)  
  
- [Paměť](#Memory)  
  
- [Moduly](#Modules)  
  
- [Porty](#Ports)  
  
- [Procesy](#Processes)  
  
- [Programy](#Programs)  
  
- [Vlastnosti](#Properties)  
  
- [Bloky zásobníku](#StackFrames)  
  
- [Vlákna](#Threads)  
  
- [Vizualizérů typů](#TypeVisualizers)  
  
  Entity, které můžete implementovat rozhraní jsou:  
  
- Ladicí stroj (DE)  
  
- Dodavatele portu (PS)  
  
- Chyba při vyhodnocování výrazu (EE)  
  
- Visual Studio (VS)  
  
##  <a name="Breakpoints"></a> Zarážky  
 Tato rozhraní se vztahují k provádění a sledování zarážky.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Představuje zarážku vázán na umístění v paměti.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Odeslaný DE při zarážku je vázán na umístění v paměti.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|sada VS|Představuje kontrolní součet dokumentu pro žádost o zarážku.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Odeslaný DE při zarážky se nezdaří navázat na umístění v paměti.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Odeslaný DE při dosažení zarážky.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|sada VS|Představuje žádost pro zarážku. použité při vytváření čekající zarážkou.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|sada VS|Představuje žádost pro zarážku. použité při vytváření čekající zarážkou.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Představuje informace, které slouží k vytvoření vazby zarážky.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Odeslaný DE po zarážku nevázaného z umístění v paměti.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Představuje Neplatná zarážka (vrácené `IDebugBreakpointErrorEvent2`).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Představuje informace o řešení o Neplatná zarážka.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Představuje pozici ve funkci, ve kterém byla nastavena zarážka.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Představuje zarážku, který je vázaný; použité při vytváření vázaná zarážka.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Představuje výčet v rámci sady vazby zarážky.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Představuje výčet v rámci sady zarážek, které nebylo možné svázat do umístění v paměti.|  
  
##  <a name="Contexts"></a> Kontexty  
 Tato rozhraní představují různé druhy kontextech v rámci programu, který se právě ladí.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Představuje počáteční pozici kódu instrukce.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Rozšiřuje [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) rozhraní povolit načtení modulu a proces rozhraní.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Představuje pozici v dokumentu.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Představuje kontext, ve kterém se má vyhodnotit výraz.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Představuje výchozí umístění v paměti kolekce bajtů.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Představuje kontext rámce zásobníku v zarážky nebo výjimky.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Představuje kontext rámce zásobníku v zarážky nebo výjimky.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|V rámci sady kontexty kód představuje výčet.|  
  
##  <a name="CoreServer"></a> Jádro serveru  
 Tato rozhraní představovat počítač, na kterém je program laděn. Jsou implementovány pomocí [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ale může volat do ladicí stroj.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|sada VS|Poskytuje přístup k porty a dodavatelé portů, jakož i informace o počítači.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|sada VS|Představuje [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , který podporuje vzdálené ladění.|  
  
##  <a name="DebugEngines"></a> Ladicí stroje  
 Tato rozhraní představují ladění modulů a jejich související události.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Představuje vlastního ladicího stroje.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Představuje vlastního ladicího stroje, který podporuje načítání symbolů, JustMyCode a výjimky.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Každá nová instance DE odesílaných označující, že je připravená pro zpracování úlohy ladění.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Představuje vlastního ladicího stroje, který podporuje spouštění programů.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Představuje uzel program, který zpracovává více ladicí stroj.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Poskytuje způsob, jakým SDM získat rozhraní k ladicímu stroji z vlákna, programu nebo blok zásobníku.|  
  
##  <a name="Documents"></a> Dokumenty  
 Tato rozhraní představují dokumentů (zdrojové soubory) a jejich přidružených prvků.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Odeslaný DE požádat o otevření dokumentu.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Představuje datový proud zpětně přeložený pokyny z dokumentu.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Reprezentuje dokument, získáte ho od DE, zadáte název a ID (CLSID) třídy.|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Představuje kontrolní součet pro ladicí dokumentu a umožňuje předání kontrolní součet mezi komponentami.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Představuje kontext dokumentu, na pozici v rámci dokumentu odpovídající konkrétním kontextu příkazu a kódu.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Představuje obecné pozici v rámci dokumentu.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|sada VS|Představuje pozici ve zdrojovém souboru jako odsazení znaku.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Reprezentuje textový dokument poskytnutých DE (odvozený od [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), zadání vlastní text.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Odeslaný DE a zadejte změny do zdrojového souboru, který je v paměti.|  
  
##  <a name="Events"></a> Události  
 Tato rozhraní představují všechny události, které jsou odeslány mezi DE a správce ladění relace (SDM).  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Odeslaný DE požádat o otevření dokumentu.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Ladicí stroj (DE) odešle toto rozhraní Správce ladění relace (SDM) Chcete-li nastavit stav panelu zprávy během načítání symbolů.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Odeslaný DE při přerušení v programu bylo dokončeno.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Odeslaný DE, když je vytvořena vazba zarážku.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Selhání zarážky vázat odesílaných DE.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Odeslaný DE při dosažení zarážky.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Odeslaný DE po nevázaného zarážku.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Odeslaný DE k určení, zda by se měla zastavit v konkrétních místech.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Odeslaný DE a zadejte změny do zdrojového souboru, který je v paměti.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Každá nová instance DE odesílaných označující, že je připravená pro zpracování úlohy ladění.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Odeslaný DE označující, že laděný program je připraven ke spuštění první instrukci.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Rozhraní, které se používá jinými rozhraními události, které může vrátit chybu, k poskytování čitelné chybové zprávy.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE, PS|Základní rozhraní, které všechny události jsou odvozené rozhraní.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|sada VS|Představuje rozhraní implementované SDM, ke které se odesílají události (vyjádřený jako objekty implementace rozhraní konkrétní události).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Odeslaný DE při došlo k výjimce v programu, který se právě ladí.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Po dokončení vyhodnocení výrazu asynchronní odesílaných DE.|  
|IDebugFindSymbolEvent2||ZASTARALÉ. NEPOUŽÍVEJTE.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Odeslaný DE po dokončení zpracování zachycené výjimky.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Po dokončení načítání program odesílaných DE.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Odeslaný DE mít IDE zobrazení informačních zpráv uživateli.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Odeslaný DE při načtení modulu nebo byla uvolněna.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Signály [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ladicího programu uživatelského rozhraní uživatele upozornit, že symbolů nebyl nalezen pro spuštěnou spustitelný soubor.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Odeslaný DE mít zobrazení IDE libovolný řetězec.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, DE|Odeslaný port pro komunikaci portu události na jakékoli naslouchací proces.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Odeslaný DE nebo portu při procesu.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Odeslaný DE nebo portu při zlikvidování procesu.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Odeslaný DE nebo port po vytvoření programu v jazyce.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Odeslaný DE nebo portu při zlikvidování programu.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Umožňuje ladicí stroj přepsat výchozí chování [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] uživatelského rozhraní při ukončení relace ladění.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Odesílat ladicího stroje (DE) Správce ladění relace (SDM) Pokud se změní název programu.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Odeslaný DE při nové vlastnosti (reprezentované `IDebugProperty2` rozhraní) byla vytvořena.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Odeslaný DE při zlikvidování vlastnost.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Odeslaný DE při krokování z celkového počtu nebo funkci tak, že návratová hodnota může být správně zobrazen.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|sada VS|Umožňuje ladit weby snadněji číst nastavení metriky vzdáleně.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Po dokončení kroku do, přes nebo mimo instrukce odesílaných DE.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Odešle DE udávající úspěch nebo selhání načítání symbolů pro modul.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Po vytvoření vlákna odesílaných DE.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Odeslaný DE při zlikvidování vlákno.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Odeslaný DE vlákno se při změně jeho názvu.|  
  
##  <a name="Expressions"></a> Výrazy  
 Tato rozhraní představují výrazů, který se má vyhodnotit v konkrétním kontextu.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Představuje výraz k vyhodnocení. Získané [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) rozhraní.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Představuje kontext, ve kterém je výraz vyhodnocen. Získané [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) rozhraní.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Po dokončení vyhodnocení výrazu asynchronní odesílaných DE.|  
  
##  <a name="Memory"></a> Paměť  
 Tato rozhraní představují sekvence bajtů v paměti.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Představuje posloupnost bajtů v paměti, který může číst nebo zapisovat do.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Představuje umístění v paměti pořadí bajtů.|  
  
##  <a name="Modules"></a> Moduly  
 Tato rozhraní představuje modul, který odpovídá spustitelný soubor nebo. Soubor knihovny DLL.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Představuje jeden spustitelný soubor nebo knihovny DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Představuje [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , který podporuje symboly.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Odeslaný DE při načtení modulu nebo byla uvolněna.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Představuje informace o zdrojovém serveru, který je obsažen v souboru PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Představuje výčet v rámci sady modulů, které jsou známé podle [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
##  <a name="Ports"></a> Porty  
 Tato rozhraní představují porty a dodavatelé portů.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Představuje výchozí port v místním počítači.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|sada VS|Umožňuje ladicího stroje, který používá model DCOM klást [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] uživatelského rozhraní, abyste měli jistotu, že brána firewall neblokuje vzdálené ladění.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|Reprezentuje port.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Odeslaný port pro komunikaci portu události na jakékoli naslouchací proces.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Reprezentuje port, který můžete spustit a ukončit procesy.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Umožňuje vytvářet a rušit registraci programy s portem; Umožňuje port, který chcete sledovat programy, které jsou právě laděny.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Představuje vlastní uživatelské rozhraní pro výběr portu.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|sada VS|Představuje žádost o portu, ze kterého bude nový port vytvořena nebo nachází.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Představuje dodavatele portů.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Představuje dodavatele portů, které můžete zachovat (Uložit na disk) informace o portech ho vytvořili.|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Umožňuje [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] uživatelského rozhraní k zobrazení textu v **přenosu informací** část **připojit k procesu** dialogové okno.|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|sada VS|Umožňuje dotazování na informace o cílovém počítači.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Výčet představuje sadu portů.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|sada VS|Představuje výčet v rámci sady dodavatelé portů.|  
  
##  <a name="Processes"></a> Procesy  
 Tato rozhraní představují procesy, jeden spustitelný soubor, který obsahuje jeden nebo více programů.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Představuje proces, který běží na počítači.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Představuje proces, který se aktivně podporuje ladění (používá k nahrazení krokem, pokračovat a na provádění metod [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) rozhraní).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Odeslaný DE nebo portu při procesu.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Odeslaný DE nebo portu při zlikvidování procesu.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Představuje proces, který musí sledovat relace je k němu připojené.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Představuje Výčtový objekt sadu procesů na portu.|  
  
##  <a name="Programs"></a> Programy  
 Tato rozhraní představují programy, logické jednotky spuštění, které neodpovídají nutně fyzické spustitelného souboru nebo modulu.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Představuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který potřebuje pracovat ve vzájemné součinnosti s jinými programy právě laděny ve stejnou dobu.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Představuje logickou jednotkou spouštění.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Odeslaný DE nebo port po vytvoření programu v jazyce.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Odeslaný DE nebo portu při zlikvidování programu.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Představuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , které mohou být zpracovány více ladicí stroj.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Představuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který musí být schopen sledovat relace je k němu připojené.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Představuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , které vracejí informace o procesu, ve kterém je spuštěná.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Představuje program, který lze ladit.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Umožňuje programu uzel upozornit pokus o připojení k programu přidružené.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Poskytuje způsob, jakým SDM k dotazování DE o programech, že DE řídí.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|sada VS|DEs používá k registraci programy SDM lze zobrazit, že jsou právě laděny.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Představuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , který by mohl zařazovat rozhraní hranice vlákna nebo procesu.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Představuje Výčtový objekt řadu programů.|  
  
##  <a name="Properties"></a> Vlastnosti  
 Tato rozhraní představují vlastnosti, hodnoty související s konkrétním kontextu, obvykle výsledkem vyhodnocení výrazu.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Představuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) vlastním způsobem, který můžete zobrazit její hodnotu.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Reprezentuje hodnotu rámec zásobníku, dokumentu nebo výsledek vyhodnocení výrazu.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Představuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) libovolně dlouhé řetězce, který podporuje.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Odeslaný DE při nové vlastnosti (reprezentované [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) rozhraní) byla vytvořena.|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Odeslaný DE při zlikvidování vlastnost.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Představuje odkaz na vlastnost, která mohou existovat mimo všechny konkrétní rámec zásobníku.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Představuje výčet přes sadu [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury, které popisují proměnné, registry, parametry a výrazy.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Představuje výčet přes sadu [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury.|  
  
##  <a name="StackFrames"></a> Rámce zásobníku  
 Tato rozhraní představují rámec zásobníku, kontext v které zarážky nebo výjimky došlo k chybě.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Představuje kontext v které zarážky nebo výjimky došlo k chybě.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Představuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) které dokáže zpracovat zachycení výjimky.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Představuje výčet přes sadu [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) struktury, které určují funkce sekvence použít můžete přejít na konkrétní rámec zásobníku volání.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Představuje výčet přes sadu [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury, které popisují rámce zásobníku.|  
  
##  <a name="Threads"></a> Vlákna  
 Tato rozhraní představují vlákna a jejich související události.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Představuje vlákno provádění.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Po vytvoření vlákna odesílaných DE.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Odeslaný DE při zlikvidování vlákno.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Odeslaný DE vlákno se při změně jeho názvu.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|V rámci sady vláken představuje výčet.|  
  
##  <a name="TypeVisualizers"></a> Vizualizérů typů  
 Tato rozhraní podporují vizualizérů typů. Tato rozhraní jsou obvykle implementovány vyhodnocovače výrazů.  
  
|Rozhraní|Implementováno|Popis|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Představuje pole bajtů, které se budou zobrazovat vizualizér typů.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Poskytuje metody pro získání přístupu k datům, které se mají předat typ vizualizéru.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Reprezentuje vlastnost, která poskytuje přístup k [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implementace.|  
  
## <a name="see-also"></a>Viz také  
 [Reference k rozhraní API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Vytvoření vlastního ladicího stroje](../../../extensibility/debugger/creating-a-custom-debug-engine.md)

