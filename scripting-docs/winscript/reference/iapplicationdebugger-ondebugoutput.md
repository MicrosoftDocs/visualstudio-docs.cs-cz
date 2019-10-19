---
title: 'Iapplicationdebugger –:: onDebugOutput | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebugOutput
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebugOutput
ms.assetid: 978d8bcf-16dc-4f24-a6bc-206adee2b2e9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ebbb7fb9f69af2f0977434a29015d79e8cf9178
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577849"
---
# <a name="iapplicationdebuggerondebugoutput"></a>IApplicationDebugger::onDebugOutput
Zpracovává výstupní událost ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT onDebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstr`  
 pro Řetězec, který se má zobrazit v ladicím programu  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program obvykle zobrazuje `pstr` v okně výstupu.  
  
 Tato metoda je volána, když je volána `IDebugApplication::DebugOutput`.  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iapplicationdebugger –](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)