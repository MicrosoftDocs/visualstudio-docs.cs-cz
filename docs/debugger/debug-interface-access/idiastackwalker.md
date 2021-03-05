---
description: Poskytuje metody pro procházení zásobníku pomocí informací v souboru. pdb.
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a86609f43bb6e825dac1b595b5e32951c3313a34
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147336"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Poskytuje metody pro procházení zásobníku pomocí informací v souboru. pdb.

## <a name="syntax"></a>Syntax

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDiaStackWalker` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Načte enumerátor rámce zásobníku pro platformy x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Načte enumerátor rámce zásobníku pro konkrétní typ platformy.|

## <a name="remarks"></a>Poznámky
Toto rozhraní slouží k získání seznamu rámců zásobníku pro načtený modul. Každá z metod je předána objektu [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (implementováno klientskou aplikací), který poskytuje potřebné informace pro vytvoření seznamu rámců zásobníku.

## <a name="notes-for-callers"></a>Poznámky pro volající
Toto rozhraní se získá voláním `CoCreateInstance` metody s identifikátorem třídy `CLSID_DiaStackWalker` a ID rozhraní `IID_IDiaStackWalker` . Příklad ukazuje, jak se toto rozhraní získává.

## <a name="example"></a>Příklad
Tento příklad ukazuje, jak získat `IDiaStackWalker` rozhraní.

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

KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
