---
title: 'IDiaSession:: findChildren – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cca6778e5697c5f8821322c19d706d733d7f2b9f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742290"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
Načte všechny podřízené položky zadaného nadřazeného identifikátoru, který se shoduje s názvem a typem symbolu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT findChildren ( 
   IDiaSymbol*       parent,
   SymTagEnum        symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametry
 `parent`

pro Objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) představující nadřazený prvek. Pokud je tento nadřazený symbol funkce, modul nebo blok, pak jsou jeho Lexikální podřízené prvky vráceny v `ppResult`. Pokud je nadřazený symbol typu, pak jsou vráceny podřízené třídy. Pokud je tento parametr `NULL`, musí být `symtag` nastaven na `SymTagExe` nebo `SymTagNull`, což vrátí globální obor (soubor. exe).

 `symtag`

pro Určuje značku symbolu podřízených objektů, které mají být načteny. Hodnoty jsou pořízeny výčtem [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) . Nastavte na `SymTagNull` pro načtení všech podřízených objektů.

 `name`

pro Určuje název podřízených objektů, které mají být načteny. Nastavte na `NULL` pro všechny podřízené položky, které se mají načíst.

 `compareFlags`

pro Určuje možnosti porovnání použité pro porovnávání názvů. Hodnoty výčtového výčtu [namesearchoptions –](../../debugger/debug-interface-access/namesearchoptions.md) lze použít samostatně nebo v kombinaci.

 `ppResult`

mimo Vrátí objekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , který obsahuje seznam načtených podřízených symbolů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby.

## <a name="example"></a>Příklad
 Následující příklad ukazuje, jak najít místní proměnné funkce `pFunc`, které odpovídají názvu `szVarName`.

```C++
IDiaEnumSymbols* pEnum;
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );
```

## <a name="see-also"></a>Viz také:
- [Přehled](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [NameSearchOptions – výčet](../../debugger/debug-interface-access/namesearchoptions.md)
- [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)