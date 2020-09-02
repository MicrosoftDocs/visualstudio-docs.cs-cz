---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27aab0ca87e589661798028ff38fb019dae815ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150141"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Udržuje kontext zásobníku mezi voláními metody [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IDiaStackWalkFrame` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Načte hodnotu registru.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Nastaví hodnotu registru.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Načte paměť z image.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Vyhledá zadaný rámec zásobníku pro nejbližší návratovou adresu funkce.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Vyhledá zadaný rámec zásobníku pro zpáteční adresu na zadané adrese nebo na ní.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní se používá při provádění programu ke čtení a zápisu registrů a také k přístupu do paměti a k nalezení návratových adres.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Klientská aplikace implementuje toto rozhraní a předá instanci rozhraní metodě [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) . Stejná instance tohoto rozhraní se znovu použije a znovu zachová stav registrů během každého vyvolání `execute` metody. `execute`Metoda také používá toto rozhraní k určení zpáteční adresy.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2. h  
  
 Knihovna: diaguids. lib  
  
 KNIHOVNA DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
