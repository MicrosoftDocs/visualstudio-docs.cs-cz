---
title: 'IDebugEngineProgram2:: WatchForThreadStep | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59489af368c2e95a2d3cc93edbd6f7ab02a1c156
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195656"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Sleduje spuštění (nebo zastaví sledování provádění) k tomu, aby se v daném vlákně stalo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pOriginatingProgram`  
 pro Objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , který představuje program, který je v programu Step.  
  
 `dwTid`  
 pro Určuje identifikátor vlákna, které se má sledovat.  
  
 `fWatch`  
 pro Nenulová ( `TRUE` ) znamená zahájit sledování spuštění na vlákně identifikovaném `dwTid` . v opačném případě nula ( `FALSE` ) znamená zastavit sledování provádění `dwTid` .  
  
 `dwFrame`  
 pro Určuje index rámce, který řídí typ kroku. Pokud je tato hodnota nula (0), je typ kroku "krok do" a program by měl být zastaven pokaždé, když je vlákno identifikováno `dwTid` . Pokud `dwFrame` je nenulová, je typ kroku "Krokovat s" a program by měl být zastaven pouze v případě, že vlákno identifikované pomocí `dwTid` je spuštěno v rámci, jehož index je roven nebo vyšší v zásobníku než `dwFrame` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Když správce ladění relace (SDM) provede program označený `pOriginatingProgram` parametrem, upozorní všechny ostatní připojené programy voláním této metody.  
  
 Tato metoda je platná pouze pro krokování ve stejném vlákně.  
  
## <a name="see-also"></a>Viz také  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
