---
description: Představuje numerický alias pro proměnnou a umožňuje vyhodnocovacímu filtru výrazů (EE) získat doménu aplikace pro daný alias.
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ca97fbe23e9b0c84c39e591c0fd9cfb997fca5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059038"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> V aplikaci Visual Studio 2015 je tento způsob implementace vyhodnocovacích vyhodnocení výrazů zastaralý. Informace o implementaci vyhodnocovacích vyhodnocení výrazů CLR naleznete v tématu [vyhodnocovací filtry výrazů CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [Ukázka vyhodnocovacího filtru spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Představuje numerický alias pro proměnnou a umožňuje vyhodnocovacímu filtru výrazů (EE) získat doménu aplikace pro daný alias.

## <a name="syntax"></a>Syntax

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno pomocí spravovaného ladicího stroje (DE).

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) implementuje toto rozhraní následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Načte identifikátor pro doménu aplikace.|

## <a name="remarks"></a>Poznámky
 Alias je desetinné číslo ve formě řetězce následovaný znakem #, například 1001 #.

## <a name="requirements"></a>Požadavky
 Záhlaví: ee. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
