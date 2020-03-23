---
title: StopTrackingAndCleanup | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: ee30bf031761fa7920dadad04d8f17a1bcc0b3a2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631988"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Zastaví veškeré sledování a uvolní paměť používanou v relaci sledování.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Návratová hodnota

 Vrátí **hresult** s **succeeded** bit nastavit, pokud sledování bylo zastaveno.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *FileTracker.h*

## <a name="see-also"></a>Viz také

- [StartTrackingContext](../msbuild/starttrackingcontext.md)