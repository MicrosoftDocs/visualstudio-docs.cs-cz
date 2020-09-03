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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632005"
---
# <a name="suspendtracking"></a>SuspendTracking

Pozastaví sledování v aktuálním kontextu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Vrácená hodnota

 Hodnota **HRESULT** s **úspěšným** bitem nastaveným v případě pozastavení sledování.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [ResumeTracking](../msbuild/resumetracking.md)