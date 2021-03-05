---
description: Toto rozhraní popisuje port.
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ca2d1d59c66c87c2dbb0fc256481d35ad590dbe
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142619"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Toto rozhraní popisuje port. Tento popis slouží k přidání portu na dodavatele portu.

## <a name="syntax"></a>Syntax

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Visual Studio obvykle implementuje toto rozhraní v procesu získání ladicího portu od dodavatele portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se předává do [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , aby se vytvořil port pro ladění. Volání [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) vrací toto rozhraní, které představuje požadavek použitý k vytvoření portu na prvním místě.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugPortRequest2` .

|Metoda|Popis|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Získá název portu, který se má vytvořit.|

## <a name="remarks"></a>Poznámky
 Ladicí stroj obvykle nekomunikuje s dodavatelem portu a nebude ho používat pro toto rozhraní.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
