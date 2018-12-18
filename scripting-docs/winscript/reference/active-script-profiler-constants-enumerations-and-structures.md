---
title: Konstanty profileru aktivních skriptů, výčty a struktury | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a37f64b14d0d732e48de66bb5268d47c95426937
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792144"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Konstanty, výčty a struktury profileru aktivních skriptů
Následující výčty jsou používány rozhraní profileru aktivních skriptů.  
  
## <a name="constants-enumerations-and-structures"></a>Konstanty, výčty a struktury  
  
|Konstanty|Popis|  
|---------------|-----------------|  
|[Profiler_external_object_address – typ](../../winscript/reference/profiler-external-object-address-type.md)|Adresa externího objektu profileru. Použít v [profiler_heap_object – struktura](../../winscript/reference/profiler-heap-object-structure.md) a [profiler_heap_object_relationship – struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Profiler_heap_object_id – typ](../../winscript/reference/profiler-heap-object-id-type.md)|ID objektu haldy. Použít v [profiler_heap_object – struktura](../../winscript/reference/profiler-heap-object-structure.md)[profiler_heap_object_scope_list – struktura](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [profiler_heap_object_optional_info – struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md)a [Profiler_heap_object_relationship – struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Profiler_heap_object_name_id – typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|ID názvu objektu haldy. Použít v [profiler_heap_object – struktura](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Výčty|Popis|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK – výčet](../../winscript/reference/profiler-event-mask-enumeration.md)|Určuje typy událostí, které by měl být profilovaným.|  
|[PROFILER_HEAP_ENUM_FLAGS – výčet](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Příznaky, které představují zda doplňující informace o objektu haldy odkazoval na relaci objekt má přístup. Používány [iactivescriptprofilercontrol5::enumheap2 – metoda](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[PROFILER_HEAP_OBJECT_FLAGS – výčet](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Příznaky, které představují základní informace o objektu haldy. Používány [profiler_heap_object – struktura](../../winscript/reference/profiler-heap-object-structure.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE – výčet](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Představuje různé typy volitelné informace. Použít v [profiler_heap_object_optional_info – struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[PROFILER_RELATIONSHIP_INFO – výčet](../../winscript/reference/profiler-relationship-info-enumeration.md)|Představuje informace o objektu v relaci. Použít v [profiler_heap_object_relationship – struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_SCRIPT_TYPE – výčet](../../winscript/reference/profiler-script-type-enumeration.md)|Určuje typ skriptu.|  
  
|Struktury|Popis|  
|----------------|-----------------|  
|[Profiler_heap_object – struktura](../../winscript/reference/profiler-heap-object-structure.md)|Představuje objekty haldy získané nástrojem [iactivescriptprofilercontrol3::enumheap – metoda](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Profiler_heap_object_optional_info – struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Volitelné informace o objektech halda představuje.|  
|[Profiler_heap_object_relationship – struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Představuje relaci objektu haldy.|  
|[Profiler_heap_object_relationship_list – struktura](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Představuje seznam vztahy, které patří do objektu haldy.|  
|[Profiler_heap_object_scope_list – struktura](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Tato struktura je přidružen pouze objekty funkce. V seznamu obor představuje uzavření účtu pro funkci jako seznam obory, kde každý obor je objekt haldy s seznamem přidružené vlastnosti představující proměnné v každém daném oboru. V některých případech nemusí být k dispozici, názvy objektů v tomto oboru pouze jejich ID.|  
|[Struktura PROFILER_PROPERTY_TYPE_SUBSTRING_INFO](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Představuje informace o typu dílčí řetězec.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní profileru aktivních skriptů](../../winscript/reference/active-script-profiler-interfaces.md)