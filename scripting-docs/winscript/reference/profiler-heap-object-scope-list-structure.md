---
title: Profiler_heap_object_scope_list – struktura | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f0972faee11e15bd5d0e9a219e439df49d9672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796443"
---
# <a name="profilerheapobjectscopelist-structure"></a>PROFILER_HEAP_OBJECT_SCOPE_LIST – struktura
Tato struktura je přidružen pouze objekty funkce. V seznamu obor představuje uzavření účtu pro funkci jako seznam obory, kde každý obor je objekt haldy s seznamem přidružené vlastnosti představující proměnné v každém daném oboru. V některých případech je k dispozici názvy objektů v oboru nebudou k dispozici a pouze jejich index do seznamu vlastností.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|count|UINT|Počet oborů|  
|scopes|[Profiler_heap_object_id – typ](../../winscript/reference/profiler-heap-object-id-type.md)|Pole obory.|