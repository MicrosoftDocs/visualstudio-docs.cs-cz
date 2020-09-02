---
title: IDebugFunctionObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2 interface
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4150480d2e6686992d78727b6fed817da270145
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728427"
---
# <a name="idebugfunctionobject2"></a>IDebugFunctionObject2
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Představuje funkci a vylepšuje rozhraní [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Vyhodnocení výrazu (EE) implementuje toto rozhraní, aby reprezentovalo funkci.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Metody tohoto rozhraní **odIDebugFunctionObject** následující způsoby:

- Metoda **IDebugEvaluate** přebírá příznaky.

- Metoda **CreateObject** přebírá příznaky a má časový limit.

- Metoda **CreateStringObjectWithLength** trvá délku.

## <a name="methods"></a>Metody
 Toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|Vytvoří objekt, který používá konstruktor se zadaným nastavením příznaku vyhodnocení a hodnotou časového limitu.|
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|Vytvoří objekt String, který má zadanou délku.|
|[Vyhodnotit](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|Volá funkci a vrátí výslednou hodnotu jako objekt.|

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
