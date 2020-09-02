---
title: 'IDiaStackWalkFrame:: readMemory – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f682f3fe0e300f84dc28b959497138a5019f954b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464826"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Načte paměť z image.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametry
 `type`

pro Jedna z hodnot výčtu [výčtu memorytypeenum –](../../debugger/debug-interface-access/memorytypeenum.md) , která určuje typ paměti pro přístup.

 `va`

pro Zahajte čtení umístění virtuální adresy v obrázku.

 `cbData`

pro Velikost vyrovnávací paměti dat (v bajtech).

 `pcbData`

mimo Vrátí počet vrácených bajtů. Pokud `data` je `NULL` , pak `pcbData` obsahuje celkový počet bajtů dat, která jsou k dispozici.

 `data`

mimo Vyrovnávací paměť, která se má vyplnit daty ze zadaného umístění.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)