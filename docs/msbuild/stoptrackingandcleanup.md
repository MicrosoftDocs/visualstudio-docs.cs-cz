---
title: StopTrackingAndCleanup | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a80fcde7aeab601791c033bd21effce175b2cb9
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579562"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Zastaví všechna sledování a uvolní veškerou paměť využívanou relací sledování.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Návratová hodnota
 Vrátí hodnotu **HRESULT** s **úspěšně** nastaveným bitem, pokud bylo sledování zastaveno.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také
- [StartTrackingContext](../msbuild/starttrackingcontext.md)