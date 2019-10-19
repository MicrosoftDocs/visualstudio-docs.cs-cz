---
title: Výčet SCRIPTGCTYPE – | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fce16c756cf06c8cf01937114402832570a0cd3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574396"
---
# <a name="scriptgctype-enumeration"></a>SCRIPTGCTYPE – výčet
Typ uvolňování paměti, který má být proveden. Používá se v metodě [iactivescriptgarbagecollector –:: CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Hodnoty výčtu  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|Proveďte normální uvolňování paměti. Celočíselná hodnota je 0.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Proveďte vyčerpávající shromažďování paměti. Celočíselná hodnota je 1.|  
  
## <a name="see-also"></a>Viz také:  
 [Konstanty, výčty a kódy chyb aktivních skriptů](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)