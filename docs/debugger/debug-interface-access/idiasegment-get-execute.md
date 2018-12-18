---
title: Idiasegment::get_execute – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e18aba27c0588f60f1e1f5ab3c0612eddc8f120c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843012"
---
# <a name="idiasegmentgetexecute"></a>IDiaSegment::get_execute
Získá příznak, který určuje, zda je spustitelný soubor segmentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_execute (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Vrátí `TRUE` , pokud segment je označená jako spustitelného souboru; jinak vrátí hodnotu, vrátí `FALSE`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` -li tato vlastnost není podporována. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)