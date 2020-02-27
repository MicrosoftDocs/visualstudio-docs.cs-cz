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
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632495"
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