---
title: IDebugClassField | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734298"
---
# <a name="idebugclassfield"></a>IDebugClassField
Toto rozhraní představuje třídu jako typ.

## <a name="syntax"></a>Syntax

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Zprostředkovatel symbolů implementuje toto rozhraní u stejného objektu, který implementuje rozhraní [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) . Toto rozhraní je specializace, která představuje typ třídy.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Řada rozhraní obsahuje metody, které mohou vrátit toto rozhraní, včetně [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)a [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Můžete také použít [QueryInterface](/cpp/atl/queryinterface) k získání tohoto rozhraní z rozhraní [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , pokud metoda [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) vrací příznak `FIELD_TYPE_CLASS` .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod v rozhraních [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) a [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) implementuje toto rozhraní následující:

|Metoda|Popis|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Vytvoří enumerátor pro základní třídy této třídy.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Určuje, zda je ve třídě definováno konkrétní rozhraní.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Vytvoří enumerátor pro vnořené třídy této třídy.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Získá třídu, která uzavře tuto třídu.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Vytvoří enumerátor pro rozhraní implementované touto třídou.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Vytvoří enumerátor pro konstruktory této třídy.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Získá název výchozího indexeru.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Vytvoří enumerátor pro vnořené enumerátory této třídy.|

## <a name="requirements"></a>Požadavky
 Záhlaví: SH. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
