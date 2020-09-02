---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 315af434271d57a8547963f2538ff1b799ef4fd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150026"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Rozhraní (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [Výčet SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
