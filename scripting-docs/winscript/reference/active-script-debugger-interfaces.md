---
title: Rozhraní ladicího programu aktivních skriptů | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 477374d93e4d8d5139197dcd49fef0e930e5ff32
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572698"
---
# <a name="active-script-debugger-interfaces"></a>Rozhraní ladicího programu aktivních skriptů
Hlavičkové soubory activdbg. h a activdbg100. h poskytují rozhraní, výčty a struktury uvedené v této části. Jsou pro ladění skriptu.  
  
> [!NOTE]
> Rozhraní `IJSDebug*` a rozhraní `IEnumJsStackFrames` byly nejprve vydány v aplikaci Internet Explorer 11 pro ladění nativního kódu pomocí skriptu. Hlavičkový soubor pro tato rozhraní je Jscript9diag. h.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Následující rozhraní umožňují jazykově neutrální ladění:  
  
- [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
- [IActiveScriptDebug – rozhraní](../../winscript/reference/iactivescriptdebug-interface.md)  
  
- [IActiveScriptErrorDebug – rozhraní](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
- [IActiveScriptErrorDebug110 – rozhraní](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
- [IActiveScriptSiteDebug – rozhraní](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
- [IActiveScriptSiteDebug32 – rozhraní](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
- [IActiveScriptSiteDebugEx – rozhraní](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
- [IActiveScriptWinRTErrorDebug – rozhraní](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
- [IApplicationDebugger – rozhraní](../../winscript/reference/iapplicationdebugger-interface.md)  
  
- [IApplicationDebuggerUI – rozhraní](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
- [IDebugApplication – rozhraní](../../winscript/reference/idebugapplication-interface.md)  
  
- [IDebugApplication110 – rozhraní](../../winscript/reference/idebugapplication110-interface.md)  
  
- [IDebugApplicationNode – rozhraní](../../winscript/reference/idebugapplicationnode-interface.md)  
  
- [IDebugApplicationNode100 – rozhraní](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
- [IDebugApplicationNodeEvents – rozhraní](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
- [IDebugApplicationThread – rozhraní](../../winscript/reference/idebugapplicationthread-interface.md)  
  
- [IDebugApplicationThread110 – rozhraní](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
- [IDebugApplicationThreadEvents110 – rozhraní](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
- [IDebugAsyncOperation – rozhraní](../../winscript/reference/idebugasyncoperation-interface.md)  
  
- [IDebugAsyncOperationCallBack – rozhraní](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
- [IDebugCodeContext – rozhraní](../../winscript/reference/idebugcodecontext-interface.md)  
  
- [IDebugCookie – rozhraní](../../winscript/reference/idebugcookie-interface.md)  
  
- [IDebugDocument – rozhraní](../../winscript/reference/idebugdocument-interface.md)  
  
- [IDebugDocumentContext – rozhraní](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
- [IDebugDocumentHelper – rozhraní](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
- [IDebugDocumentHost – rozhraní](../../winscript/reference/idebugdocumenthost-interface.md)  
  
- [IDebugDocumentInfo – rozhraní](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
- [IDebugDocumentProvider – rozhraní](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
- [IDebugDocumentText – rozhraní](../../winscript/reference/idebugdocumenttext-interface.md)  
  
- [IDebugDocumentTextAuthor – rozhraní](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
- [IDebugDocumentTextEvents – rozhraní](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
- [IDebugDocumentTextExternalAuthor – rozhraní](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
- [IDebugExpression – rozhraní](../../winscript/reference/idebugexpression-interface.md)  
  
- [IDebugExpressionCallBack – rozhraní](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
- [IDebugExpressionContext – rozhraní](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
- [IDebugFormatter – rozhraní](../../winscript/reference/idebugformatter-interface.md)  
  
- [IDebugHelper – rozhraní](../../winscript/reference/idebughelper-interface.md)  
  
- [IDebugSessionProvider – rozhraní](../../winscript/reference/idebugsessionprovider-interface.md)  
  
- [IDebugSessionProviderEx – rozhraní](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
- [IDebugStackFrame – rozhraní](../../winscript/reference/idebugstackframe-interface.md)  
  
- [IDebugStackFrameSniffer – rozhraní](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
- [IDebugStackFrameSnifferEx – rozhraní](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
- [IDebugSyncOperation – rozhraní](../../winscript/reference/idebugsyncoperation-interface.md)  
  
- [IDebugThreadCall – rozhraní](../../winscript/reference/idebugthreadcall-interface.md)  
  
- [IEnumDebugApplicationNodes – rozhraní](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
- [IEnumDebugCodeContexts – rozhraní](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
- [IEnumDebugExpressionContexts – rozhraní](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
- [IEnumDebugStackFrames – rozhraní](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
- [IEnumJsStackFrames – rozhraní](../../winscript/reference/ienumjsstackframes-interface.md)  
  
- [IEnumRemoteDebugApplications – rozhraní](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
- [IEnumRemoteDebugApplicationThreads – rozhraní](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
- [IJsDebug – rozhraní](../../winscript/reference/ijsdebug-interface.md)  
  
- [IJsDebugBreakPoint – rozhraní](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
- [IJsDebugDataTarget – rozhraní](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
- [IJsDebugFrame – rozhraní](../../winscript/reference/ijsdebugframe-interface.md)  
  
- [IJsDebugProcess – rozhraní](../../winscript/reference/ijsdebugprocess-interface.md)  
  
- [IJsDebugProperty – rozhraní](../../winscript/reference/ijsdebugproperty-interface.md)  
  
- [IJsDebugStackWalker – rozhraní](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
- [IJsEnumDebugProperty – rozhraní](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
- [IMachineDebugManager – rozhraní](../../winscript/reference/imachinedebugmanager-interface.md)  
  
- [IMachineDebugManagerCookie – rozhraní](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
- [IMachineDebugManagerEvents – rozhraní](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
- [IProcessDebugManager – rozhraní](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
- [IProvideExpressionContexts – rozhraní](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
- [IRemoteDebugApplication – rozhraní](../../winscript/reference/iremotedebugapplication-interface.md)  
  
- [IRemoteDebugApplication110 – rozhraní](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
- [IRemoteDebugApplicationEx – rozhraní](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
- [IRemoteDebugApplicationEvents – rozhraní](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
- [IRemoteDebugApplicationThread – rozhraní](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
- [IRemoteDebugApplicationThreadEx – rozhraní](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
- [ISetNextStatement – rozhraní](../../winscript/reference/isetnextstatement-interface.md)  
  
- [ISimpleConnectionPoint – rozhraní](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
- [IWebAppDiagnosticsSetup – rozhraní](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
- [IWebAppDiagnosticsObjectInitialization – rozhraní](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
  V následující části jsou uvedeny konstanty, výčty a struktury používané pro ladění:  
  
- [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>Viz také:  
 [Přehled ladění aktivních skriptů](../../winscript/active-script-debugging-overview.md)