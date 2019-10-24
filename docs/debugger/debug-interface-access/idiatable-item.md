---
title: 'IDiaTable:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738716"
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

pro Index položky tabulky v rozsahu 0 až `count`-1, kde `count` vrací metoda [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).

 `element`

mimo Vrátí objekt `IUnknown`, který představuje zadanou položku tabulky.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tabulka představuje kolekci objektů. V závislosti na těchto objektech lze parametr elementu přetypovat na příslušné rozhraní. Například pokud tabulka obsahuje objekty [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , parametr elementu lze přetypovat na rozhraní `IDiaSegment`.

 Je to běžnější přístup k volání metody `QueryInterface` v rozhraní [IDiaTable](../../debugger/debug-interface-access/idiatable.md) pro příslušné rozhraní enumerátoru a k přístupu k obsahu tabulky použijte metody čítače výčtu. Příklad naleznete v rozhraní [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) .

## <a name="see-also"></a>Viz také:
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)