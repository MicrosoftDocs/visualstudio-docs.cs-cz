---
title: 'IDiaSymbol:: get_backEndMajor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndMajor method
ms.assetid: 900a05dd-c29b-44ad-b46b-f43bda819a66
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 725e08bbe9ae41dc44fb90033bec994a9ca45ab6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863562"
---
# <a name="idiasymbolget_backendmajor"></a>IDiaSymbol::get_backEndMajor
Načte číslo hlavní verze kompilátoru pro back-end.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_backEndMajor ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí číslo hlavní verze back-endu. Viz poznámky.

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