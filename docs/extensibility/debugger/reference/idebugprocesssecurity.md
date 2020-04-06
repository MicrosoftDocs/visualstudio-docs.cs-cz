---
title: IDebugProcessSecurity | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723188"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`implementována dodavatelem portu, aby uživatele varovala, že připojení k procesu není bezpečné.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugProcessSecurity`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Získá uživatelské jméno od dodavatele portu.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Varuje uživatele, že připojení k procesu ladění je nebezpečné.|

## <a name="remarks"></a>Poznámky
 Implementujte toto rozhraní zobrazit upozornění a umožnit uživateli zrušit, pokud proces, ke kterému se připojujete lze považovat za nebezpečné.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Porty](../../../extensibility/debugger/ports.md)
- [Dodavatelé portů](../../../extensibility/debugger/port-suppliers.md)
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
