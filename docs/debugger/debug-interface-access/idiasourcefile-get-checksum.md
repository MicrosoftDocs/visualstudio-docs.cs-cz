---
description: Načte bajty kontrolního součtu.
title: 'IDiaSourceFile:: get_checksum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8aac5b35c98b8bb5b11bc623a274949ee32d9229
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147595"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
Načte bajty kontrolního součtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametry
 `cbData`

pro Velikost vyrovnávací paměti dat (v bajtech).

 `pcbData`

mimo Vrátí počet bajtů kontrolního součtu. Tento parametr nemůže být `NULL` .

 `data`

[in, out] Vyrovnávací paměť, která je vyplněna bajty kontrolního součtu. Pokud je tento parametr `NULL` , pak `pcbData` vrátí požadovaný počet bajtů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Chcete-li určit typ algoritmu kontrolního součtu, který byl použit k vygenerování bajtů kontrolního součtu, zavolejte metodu [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .

 Kontrolní součet se obvykle generuje z image zdrojového souboru, takže změny ve zdrojovém souboru se projeví ve změnách v bajtech kontrolního součtu. Pokud bajty kontrolního součtu neodpovídají kontrolnímu součtu vygenerovanému z načtené bitové kopie souboru, měl by se soubor považovat za poškozený nebo úmyslně poškodit.

 Typické kontrolní součty nejsou větší než 32 bajtů, ale nepředpokládají, což je maximální velikost kontrolního součtu. Nastavte `data` parametr na `NULL` , chcete-li získat počet bajtů vyžadovaných k načtení kontrolního součtu. Pak přidělte vyrovnávací paměť odpovídající velikosti a zavolejte tuto metodu, jakmile se nová vyrovnávací paměť dokončí.

## <a name="see-also"></a>Viz také
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
