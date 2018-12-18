---
title: Třída Task – vnitřní členy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92ddc4b00f9d8eb37893e1db7ae44802e04e9c46
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764820"
---
# <a name="task-class---internal-members"></a>Třída Task – vnitřní členy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto téma popisuje interní členy <xref:System.Threading.Tasks.Task?displayProperty=fullName> třída, která vám pomůže implementovat vlastní ladicího programu. Obecné informace o této třídy, najdete v článku <xref:System.Threading.Tasks.Task> téma referenčních informací.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v knihovně mscorlib.dll)  
  
 Protože tyto vnitřní členy nemůže získat přístup z rozhraní .NET Framework, je k dispozici v Common Intermediate Language (CIL) následující syntaxi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|Název|Popis|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion – metoda](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Nastaví nebo vymaže stav bit TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[NotifyDebuggerOfWaitCompletion – metoda](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Zástupný symbol metoda použitá jako cíl zarážku ladicím programem.|  
  
### <a name="fields"></a>Pole  
  
|Název|Popis|  
|----------|-----------------|  
|[m_action –](../../extensibility/debugger/m-action-field.md)|Delegát, který představuje kód pro spuštění v <xref:System.Threading.Tasks.Task> objektu.|  
|[m_contingentproperties –](../../extensibility/debugger/m-contingentproperties-field.md)|Ukládá další vlastnosti <xref:System.Threading.Tasks.Task> objektu.|  
|[m_parent –](../../extensibility/debugger/m-parent-field.md)|Pomocné pole <xref:System.Threading.Tasks.Task?displayProperty=fullName> nadřazená vlastnost.|  
|[m_stateflags –](../../extensibility/debugger/m-stateflags-field.md)|Ukládá informace o aktuálním stavu <xref:System.Threading.Tasks.Task> objektu.|  
|[m_stateobject –](../../extensibility/debugger/m-stateobject-field.md)|Objekt představující data, která se použije akci.|  
|[m_taskid –](../../extensibility/debugger/m-taskid-field.md)|Pomocné pole <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> vlastnost.|  
|[s_taskidcounter –](../../extensibility/debugger/s-taskidcounter-field.md)|Další dostupné identifikátorem <xref:System.Threading.Tasks.Task> objektu.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Označuje, že daná úloha se zrušila, než se dosáhlo do stavu spuštěno, nebo že úloha potvrzení jeho zrušení a dokončit bez výjimky.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Určuje, zda je spuštěn úkol.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Označuje, že úloha byla dokončena kvůli neošetřené výjimce.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Označuje, že úloha úspěšně dokončil provádění.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Označuje, že úkol neskončí jeho delegáta a implicitně čeká na dokončení připojených podřízených úloh.|  
  
## <a name="remarks"></a>Poznámky  
 Následující vnitřní metody jsou užitečné pro modul ladicího programu, protože jejich vstupu do označit <xref:System.Threading.Tasks.Task> spuštění kódu:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Interní informace o paralelním rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

