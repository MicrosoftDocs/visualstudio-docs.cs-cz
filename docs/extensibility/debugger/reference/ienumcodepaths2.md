---
description: Toto rozhraní představuje seznam cest kódu.
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e8ff8b4532ab67a969c8270eeb83bdf715e0b1c0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091731"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Toto rozhraní představuje seznam cest kódu.

## <a name="syntax"></a>Syntax

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní tak, aby představovalo seznam cest kódu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pro získání tohoto rozhraní volejte [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumCodePaths2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Načte zadaný počet cest kódu v sekvenci výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Přeskočí zadaný počet cest kódu v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Získá počet cest kódu v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Cesta kódu představuje bod větve nebo volání funkce v programu. Seznam cest kódu představuje cestu, přes kterou byl proveden provádění kódu.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
