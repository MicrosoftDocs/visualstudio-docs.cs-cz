---
title: Výčet DOCUMENTNAMETYPE – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575879"
---
# <a name="documentnametype-enumeration"></a>Výčet DOCUMENTNAMETYPE
Popisuje, jaký typ získat pro dokument.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Získá název tak, jak se zobrazuje ve stromu aplikace.|  
|DOCUMENTNAMETYPE_TITLE|Získá název tak, jak se zobrazuje v záhlaví prohlížeče.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Získá název souboru bez cesty.|  
|DOCUMENTNAMETYPE_URL|Získá adresu URL dokumentu.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Získá název připojený ke výčtu pro identifikaci.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a struktury ladicího programu aktivních skriptů](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)