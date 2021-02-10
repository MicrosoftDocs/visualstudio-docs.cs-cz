---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dd4f85bfdfb58baff3301c2d858f52933f16d1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958593"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Představuje přizpůsobené uživatelské rozhraní pro výběr portu.

## <a name="syntax"></a>Syntax

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno pomocí dodavatelů portů. Dodavatel portu definuje svůj výběr portů tím, že ho zveřejňuje jako CLSID a odkazuje na `metricPortPickerCLSID` metriku na vystavené CLSID.

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody `IDebugPortPicker` .

|Metoda|Popis|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Zobrazí zadané dialogové okno, ve kterém může uživatel vybrat port.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Nastaví poskytovatele služby.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
