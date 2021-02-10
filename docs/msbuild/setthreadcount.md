---
title: SetThreadCount | Microsoft Docs
description: Přečtěte si, jak MSBuild používá SetThreadCount k nastavení počtu globálních vláken a přiřazení tohoto počtu k aktuálnímu vláknu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7282b8c4589007492e48994628910b3a4ef0691
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966159"
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