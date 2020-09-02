---
title: 'IDiaTable:: Item | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6112a4580a68a98407723afab1ec3310d0f1cca9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62574798"
---
# <a name="idiatableitem"></a>IDiaTable::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte odkaz na zadanou položku v tabulce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `index`  
 pro Index položky tabulky v rozsahu 0 až `count` -1, kde `count` je vrácen metodou [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).  
  
 `element`  
 mimo Vrátí `IUnknown` objekt, který představuje zadanou položku tabulky.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tabulka představuje kolekci objektů. V závislosti na těchto objektech lze parametr elementu přetypovat na příslušné rozhraní. Například pokud tabulka obsahuje objekty [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , parametr elementu lze přetypovat na `IDiaSegment` rozhraní.  
  
 Je to běžnější přístup k volání `QueryInterface` metody v rozhraní [IDiaTable](../../debugger/debug-interface-access/idiatable.md) pro příslušné rozhraní enumerátoru a k přístupu k obsahu tabulky použijte metody čítače výčtu. Příklad naleznete v rozhraní [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
