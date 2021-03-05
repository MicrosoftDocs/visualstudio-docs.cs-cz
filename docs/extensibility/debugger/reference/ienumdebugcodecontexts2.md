---
description: Toto rozhraní vytvoří výčet kontextů kódu přidružených k relaci ladění nebo ke konkrétnímu programu nebo dokumentu.
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 82e3583333c784fffa55abf2e86f5a7335aeb7c1
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226927"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Toto rozhraní vytvoří výčet kontextů kódu přidružených k relaci ladění nebo ke konkrétnímu programu nebo dokumentu.

## <a name="syntax"></a>Syntax

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní tak, aby představovalo seznam kontextů kódu pro konkrétní pozici v programu, nebo seznam kontextů kódu pro konkrétní kontext dokumentu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Voláním [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) získáte toto rozhraní, které představuje seznam kontextů kódu pro konkrétní pozici textu ve zdrojovém dokumentu programu.

 Zavolejte [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) pro získání tohoto rozhraní, které představuje seznam všech kontextů kódu v konkrétním zdrojovém dokumentu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IEnumDebugCodeContexts2` .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Načte zadaný počet kontextů kódu ve výčtové sekvenci.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Přeskočí zadaný počet kontextů kódu v sekvenci výčtu.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Obnoví posloupnost výčtu na začátek.|
|[Klonovat](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Získá počet kontextů kódu v enumerátoru.|

## <a name="remarks"></a>Poznámky
 Visual Studio volá [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) k naplnění seznamu kontextů kódu, ze kterého může uživatel vybírat při nastavování dalšího příkazu nebo zobrazení zpětného překladu zdrojového souboru. Může dojít k více kontextům kódu, například když existuje více instancí šablony stylu C++.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
