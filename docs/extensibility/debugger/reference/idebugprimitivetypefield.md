---
description: Představuje hodnotu výčtu primitivního typu z rozhraní IDebugField.
title: IDebugPrimitiveTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPrimitiveTypeField interface
ms.assetid: 73a428fd-797e-4ceb-8392-ba16f1c5226b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ba0fd92098d8089f6d80573c1db53e0b7e003b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150299"
---
# <a name="idebugprimitivetypefield"></a>IDebugPrimitiveTypeField
Představuje hodnotu výčtu primitivního typu z rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Syntax

```
IDebugPrimitiveTypeField : IDebugField
```

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) implementuje toto rozhraní následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetPrimitiveType](../../../extensibility/debugger/reference/idebugprimitivetypefield-getprimitivetype.md)|Načte primitivní typ přidružený k tomuto poli.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
