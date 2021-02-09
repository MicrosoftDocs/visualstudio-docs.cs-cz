---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3642c17f342f824ea920fcf4adf0e11f5ef93215
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855030"
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

## <a name="see-also"></a>Viz také
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)