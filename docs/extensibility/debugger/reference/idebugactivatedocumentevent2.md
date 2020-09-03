---
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f601027ce9e71dff6687bcd6aa1b08f13f5ce0cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736616"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Ladicí stroj (DE) používá toto rozhraní k vyžádání dokumentu, který má být načten.

## <a name="syntax"></a>Syntax

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, když potřebuje zdrojový soubor, který se má otevřít. Toto rozhraní je implementováno pouze ladicími moduly, které pracují s nebo jsou součástí překladačů skriptů. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se musí implementovat na stejný objekt jako toto rozhraní (SDM používá pro přístup k rozhraní [QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` .).

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události v případě, že musí mít otevřený zdrojový soubor. Událost se posílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , kterou poskytuje SDM, když je připojená k laděnému programu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugActivateDocumentEvent2` .

|Metody|Popis|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Načte dokument, který se má aktivovat.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Získá kontext dokumentu, který popisuje pozici v dokumentu.|

## <a name="remarks"></a>Poznámky
 Typický scénář, ve kterém se používá toto rozhraní, je, pokud dojde k chybě analýzy v kódu skriptu na stránce HTML, skript DE pošle toto rozhraní do SDM, aby se mohl zobrazit dokument s chybou analýzy.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
