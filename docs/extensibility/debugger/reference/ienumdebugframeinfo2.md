---
title: IEnumDebugFrameInfo2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716607"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Toto rozhraní vyjmenovává struktury [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

## <a name="syntax"></a>Syntaxe

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní poskytnout seznam struktur, které popisuje aktuální zásobník volání.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) získat toto rozhraní vždy, když dojde k zarážka, výjimky nebo zastavení dojde v programu, který je laděn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugFrameInfo2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Načte zadaný počet [frameinfo](../../../extensibility/debugger/reference/frameinfo.md) struktur v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Přeskočí zadaný počet [frameinfo](../../../extensibility/debugger/reference/frameinfo.md) struktur v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Získá počet [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury v čítači výčtu.|

## <a name="remarks"></a>Poznámky
 Visual Studio získá toto rozhraní jako první krok ke zpracování zarážku, výjimku nebo uživatelem generované pauza v programu, který je laděn. Seznam [frameinfo](../../../extensibility/debugger/reference/frameinfo.md) struktury představuje aktuální zásobník volání, s aktuální volání funkce na začátku seznamu a nejstarší volání funkce na konci seznamu. Každý `FRAMEINFO` představuje rámec zásobníku, kontext, ve kterém lze vyhodnocovat výrazy a místní proměnné.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
