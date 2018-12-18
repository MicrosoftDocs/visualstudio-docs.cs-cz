---
title: Idiatable::Item – | Dokumentace Microsoftu
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
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d1ebea7d657683d4174784a92ca2213851dcae9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816733"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Získá odkaz na zadané položce v tabulce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 [in] Index položky tabulky uvedeným v rozsahu 0 až `count`-1, kde `count` je vrácený [idiatable::get_count –](../../debugger/debug-interface-access/idiatable-get-count.md)metody.  
  
 `element`  
 [out] Vrátí `IUnknown` objekt, který reprezentuje položku zadané tabulky.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tabulka představuje kolekci objektů. V závislosti na tyto objekty parametr element přetypovat na odpovídající rozhraní. Například, pokud tabulka obsahuje [idiasegment –](../../debugger/debug-interface-access/idiasegment.md) objekty, pak parametr element může být převeden na `IDiaSegment` rozhraní.  
  
 To je běžnější přístup k volání `QueryInterface` metoda ve [idiatable –](../../debugger/debug-interface-access/idiatable.md) rozhraní pro příslušné enumerátor rozhraní a používat čítače výčtu specifické metody pro přístup k obsahu tabulky. Zobrazit [idiaenuminjectedsources –](../../debugger/debug-interface-access/idiaenuminjectedsources.md) rozhraní pro příklad.  
  
## <a name="see-also"></a>Viz také  
 [Idiatable –](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable::get_count –](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [Idiasegment –](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)



