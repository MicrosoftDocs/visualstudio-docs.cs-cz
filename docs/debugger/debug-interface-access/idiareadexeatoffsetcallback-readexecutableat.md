---
description: Přečte zadaný počet bajtů od zadaného posunu ze spustitelného souboru.
title: 'IDiaReadExeAtOffsetCallback:: ReadExecutableAt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9986ba6d493353644d8387b2df36a96cbf542933
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157361"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
Přečte zadaný počet bajtů od zadaného posunu ze spustitelného souboru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parametry
 Posunutí

pro Posun ve spustitelném souboru, který má začít číst.

 cbData

pro Počet bajtů, které se mají přečíst

 pcbData

mimo Vrátí počet přečtených bajtů.

 data []

[in, out] Pole, které je vyplněno bajty přečtenými ze souboru.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána kódem podpory DIA pro načtení datových bajtů ze spustitelného souboru pomocí absolutního posunu souboru. Tato metoda je volána v podpoře metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Viz také
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
