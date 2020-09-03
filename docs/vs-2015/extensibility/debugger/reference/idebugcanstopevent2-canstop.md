---
title: 'IDebugCanStopEvent2:: po spuštění | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8167013489b3b37e254100f7547cd61d54529b95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191190"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Upozorní modul ladění (DE) na to, jestli se má zastavit v aktuálním umístění kódu, nebo jenom pokračovat v provádění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fCanStop`  
 pro Non-Zero ( `TRUE` ), pokud by měl příkaz de zastavit v aktuálním umístění kódu; v opačném případě nula ( `FALSE` ).  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Příjemce této události obvykle volá metodu [getdůvod](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) k určení příčiny, proč de chce zastavit, a pak zavolá `IDebugCanStopEvent2::CanStop` metodu s příslušnou odpovědí.  
  
 Pokud se operace DE zastaví, pošle událost, která popisuje důvod zastavení. K dispozici jsou obvykle dvě události, které jsou odeslány, uživatel nebo přerušení signálu reprezentované rozhraním [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) a událost zarážky reprezentované rozhraním [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
