---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: add26689122ffe4944b4bbad15106a825d43ccf0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794823"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode
Ladicí program v režimu krokování vynutí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ForceStepMode(  
   IRemoteDebugApplicationThread*  pStepThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStepThread`  
 [v] Vlákno pro monitorování ladění procesu krok. Pokud hodnotu null, PDM vymaže jeho taktování přístup z více vláken.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metodu `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iremotedebugapplicationex – rozhraní](http://msdn.microsoft.com/en-us/2f65fa67-06b7-4053-8945-22383ab66343)