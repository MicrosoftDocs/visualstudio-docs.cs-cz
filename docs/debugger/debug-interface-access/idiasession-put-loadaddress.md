---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39db3bc0e0107e734f5de3f6902a2ca0fcc55bb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741893"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
Nastaví adresu zatížení pro spustitelný soubor, který odpovídá symbolům v tomto úložišti symbolů.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT put_loadAddress ( 
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Parametry
 `NewVal`

pro Načíst adresu pro spustitelný soubor.

## <a name="remarks"></a>Poznámky
 Vlastnosti virtuální adresy symbolu (VA) se vypočítávají pomocí hodnoty této metody. Pokud je tato vlastnost nastavená na nenulovou hodnotu, virtuální adresy se nepočítají.

> [!NOTE]
> Tato metoda musí být volána, když získáte objekt [IDiaSession](../../debugger/debug-interface-access/idiasession.md) a před tím, než začnete používat objekt, pokud potřebujete použít jakékoli virtuální vlastnosti na symbolech.

## <a name="see-also"></a>Viz také:
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)