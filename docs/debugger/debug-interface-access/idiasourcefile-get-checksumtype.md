---
title: 'IDiaSourceFile:: get_checksumType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88a192c9328d37447f12226a3d564ecae58fe41f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465319"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
Načte typ kontrolního součtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí typ kontrolního součtu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Typ kontrolního součtu je hodnota, kterou lze namapovat na algoritmus kontrolního součtu. Například standardní formát souboru PDB může mít obvykle jednu z následujících hodnot:

|Typ kontrolního součtu|Popisek CryptoAPI|Popis|
|-------------------|---------------------|-----------------|
|0|\<none>|K dispozici není žádný kontrolní součet.|
|1|`CALG_MD5`|byl vygenerován kontrolní součet algoritmu hash MD5.|
|2|`CALG_SHA1`|byl vygenerován kontrolní součet algoritmu hash SHA1.|

 `CryptoAPI`Popisky jsou z `ALG_ID` výčtu. Další informace o algoritmech hash najdete v `CryptoAPI` části Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] .

 Chcete-li získat skutečné bajty kontrolního součtu pro zdrojový soubor, zavolejte metodu [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .

## <a name="see-also"></a>Viz také
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)