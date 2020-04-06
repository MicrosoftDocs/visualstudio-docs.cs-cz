---
title: IDebugProperty3::DestroyObjectID | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f465bc06712c5032c6e90288ebd02406de4f2330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721198"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Zničí jedinečné ID přidružené k této vlastnosti, což znamená, že volající již nestará o identifikaci této vlastnosti jedinečně ze všech ostatních vlastností.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud ladicí modul nemusí podporovat jedinečné ID pro vlastnost (protože již sleduje je jedinečně interně), pak může jednoduše vrátit `E_NOTIMPL` pro tuto metodu.

 Jedinečné ID jsou vytvořeny s voláním [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) metoda, když volající chce, aby se ujistil, že tato vlastnost je jednoznačně identifikován mezi všechny ostatní vlastnosti.

## <a name="see-also"></a>Viz také
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
