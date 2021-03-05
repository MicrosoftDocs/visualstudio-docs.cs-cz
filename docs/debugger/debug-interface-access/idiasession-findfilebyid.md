---
description: Načte zdrojový soubor podle identifikátoru zdrojového souboru.
title: 'IDiaSession:: findFileById | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1bf868f91d0eb8d1c80382632be40f348889ab12
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147854"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Načte zdrojový soubor podle identifikátoru zdrojového souboru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findFileById ( 
   DWORD            uniqueId,
   IDiaSourceFile** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `uniqueId`

pro Určuje identifikátor zdrojového souboru.

 `ppResult`

mimo Vrátí objekt [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , který představuje načtený zdrojový soubor.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Identifikátor zdrojového souboru je jedinečná hodnota, která se interně používá pro DIA SDK, aby všechny zdrojové soubory byly jedinečné. Tato metoda se obvykle používá interně pro DIA SDK.

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
