---
description: IDebugProcessSecurity je implementován dodavatelem portu, aby upozornil uživatele, který je připojen k procesu, není bezpečný.
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5e2ca72cc3d9c1d204c6fb1f90ccc9b03060cff
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166096"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` je implementován dodavatelem portu, aby upozornil uživatele, který je připojen k procesu, není bezpečný.

## <a name="syntax"></a>Syntax

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugProcessSecurity` .

|Metoda|Popis|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Získá uživatelské jméno z dodavatele portu.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Upozorňuje uživatele, že připojení k procesu ladění není bezpečné.|

## <a name="remarks"></a>Poznámky
 Implementací tohoto rozhraní zobrazíte upozornění a umožníte uživateli, aby se mohl zrušit, pokud proces, ke kterému se připojujete, může být považován za nebezpečný.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Porty](../../../extensibility/debugger/ports.md)
- [Dodavatelé portů](../../../extensibility/debugger/port-suppliers.md)
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
