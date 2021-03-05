---
description: Toto rozhraní představuje zdrojový dokument.
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96bf5821cb463b8a99f7376cb99b81ab8cae2206
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167344"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Toto rozhraní představuje zdrojový dokument.

## <a name="syntax"></a>Syntax

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] obvykle implementuje toto rozhraní. Ladicí stroj (DE) může toto rozhraní implementovat i v případě, že potřebuje dodat zdrojový kód a zdroj na disku neexistuje.  V takových případech by měl DE implementovat také rozhraní [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) a [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) a také některé další metody rozhraní [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) a [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 Metody v `IDebugDocumentContext2` `IDebugDisassemblyStream2` `IDebugDocumentPosition2` rozhraních,, a `IDebugActivateDocumentEvent2` vrací toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugDocument2` .

|Metoda|Popis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Získá název dokumentu v jednom z několika forem.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Získá identifikátor třídy dokumentu.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je implementováno pouze v případě, že zdrojový kód DE dodá. Například když ladíte skript na stránce HTML, DE dodá zdrojový kód, protože zdroj se stahuje nebo generuje dynamicky a neexistuje jako soubor na disku. Při ladění tradičních jazyků, jako je například C++, není nutné toto rozhraní implementovat.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
