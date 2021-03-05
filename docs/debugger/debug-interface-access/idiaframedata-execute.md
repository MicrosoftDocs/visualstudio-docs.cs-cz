---
description: Provede unwinding zásobníku a vrátí výsledky v rozhraní rámce procházení zásobníku.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 483854d0bea61af1bf8bd1f5338770fcc49b37be
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157810"
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
