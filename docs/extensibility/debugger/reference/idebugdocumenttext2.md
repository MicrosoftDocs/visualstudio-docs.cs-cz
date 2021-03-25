---
description: Toto rozhraní představuje textový dokument.
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 557ae68e63280348ab315c3240e05dbfc38a8d4d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066279"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Toto rozhraní představuje textový dokument.

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní, když je zdrojový kód, který je potřeba dodat, v textovém formátu. Vzhledem k tomu, že se jedná o nejobvyklejší případ, je-li DE implementuje rozhraní [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , měla by také implementovat `IDebugDocumentText2` rozhraní.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Použijte `QueryInterface` metodu pro získání tohoto rozhraní z `IDebugDocument2` rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod v `IDebugDocument2` rozhraní implementuje toto rozhraní následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetSize –](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Načte velikost textu na této pozici v dokumentu.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Načte text ze zadané pozice v dokumentu.|

## <a name="remarks"></a>Poznámky
 Objekt, který implementuje toto rozhraní, musí také implementovat <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> rozhraní, které poskytuje <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> rozhraní pro objekt [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
