---
description: Načte číslo sestavení back-endu kompilátoru.
title: 'IDiaSymbol:: get_backEndBuild | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 02864e046e5227d22e6c07fb70efad80b53e3689
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156494"
---
# <a name="idiasymbolget_backendbuild"></a>IDiaSymbol::get_backEndBuild
Načte číslo sestavení back-endu kompilátoru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_backEndBuild ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí číslo sestavení back-endu. Viz poznámky.

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
