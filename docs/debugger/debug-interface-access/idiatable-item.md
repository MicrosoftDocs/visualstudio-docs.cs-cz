---
title: 'IDiaTable:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db3baeaf7c30e0fa381c1d99d7a53e1eac5e2862
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853266"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Načte odkaz na zadanou položku v tabulce.

## <a name="syntax"></a>Syntaxe

```C++
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
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)