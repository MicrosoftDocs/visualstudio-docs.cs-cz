---
title: 'IDiaSession:: get_globalScope | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_globalScope method
ms.assetid: 75d128a8-3dce-40ed-b392-de3fdda041b7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc1e935ab47fd815c8f132dbeee21e21c9ba6350
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85465445"
---
# <a name="idiasessionget_globalscope"></a>IDiaSession::get_globalScope
Načte odkaz na globální rozsah.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_globalScope ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , který představuje globální rozsah.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)