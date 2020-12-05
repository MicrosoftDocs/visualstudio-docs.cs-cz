---
title: Vnitřní rozšíření pro .NET Framework | Microsoft Docs
description: Tyto prostředky popisují interní typy, metody a pole tříd, které slouží k implementaci vlastního ladicího programu pro paralelní rozšíření .NET Framework.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f9625af464e2695c6dd4302f4f7590d20e8f6af7
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606590"
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
