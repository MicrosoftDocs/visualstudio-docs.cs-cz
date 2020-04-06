---
title: IEnumCodePaths2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717713"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Toto rozhraní představuje seznam cest kódu.

## <a name="syntax"></a>Syntaxe

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující seznam cest kódu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumCodePaths2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Načte zadaný počet cest kódu v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Přeskočí zadaný počet cest kódu v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Získá počet cest kódu v čítači výčtu.|

## <a name="remarks"></a>Poznámky
 Cesta kódu představuje větev bod nebo volání funkce v programu. Seznam cest kódu představuje cestu, přes kterou spuštění kódu přijata.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
