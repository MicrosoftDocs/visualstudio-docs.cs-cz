---
title: IDebugPortSupplier2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4aa26aa37b40c0e483342e6eb93cbac15bbbfc2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119471"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Toto rozhraní poskytuje porty pro relaci ladění správce (SDM).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Vlastní port dodavatele implementuje toto rozhraní k reprezentování jiného dodavatele portu.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Volání `CoCreateInstance` k portu dodavateli `GUID` vrátí toto rozhraní (to je typické způsob, jak můžete získat toto rozhraní). Příklad:  
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 Volání [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) vrátí toto rozhraní představující aktuální dodavatele port používán [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) vrátí toto rozhraní představující dodavatele port, který vytvořili port.  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) představuje seznam `IDebugPortSupplier` rozhraní ( `IEnumDebugPortSuppliers` rozhraní se získávají z [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), představující všechny dodavatele port zaregistrována [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 Modul ladění obvykle nekomunikuje s jiného dodavatele portu.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugPortSupplier2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Získá název dodavatele portu.|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Získá identifikátor dodavatele portu.|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Získá port od jiného dodavatele portu.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Vytvoří výčet porty, které již existují.|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Ověřuje, že port dodavatele podporuje přidání nové porty.|  
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Přidá port.|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Odebere port.|  
  
## <a name="remarks"></a>Poznámky  
 Port dodavatele můžete identifikovat podle názvu a podle ID, přidat a odebrat porty a výčet všechny porty, které poskytuje dodavatel port.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)