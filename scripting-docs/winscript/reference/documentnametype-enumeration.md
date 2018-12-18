---
title: Výčet DOCUMENTNAMETYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791682"
---
# <a name="documentnametype-enumeration"></a>Výčet DOCUMENTNAMETYPE
Popisuje, jaký typ získat pro dokument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|DOCUMENTNAMETYPE_APPNODE|Získá název, jak se zobrazuje ve stromu aplikace.|  
|DOCUMENTNAMETYPE_TITLE|Získá název, jak se objevuje v záhlaví okna prohlížeče.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Získá název souboru bez cesty.|  
|DOCUMENTNAMETYPE_URL|Získá adresu URL dokumentu.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Získá název spolu s výčtu pro identifikaci.|  
  
## <a name="see-also"></a>Viz také  
 [Konstanty ladicího programu aktivních skriptů, výčty a struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)