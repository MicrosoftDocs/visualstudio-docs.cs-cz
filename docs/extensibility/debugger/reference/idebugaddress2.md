---
title: IDebugAddress2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 402d8c8bcb50c570ff680b8fe1cf8d26f037ba17
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736569"
---
# <a name="idebugaddress2"></a>IDebugAddress2
Toto rozhraní poskytuje přístup k ID procesu, který vlastní objekt, jehož adresa je reprezentována tímto rozhraním.

## <a name="syntax"></a>Syntaxe

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní na stejném objektu, který implementuje rozhraní [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md) Toto rozhraní poskytuje přístup k ID procesu, který vlastní objekt, který souvisí s touto adresou.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí [rozhraní QueryInterface](/cpp/atl/queryinterface) získáte toto rozhraní z rozhraní [IDebugAddress.](../../../extensibility/debugger/reference/idebugaddress.md)

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z rozhraní [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Načte ID procesu, který vlastní objekt reprezentovaný tímto rozhraním.|

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
