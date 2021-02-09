---
title: 'IDiaEnumFrameData:: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e5c2b6b70c1e6c4b68c5597aa71f17fb491be1ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99856885"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Clone( 
   IDiaEnumFrameData** ppenum
);
```

#### <a name="parameters"></a>Parametry
 ppenum

mimo Vrátí objekt [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) , který obsahuje duplikát objektu Enumerator. Data rámce nejsou duplikována, pouze enumerátor.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)