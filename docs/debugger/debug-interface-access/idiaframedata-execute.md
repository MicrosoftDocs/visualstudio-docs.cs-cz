---
title: 'IDiaFrameData:: Execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2587d10b613200b1bf850636f613abbb497e04de
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467447"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Provede unwinding zásobníku a vrátí výsledky v rozhraní rámce procházení zásobníku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parametry
 `frame`

pro Objekt [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) , který obsahuje stav registrů rámců.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. V následující tabulce jsou uvedeny možné návratové hodnoty pro tuto metodu.

|Hodnota|Popis|
|-----------|-----------------|
|E_DIA_INPROLOG|V kódu prologu nelze spustit rámec zásobníku.|
|E_DIA_SYNTAX|V programu Frame program došlo k chybě analýzy.|
|E_DIA_FRAME_ACCESS|Nelze získat přístup k registrům nebo paměti.|
|E_DIA_VALUE|Chyba při výpočtu hodnoty (například dělení nulou).|

## <a name="remarks"></a>Poznámky
 Tato metoda je volána během ladění pro odvinutí zásobníku. Objekt [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) je implementován klientskou aplikací pro příjem aktualizací registrů a k poskytnutí metod používaných `execute` metodou.

## <a name="see-also"></a>Viz také
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)