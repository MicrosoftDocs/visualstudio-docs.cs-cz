---
title: Výčet SOURCE_TEXT_ATTR | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573001"
---
# <a name="source_text_attr-enumeration"></a>SOURCE_TEXT_ATTR – výčet
Popisují atributy jednoho znaku zdrojového textu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Hodnota|Popis|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Znak je součástí klíčového slova jazyka, například klíčové slovo jazyka VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Znak je součástí bloku komentáře.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Znak není součástí zdrojového textu zkompilovaného jazyka. Například HTML obklopující blok skriptu.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Znak je součástí operátoru jazyka. Například:, aritmetický operátor **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Znak je součástí číselné konstanty jazyka.  Například konstanta 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Znak je součástí konstanty řetězce jazyka. Například řetězec "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Znak označuje začátek bloku funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Metody `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` a `IActiveScriptDebug::GetScriptTextAttributes` obvykle vrací jeden textový atribut na znak, pokud:  
  
- Příznak GETATTRTYPE_DEPSCAN je nastaven. v takovém případě může metoda vracet příznaky SOURCETEXT_ATTR_IDENTIFIER a SOURCETEXT_ATTR_MEMBERLOOKUP.  
  
- Příznak GETATTRFLAG_THIS je nastaven. v takovém případě může metoda vracet příznak SOURCETEXT_ATTR_THIS,  
  
- Příznak GETATTRFLAG_HUMANTEXT je nastaven. v takovém případě může metoda vracet příznak SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)