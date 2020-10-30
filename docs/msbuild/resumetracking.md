---
title: ResumeTracking | Microsoft Docs
description: Přečtěte si syntaxi, požadavky a návratovou hodnotu pro MSBuild ResumeTracking, která pokračuje v sledování v aktuálním kontextu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9af7c90342638fb0c154e7de21fa111d560905d0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048427"
---
# <a name="resumetracking"></a>ResumeTracking

Pokračuje v sledování v aktuálním kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Vrácená hodnota

 Hodnota **HRESULT** s **úspěšným** bitem nastaveným v případě, že sledování bylo obnoveno. **E_FAIL** se vrátí, pokud sledování nejde obnovit, protože kontext není dostupný.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [SuspendTracking](../msbuild/suspendtracking.md)