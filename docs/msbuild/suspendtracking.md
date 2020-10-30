---
title: SuspendTracking | Microsoft Docs
description: Přečtěte si syntaxi, požadavky a návratovou hodnotu pro MSBuild SuspendTracking, která pozastaví sledování v aktuálním kontextu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048092"
---
# <a name="suspendtracking"></a>SuspendTracking

Pozastaví sledování v aktuálním kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Vrácená hodnota

 Hodnota **HRESULT** s **úspěšným** bitem nastaveným v případě pozastavení sledování.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [ResumeTracking](../msbuild/resumetracking.md)