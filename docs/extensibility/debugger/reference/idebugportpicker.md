---
title: IDebugPortPicker | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724843"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Představuje vlastní u(a) pro výběr portu.

## <a name="syntax"></a>Syntaxe

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno dodavateli portů. Dodavatel portu definuje jejich výběr portů tím, že jej `metricPortPickerCLSID` vystaví jako CLSID a namíří metriku na exponovaný identifikátor CLSID.

## <a name="methods"></a>Metody
 V následující tabulce jsou `IDebugPortPicker`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zobrazí zadané dialogové okno, které umožňuje uživateli vybrat port.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Nastaví poskytovatele služeb.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
