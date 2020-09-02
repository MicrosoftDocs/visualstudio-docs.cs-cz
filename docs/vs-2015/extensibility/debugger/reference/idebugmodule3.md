---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 326efe27ae35de1550ebc8230ab3c94229589640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690954"
---
# <a name="idebugmodule3"></a>IDebugModule3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje modul, který podporuje alternativní umístění symbolů a JustMyCode stavů.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní pro podporu alternativních umístění symbolů a pro práci s JustMyCode stavy (viz [Glosář ladicího programu sady Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) pro definici "JustMyCode").  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní vrátí volání [getsymbolsearchinfo –](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) . DE pošle rozhraní [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) do Správce ladění relace (SDM) pomocí metody [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . Také volání [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na rozhraní [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) vrací toto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Kromě metod v rozhraní [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) toto rozhraní implementuje následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Vrátí seznam cest prohledávaných pro symboly a výsledky hledání jednotlivých cest.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Načte a inicializuje symboly pro aktuální modul.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Vrátí příznak určující, zda modul představuje uživatelský kód.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Určuje, zda má být modul považován za uživatelský kód.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Studio je typickým příjemcem tohoto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
