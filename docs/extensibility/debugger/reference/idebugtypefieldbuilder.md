---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81532e2616eefb9cb584eae1a70371fd2f963be1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718396"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
Představuje schopnost vytvořit pole, které představuje typ.

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder : IUnknown
```

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se získává od poskytovatele symbolů.

## <a name="methods"></a>Metody
 Toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Vytvoří objekt, který představuje primitivní typ.|
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Vytvoří ukazatel na zadaný typ.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
