---
title: Idiaenumsymbolsbyaddr::prev – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 369aeb1294f999a8ef5a43a266bd596002d24cbd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783051"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte předchozí symboly v pořadí podle adresy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Počet symbolů v enumerátor, který se má načíst.  
  
 rgelt  
 [out] Pole, které je v tankujeme [idiasymbol –](../../debugger/debug-interface-access/idiasymbol.md) objekty, které představují požadované symboly.  
  
 pceltFetched  
 [out] Vrátí počet symbolů v načtených enumerátor.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` Pokud neexistují žádné předchozí symboly. V opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda aktualizuje pozice čítače výčtu počet načtených prvků.  
  
## <a name="see-also"></a>Viz také  
 [Idiaenumsymbolsbyaddr –](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



