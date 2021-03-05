---
description: Poskytuje podporu národního prostředí pro dodavatele portu.
title: IDebugPortSupplierLocale2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierLocale2 interface
ms.assetid: 910e7220-da2a-4339-9fff-9fb1bad3c28c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c29bd3fb882be6529daa0d26ab4cde23c11d0bc0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167058"
---
# <a name="idebugportsupplierlocale2"></a>IDebugPortSupplierLocale2
Poskytuje podporu národního prostředí pro dodavatele portu.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplierLocale2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní k nastavení národního prostředí.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody **IDebugPortSupplierLocale2**.

|Metoda|Popis|
|------------|-----------------|
|[SetLocale](../../../extensibility/debugger/reference/idebugportsupplierlocale2-setlocale.md)|Nastaví národní prostředí pro dodavatele portu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Portpriv. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
