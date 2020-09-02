---
title: Funkce Cvisenabled – | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53de9ee136c9bd12c732339b4c1c8a223fe1a3ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330062"
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