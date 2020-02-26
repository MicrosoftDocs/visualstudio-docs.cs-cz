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
ms.openlocfilehash: 5b1eb28d5a54af1708fa8d3ea7a12887174a15bb
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579587"
---
# <a name="setthreadcount"></a>SetThreadCount
Nastaví počet globálních vláken a přiřadí tento počet k aktuálnímu vláknu.

## <a name="syntax"></a>Syntaxe

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parametry
[in] `threadCount`

 Počet vláken, která se mají použít.

## <a name="return-value"></a>Návratová hodnota
 Hodnota **HRESULT** s **úspěšně** nastaveným bitem, pokud byl počet vláken aktualizován.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *stoper. h*