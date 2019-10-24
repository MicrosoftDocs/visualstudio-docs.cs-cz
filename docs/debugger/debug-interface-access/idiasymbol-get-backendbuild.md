---
title: 'IDiaSymbol:: get_backEndBuild | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e45d2a32740393033851b6c97799ba32f2b0a46b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741015"
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
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí `S_FALSE` nebo kód chyby.

> [!NOTE]
> Návratová hodnota `S_FALSE` znamená, že vlastnost není k dispozici pro symbol.

## <a name="remarks"></a>Poznámky
 Kompilátor se obvykle skládá ze dvou primárních elementů: front-end (analyzátor), který zpracovává analýzu zdrojového kódu do přechodného formátu, a back-endu (generátor kódu), který převede zprostředkující formulář na sestavení. Pro front-end je neobvyklá verze, která má jinou verzi než back-end.

 Číslo verze front-endu nebo back-endu se skládá ze tří částí: \<major >. \<minor >. \<build >, kde \<major > je hlavní číslo verze, \<minor > je číslo dílčí verze a \<build > je číslo sestavení. Například 13.10.3077.

## <a name="requirements"></a>Požadavky

|Požadavek|Popis|
|-----------------|-----------------|
|Hlaviček|Dia2. h|
|Znění|DIA SDK v 7.0|

## <a name="see-also"></a>Viz také:
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)