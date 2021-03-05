---
description: Toto rozhraní poskytuje porty pro správce ladění relace (SDM).
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5e9523212ea83182e69e83b4f8353f1a9ba7dd8c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172036"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Toto rozhraní poskytuje porty pro správce ladění relace (SDM).

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
Vlastní dodavatel portu implementuje toto rozhraní, aby představovalo dodavatele portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
Volání `CoCreateInstance` s poskytovatelem portu `GUID` vrátí toto rozhraní (Toto je typický způsob, jak získat toto rozhraní). Například:

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

Volání [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) vrátí toto rozhraní, které představuje aktuálního dodavatele portu používaného v [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) vrátí toto rozhraní, které představuje dodavatele portu, který vytvořil port.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) představuje seznam `IDebugPortSupplier` rozhraní ( `IEnumDebugPortSuppliers` rozhraní se získává z [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), které představuje všechny dodavatele portů zaregistrované v [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ).

Ladicí stroj obvykle nekomunikuje s dodavatelem portu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDebugPortSupplier2` .

|Metoda|Popis|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Získá název dodavatele portu.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Získá identifikátor dodavatele portu.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Získá port od dodavatele portu.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Vytvoří výčet portů, které již existují.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Ověřuje, že dodavatel portu podporuje přidávání nových portů.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Přidá port.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Odebere port.|

## <a name="remarks"></a>Poznámky
Dodavatel portu se může identifikovat podle názvu a ID, přidat a odebrat porty a vytvořit výčet všech portů, které dodavatel portů poskytuje.

## <a name="requirements"></a>Požadavky
Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
