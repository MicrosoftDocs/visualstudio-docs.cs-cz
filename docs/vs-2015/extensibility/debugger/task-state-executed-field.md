---
title: TASK_STATE_EXECUTED pole | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6dcfb6c7b4b79d1abd2b393e32b9795f613c205a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162227"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED – pole
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Úloha je spuštěna, ale ještě nebyla dokončena.  
  
 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v mscorlib.dll)  
  
 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntax  
  
```  
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) obsahuje tuto hodnotu, <xref:System.Threading.Tasks.Task.Status%2A> vlastnost vrátí hodnotu <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .  
  
## <a name="see-also"></a>Viz také  
 [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
