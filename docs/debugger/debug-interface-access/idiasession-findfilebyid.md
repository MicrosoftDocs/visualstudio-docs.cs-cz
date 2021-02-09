---
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
ms.openlocfilehash: 172a02a2b2d818132131b94192af39d45e390254
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864255"
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