---
title: IDebugPointerField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63ac5f4f7e357ba256d7a796654100480a34533a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116409"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Toto rozhraní představuje typ ukazatele.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Zprostředkovatel symbol implementuje toto rozhraní představovat ukazatel.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Použití [QueryInterface](/cpp/atl/queryinterface) k získání tohoto rozhraní z [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) rozhraní Pokud [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) vrátí `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Kromě metod na `IDebugField` a `IDebugContainerField` rozhraní, toto rozhraní implementuje následující metodu:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Vrátí [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující cíl ukazatele.|  
  
## <a name="remarks"></a>Poznámky  
 V jazyce C/C++ ukazatel může být kontejner, pokud se používá s zápis pole. Například uděleno `char *pString`, `pString` má typ ukazatel na `char`. `pString[3]` má typ kontejneru, který je ukazatelem na `char` který odkazuje element čtvrtý tohoto kontejneru.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel rozhraní symbol](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)