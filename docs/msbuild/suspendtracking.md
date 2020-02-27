---
title: SuspendTracking | Microsoft Docs
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
ms.openlocfilehash: 950c6a07a46f7f4b970912e576257a577021367e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632005"
---
# <a name="suspendtracking"></a>SuspendTracking

Pozastaví sledování v aktuálním kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Návratová hodnota

 Hodnota **HRESULT** s **úspěšným** bitem nastaveným v případě pozastavení sledování.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [ResumeTracking](../msbuild/resumetracking.md)