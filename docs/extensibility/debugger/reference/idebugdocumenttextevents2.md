---
description: Toto rozhraní slouží k upozornění sady Visual Studio na změny zdrojového dokumentu, které jsou dodány ladicím modulem.
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: edf7cd483b39fb1fb5dc182a08bbbca8295b2359
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094091"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Toto rozhraní slouží k upozornění sady Visual Studio na změny zdrojového dokumentu, které jsou dodány ladicím modulem.

## <a name="syntax"></a>Syntax

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 DE implementuje toto rozhraní pro podporu provádění změn zdrojového kódu. Toto rozhraní je obvykle implementováno na stejném objektu, který implementuje rozhraní [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Získá toto rozhraní prostřednictvím volání <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metody. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>Rozhraní je získáno z volání <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> metody. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>Rozhraní je získáno voláním metody [QueryInterface](/cpp/atl/queryinterface) v rozhraní [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDebugDocumentTextEvents2` .

|Metoda|Popis|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Indikuje, že celý dokument byl zničen.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Upozorní ladicí balíček, že text byl vložen do dokumentu.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Upozorní ladicí balíček, že text byl z dokumentu odebrán.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Upozorní ladicí balíček, že text byl v dokumentu nahrazen.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Oznamuje balíčku ladění, že jsou v dokumentu aktualizovány atributy textu.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Oznamuje přijímači události, že byly aktualizovány atributy dokumentu.|

## <a name="remarks"></a>Poznámky
 Výhodou rozhraní mohou být pouze moduly ladění, které poskytují vlastní dokumenty `IDebugDocumentTextEvent2` . Příkladem může být skriptovací ladicí stroj. V procesu interpretace skriptů lze vytvořit nový zdrojový kód, který není přítomen v žádném souboru na disku a je znám pouze v případě DE.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
