---
title: 'IDiaEnumStackFrames:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77d50a6c59ea376950d8cd4653f29ba7d04f36ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467839"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Načte zadaný počet prvků rámce zásobníku z sekvence výčtu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parametry
 celt

pro Počet elementů StackFrame ve výčtu, který má být načten.

 rgelt

mimo Pole, které se má vyplnit požadovanými [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objekty.

 pceltFetched

mimo Vrátí počet prvků rámce zásobníku v načteném enumerátoru.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , zda nejsou k dispozici žádné další rámce zásobníku. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)