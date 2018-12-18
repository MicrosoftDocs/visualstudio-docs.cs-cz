---
title: IDebugEnumField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dba0f00687725416755f26151d8a6d657e312923
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113904"
---
# <a name="idebugenumfield"></a>IDebugEnumField
Toto rozhraní představuje typ výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní představují výčet implementuje poskytovatele symbol.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Použití [QueryInterface](/cpp/atl/queryinterface) k získání tohoto rozhraní z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) rozhraní Pokud [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) vrátí `FIELD_TYPE_ENUM`.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce VTable pořadí  
 Kromě metod na `IDebugField` a `IDebugContainerField` rozhraní, toto rozhraní implementuje následujících metod:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Vrátí [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující název pro tento typ výčtu.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Vrací název konstanta výčtu spojené s danou hodnotou.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Vrátí hodnotu spojené s tímto názvem konstantní dané – výčet|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Vrátí hodnotu přidruženou konstantní název daného výčtu ale případu bude ignorována.|  
  
## <a name="remarks"></a>Poznámky  
 Je základní symbol, který je ve skutečnosti vázána k umístění s [vazby](../../../extensibility/debugger/reference/idebugbinder-bind.md).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel rozhraní symbol](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Vazby](../../../extensibility/debugger/reference/idebugbinder-bind.md)