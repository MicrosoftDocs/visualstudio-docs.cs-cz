---
title: 'IDiaStackWalkHelper:: readMemory – | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bef01cd29bb2312bd682f2f1f1150ee78da293e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150057"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přečte blok dat z image spustitelného souboru v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 pro Hodnota z výčtu [výčtu memorytypeenum –](../../debugger/debug-interface-access/memorytypeenum.md) určující typ paměti, která se má číst.  
  
 VA  
 pro Virtuální adresa v imagi, ze které se má začít číst.  
  
 `cbData`  
 pro Velikost vyrovnávací paměti dat v bajtech  
  
 `pcbData`  
 mimo Vrátí počet bajtů, které jsou ve skutečnosti čteny. Pokud `pbData` je `NULL` , pak toto je celkový počet bajtů dat, která jsou k dispozici.  
  
 `pbData`  
 [in, out] Vyrovnávací paměť, která je vyplněna čtenou pamětí.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum – výčet](../../debugger/debug-interface-access/memorytypeenum.md)
