---
title: 'IDiaSourceFile:: get_checksumType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: c85c6ce8f03534c3ed810e530dbd12d8c6d115be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741834"
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
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Typ kontrolního součtu je hodnota, kterou lze namapovat na algoritmus kontrolního součtu. Například standardní formát souboru PDB může mít obvykle jednu z následujících hodnot:

|Typ kontrolního součtu|Popisek CryptoAPI|Popis|
|-------------------|---------------------|-----------------|
|0,8|\<none >|K dispozici není žádný kontrolní součet.|
|první|`CALG_MD5`|byl vygenerován kontrolní součet algoritmu hash MD5.|
|odst|`CALG_SHA1`|byl vygenerován kontrolní součet algoritmu hash SHA1.|

 Popisky `CryptoAPI` jsou z výčtu `ALG_ID`. Další informace o algoritmech hash naleznete v části `CryptoAPI` [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)] Microsoft.

 Chcete-li získat skutečné bajty kontrolního součtu pro zdrojový soubor, zavolejte metodu [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .

## <a name="see-also"></a>Viz také:
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)