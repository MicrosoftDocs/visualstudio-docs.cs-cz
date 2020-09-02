---
title: 'IDiaStackWalker:: getEnumFrames2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames2 method
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25090ae66d28ebd9eb62f62f14979de1e82c5302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144721"
---
# <a name="idiastackwalkergetenumframes2"></a>IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte enumerátor rámce zásobníku pro konkrétní typ platformy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cpuid`  
 pro Hodnota z výčtu [výčtu CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) , která určuje typ platformy.  
  
 `pHelper`  
 pro Pomocný objekt [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) .  
  
 `ppEnum`  
 mimo Vrátí objekt [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) obsahující seznam objektů [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li získat seznam rámců zásobníku jenom pro platformu x86, zavolejte metodu [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [Výčet CV_CPU_TYPE_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
