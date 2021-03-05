---
description: Představuje rozšířenou verzi vyhodnocovacího filtru výrazů (EE).
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 150ede0d3063fa8905b7cdfa5d67da16c0f68eed
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152231"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Představuje rozšířenou verzi vyhodnocovacího filtru výrazů (EE).

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno pomocí vyhodnocovacího filtru výrazů.

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) toto rozhraní implementuje následující metody:

|Metoda|Popis|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Načte objekt služby s daným jedinečným identifikátorem.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Předvede moduly určené zadaným poskytovatelem symbolů.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Povolí vyhodnocení výrazu (EE) pro určení rozhraní zpětného volání, které stroj ladicího programu (DE) použije ke čtení nastavení metriky.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Nastaví cestu k modulu CLR (Common Language Runtime) zavedenému v ladicím programu.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Umožňuje ladicímu stroji před inicializací předat zpětné volání vyhodnocení výrazu.|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md) (Ukončení)|Zastaví a vyčistí vyhodnocovací filtr výrazů.|

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
