---
title: 'IDiaStackWalkFrame:: readMemory – | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97a868973d2a514150b8d728e685523e918f88f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150165"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte paměť z image.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 pro Jedna z hodnot výčtu [výčtu memorytypeenum –](../../debugger/debug-interface-access/memorytypeenum.md) , která určuje typ paměti pro přístup.  
  
 `va`  
 pro Zahajte čtení umístění virtuální adresy v obrázku.  
  
 `cbData`  
 pro Velikost vyrovnávací paměti dat (v bajtech).  
  
 `pcbData`  
 mimo Vrátí počet vrácených bajtů. Pokud `data` je `NULL` , pak `pcbData` obsahuje celkový počet bajtů dat, která jsou k dispozici.  
  
 `data`  
 mimo Vyrovnávací paměť, která se má vyplnit daty ze zadaného umístění.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
