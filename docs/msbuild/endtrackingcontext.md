---
title: EndTrackingContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b71f214a745222956c7dc9d582cc7fb2f1cfc427
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579700"
---
# <a name="endtrackingcontext"></a>EndTrackingContext
Ukončí aktuální sledovací kontext.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Návratová hodnota
Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl kontext sledování ukončen.

## <a name="requirements"></a>Požadavky
**Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také
- [StartTrackingContext](../msbuild/starttrackingcontext.md)
