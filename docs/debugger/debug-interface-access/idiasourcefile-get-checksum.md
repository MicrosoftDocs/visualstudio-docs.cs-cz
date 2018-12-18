---
title: Idiasourcefile::get_checksum – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f0484fce6f5355361c0c5156cd3c7ad827775c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919426"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
Načte kontrolní součet bajtů.  
  
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
 [in] Velikost vyrovnávací paměti dat v bajtech.  
  
 `pcbData`  
 [out] Vrátí počet bajtů kontrolního součtu. Tento parametr nemůže mít `NULL`.  
  
 `data`  
 [out v] Vyrovnávací paměť je vyplněna kontrolní součet bajtů. Pokud je tento parametr `NULL`, pak `pcbData` vrátí počet bajtů potřebných.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li určit typ kontrolního součtu algoritmus, který se použil k vygenerování kontrolních součtů bajtů, zavolejte [idiasourcefile::get_checksumtype –](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) metody.  
  
 Kontrolní součet se obvykle vygeneruje z bitové kopie souboru se zdrojovým tak změny v bajtech kontrolní součet se projeví změny ve zdrojovém souboru. Pokud kontrolní součet bajtů neodpovídá kontrolní součet vygenerovaná načíst obrázek soubor, pak tento soubor by měl být poškozen nebo manipulováno.  
  
 Typické kontrolní součty nejsou nikdy velikosti více než 32 bajtů, ale Nepředpokládejte, že je maximální velikost kontrolní součet. Nastavte `data` parametr `NULL` zobrazíte počet bajtů vyžadovaných k načtení kontrolního součtu. Potom přidělení vyrovnávací paměti odpovídající velikosti a volat tuto metodu jednou se nové vyrovnávací paměti.  
  
## <a name="see-also"></a>Viz také  
 [Idiasourcefile –](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)