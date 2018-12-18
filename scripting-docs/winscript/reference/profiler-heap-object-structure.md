---
title: Profiler_heap_object – struktura | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad50f03806cbf98450c0fc917f1a97ca7305d05c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796518"
---
# <a name="profilerheapobject-structure"></a>PROFILER_HEAP_OBJECT – struktura
Představuje objekty haldy získané nástrojem [iactivescriptprofilercontrol3::enumheap – metoda](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;    union {        PROFILER_HEAP_OBJECT_ID objectId;        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;    };    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;    USHORT flags;     USHORT optionalInfoCount;} PROFILER_HEAP_OBJECT;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|objectId|[Profiler_heap_object_id – typ](../../winscript/reference/profiler-heap-object-id-type.md)|ID objektu haldy.|  
|externalObjectAddress|[Profiler_external_object_address – typ](../../winscript/reference/profiler-external-object-address-type.md)|Adresa externí objekt objektu, například objekt přidělené C++, který je mimo haldě JavaScript.|  
|typeNameId|[Profiler_heap_object_name_id – typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|ID názvu typu objektu haldy načítají [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md). Pouze jeden z `externalObjectAddress` nebo `typeName` je k dispozici v závislosti na tom `flags` hodnotu.|  
|příznaky|[PROFILER_HEAP_OBJECT_FLAGS – výčet](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Příznaky, které obsahují základní informace o objektu haldy.|  
|optionalInfoCount|USHORT –|Počet [profiler_heap_object_optional_info – struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md) záznamy, které jsou k dispozici pro objekt haldy.|