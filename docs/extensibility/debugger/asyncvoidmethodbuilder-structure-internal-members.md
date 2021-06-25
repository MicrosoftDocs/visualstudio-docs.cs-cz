---
description: Toto téma popisuje interní členy třídy System.Runtime.CompilerServices.AsyncVoidMethodBuilder.
title: Struktura AsyncVoidMethodBuilder – vnitřní členy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d6606e26d14ba114ed8346c0cc11a81f8bdd3e8e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903630"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Struktura AsyncVoidMethodBuilder – interní členy
Toto téma popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> třídy. Obecné informace o této třídě najdete v <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> referenčním tématu.

 **Obor názvů:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Sestavení:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že nemůžete přistupovat k těmto interním členům z .NET Framework, je následující syntaxe k dispozici v souboru Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interní členové

|Název|Description|
|----------|-----------------|
|[ObjectIdForDebugger – vlastnost](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Získá objekt, který lze použít k jednoznačné identifikaci tohoto tvůrce ladicího programu.|
|[m_objectIdForDebugger pole](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Představuje laxně inicializované objekt, který ladicí program používá k jednoznačné identifikaci tohoto tvůrce.|

## <a name="see-also"></a>Viz také
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Interní informace o paralelním rozšíření pro .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
