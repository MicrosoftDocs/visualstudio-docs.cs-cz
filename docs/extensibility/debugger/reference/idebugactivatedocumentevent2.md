---
title: IDebugActivateDocumentEvent2 | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736616"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
Ladicí modul (DE) používá toto rozhraní k vyžádání načtení dokumentu.

## <a name="syntax"></a>Syntaxe

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní, když potřebuje zdrojový soubor, který má být otevřen. Toto rozhraní je implementováno pouze ladicími moduly, které pracují s interprety skriptu nebo jsou součástí jejich interpretů. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto `IDebugEvent2` rozhraní (SDM používá [QueryInterface](/cpp/atl/queryinterface) pro přístup k rozhraní).

## <a name="notes-for-callers"></a>Poznámky pro volající
 DE vytvoří a odešle tento objekt události, když potřebuje otevřít zdrojový soubor. Událost je odeslána pomocí funkce zpětného volání [IDebugCallBack2](../../../extensibility/debugger/reference/idebugeventcallback2.md) zajišťované sdm, když je připojena k programu, který je odladěn.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 V následující tabulce jsou `IDebugActivateDocumentEvent2`uvedeny metody .

|Metody|Popis|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Získá dokument aktivovat.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Získá kontext dokumentu, který popisuje pozici v rámci dokumentu.|

## <a name="remarks"></a>Poznámky
 Typický scénář, ve kterém se používá toto rozhraní je, pokud dojde k chybě analýzy v kódu skriptu na stránce HTML, skript DE odešle toto rozhraní do SDM tak, aby dokument s chybou analýzy lze zobrazit.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
