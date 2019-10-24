---
title: 'IDiaStackWalkFrame:: readMemory – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741480"
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

mimo Vrátí počet vrácených bajtů. Pokud je `data` `NULL`, pak `pcbData` obsahuje celkový počet bajtů dat, který je k dispozici.

 `data`

mimo Vyrovnávací paměť, která se má vyplnit daty ze zadaného umístění.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také:
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)