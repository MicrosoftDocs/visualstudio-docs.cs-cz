---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2366c933bf072c295b29d06ff5610bd3735c0077
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741511"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Poskytuje metody pro procházení zásobníku pomocí informací v souboru. pdb.

## <a name="syntax"></a>Syntaxe

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
Následující tabulka ukazuje metody `IDiaStackWalker`.

|Metoda|Popis|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Načte enumerátor rámce zásobníku pro platformy x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Načte enumerátor rámce zásobníku pro konkrétní typ platformy.|

## <a name="remarks"></a>Poznámky
Toto rozhraní slouží k získání seznamu rámců zásobníku pro načtený modul. Každá z metod je předána objektu [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (implementováno klientskou aplikací), který poskytuje potřebné informace pro vytvoření seznamu rámců zásobníku.

## <a name="notes-for-callers"></a>Poznámky pro volající
Toto rozhraní se získá voláním metody `CoCreateInstance` s identifikátorem třídy `CLSID_DiaStackWalker` a ID rozhraní `IID_IDiaStackWalker`. Příklad ukazuje, jak se toto rozhraní získává.

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak získat rozhraní `IDiaStackWalker`.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

Knihovna: diaguids. lib

Knihovna DLL: Msdia80. dll

## <a name="see-also"></a>Viz také:
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
