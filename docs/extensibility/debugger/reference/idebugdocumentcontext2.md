---
title: IDebugDocumentContext2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731728"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Toto rozhraní představuje pozici v dokumentu zdrojového souboru.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí modul (DE) implementuje toto rozhraní jako součást jeho podpory ladění na úrovni zdrojového kódu. Kromě pozice ve zdrojovém kódu toto rozhraní poskytuje metody pro porovnání kontextů a procházení dokumentu zdrojového kódu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Metody na několika rozhraních, většinou [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) a [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) rozhraní, vrátí toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugDocumentContext2`uvedeny metody .

|Metoda|Popis|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Získá dokument, který obsahuje tento kontext dokumentu.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Získá zobrazitelný název dokumentu, který obsahuje tento kontext dokumentu.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Načte seznam všech kontextů kódu přidružených k tomuto kontextu dokumentu.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Získá jazyk přidružený k tomuto kontextu dokumentu.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Získá rozsah příkazu souboru tohoto kontextu dokumentu.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Získá rozsah zdroje souboru tohoto kontextu dokumentu.|
|[Porovnání](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Porovná tento kontext dokumentu s daným polem kontextů dokumentu.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Přesune kontext dokumentu o daný počet příkazů nebo řádků.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
