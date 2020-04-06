---
title: Třída úkolů - Interní členové | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712737"
---
# <a name="task-class---internal-members"></a>Třída úloh - interní členové
Tento článek popisuje interní členy <xref:System.Threading.Tasks.Task?displayProperty=fullName> třídy, které vám pomohou implementovat vlastní ladicí program. Obecné informace o této třídě <xref:System.Threading.Tasks.Task> naleznete v referenčním článku.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že k těmto interním členům nemáte přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

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

|Name (Název)|Popis|
|----------|-----------------|
|[SetNotificationForWaitCompletion – metoda](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Nastaví nebo vymaže bit stavu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|
|[NotifyDebuggerOfWaitCompletion – metoda](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Zástupná metoda použitá ladicím programem jako cíl zarážky.|

### <a name="fields"></a>Fields (Pole)

|Name (Název)|Popis|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegát, který představuje kód ke <xref:System.Threading.Tasks.Task> spuštění v objektu.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Ukládá další vlastnosti objektu. <xref:System.Threading.Tasks.Task>|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Záložní pole pro <xref:System.Threading.Tasks.Task?displayProperty=fullName> nadřazenou vlastnost.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Ukládá informace o aktuálním <xref:System.Threading.Tasks.Task> stavu objektu.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Objekt, který představuje data, která budou použita akce.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Záložní pole pro <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> vlastnost.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Další dostupný identifikátor <xref:System.Threading.Tasks.Task> objektu.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Označuje, že úloha byla zrušena před dosažením spuštěného stavu nebo že úloha potvrdila jeho zrušení a dokončení bez výjimky.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Označuje, že úloha je spuštěna.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Označuje, že úkol byl dokončen z důvodu neošetřené výjimky.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Označuje, že úloha byla úspěšně dokončena.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Označuje, že úloha byla dokončena při provádění svého delegáta a implicitně čeká na dokončení připojených podřízených úloh.|

## <a name="remarks"></a>Poznámky
 Následující vnitřní metody jsou užitečné pro ladicí modul, <xref:System.Threading.Tasks.Task> protože označují vstup do spuštění kódu:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Viz také
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Vnitřní rozhraní paralelního rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
