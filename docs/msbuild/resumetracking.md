---
title: Pokračovatv sledování | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632495"
---
# <a name="resumetracking"></a>ResumeTracking

Obnoví sledování v aktuálním kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Návratová hodnota

 **HRESULT** s **succeeded** bit nastavit, pokud sledování bylo obnoveno. **E_FAIL** je vrácena, pokud sledování nelze obnovit, protože kontext nebyl k dispozici.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *FileTracker.h*

## <a name="see-also"></a>Viz také

- [SuspendTracking](../msbuild/suspendtracking.md)