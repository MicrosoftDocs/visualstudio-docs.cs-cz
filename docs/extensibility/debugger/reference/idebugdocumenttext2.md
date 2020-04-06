---
title: IDebugDocumentText2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731561"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Toto rozhraní představuje textový dokument.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní, když zdrojový kód, který potřebuje zadat, je v textové podobě. Vzhledem k tomu, že se jedná o nejtypičtější případ, pokud DE `IDebugDocumentText2` implementuje rozhraní [IDebugDocument2,](../../../extensibility/debugger/reference/idebugdocument2.md) měl by také implementovat rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Pomocí `QueryInterface` metody získat toto `IDebugDocument2` rozhraní z rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod na `IDebugDocument2` rozhraní toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Načte velikost textu na tomto místě v dokumentu.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Načte text ze zadaného umístění v dokumentu.|

## <a name="remarks"></a>Poznámky
 Objekt, který implementuje toto <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> rozhraní musí také <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> implementovat rozhraní, které poskytuje rozhraní pro objekt [IDebugDocumentTextEvents2.](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
