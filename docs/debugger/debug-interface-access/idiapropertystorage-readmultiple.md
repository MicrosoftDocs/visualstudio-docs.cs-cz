---
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9cd1e419e1d08120274fc627a672eb52331ca50f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742875"
---
# <a name="idiapropertystoragereadmultiple"></a>IDiaPropertyStorage::ReadMultiple
Přečte zadané vlastnosti z aktuální sady vlastností.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadMultiple( 
   ULONG          cpspec,
   PROPSPEC const rgpspec,
   PROPVARIANT    rgvar
);
```

#### <a name="parameters"></a>Parametry
 `cpspec`

pro Počet vlastností určených v poli `rgpspec`. Pokud je nula, metoda nevrátí žádné vlastnosti, ale vrátí `S_OK` jako kód úspěšnosti.

 `rgpspec`

pro Pole vlastností, které mají být čteny. Vlastnosti lze zadat buď ID vlastnosti, nebo nepovinným názvem řetězce. V určitém pořadí v poli není nutné zadávat vlastnosti. Pole může obsahovat duplicitní vlastnosti. výsledkem jsou duplicitní hodnoty vlastností při návratu pro jednoduché vlastnosti. Nejednoduché vlastnosti by měly vracet odepření přístupu při pokusu o jejich otevření podruhé. Pole může obsahovat kombinaci ID vlastností a ID řetězců. V tomto poli musí být minimálně `cpspec` počet hodnot vlastností.

 `rgvar`

[in, out] Pole struktur `PROPVARIANT` (v oboru názvů Microsoft. VisualStudio. OLE. Interop), které se má vyplnit hodnotami pro každou vlastnost. Velikost pole musí být alespoň `cpspec` prvky. Volající nemusí v poli inicializovat hodnoty.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`. Vrátí `S_FALSE`, pokud nebyla nalezena jedna nebo více vlastností. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud vlastnost nebyla nalezena, odpovídající položka v `rgvar`ovém poli obsahuje `VARIANT` typu `VT_EMPTY`.

## <a name="see-also"></a>Viz také:
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)