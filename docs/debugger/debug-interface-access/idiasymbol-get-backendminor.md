---
description: Načte číslo dílčí verze kompilátoru back-end.
title: 'IDiaSymbol:: get_backEndMinor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMinor method
ms.assetid: 37f38d19-6685-440d-a477-7127c4f8699e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9506e142728235ad58560ab787c881c47b729a4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156473"
---
# <a name="idiasymbolget_backendminor"></a>IDiaSymbol::get_backEndMinor
Načte číslo dílčí verze kompilátoru back-end.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_backEndMinor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí číslo vedlejší verze back-endu. Viz poznámky.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí, `S_OK` jinak vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Kompilátor se obvykle skládá ze dvou primárních elementů: front-end (analyzátor), který zpracovává analýzu zdrojového kódu do přechodného formátu, a back-endu (generátor kódu), který převede zprostředkující formulář na sestavení. Pro front-end je neobvyklá verze, která má jinou verzi než back-end.

 Číslo verze na front-end nebo back-end se skládá ze tří částí: \<major> . \<minor> . \<build> , kde \<major> je hlavní číslo verze, \<minor> je číslo podverze a \<build> číslo sestavení. Například 13.10.3077.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Verze:|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
