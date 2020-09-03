---
title: Metoda GetTaskSchedulersForDebugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 995bf40669a4480f6f1ddfe8071a7885a4659c9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152716"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger – metoda
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Načte pole všech <xref:System.Threading.Tasks.TaskScheduler> objektů, které jsou aktuálně aktivní.  
  
 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v mscorlib.dll)  
  
 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntax  
  
```  
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pole všech <xref:System.Threading.Tasks.TaskScheduler> objektů, které jsou v tuto chvíli aktivní <xref:System.AppDomain> .  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda není bezpečná pro přístup z více vláken a neměla by se používat souběžně s jinými instancemi <xref:System.Threading.Tasks.TaskScheduler> . Měla by být volána z ladicího programu pouze v případě, že ladicí program pozastavil všechna ostatní vlákna.  
  
## <a name="see-also"></a>Viz také  
 [TaskScheduler – třída](../../extensibility/debugger/taskscheduler-class-internal-members.md)
