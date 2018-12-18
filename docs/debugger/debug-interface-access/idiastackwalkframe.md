---
title: Idiastackwalkframe – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f16d6f824b3b150406c23cce87e186fe9b120999
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31465626"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Udržuje zásobník kontextu mezi volání [idiaframedata::Execute –](../../debugger/debug-interface-access/idiaframedata-execute.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDiaStackWalkFrame`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Načte hodnotu registru.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Nastaví hodnotu registru.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Přečte paměti z bitové kopie.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Vyhledá zadaný zásobníku pro nejbližší funkce zpáteční adresu.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Vyhledá zadaný zásobníku pro zpáteční adresu nebo blízko zadaná adresa.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní se používá během spuštění programu pro čtení a zápis registry a také přístup k paměti a najít návratové adresy.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Klientská aplikace implementuje toto rozhraní a předá instanci rozhraní [idiaframedata::Execute –](../../debugger/debug-interface-access/idiaframedata-execute.md) metoda. Stejnou instanci tohoto rozhraní slouží znovu a znovu pro uchování stavu registrů při každém vyvolání `execute` metoda. `execute` Metoda toto rozhraní používá rovněž k určení zpáteční adresu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Dia2.h  
  
 Knihovna: diaguids.lib  
  
 Knihovny DLL: msdia80.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní (přístup k rozhraní SDK ladění)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)