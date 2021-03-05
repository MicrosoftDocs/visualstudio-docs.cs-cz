---
description: Rozšiřuje IDebugTypeFieldBuilder tak, aby bylo možné vytvářet typy polí.
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e73642024cb379e804559ba8dd55eb44722cf580
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223001"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Rozšiřuje **IDebugTypeFieldBuilder** tak, aby bylo možné vytvářet typy polí.

## <a name="syntax"></a>Syntax

```
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder
```

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní lze získat od poskytovatele symbolů.

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) implementuje toto rozhraní následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Vytvoří pole zadaného typu a velikosti.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
