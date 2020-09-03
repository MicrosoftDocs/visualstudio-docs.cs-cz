---
title: Vnitřní rozšíření pro .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a3583e94a0bfff4474db03aa9d083add921f3da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738269"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Vnitřní rozšíření pro .NET Framework
Tato část popisuje interní typy, metody a pole tříd, které vám pomůžou implementovat vlastní ladicí program pro paralelní rozšíření .NET Framework.

## <a name="in-this-section"></a>V této části
 [Task – třída](../../extensibility/debugger/task-class-internal-members.md) Popisuje interní datové členy <xref:System.Threading.Tasks.Task?displayProperty=fullName> třídy.

 [TaskScheduler – třída](../../extensibility/debugger/taskscheduler-class-internal-members.md) Popisuje interní datové členy <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> třídy.

 [ContingentProperties – třída](../../extensibility/debugger/contingentproperties-class-internal-members.md) Popisuje interní datové členy `System.Threading.Tasks.ContingentProperties` třídy.

 [Struktura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struktury.

 [ \<TResult> Struktura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> struktury.

 [Struktura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struktury.

## <a name="see-also"></a>Viz také
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Rozšiřitelnost ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Paralelní programování](/dotnet/standard/parallel-programming/index)
