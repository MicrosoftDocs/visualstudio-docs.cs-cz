---
title: SetThreadCount | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632326"
---
# <a name="setthreadcount"></a>SetThreadCount

Nastaví počet globálních vláken a přiřadí tento počet k aktuálnímu vláknu.

## <a name="syntax"></a>Syntaxe

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parametry

pro `threadCount`

 Počet vláken, která se mají použít.

## <a name="return-value"></a>Vrácená hodnota

 Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl počet vláken aktualizován.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*