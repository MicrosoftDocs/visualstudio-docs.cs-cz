---
title: IDebugProgram3::ExecuteOnThread | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: afca4a97380d010897ca1dfb7c6229f3f1897ef9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865940"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Spustí ladicí program. Vlákno se vrátí do poskytnout informace o ladicího programu, ve které vlákno je uživatel zobrazení při provádění programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Existují tři způsoby, že ladicí program může pokračovat v provádění po zastavení:  
  
- Spusťte: Zrušit všechny předchozí krok a spusťte až k další zarážce a tak dále.  
  
- Krok: Zrušit všechny původní kroku a spustit, dokud se nedokončí nový krok.  
  
- Pokračovat: Spusťte znovu a ponechání aktivní žádné staré kroku.  
  
  Vlákno předán `ExecuteOnThread` je užitečné, když se budete rozhodovat, ve kterém kroku zrušit. Pokud si nejste jisti vlákno, spusťte zruší všechny kroky. Se znalostí vlákna stačí zrušit kroku na aktivní vlákno.  
  
## <a name="see-also"></a>Viz také  
 [Spuštění](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)