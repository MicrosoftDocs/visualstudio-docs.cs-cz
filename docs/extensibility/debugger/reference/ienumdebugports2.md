---
description: Toto rozhraní vytvoří výčet portů počítače nebo dodavatele portu.
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4b93aa34870d05b9a4ec0a9a0aa92f681735dfe3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224457"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Toto rozhraní vytvoří výčet portů počítače nebo dodavatele portu.

## <a name="syntax"></a>Syntax

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vlastní dodavatel portu implementuje toto rozhraní tak, aby představovalo seznam portů vytvořených dodavatelem. Visual Studio implementuje toto rozhraní v podpoře vlastního dodavatele portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Zavolejte [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) pro získání tohoto rozhraní, které představuje seznam portů vytvořených dodavatelem portu. Zavolejte [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) pro získání tohoto rozhraní, které představuje seznam portů uložených na disk.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugPorts2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Načte zadaný počet portů v sekvenci výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Přeskočí zadaný počet portů v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Získá počet portů v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Visual Studio používá toto rozhraní, které vám pomůžou naplnit seznam portů používaných pro připojení k procesům.

 Ladicí stroj obvykle toto rozhraní nepoužívá.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
