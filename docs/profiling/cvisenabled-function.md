---
title: Funkce CvIsEnabled | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92763e352d04d5aa3e88a68bad7adfcd05897027
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62945411"
---
# <a name="cvisenabled-function"></a>CvIsEnabled
Určuje, zda nějaká relace povolila zadaného zprostředkovatele ETW.

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
 `category`Kategorie.

 `level`Úroveň důležitosti.

 `pProvider`Platný objekt zprostředkovatele. Nemůže být null.

## <a name="return-value"></a>Návratová hodnota
 S_OK, pokud je aktuálně povolen zprostředkovatel. S_FALSE, pokud je zprostředkovatel aktuálně zakázán. Kód chyby v případě, že došlo k chybám. Pomocí makra FAILED zkontrolujte chybový stav a potom zkontrolujte S_OK/S_FALSE.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers.h*

## <a name="see-also"></a>Viz také
- [Odkaz na knihovnu C++](../profiling/cpp-library-reference.md)