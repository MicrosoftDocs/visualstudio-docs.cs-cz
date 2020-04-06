---
title: IDebugIDECallback | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727836"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> V sadě Visual Studio 2015 tento způsob implementace vyhodnocení výrazů je zastaralé. Informace o implementaci vyhodnocení exprese CLR naleznete v tématu [Vyhodnocení exprese CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [ukázka vyhodnocení spravovaného výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Umožňuje vyhodnocení výrazu (EE) zobrazit zprávu ve výstupním okně ladicího programu.

## <a name="syntax"></a>Syntaxe

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto zpětné volání je implementováno modulem spravovanéladění.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Může být spotřebována vyhodnocení výrazu k odeslání výstupu do výstupního okna ladicího programu.

## <a name="methods"></a>Metody
 Toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[Zobrazit zprávu](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Odešle zadaný řetězec zprávy do výstupního okna ladicího programu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Ee.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
