---
title: StopTrackingAndCleanup | Microsoft Docs
description: Přečtěte si, jak MSBuild používá StopTrackingAndCleanup k zastavení veškerého sledování a uvolnění paměti, kterou využívá relace sledování.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e74e44289e4fd04acf82170584af8645767b63e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905241"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Zastaví všechna sledování a uvolní veškerou paměť využívanou relací sledování.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Vrácená hodnota

 Vrátí hodnotu **HRESULT** s **úspěšně** nastaveným bitem, pokud bylo sledování zastaveno.

## <a name="requirements"></a>Požadavky

 **Záhlaví:** *stoper. h*

## <a name="see-also"></a>Viz také

- [StartTrackingContext](../msbuild/starttrackingcontext.md)