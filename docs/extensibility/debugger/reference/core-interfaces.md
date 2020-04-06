---
title: Základní rozhraní | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737575"
---
# <a name="core-interfaces"></a>Základní rozhraní
Následující rozhraní jsou základní rozhraní pro rozšíření ladicího [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]programu pomocí .

## <a name="discussion"></a>Diskuse
 Tato rozhraní se používají především k vytvoření ladicí modul (DE). Jsou zde organizovány podle kategorií:

- [Zarážky](#Breakpoints)

- [Kontexty](#Contexts)

- [Základní server](#CoreServer)

- [Ladicí moduly](#DebugEngines)

- [Dokumenty](#Documents)

- [Události](#Events)

- [Výrazy](#Expressions)

- [Paměti](#Memory)

- [Moduly](#Modules)

- [Porty](#Ports)

- [Procesy](#Processes)

- [Programy](#Programs)

- [Vlastnosti](#Properties)

- [Bloky zásobníku](#StackFrames)

- [Vlákna](#Threads)

- [Vizualizéry typu](#TypeVisualizers)

  Entity, které mohou implementovat rozhraní jsou:

- Ladicí modul (DE)

- Dodavatel portů (PS)

- Evaluátor výrazů (EE)

- Visual Studio (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>Zarážky
 Tato rozhraní se vztahují k implementaci a sledování zarážek.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Představuje zarážku vázanou na umístění v paměti.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Odesláno DE při zarážky je vázán a umístění v paměti.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|sada VS|Představuje kontrolní součet dokumentu pro požadavek na zarážku.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Odesláno DE, pokud se nepodaří zarážky být vázána na umístění v paměti.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Odesláno DE při dosažení zarážky.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|sada VS|Představuje požadavek na zarážku; používá při vytváření čekající zarážky.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|sada VS|Představuje požadavek na zarážku; používá při vytváření čekající zarážky.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Představuje informace, které slouží k vytvoření vazby zarážky.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Odesláno DE při zarážky je nevázaný z umístění v paměti.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Představuje neplatnou zarážku (vrácenou ). `IDebugBreakpointErrorEvent2`|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Představuje informace o řešení neplatné zarážky.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Představuje pozici ve funkci, kde je nastavena zarážka.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Představuje zarážku, která má být vázána; používá při vytváření vázané zarážky.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Představuje výčet přes sadu vázaných zarážek.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Představuje výčet přes sadu zarážek, které nelze spojít na umístění v paměti.|

## <a name="contexts"></a><a name="Contexts"></a>Kontexty
 Tato rozhraní představují různé druhy kontextů v rámci programu, který je laděn.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Představuje počáteční pozici instrukce kódu.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Rozšiřuje rozhraní [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) povolit načítání modulu a rozhraní procesu.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Představuje pozici v dokumentu.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Představuje kontext, ve kterém chcete vyhodnotit výraz.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Představuje počáteční umístění v paměti kolekce bajtů.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Představuje kontext rámce zásobníku na zarážku nebo výjimku.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Představuje kontext rámce zásobníku na zarážku nebo výjimku.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Představuje výčet přes sadu kontextů kódu.|

## <a name="core-server"></a><a name="CoreServer"></a>Základní server
 Tato rozhraní představují počítač, na kterém je program laděn. Tyto jsou [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementovány, ale mohou být volány do ladicí motory.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|sada VS|Poskytuje přístup k portům a dodavatelům portů a také k informacím o počítači.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|sada VS|Představuje [IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) který podporuje vzdálené ladění.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>Ladicí moduly
 Tato rozhraní představují ladicí moduly a jejich přidružené události.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Představuje vlastní ladicí modul.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Představuje vlastní ladicí modul, který podporuje načítání symbolů, JustMyCode a výjimky.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Odesláno každou novou instancí DE k označení, že je připraven ke zpracování úloh ladění.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Představuje vlastní ladicí modul, který podporuje spouštění programů.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Představuje uzel programu, který zpracovává více ladicích modulů.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Poskytuje způsob, jak SDM získat rozhraní k ladicí modul z vlákna, programu nebo zásobníku rámce.|

## <a name="documents"></a><a name="Documents"></a>Dokumenty
 Tato rozhraní představují dokumenty (zdrojové soubory) a jejich přidružené prvky.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Odesláno DE požádat o dokument, který má být otevřen.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Představuje datový proud rozebrán instrukcí z dokumentu.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Představuje dokument dodaný DE, určující název a ID třídy (CLSID).|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Představuje kontrolní součet pro ladicí dokument a umožňuje předávání kontrolního součtu mezi součástmi.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Představuje kontext dokumentu, pozici v rámci dokumentu odpovídající konkrétní příkaz a kontext kódu.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Představuje obecné pozice v dokumentu.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|sada VS|Představuje pozici ve zdrojovém souboru jako posun znaků.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Představuje textový dokument dodaný DE (odvozený z [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), zadání skutečného textu.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Odesláno DE určit změny zdrojového souboru, který je v paměti.|

## <a name="events"></a><a name="Events"></a>Události
 Tato rozhraní představují všechny události, které jsou odesílány mezi DE a správce ladění relace (SDM).

| Rozhraní | Implementováno | Popis |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Odesláno DE požádat o dokument, který má být otevřen. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Ladicí modul (DE) odešle toto rozhraní správci ladění relace (SDM) k nastavení zprávy stavového řádku během načítání symbolů. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Odesláno DE po dokončení přerušení programu. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Odesláno DE při zarážka je vázána. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Odesláno DE při přerušení není vázána. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Odesláno DE při dosažení zarážky. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Odesláno DE při zarážka je nevázaný. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Odesláno DE k určení, zda by měl zastavit na určitém místě. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Odesláno DE určit změny zdrojového souboru, který je v paměti. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Odesláno každou novou instancí DE k označení, že je připraven ke zpracování úloh ladění. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Odesláno DE k označení program, který je odladěn je připraven ke spuštění první instrukce. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Rozhraní, které je používáno jinými rozhraními událostí, které mohou vrátit chybu, k poskytování chybových zpráv čitelných pro člověka. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Základní rozhraní, ze kterého jsou odvozeny všechny ostatní rozhraní událostí. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | sada VS | Představuje rozhraní implementované SDM, do kterého jsou odesílány události (vyjádřené jako objekty implementující určité rozhraní události). |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Odesláno DE, pokud došlo k výjimce v programu, který je laděn. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Odesláno DE po dokončení vyhodnocení asynchronního výrazu. |
| IDebugFindSymbolEvent2 | | Zastaralé. NEPOUŽÍVEJTE. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Odesláno DE při zpracování pro zachycenou výjimku byla dokončena. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Odesláno DE po dokončení načítání programu. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | Odeslané DE, aby ide zobrazit informační zprávu pro uživatele. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Odesláno DE při načtení nebo uvolnění modulu. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Signalizuje [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uživatelskérozhraní ladicího programu, aby uživatele varoval, že symboly nelze nalézt pro spuštěný spustitelný soubor. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | Odeslané DE mít IDE zobrazit libovolný řetězec. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Odesláno portem pro komunikaci událostí portu s libovolným naslouchacíproces. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Odesláno DE nebo portem po vytvoření procesu. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Odesláno DE nebo portem, pokud byl proces zničen. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Odesláno de nebo portem po vytvoření programu. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Odesláno de nebo portem, pokud byl program zničen. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Umožňuje ladicí modul přepsat výchozí chování [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hlavního nastavení při ukončení relace ladění. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Odesláno z ladicího modulu (DE) do správce ladění relace (SDM) při změně názvu programu. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Odesláno DE při vytvoření nové vlastnosti (reprezentované `IDebugProperty2` rozhraním). |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Odesláno DE, když byl majetek zničen. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Odesláno DE při krokování z nebo přes funkci, takže vrácená hodnota může být správně zobrazena. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | sada VS | Umožňuje ladit motory číst nastavení metriky na dálku. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Odesláno DE po dokončení kroku do, přes nebo z instrukce. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Odesláno DE k označení úspěchu nebo neúspěchu načítání symbolů pro modul. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Odesláno DE po vytvoření vlákna. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Odesláno DE po zničení vlákna. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Odesláno DE při změně názvu vlákna. |

## <a name="expressions"></a><a name="Expressions"></a>Výrazy
 Tato rozhraní představují výrazy, které mají být vyhodnoceny v určitém kontextu.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Představuje výraz, který má být vyhodnocen. Získané z rozhraní [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Představuje kontext, ve kterém je vyhodnocen výraz. Získané z rozhraní [IDebugStackFrame2.](../../../extensibility/debugger/reference/idebugstackframe2.md)|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Odesláno DE po dokončení vyhodnocení asynchronního výrazu.|

## <a name="memory"></a><a name="Memory"></a>Paměti
 Tato rozhraní představují sekvence bajtů v paměti.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Představuje posloupnost bajtů v paměti, které lze číst nebo zapisovat do.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Představuje umístění v paměti posloupnost bajtů.|

## <a name="modules"></a><a name="Modules"></a>Moduly
 Tato rozhraní představují modul, který odpovídá spustitelnému souboru nebo . soubor DLL.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Představuje jeden spustitelný soubor nebo DLL.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Představuje [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) který podporuje symboly.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Odesláno DE při načtení nebo uvolnění modulu.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Představuje informace o zdrojovém serveru, který je obsažen v souboru PDB.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Představuje výčet přes sadu modulů, které jsou známé [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|

## <a name="ports"></a><a name="Ports"></a>Porty
 Tato rozhraní představují porty a dodavatele portů.

| Rozhraní | Implementováno | Popis |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Představuje výchozí port v místním počítači. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | sada VS | Povolí ladicí modul, který používá [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] DCOM požádat uživatelské ho uživatelského zařízení, aby se ujistil, že brána firewall nebude blokovat vzdálené ladění. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Představuje port. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Odesláno portem pro komunikaci událostí portu s libovolným naslouchacíproces. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | Představuje port, který může spouštět a ukončovat procesy. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Používá se k registraci a zrušení registrace programů pomocí portu; umožňuje portu sledovat aktuálně laděné programy. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Představuje vlastní u(a) pro výběr portu. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | sada VS | Představuje požadavek na port, ze kterého bude vytvořen nebo umístěn nový port. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Představuje dodavatele přístavů. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Představuje dodavatele portů, které mohou ukládat (uložit na disk) informace o portech, které vytvořil. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Umožňuje ui zobrazit text uvnitř části **Informace o přenosu** v dialogovém okně Připojit k **procesu.** [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | sada VS | Umožňuje dotazování na informace o cílovém počítači. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Představuje výčet přes sadu portů. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | sada VS | Představuje výčet přes sadu dodavatelů portů. |

## <a name="processes"></a><a name="Processes"></a>Procesy
 Tato rozhraní představují procesy, jeden spustitelný soubor, který obsahuje jeden nebo více programů.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Představuje proces, který je spuštěn v počítači.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Představuje proces, který aktivně podporuje ladění (slouží k nahrazení step, continue a execute metody v rozhraní [IDebugProgram2).](../../../extensibility/debugger/reference/idebugprogram2.md)|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Odesláno DE nebo portem po vytvoření procesu.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Odesláno DE nebo portem, pokud byl proces zničen.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Představuje proces, který musí sledovat, která relace je k němu připojena.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Představuje výčet sadu procesů na portu.|

## <a name="programs"></a><a name="Programs"></a>Programy
 Tato rozhraní představují programy, logické jednotky provádění, které nemusí nutně odpovídat fyzickéspustitelnému souboru nebo modulu.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Představuje [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) který potřebuje pracovat ve shodě s jinými programy jsou laděny současně.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Představuje logickou jednotku provádění.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Odesláno de nebo portem po vytvoření programu.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Odesláno de nebo portem, pokud byl program zničen.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Představuje [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) které mohou být zpracovány více ladicích strojů.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Představuje [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) který musí být schopen sledovat, která relace je k němu připojena.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Představuje [IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) který může vrátit informace o procesu, ve kterém je spuštěn.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Představuje program, který lze ladit.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Umožňuje upozorňování uzlu programu na pokus o připojení k přidruženému programu.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Poskytuje způsob, jak SDM dotaz DE o programech řízených tímto DE.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|sada VS|Používá des zaregistrovat programy s SDM ukázat, že jsou laděny.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Představuje [IDebugProgramNode2,](../../../extensibility/debugger/reference/idebugprogramnode2.md) který může zařazovat rozhraní přes hranice vlákna nebo procesu.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Představuje výčet sadu programů.|

## <a name="properties"></a><a name="Properties"></a>Vlastnosti
 Tato rozhraní představují vlastnosti, hodnotu přidruženou k určitému kontextu, obvykle výsledek vyhodnocení výrazu.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Představuje [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) který můžete zobrazit jeho hodnotu vlastním způsobem.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Představuje hodnotu rámce zásobníku, dokumentu nebo výsledku vyhodnocení výrazu.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Představuje [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) který podporuje libovolně dlouhé řetězce.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Odesláno DE při vytvoření nové vlastnosti (reprezentované rozhraní [IDebugProperty2).](../../../extensibility/debugger/reference/idebugproperty2.md)|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Odesláno DE, když byl majetek zničen.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Představuje odkaz na vlastnost, která může existovat mimo jakýkoli konkrétní rámec zásobníku.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Představuje výčet přes sadu [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury, které popisují proměnné, registry, parametry a výrazy.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Představuje výčet přes sadu [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktury.|

## <a name="stack-frames"></a><a name="StackFrames"></a>Rámy stohování
 Tato rozhraní představují rámec zásobníku, kontext, ve kterém došlo k zarážky nebo výjimky.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Představuje kontext, ve kterém došlo k zarážky nebo výjimky.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Představuje [IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) který může zpracovávat zachycené výjimky.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Představuje výčet nad sadou [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) struktury, které určují posloupnost volání funkce slouží k doručení na konkrétní rámec zásobníku.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Představuje výčet přes sadu [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury, které popisují rámce zásobníku.|

## <a name="threads"></a><a name="Threads"></a>Vlákna
 Tato rozhraní představují vlákna a jejich přidružené události.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Představuje vlákno provádění.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Odesláno DE po vytvoření vlákna.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Odesláno DE po zničení vlákna.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Odesláno DE při změně názvu vlákna.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Představuje výčet přes sadu podprocesů.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>Vizualizéry typu
 Tato rozhraní poskytují podporu pro vizualizéry typu. Tato rozhraní jsou obvykle implementovány vyhodnocení výrazu.

|Rozhraní|Implementováno|Popis|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Představuje pole bajtů, které mají být prezentovány na typ vizualizéru.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Poskytuje metody pro získání přístupu k datům, která mají být předána vizualizéru typu.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Představuje vlastnost, která poskytuje přístup k implementací [IPropertyProxyEESide.](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|

## <a name="see-also"></a>Viz také
- [Referenční informace k rozhraním API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Vytvoření vlastního ladicího stroje](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
