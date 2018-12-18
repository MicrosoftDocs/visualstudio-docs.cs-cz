---
title: Třída Task – vnitřní členy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9e9bbf6bbf42b8008850b540a59fa2b5d75b199
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276761"
---
# <a name="task-class---internal-members"></a>Třída úlohy – vnitřní členy
Tento článek popisuje interní členy <xref:System.Threading.Tasks.Task?displayProperty=fullName> třída, která vám pomůže implementovat vlastní ladicího programu. Obecné informace o této třídy, najdete v článku <xref:System.Threading.Tasks.Task> článku.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v *mscorlib.dll*)  
  
 Protože tyto vnitřní členy nemůže získat přístup z rozhraní .NET Framework, je k dispozici v Common Intermediate Language (CIL) následující syntaxi.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
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
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Označuje, že úloha zrušena dříve, než se dosáhlo do stavu spuštěno, nebo že úloha potvrzené jeho zrušení a dokončit bez výjimky.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Určuje, zda je spuštěn úkol.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Označuje, že úloha byla dokončena kvůli neošetřené výjimce.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Označuje, že úloha úspěšně dokončil provádění.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Označuje, že úkol dokončen jeho delegáta a implicitně čeká na dokončení připojených podřízených úloh.|  
  
## <a name="remarks"></a>Poznámky  
 Následující vnitřní metody jsou užitečné pro modul ladicího programu, protože jejich vstupu do označit <xref:System.Threading.Tasks.Task> spuštění kódu:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Viz také:  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Interní informace o paralelním rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)