---
title: 'IDiaFrameData:: get_program | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1480b7e3273e3746f95c01ab8913eb5c934edc39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99864941"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
Načte řetězec programu, který se používá k výpočtu sady registrů před voláním do aktuální funkce.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_program ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí řetězec programu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Řetězec programu je sekvence maker, která jsou interpretována za účelem vytvoření prologu. Například typický rámec zásobníku může použít řetězec programu `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Formát je zpětný polský zápis, kde operátory následují za operandy. `T0` představuje dočasnou proměnnou v zásobníku. Tento příklad provádí následující kroky:

1. Přesunout obsah registru `ebp` do `T0` .

2. Přidejte `4` k hodnotě v, pokud `T0` chcete vytvořit adresu, získat hodnotu z této adresy a uložit hodnotu v registru `eip` .

3. Získá hodnotu z adresy uložené v `T0` a uloží tuto hodnotu do pole Register `ebp` .

4. Přidejte `8` k hodnotě v `T0` a uložte tuto hodnotu do pole Register `esp` .

   Všimněte si, že řetězec programu je specifický pro procesor a na konvenci volání nastavené pro funkci reprezentovanou aktuálním rámcem zásobníku.

## <a name="see-also"></a>Viz také
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)