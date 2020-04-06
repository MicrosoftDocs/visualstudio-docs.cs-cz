---
title: IDebugClassField | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734298"
---
# <a name="idebugclassfield"></a>IDebugClassField
Toto rozhraní představuje třídu jako typ.

## <a name="syntax"></a>Syntaxe

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolu implementuje toto rozhraní na stejném objektu, který implementuje rozhraní [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md) Toto rozhraní je specializace, která představuje typ třídy.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Počet rozhraní mají metody, které mohou vrátit toto rozhraní včetně [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)a [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Také můžete použít [QueryInterface](/cpp/atl/queryinterface) získat toto rozhraní z rozhraní [IDebugContainerField,](../../../extensibility/debugger/reference/idebugcontainerfield.md) `FIELD_TYPE_CLASS`pokud [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metoda vrátí příznak .

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod v rozhraních [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) a [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) toto rozhraní implementuje následující:

|Metoda|Popis|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Vytvoří čítač výčtu pro základní třídy této třídy.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Určuje, zda je ve třídě definováno určité rozhraní.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Vytvoří čítač výčtu pro vnořené třídy této třídy.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Získá třídu, která obklopuje tuto třídu.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Vytvoří čítač pro rozhraní implementované touto třídou.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Vytvoří čítač výčtu pro konstruktory této třídy.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Získá název výchozí indexeru.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Vytvoří čítač výčtu pro vnořené čítače výčtu této třídy.|

## <a name="requirements"></a>Požadavky
 Záhlaví: sh.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
