---
description: Nastaví cestu nebo cesty, ve kterých jsou vyhledávány symboly ladění.
title: 'IDebugEngine3:: SetSymbolPath | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3bc24aa6ae07505f4f1fce16593f11e44e752a9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066110"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Nastaví cestu nebo cesty, ve kterých jsou vyhledávány symboly ladění.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>Parametry

`szSymbolSearchPath`\
pro Řetězec obsahující cestu pro hledání symbolů nebo cesty. Podrobnosti najdete v části "poznámky". Nemůže mít hodnotu null.

`szSymbolCachePath`\
pro Řetězec obsahující místní cestu, kam lze symboly ukládat do mezipaměti. Nemůže mít hodnotu null.

`Flags`\
pro Nepoužívá se; Vždycky nastavte na 0.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Řetězec `szSymbolSearchPath` je seznam jedné nebo více cest, které jsou odděleny středníky, pro hledání symbolů. Tyto cesty mohou být místní cesta, cesta ve stylu UNC nebo adresa URL. Tyto cesty mohou být také kombinací různých typů. Pokud je cesta ve formátu UNC (například \\ \Symserver\Symbols), pak modul ladění by měl určit, zda je cesta k serveru symbolů a zda má být schopna načíst symboly z tohoto serveru, ukládat je do mezipaměti v cestě určené parametrem `szSymbolCachePath` .

 Cesta k symbolu může také obsahovat jednu nebo více umístění mezipaměti. Mezipaměti jsou uvedené v pořadí podle priority, první mezipaměť s nejvyšší prioritou a oddělené symboly *. Například:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Metoda [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) provádí skutečné zatížení symbolů.

## <a name="see-also"></a>Viz také
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
