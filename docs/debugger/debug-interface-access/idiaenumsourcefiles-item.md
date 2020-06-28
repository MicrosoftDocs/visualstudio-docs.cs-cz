---
title: 'IDiaEnumSourceFiles:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Item method
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5175d38da97a0b3e64ad94692c62425ba6e9cc83
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467916"
---
# <a name="idiaenumsourcefilesitem"></a>IDiaEnumSourceFiles::Item
Načte zdrojový soubor prostřednictvím indexu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   DWORD            index,
   IDiaSourceFile** sourceFile
);
```

#### <a name="parameters"></a>Parametry
 index

pro Index objektu [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , který se má načíst Index je v rozsahu 0 až `count` -1, kde `count` je vrácen metodou [IDiaEnumSourceFiles:: get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md) .

 Požadovaný sourcefile

mimo Vrátí objekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) představující požadovaný zdrojový soubor.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)