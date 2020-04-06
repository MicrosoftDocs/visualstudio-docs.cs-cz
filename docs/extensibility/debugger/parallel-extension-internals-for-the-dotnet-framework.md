---
title: Vnitřní zabezpečení paralelního rozšíření pro rozhraní .NET Framework | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738269"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Vnitřní rozhraní paralelního rozšíření pro rozhraní .NET Framework
Tato část popisuje vnitřní typy, metody a pole tříd, které vám pomohou implementovat vlastní ladicí program pro paralelní rozšíření rozhraní .NET Framework.

## <a name="in-this-section"></a>V tomto oddílu
 [Třída úkolu](../../extensibility/debugger/task-class-internal-members.md) Popisuje interní datové členy <xref:System.Threading.Tasks.Task?displayProperty=fullName> třídy.

 [Třída TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) Popisuje interní datové členy <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> třídy.

 [Třída ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) Popisuje interní datové členy `System.Threading.Tasks.ContingentProperties` třídy.

 [Struktura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) Popisuje vnitřní členy <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> struktury.

 [AsyncTaskMethodBuilder\<TResult> struktura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) Popisuje vnitřní <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> členy struktury.

 [AsyncVoidMethodBuilder struktura](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) Popisuje vnitřní členy <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> struktury.

## <a name="see-also"></a>Viz také
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Rozšiřitelnost ladicího programu visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Paralelní programování](/dotnet/standard/parallel-programming/index)
