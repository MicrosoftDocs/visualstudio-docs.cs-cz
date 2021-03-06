---
description: Toto rozhraní vypíše zarážky chyb spojené s nevyřízenou zarážkou.
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 71667ef0de4d72d2d6db2619c41c68b7949803e8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086583"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Toto rozhraní vypíše zarážky chyb spojené s nevyřízenou zarážkou.

## <a name="syntax"></a>Syntax

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní jako součást podpory zarážek.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Visual Studio volá [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) k získání tohoto rozhraní, které představuje seznam zarážek, které nelze svázat, nebo [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) pro získání tohoto rozhraní, které představuje seznam zarážek, které nejsou vázané.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugErrorBreakpoints2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Načte zadaný počet chybových zarážek ve výčtové sekvenci.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Přeskočí zadaný počet chybových zarážek v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Získá počet chybových zarážek v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní obsahuje seznam rozhraní [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) , z nichž každý popisuje zarážku, která nemohla být vázaná a proč nemohla být vázaná. Visual Studio používá `IEnumDebugErrorBreakpoint2` rozhraní k aktualizaci zarážek zobrazených v integrovaném vývojovém prostředí (IDE).

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
