---
title: Konstanty, výčty a struktury profileru aktivních skriptů | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572688"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Konstanty, výčty a struktury profileru aktivních skriptů
Rozhraní profileru aktivních skriptů používají následující výčty.  
  
## <a name="constants-enumerations-and-structures"></a>Konstanty, výčty a struktury  
  
|Konstanty|Popis|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS – typ](../../winscript/reference/profiler-external-object-address-type.md)|Adresa externího objektu profileru. Používá se ve [struktuře PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) a [struktuře PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_HEAP_OBJECT_ID – typ](../../winscript/reference/profiler-heap-object-id-type.md)|ID objektu haldy. Používá se ve struktuře [PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)[struktury PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), struktuře [PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)a [struktuře PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_HEAP_OBJECT_NAME_ID – typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|ID názvu objektu haldy. Používá se ve [struktuře PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Výčty|Popis|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK – výčet](../../winscript/reference/profiler-event-mask-enumeration.md)|Určuje typy událostí, které se mají profilovat.|  
|[PROFILER_HEAP_ENUM_FLAGS – výčet](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Příznaky, které reprezentují, zda jsou vystaveny další informace o objektu haldy, na který odkazuje objekt v relaci objektu. Používá se v [metodě IActiveScriptProfilerControl5:: enumheap2 –](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[PROFILER_HEAP_OBJECT_FLAGS – výčet](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Příznaky, které reprezentují základní informace o objektu haldy. Používá se ve [struktuře PROFILER_HEAP_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE – výčet](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Představuje různé typy volitelných informací. Používá se ve [struktuře PROFILER_HEAP_OBJECT_OPTIONAL_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[PROFILER_RELATIONSHIP_INFO – výčet](../../winscript/reference/profiler-relationship-info-enumeration.md)|Představuje informace o objektu v relaci. Používá se ve [struktuře PROFILER_HEAP_OBJECT_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER_SCRIPT_TYPE – výčet](../../winscript/reference/profiler-script-type-enumeration.md)|Určuje typ skriptu.|  
  
|Struktury|Popis|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT – struktura](../../winscript/reference/profiler-heap-object-structure.md)|Představuje objekty haldy získané [metodou IActiveScriptProfilerControl3:: enumheap –](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO – struktura](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Představuje volitelné informace o objektech haldy.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP – struktura](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Představuje relaci objektu haldy.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST – struktura](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Představuje seznam vztahů, které patří do objektu haldy.|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST – struktura](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Tato struktura je přidružena pouze k objektům funkcí. Seznam rozsah představuje ukončení funkce jako seznam oborů, kde každý obor je objekt haldy s přidruženým seznamem vlastností, který představuje proměnné v daném oboru. V některých případech nemusí být názvy objektů v tomto oboru k dispozici, pouze jejich ID.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO – struktura](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Představuje informace o typu podřetězce.|  
  
## <a name="see-also"></a>Viz také:  
 [Rozhraní profileru aktivních skriptů](../../winscript/reference/active-script-profiler-interfaces.md)