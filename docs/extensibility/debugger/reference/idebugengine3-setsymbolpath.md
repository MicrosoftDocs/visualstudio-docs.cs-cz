---
title: IDebugEngine3::SetSymbolPath | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730671"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Nastaví cestu nebo cesty, které jsou vyhledávány pro ladění symboly.

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
[v] Řetězec obsahující cestu nebo cesty pro vyhledávání symbolů. Podrobnosti viz "Poznámky". Nemůže mít hodnotu null.

`szSymbolCachePath`\
[v] Řetězec obsahující místní cestu, kde mohou být symboly ukládány do mezipaměti. Nemůže mít hodnotu null.

`Flags`\
[v] Nepoužívá se; vždy nastavena na 0.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Řetězec `szSymbolSearchPath` je seznam jedné nebo více cest oddělených středníky k hledání symbolů. Tyto cesty mohou být místní cesta, cesta ve stylu UNC nebo adresa URL. Tyto cesty mohou být také kombinací různých typů. Pokud je cesta UNC (například \\\Symserver\Symbols), měl by ladicí modul určit, zda je cesta k serveru symbolů, a měl `szSymbolCachePath`by být schopen načíst symboly z tohoto serveru a ukládat je do mezipaměti v cestě určené programem .

 Cesta se symbolem může také obsahovat jedno nebo více umístění mezipaměti. Mezipaměti jsou uvedeny v pořadí podle priority, nejprve s mezipamětí s nejvyšší prioritou a jsou odděleny symboly * . Například:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Metoda [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) provádí skutečné zatížení symbolů.

## <a name="see-also"></a>Viz také
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
