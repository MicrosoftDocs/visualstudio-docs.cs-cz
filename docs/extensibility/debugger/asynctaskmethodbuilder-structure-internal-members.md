---
title: AsyncTaskMethodBuilder Struktura - Interní členové | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c918890551515ab9fadbf329d4c3ee96621c7aae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739372"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder struktura - interní členy
Toto téma popisuje interní <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> členy třídy. Obecné informace o této třídě <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> naleznete v referenčním tématu.

 **Obor názvů:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Sestava:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že k těmto interním členům nelze získat přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interní členové

|Name (Název)|Popis|
|----------|-----------------|
|[Vlastnost ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Získá objekt, který může být použit k jednoznačné identifikaci tohoto tvůrce ladicího programu.|
|[m_builder pole](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Představuje obecný objekt tvůrce, na který tato neobecná instance deleguje.|

## <a name="see-also"></a>Viz také
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Vnitřní rozhraní paralelního rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
