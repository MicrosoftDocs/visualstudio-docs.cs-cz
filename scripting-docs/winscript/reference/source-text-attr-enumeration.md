---
title: SOURCE_TEXT_ATTR – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796452"
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR – výčet
Popisují atributy jednoho znaku zdrojového textu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Hodnota|Popis|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Znak, který je součástí klíčové slovo jazyka, například VBScript, – klíčové slovo `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Znak, který je součástí blok komentáře.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Znak, který není součástí kompilované jazyk zdrojový text. Například HTML kolem blok skriptu.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Znak, který je součástí operátor jazyka. Příklad:, aritmetického operátoru  **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Znak, který je součástí číselnou konstantu jazyk.  Například konstanta 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Znak, který je součástí jazyk řetězcová konstanta. Například řetězec "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Znak, který označuje začátek blok – funkce|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, a `IActiveScriptDebug::GetScriptTextAttributes` metody vrací jeden atribut text na znaku, pokud:  
  
-   Nastavený příznak GETATTRTYPE_DEPSCAN, v takovém případě může metodu vrátit příznaky SOURCETEXT_ATTR_IDENTIFIER a SOURCETEXT_ATTR_MEMBERLOOKUP  
  
-   Nastavený příznak GETATTRFLAG_THIS, v takovém případě může metoda vrátí příznak SOURCETEXT_ATTR_THIS  
  
-   Je nastaven příznak GETATTRFLAG_HUMANTEXT, v takovém případě může metoda vrátí příznak SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Viz také  
 [Konstanty ladicího programu aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)