---
title: 'IDebugProgram3:: ExecuteOnThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfc64f8ae928b4bb0057a16b8a74c6ddbff588c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148634"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Spustí ladicí program. Vlákno je vráceno, aby poskytovalo ladicí informace o tom, ve kterém vlákně se uživatel zobrazuje při provádění programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 pro Objekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Existují tři různé způsoby, jak může ladicí program pokračovat v provádění po zastavení:  
  
- Execute: zrušit všechny předchozí kroky a spustit až do další zarážky atd.  
  
- Krok: zrušit všechny staré kroky a spustit až do dokončení nového kroku.  
  
- Pokračovat: Spusťte znovu a nechejte aktivní všechny staré kroky.  
  
  Vlákno předané do `ExecuteOnThread` je užitečné při rozhodování, který krok chcete zrušit. Pokud vlákno neznáte, spuštění příkazu provést zruší všechny kroky. Ve znalostech vlákna stačí krok zrušit pouze v aktivním vlákně.  
  
## <a name="see-also"></a>Viz také  
 [Spustit](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
