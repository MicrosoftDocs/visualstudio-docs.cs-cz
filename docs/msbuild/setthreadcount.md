---
title: SetThreadCount | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 102f46ec639719bb2bec70a38c6c7177c63793c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632326"
---
# <a name="setthreadcount"></a>SetThreadCount

Nastaví globální počet vláken a přiřadí tento počet aktuálnímu vláknu.

## <a name="syntax"></a>Syntaxe

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parametry

[v]`threadCount`

 Počet podprocesů, které chcete použít.

## <a name="return-value"></a>Návratová hodnota

 **HRESULT** s **succeeded** bit nastavit, pokud počet vláken byla aktualizována.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *FileTracker.h*