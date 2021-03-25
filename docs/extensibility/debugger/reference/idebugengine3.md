---
description: Představuje jeden ladicí stroj (DE), který ovládá ladění jednoho nebo více modulů.
title: IDebugEngine3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3a10f439ba344b71cd31fd990928b7804b6c11d4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066187"
---
# <a name="idebugengine3"></a>IDebugEngine3
Představuje jeden ladicí stroj (DE), který ovládá ladění jednoho nebo více modulů.

## <a name="syntax"></a>Syntax

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno vlastním DE (pokud podporuje symboly) pro povolení stavu JustMyCode. Toto rozhraní musí být implementováno pomocí DE, pokud podporuje symboly a JustMyCode.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se volá správcem ladění relace (SDM), který bude předávat uživatelské možnosti pro umístění, ze kterých se mají načíst symboly. Také se volá za účelem nastavení identifikátoru GUID modulu při jeho vytvoření (GUID je založené na metrikách od doby registrace motoru). Model SDM také volá toto rozhraní, aby nastavil stav JustMyCode a nastavila všechny výjimky, které ladicí program v zadaném stavu zná.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) `IDebugEngine3` rozhraní zpřístupňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Nastaví cestu nebo cesty, které bude DE použít pro hledání symbolů ladění.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Načte symboly pro všechny moduly, které ještě nebyly načteny jejich symboly.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Obsahuje informace o JustMyCode informacích.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Nastaví identifikátor GUID z metrik.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Nastaví všechny výjimky, které jsou aktuálně nedokončené do zadaného stavu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
