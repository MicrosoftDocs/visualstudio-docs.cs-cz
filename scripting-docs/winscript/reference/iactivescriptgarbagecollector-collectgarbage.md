---
title: 'Iactivescriptgarbagecollector –:: CollectGarbage | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573587"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
Aktivní Hostitel skriptu volá tuto metodu, aby se spustilo uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parametry  
 `scriptgctype`  
 pro [Výčet scriptgctype –](../../winscript/reference/scriptgctype-enumeration.md) , který určuje, jestli se má provádět normální nebo vyčerpávající uvolňování paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí HRESULT.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptGarbageCollector – rozhraní](../../winscript/reference/iactivescriptgarbagecollector-interface.md)