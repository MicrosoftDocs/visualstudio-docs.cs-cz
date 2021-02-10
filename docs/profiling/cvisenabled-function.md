---
title: Funkce Cvisenabled – | Microsoft Docs
description: Podívejte se na referenční informace o funkci Vizualizátor souběžnosti sady SDK Cvisenabled – (knihovna C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0be750f62e248b3d9f837c5baa561765e14bfba5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940940"
---
# <a name="cvisenabled-function"></a>Cvisenabled – – funkce
Určuje, zda jakákoli relace povolila zadaného zprostředkovatele ETW.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvIsEnabled(
   _In_ PCV_PROVIDER pProvider
);
HRESULT CvIsEnabledEx(
   _In_ PCV_PROVIDER pProvider,
   _In_ CV_IMPORTANCE level,
   _In_ int category
);
```

#### <a name="parameters"></a>Parametry
 `category` Kategorií.

 `level` Úroveň důležitosti.

 `pProvider` Platný objekt poskytovatele. Nemůže mít hodnotu NULL.

## <a name="return-value"></a>Vrácená hodnota
 S_OK, pokud je zprostředkovatel aktuálně povolen. S_FALSE, pokud je zprostředkovatel aktuálně zakázaný. Kód chyby v případě, že došlo k chybám. Pomocí neúspěšného makra zkontrolujte chybový stav a potom vyhledejte S_OK/S_FALSE.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers. h*

## <a name="see-also"></a>Viz také
- [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)