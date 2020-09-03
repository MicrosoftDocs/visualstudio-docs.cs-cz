---
title: Základní rozhraní | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 94703f13eba0c58aad24597bc65beeea862e79e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179216"
---
# <a name="core-interfaces"></a>Základní rozhraní
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Následující rozhraní jsou základní rozhraní pro rozšíření ladicího programu pomocí [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)] .  
  
## <a name="discussion"></a>Diskuse  
 Tato rozhraní se primárně používají k vytvoření ladicího stroje (DE). Tady jsou uspořádány podle kategorií:  
  
- [Zarážky](#Breakpoints)  
  
- [Kontexty](#Contexts)  
  
- [Základní server](#CoreServer)  
  
- [Moduly ladění](#DebugEngines)  
  
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
  
- [Typy vizualizací](#TypeVisualizers)  
  
  Entity, které mohou implementovat rozhraní:  
  
- Ladicí stroj (DE)  
  
- Dodavatel portu (PS)  
  
- Vyhodnocení výrazu (EE)  
  
- Visual Studio (VS)  
  
## <a name="breakpoints"></a><a name="Breakpoints"></a> Zarážky  
 Tato rozhraní souvisejí s implementací a sledováním zarážek.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Představuje zarážku, která je vázaná na umístění v paměti.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Odesílá se pomocí DE, když je zarážka svázána s umístěním v paměti.|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|sada VS|Představuje kontrolní součet dokumentu pro požadavek na zarážku.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Odesílá se pomocí DE, když se zarážka nepovede svázat s umístěním v paměti.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Odesílá se DE při dosažení zarážky.|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|sada VS|Představuje požadavek na zarážku; používá se při vytváření nedokončené zarážky.|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|sada VS|Představuje požadavek na zarážku; používá se při vytváření nedokončené zarážky.|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Představuje informace použité k navázání zarážky.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Odesílá se pomocí DE, pokud je zarážka nevázaná z umístění v paměti.|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Představuje neplatnou zarážku (vrácenou funkcí `IDebugBreakpointErrorEvent2` ).|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Představuje informace o řešení neplatného zarážky.|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Představuje pozici ve funkci, kde je nastavena zarážka.|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Představuje zarážku, která má být svázaná; používá se při vytváření vázané zarážky.|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Představuje výčet v rámci sady vázaných zarážek.|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Představuje výčet v rámci sady zarážek, které nebylo možné svázat s umístěním v paměti.|  
  
## <a name="contexts"></a><a name="Contexts"></a> Kontexty  
 Tato rozhraní reprezentují různé druhy kontextů v laděném programu.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Představuje počáteční pozici instrukce kódu.|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Rozšiřuje rozhraní [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , aby bylo možné načíst rozhraní modulu a procesu.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Představuje pozici v dokumentu.|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Představuje kontext, ve kterém se má vyhodnotit výraz.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Představuje počáteční umístění v paměti kolekce bajtů.|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Představuje kontext rámce zásobníku na zarážce nebo výjimce.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Představuje kontext rámce zásobníku na zarážce nebo výjimce.|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Představuje výčet v rámci sady kontextů kódu.|  
  
## <a name="core-server"></a><a name="CoreServer"></a> Základní server  
 Tato rozhraní reprezentují počítač, na kterém je program laděn. Tyto jsou implementovány nástrojem, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ale mohou být volány moduly ladění.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|sada VS|Poskytuje přístup k portům a dodavatelům portů a také informacím o počítači.|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|sada VS|Představuje [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , který podporuje vzdálené ladění.|  
  
## <a name="debug-engines"></a><a name="DebugEngines"></a> Moduly ladění  
 Tato rozhraní označují moduly ladění a jejich přidružené události.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Představuje vlastní ladicí stroj.|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Představuje vlastní ladicí stroj, který podporuje načítání symbolů, JustMyCode a výjimek.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Odesílá se každou novou instancí DE k označení, že je připravena zpracovat úlohy ladění.|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Představuje vlastní ladicí stroj, který podporuje spouštění programů.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Představuje uzel programu, který zpracovává více ladicích modulů.|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|Poskytuje způsob, jak má model SDM získat rozhraní ladicího stroje z vlákna, programu nebo rámce zásobníku.|  
  
## <a name="documents"></a><a name="Documents"></a> Document  
 Tato rozhraní reprezentují dokumenty (zdrojové soubory) a jejich přidružené prvky.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Odesílá se nástrojem DE pro vyžádání dokumentu, který má být otevřen.|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Představuje datový proud předokumentovaných instrukcí z dokumentu.|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|Představuje dokument dodaný DE, určující název a ID třídy (CLSID).|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Představuje kontrolní součet pro dokument ladění a umožňuje předávání kontrolního součtu mezi komponentami.|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Představuje kontext dokumentu, pozice v dokumentu odpovídající konkrétnímu příkazu a kontextu kódu.|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Představuje obecnou pozici v rámci dokumentu.|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|sada VS|Představuje pozici ve zdrojovém souboru jako posun znaku.|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Představuje textový dokument poskytnutý DE (odvozenou z [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)), který poskytuje skutečný text.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Odesílá se nástrojem DE k určení změn zdrojového souboru, který je v paměti.|  
  
## <a name="events"></a><a name="Events"></a> Událost  
 Tato rozhraní představují všechny události, které jsou posílány mezi správcem nástroje DE a relace SDM.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Odesílá se nástrojem DE pro vyžádání dokumentu, který má být otevřen.|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|Ladicí stroj (DE) pošle toto rozhraní do Správce ladění relace (SDM), aby během načítání symbolů nastavil zprávu stavového řádku.|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|Odesílá se pomocí DE, když se dokončí přerušení programu.|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Odesílá se při vazbě na zarážku.|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Odesílá se z DE, když se nepovede svázat zarážku.|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Odesílá se DE při dosažení zarážky.|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Odesílá se pomocí DE, pokud je zarážka nevázaná.|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|Odesílá se nástrojem DE, aby bylo možné zjistit, zda by mělo být zastaveno v konkrétním umístění.|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Odesílá se nástrojem DE k určení změn zdrojového souboru, který je v paměti.|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Odesílá se každou novou instancí DE k označení, že je připravena zpracovat úlohy ladění.|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|Odesílá se pomocí příkazu DE, který indikuje, že program, který se právě ladí, je připravený k provedení první instrukce.|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|Rozhraní používané jinými rozhraními událostí, která mohou vracet chybu, aby bylo zajištěno, že se chybové zprávy dají přečíst lidmi.|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE, PS|Základní rozhraní, ze kterého jsou odvozena všechna ostatní rozhraní události.|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|sada VS|Představuje rozhraní implementované serverem SDM, na které se odesílají události (vyjádřené jako objekty implementující konkrétní rozhraní události).|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|Odesílá se nástrojem DE, pokud došlo k výjimce v laděném programu.|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Odesílá se DE po dokončení vyhodnocení asynchronního výrazu.|  
|IDebugFindSymbolEvent2||Zastaralé. NEPOUŽÍVEJTE.|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|Odesláno nástrojem DE při zpracování pro Zachycenou výjimku bylo dokončeno.|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|Odesílá se v době, kdy se program dokončil načítání.|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|Odesílá se nástrojem DE, aby mohl IDE zobrazit informační zprávu uživateli.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Odesílá se nástrojem DE při načtení nebo uvolnění modulu.|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|Signalizuje [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] uživatelské rozhraní ladicího programu upozorňující uživatele na to, že symboly pro spuštěný spustitelný soubor nebyly nalezeny.|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|Odesílá se nástrojem DE pro zobrazení libovolného řetězce v rozhraní IDE.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS, DE|Odesílá se portem, který komunikuje události portů do libovolného naslouchacího procesu.|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Odesílá se pomocí DE nebo port, když se vytvoří proces.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Odesílá se v případě zničení procesu pomocí DE nebo port.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Odesílá se pomocí DE nebo port, když se program vytvořil.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Odesílá se při zničení programu nástrojem DE nebo port.|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|Umožňuje ladicímu stroji [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] při ukončení ladicí relace přepsat výchozí chování uživatelského rozhraní.|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|Odesílá se z ladicího modulu (DE) do Správce ladění relace (SDM), když se změní název programu.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Odesláno pomocí DE při vytvoření nové vlastnosti (reprezentované `IDebugProperty2` rozhraním).|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Odesílá se při zničení vlastnosti DE.|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|Odesílá se nástrojem DE při rozkrokování z nebo přes funkci, aby se návratová hodnota mohla zobrazit správně.|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|sada VS|Umožňuje modulům ladění vzdáleně číst nastavení metriky.|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|Odesílá se pomocí příkazu DE po dokončení kroku do, nad nebo mimo instrukci.|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|Odesílá se DE pro indikaci úspěchu nebo neúspěchu načítání symbolů pro modul.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Odesílá se nástrojem DE při vytvoření vlákna.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Odesílá se nástrojem DE při zničení vlákna.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Odesílá se pomocí DE, když vlákno změnilo svůj název.|  
  
## <a name="expressions"></a><a name="Expressions"></a> Expression  
 Tato rozhraní označují výrazy, které mají být vyhodnoceny v určitém kontextu.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Představuje výraz, který má být vyhodnocen. Získáno z rozhraní [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) .|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Představuje kontext, ve kterém je vyhodnocen výraz. Získáno z rozhraní [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) .|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Odesílá se DE po dokončení vyhodnocení asynchronního výrazu.|  
  
## <a name="memory"></a><a name="Memory"></a> Rezident  
 Tato rozhraní označují posloupnosti bajtů v paměti.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Představuje posloupnost bajtů v paměti, které lze číst nebo do ní zapisovat.|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Představuje umístění v paměti posloupnosti bajtů.|  
  
## <a name="modules"></a><a name="Modules"></a> Aktualizuj  
 Tato rozhraní představují modul, který odpovídá spustitelnému souboru nebo. Soubor DLL.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Představuje jeden spustitelný soubor nebo DLL.|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Představuje [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , který podporuje symboly.|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Odesílá se nástrojem DE při načtení nebo uvolnění modulu.|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|Představuje informace o zdrojovém serveru, které jsou obsaženy v souboru PDB.|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Představuje výčet v rámci sady modulů, které jsou známy v [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md).|  
  
## <a name="ports"></a><a name="Ports"></a> Přístavu  
 Tato rozhraní reprezentují porty a dodavatelé portů.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS, PS|Představuje výchozí port v místním počítači.|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|sada VS|Umožňuje ladicímu stroji, který používá model DCOM k vyžádání [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] uživatelského rozhraní, aby se zajistilo, že brána firewall nebude blokovat vzdálené ladění.|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS, PS|Představuje port.|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|Odesílá se portem, který komunikuje události portů do libovolného naslouchacího procesu.|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|Představuje port, který může spouštět a ukončovat procesy.|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|Slouží k registraci a zrušení registrace programů s portem; umožňuje portu sledovat programy, které jsou právě laděny.|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|Představuje přizpůsobené uživatelské rozhraní pro výběr portu.|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|sada VS|Představuje požadavek na port, ze kterého se vytvoří nebo umístí nový port.|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|Představuje dodavatele portů.|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|Představuje dodavatele portů, které můžou uchovávat informace o portech, které se vytvořily (Uložit na disk).|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|Umožňuje [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] uživatelskému rozhraní zobrazit text v části **přenosové informace** dialogového okna **připojit k procesu** .|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|sada VS|Umožňuje dotazování na informace o cílovém počítači.|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS, PS|Představuje výčet v rámci sady portů.|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|sada VS|Představuje výčet prostřednictvím sady dodavatelů portů.|  
  
## <a name="processes"></a><a name="Processes"></a> Procesem  
 Tato rozhraní reprezentují procesy, jeden spustitelný soubor, který obsahuje jeden nebo více programů.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Představuje proces, který je spuštěn v počítači.|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Představuje proces, který aktivně podporuje ladění (používá se k nahrazení metod kroku, Continue a Execute v rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ).|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Odesílá se pomocí DE nebo port, když se vytvoří proces.|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Odesílá se v případě zničení procesu pomocí DE nebo port.|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Představuje proces, který musí sledovat, která relace je k ní připojená.|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Představuje výčet sady procesů na portu.|  
  
## <a name="programs"></a><a name="Programs"></a> Spuštěn  
 Tato rozhraní představují programy, logické jednotky provádění, které nemusí nutně odpovídat fyzickému spustitelnému souboru nebo modulu.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Představuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který potřebuje pracovat společně s jinými programy, které jsou právě laděny.|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Představuje logickou jednotku provedení.|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Odesílá se pomocí DE nebo port, když se program vytvořil.|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Odesílá se při zničení programu nástrojem DE nebo port.|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Představuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , který může být zpracován více moduly ladění.|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Představuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který musí být schopný sledovat, která relace je k ní připojená.|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Představuje [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který může vracet informace o procesu, ve kterém je spuštěný.|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Představuje program, který lze ladit.|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Umožňuje, aby byl uzel programu upozorněn na pokus o připojení k přidruženému programu.|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|Poskytuje způsob, jak má SDM odeslat dotaz na DE o programech řízených tímto DE.|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|sada VS|Používá algoritmus DEs k registraci programů v modelu SDM, aby bylo možné zobrazit, že jsou laděny.|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Představuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , který může zařazovat rozhraní napříč vláknem nebo hranicemi procesů.|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Představuje výčet sady programů.|  
  
## <a name="properties"></a><a name="Properties"></a> Vlastnosti  
 Tato rozhraní reprezentují vlastnosti, hodnotu přidruženou ke konkrétnímu kontextu, obvykle výsledek vyhodnocení výrazu.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Představuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , který může zobrazit jeho hodnotu vlastním způsobem.|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Představuje hodnotu rámce zásobníku, dokumentu nebo výsledku vyhodnocení výrazu.|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Představuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , který podporuje libovolně dlouhé řetězce.|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Odesláno pomocí DE při vytvoření nové vlastnosti (reprezentované rozhraním [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ).|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Odesílá se při zničení vlastnosti DE.|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Představuje odkaz na vlastnost, která může existovat mimo jakýkoli konkrétní rámec zásobníku.|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Představuje výčet v rámci sady [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur, které popisují proměnné, Registry, parametry a výrazy.|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Představuje výčet v rámci sady [DEBUG_REFERENCE_INFOch](../../../extensibility/debugger/reference/debug-reference-info.md) struktur.|  
  
## <a name="stack-frames"></a><a name="StackFrames"></a> Rámce zásobníku  
 Tato rozhraní reprezentují rámec zásobníku, kontext, ve kterém došlo k zarážce nebo výjimce.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Představuje kontext, ve kterém došlo k zarážce nebo výjimce.|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Představuje [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , který může zpracovávat zachycené výjimky.|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Představuje výčet v rámci sady [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) struktury, které určují sekvenci volání funkce používanou pro doručení do konkrétního bloku zásobníku.|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Představuje výčet v rámci sady [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktur, které popisují rámce zásobníku.|  
  
## <a name="threads"></a><a name="Threads"></a> Vláken  
 Tato rozhraní reprezentují vlákna a jejich přidružené události.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Představuje vlákno provádění.|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Odesílá se nástrojem DE při vytvoření vlákna.|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Odesílá se nástrojem DE při zničení vlákna.|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Odesílá se pomocí DE, když vlákno změnilo svůj název.|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Představuje výčet v rámci sady vláken.|  
  
## <a name="type-visualizers"></a><a name="TypeVisualizers"></a> Typy vizualizací  
 Tato rozhraní poskytují podporu pro typy vizualizace. Tato rozhraní jsou obvykle implementována pomocí vyhodnocovacího filtru výrazů.  
  
|Rozhraní|Implementuje|Popis|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Představuje pole bajtů, které se má předložit Vizualizér typu.|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Poskytuje metody pro získání přístupu k datům, které mají být předány do Vizualizér typu.|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|Představuje vlastnost, která poskytuje přístup k [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) implementace.|  
  
## <a name="see-also"></a>Viz také  
 [Reference k rozhraní API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Vytvoření vlastního ladicího stroje](../../../extensibility/debugger/creating-a-custom-debug-engine.md)
