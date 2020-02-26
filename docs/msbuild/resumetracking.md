---
title: ResumeTracking | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bb4663013a73d88ed7c2118816007705834162c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578447"
---
# <a name="resumetracking"></a>ResumeTracking
Pokračuje v sledování v aktuálním kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Návratová hodnota
 Hodnota **HRESULT** s **úspěšným** bitem nastaveným v případě, že sledování bylo obnoveno. **E_FAIL** se vrátí, pokud sledování nejde obnovit, protože kontext není dostupný.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také
- [SuspendTracking](../msbuild/suspendtracking.md)