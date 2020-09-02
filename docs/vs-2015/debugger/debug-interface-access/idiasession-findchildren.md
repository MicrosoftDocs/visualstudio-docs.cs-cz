---
title: 'IDiaSession:: findChildren – | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findChildren method
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf274bb0f572da11a9aa43248da7eaa72a2e73c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150422"
---
# <a name="idiasessionfindchildren"></a>IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte všechny podřízené položky zadaného nadřazeného identifikátoru, který se shoduje s názvem a typem symbolu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 pro Objekt [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) představující nadřazený prvek. Pokud je tento nadřazený symbol funkce, modul nebo blok, pak jsou jeho Lexikální podřízené prvky vráceny v `ppResult` . Pokud je nadřazený symbol typu, pak jsou vráceny podřízené třídy. Pokud je tento parametr `NULL` , `symtag` musí být nastaven na `SymTagExe` nebo `SymTagNull` , což vrátí globální obor (soubor. exe).  
  
 `symtag`  
 pro Určuje značku symbolu podřízených objektů, které mají být načteny. Hodnoty jsou pořízeny výčtem [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) . Nastavte na `SymTagNull` načtení všech podřízených objektů.  
  
 `name`  
 pro Určuje název podřízených objektů, které mají být načteny. Nastavte na hodnotu `NULL` pro všechny podřízené položky, které mají být načteny.  
  
 `compareFlags`  
 pro Určuje možnosti porovnání použité pro porovnávání názvů. Hodnoty výčtového výčtu [namesearchoptions –](../../debugger/debug-interface-access/namesearchoptions.md) lze použít samostatně nebo v kombinaci.  
  
 `ppResult`  
 mimo Vrátí objekt [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) , který obsahuje seznam načtených podřízených symbolů.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak najít místní proměnné funkce `pFunc` , které odpovídají názvu `szVarName` .  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Výčet Namesearchoptions –](../../debugger/debug-interface-access/namesearchoptions.md)   
 [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md)
