---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1558aa8ca9cad93b00cf90f02f3af6d346b036b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698665"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní se odesílá ladicím modulem (DE) do Správce ladění relace (SDM), když vytvoří vlastnost, která je přidružena k určitému dokumentu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní, aby nahlásilo, že byla vytvořena vlastnost. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) přístup k rozhraní QueryInterface `IDebugEvent2` . Toto rozhraní je implementováno, pokud DE vytvořila vlastnost přidruženou ke skriptu, který byl načten nebo vytvořen a v případě, že se tento skript musí objevit v integrovaném vývojovém prostředí.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Vlastnost DE vytvoří a pošle tento objekt události k vytvoření sestavy vlastnosti. Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojená k laděnému programu.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Následující tabulka ukazuje metodu `IDebugPropertyCreateEvent2` rozhraní.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Získá novou vlastnost.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud má vlastnost k ní přidružený konkrétní dokument nebo skript, může DE odeslat tuto událost do SDM, aby aktualizovala okno **dokumenty skriptu** s názvem dokumentu. Model SDM bude volat [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) s argumentem `guidDocument` pro načtení `VARIANT` obsahujícího ukazatele [IUnknown](https://msdn.microsoft.com/library/e6b85472-e54b-4b8c-b19f-4454d6c05a8f) . Model SDM zavolá [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na tento ukazatel, aby získal rozhraní [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , které se používá k aktualizaci okna **dokumenty skriptu** .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
