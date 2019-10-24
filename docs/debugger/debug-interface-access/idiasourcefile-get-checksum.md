---
title: 'IDiaSourceFile:: get_checksum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f4367a7862dabe248dfbe08e64c45598abe3679
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741836"
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

mimo Vrátí počet bajtů kontrolního součtu. Tento parametr nelze `NULL`.

 `data`

[in, out] Vyrovnávací paměť, která je vyplněna bajty kontrolního součtu. Pokud je tento parametr `NULL`, vrátí `pcbData` počet požadovaných bajtů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Chcete-li určit typ algoritmu kontrolního součtu, který byl použit k vygenerování bajtů kontrolního součtu, zavolejte metodu [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .

 Kontrolní součet se obvykle generuje z image zdrojového souboru, takže změny ve zdrojovém souboru se projeví ve změnách v bajtech kontrolního součtu. Pokud bajty kontrolního součtu neodpovídají kontrolnímu součtu vygenerovanému z načtené bitové kopie souboru, měl by se soubor považovat za poškozený nebo úmyslně poškodit.

 Typické kontrolní součty nejsou větší než 32 bajtů, ale nepředpokládají, což je maximální velikost kontrolního součtu. Nastavte parametr `data` na `NULL`, abyste získali počet bajtů vyžadovaných k načtení kontrolního součtu. Pak přidělte vyrovnávací paměť odpovídající velikosti a zavolejte tuto metodu, jakmile se nová vyrovnávací paměť dokončí.

## <a name="see-also"></a>Viz také:
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)