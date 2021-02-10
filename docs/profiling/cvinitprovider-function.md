---
title: Funkce CvInitProvider – | Microsoft Docs
description: Podívejte se na referenční informace o funkci Vizualizátor souběžnosti sady SDK CvInitProvider – (knihovna C).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f23d3ceadf2ee8d1a0c6b53b395c379caf505179
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940992"
---
# <a name="cvinitprovider-function"></a>CvInitProvider – – funkce
Inicializuje poskytovatele značek. Musí být volána před jakoukoliv funkcí Vizualizátor souběžnosti sady SDK.

## <a name="syntax"></a>Syntaxe

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>Parametry
 `pGuid` Identifikátor GUID zprostředkovatele Nemůže mít hodnotu NULL.

 `ppProvider` Adresa výstupní proměnné, která bude ukládat kontext poskytovatele. Nemůže mít hodnotu NULL.

## <a name="return-value"></a>Vrácená hodnota
 S_OK při úspěšné inicializaci poskytovatele nebo kódu chyby v případě, že došlo k chybám. Ke kontrole chybového stavu použijte makra SUCCEEDED nebo FAILed.

## <a name="requirements"></a>Požadavky
 **Záhlaví:** *cvmarkers. h*

## <a name="see-also"></a>Viz také
- [Referenční dokumentace knihovny C++](../profiling/cpp-library-reference.md)