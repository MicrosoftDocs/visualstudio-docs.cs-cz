---
title: IEnumDebugModules2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 612285aa4d5a249c0f922ccae88d98a7df83187b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716444"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Toto rozhraní vytváří seznam modulů.

## <a name="syntax"></a>Syntax

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní tak, aby představovalo seznam modulů načtených pro program.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [enummodules –](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) k získání tohoto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugModules2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Načte zadaný počet modulů v sekvenci výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Přeskočí zadaný počet modulů v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Získá počet modulů.|

## <a name="remarks"></a>Poznámky
 Visual Studio používá toto rozhraní primárně k aktualizaci okna **moduly** .

 Pro účely ladění v aplikaci Visual Studio je program logickou sekvencí kódových instrukcí, které mohou protínat hranice modulu, proto je potřeba seznam modulů pro jedno rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . První modul v seznamu obvykle obsahuje počáteční vstupní bod pro přidružený program.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)
