---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fdc2006b45a664496615988251081f1000cdb428
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956282"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Toto rozhraní vyčísluje struktury [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .

## <a name="syntax"></a>Syntax

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Modul ladění (DE) implementuje toto rozhraní, aby poskytoval seznam struktur, které popisují aktuální zásobník volání.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) , aby získala toto rozhraní pokaždé, když dojde k zarážce, výjimce nebo zastavení v programu, který je laděn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugFrameInfo2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Načte zadaný počet struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) ve výčtové sekvenci.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Přeskočí zadaný počet struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) ve výčtové sekvenci.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Získá počet struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Visual Studio získá toto rozhraní jako první krok ke zpracování zarážky, výjimky nebo uživatelem vygenerovaného pozastavení v laděném programu. Seznam struktur [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) představuje aktuální zásobník volání s aktuální volání funkce na začátku seznamu a nejstarší volání funkce na konci seznamu. Každý `FRAMEINFO` představuje rámec zásobníku, kontext, ve kterém lze výrazy vyhodnotit, a místní proměnné, které se prohlédly na.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
