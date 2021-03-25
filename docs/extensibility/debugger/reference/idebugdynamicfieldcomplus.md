---
description: Představuje dynamické pole pro objekt IDebugBinder.
title: IDebugDynamicFieldCOMPlus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f365bcadba5349ae43e1b75683ec100fdabbf338
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094013"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
Představuje dynamické pole pro objekt [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .

## <a name="syntax"></a>Syntax

```
IDebugDynamicFieldCOMPlus : IDebugDynamicField
```

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Načte typ daného primitivního typu.|
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Načte typ daného tokenu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
