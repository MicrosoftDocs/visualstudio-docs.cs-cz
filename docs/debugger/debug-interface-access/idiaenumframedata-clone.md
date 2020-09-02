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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c7325c861e8e5186faa4056edd9b282ab47e64d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468362"
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