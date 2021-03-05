---
description: Usnadňuje procházení zásobníku pomocí souboru ladicí databáze programu (PDB).
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb014ebf703a0775e4f18208bc17d74a3fa29f12
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156739"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Usnadňuje procházení zásobníku pomocí souboru ladicí databáze programu (PDB).

## <a name="syntax"></a>Syntax

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>Metody v pořadí VTable
 Následující tabulka uvádí metody `IDiaStackWalkHelper` :

|Metoda|Popis|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Načte hodnotu registru.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Nastaví hodnotu registru.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Přečte blok dat z image spustitelného souboru v paměti.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Vyhledá zadaný rámec zásobníku pro nejbližší návratovou adresu funkce.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Vyhledá zadaný rámec zásobníku pro návratovou adresu na zadané adrese zásobníku nebo v ní.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Načte rámec zásobníku, který obsahuje zadanou virtuální adresu.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Načte symbol, který obsahuje zadanou virtuální adresu. **Poznámka:**  Symbol musí být typu `SymTagFunctionType` (hodnota z výčtu [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Vrátí blok dat PDATA přidružený k zadané virtuální adrese.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Načte počáteční virtuální adresu spustitelného souboru, kterému byla udělena virtuální adresa někde v paměťovém prostoru spustitelného souboru.|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je voláno kódem DIA k získání informací o spustitelném souboru pro sestavení seznamu rámců zásobníku během provádění programu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Klientská aplikace implementuje toto rozhraní, aby podporovalo procházení zásobníku během provádění programu. Instance tohoto rozhraní je předána metodě [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) nebo [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
