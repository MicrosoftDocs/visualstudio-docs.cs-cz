---
title: IEnumDebugCodeContexts2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717280"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Toto rozhraní vytvoří vyjmenovává kontexty kódu přidružené k relaci ladění nebo k určitému programu nebo dokumentu.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní představující seznam kontextů kódu pro konkrétní text pozici v programu nebo seznam kontextů kódu pro konkrétní kontext dokumentu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Volání [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) získat toto rozhraní představující seznam kontextů kódu pro konkrétní pozici textu ve zdrojovém dokumentu programu.

 Volání [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) získat toto rozhraní představující seznam všech kontextů kódu v určitém zdrojovém dokumentu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IEnumDebugCodeContexts2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[Další](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Načte zadaný počet kontextů kódu v pořadí výčtu.|
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Přeskočí zadaný počet kontextů kódu v pořadí výčtu.|
|[Resetovat](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Obnoví pořadí výčtu na začátek.|
|[Klonování](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Vytvoří čítač výčtu, který obsahuje stejný stav výčtu jako aktuální čítač výčtu.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Získá počet kontextů kódu v čítači výčtu.|

## <a name="remarks"></a>Poznámky
 Visual Studio volá [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) k naplnění seznamu kontextů kódu, ze kterých si uživatel může vybrat při nastavování dalšího příkazu nebo zobrazení demontáže pro zdrojový soubor. Může dojít k více kontextům kódu, například pokud existuje více instancí šablony stylu C++.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
