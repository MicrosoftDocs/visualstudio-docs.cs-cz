---
description: Přečte zadané vlastnosti z aktuální sady vlastností.
title: 'IDiaPropertyStorage:: ReadMultiple | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadMultiple
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7d0191d17074ec41b5fc73b3e33ba94b845a96e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148148"
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

pro Počet vlastností zadaných v `rgpspec` poli Pokud je nula, metoda nevrátí žádné vlastnosti, ale vrátí `S_OK` jako kód úspěšnosti.

 `rgpspec`

pro Pole vlastností, které mají být čteny. Vlastnosti lze zadat buď ID vlastnosti, nebo nepovinným názvem řetězce. V určitém pořadí v poli není nutné zadávat vlastnosti. Pole může obsahovat duplicitní vlastnosti. výsledkem jsou duplicitní hodnoty vlastností při návratu pro jednoduché vlastnosti. Nejednoduché vlastnosti by měly vracet odepření přístupu při pokusu o jejich otevření podruhé. Pole může obsahovat kombinaci ID vlastností a ID řetězců. Toto pole musí mít alespoň `cpspec` počet hodnot vlastností.

 `rgvar`

[in, out] Pole `PROPVARIANT` struktur (v oboru názvů Microsoft. VisualStudio. OLE. Interop), které se má vyplnit hodnotami pro každou vlastnost. Pole musí mít `cpspec` Velikost alespoň prvky. Volající nemusí v poli inicializovat hodnoty.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud nebyla nalezena jedna nebo více vlastností. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud vlastnost nebyla nalezena, odpovídající položka v `rgvar` poli obsahuje `VARIANT` typ s typem `VT_EMPTY` .

## <a name="see-also"></a>Viz také
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
