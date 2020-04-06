---
title: IDebugAlias2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00e13da257c5477b3834ebb85bf6d481fe699362
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736366"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Představuje číselný alias pro proměnnou a umožňuje vyhodnocení výrazu (EE) získat doménu aplikace pro alias.

## <a name="syntax"></a>Syntaxe

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno modulem spravovanéladění (DE).

## <a name="methods"></a>Metody
 Kromě metod v rozhraní [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Načte identifikátor pro doménu aplikace.|

## <a name="remarks"></a>Poznámky
 Alias je desetinné číslo ve formě řetězce následované znakem #, například 1001#.

## <a name="requirements"></a>Požadavky
 Záhlaví: Ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
