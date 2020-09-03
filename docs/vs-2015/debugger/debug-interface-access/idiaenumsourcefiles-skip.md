---
title: 'IDiaEnumSourceFiles:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14bfe8762d914770dd2523a431bada883d003511
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189771"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Přeskočí zadaný počet zdrojových souborů v sekvenci výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 pro Počet zdrojových souborů v sekvenci výčtu, které se mají přeskočit.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí, `S_OK` jinak vrátí, `S_FALSE` Pokud neexistují žádné další zdrojové soubory, které by bylo možné přeskočit.  
  
## <a name="see-also"></a>Viz také  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
