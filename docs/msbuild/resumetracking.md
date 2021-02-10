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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd6722ca0b930d66a386732dac466a8e4fe36976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937911"
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