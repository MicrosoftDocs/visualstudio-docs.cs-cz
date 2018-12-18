---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS – výčet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab542225e0238dbd40f90d9de66d43d0791e05e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796356"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS – výčet
Příznaky, které představují zda objektu haldy odkazoval na relaci objektu je metoda getter a setter. Používány [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) metoda, pokud je zadána hodnota PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS v `enumFlags` parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Hodnota|Popis|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|Tento objekt haldy odkazoval na relaci objekt není označený příjemce nebo setter metoda.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|Objekt haldy odkazoval na relaci objektu je metoda getter. Tyto informace se uloží v vysoké 2 bajtů (16 bitů) z [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) pole.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|Objekt haldy odkazoval na relaci objektu je Metoda setter. Tyto informace se uloží v vysoké 2 bajtů (16 bitů) z `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` pole.|