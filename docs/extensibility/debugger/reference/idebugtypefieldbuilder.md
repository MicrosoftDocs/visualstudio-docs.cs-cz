---
description: Představuje schopnost vytvořit pole, které představuje typ.
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bc4f58470792cac8bdb68ede4ddf37567bac208
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223105"
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
