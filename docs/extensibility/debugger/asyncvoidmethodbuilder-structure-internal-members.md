---
title: AsyncVoidMethodBuilder struktura – interní členové | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: edb0e11f80743289f8318c9fe7d331e6528f8107
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921620"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder struktura – interní členové
Toto téma popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> třídy. Obecné informace o této třídě naleznete v <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> referenčním tématu.

 **Obor názvů:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Sestavení:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že nemůžete získat přístup k těmto interním členům z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interní členové

|Název|Description|
|----------|-----------------|
|[Vlastnost ObjectIdForDebugger –](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Získává objekt, který lze použít k jednoznačné identifikaci tohoto tvůrce do ladicího programu.|
|[m_objectIdForDebugger pole](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Představuje inicializovaný objekt laxně vytvářená, který ladicí program používá k jednoznačné identifikaci tohoto tvůrce.|

## <a name="see-also"></a>Viz také
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Vnitřní rozšíření pro .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
