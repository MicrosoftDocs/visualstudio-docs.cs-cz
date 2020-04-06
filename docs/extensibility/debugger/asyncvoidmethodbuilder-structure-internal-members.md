---
title: AsyncVoidMethodBuilder Struktura - Interní členové | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 866a53fae7bb2cc5325112b84d992da6f95af246
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739296"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder struktura - interní členy
Toto téma popisuje interní <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> členy třídy. Obecné informace o této třídě <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> naleznete v referenčním tématu.

 **Obor názvů:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Sestava:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že k těmto interním členům nelze získat přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Interní členové

|Name (Název)|Popis|
|----------|-----------------|
|[Vlastnost ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Získá objekt, který může být použit k jednoznačné identifikaci tohoto tvůrce ladicího programu.|
|[m_objectIdForDebugger pole](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Představuje líně inicializovaný objekt používaný ladicím programem k jednoznačné identifikaci tohoto tvůrce.|

## <a name="see-also"></a>Viz také
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Vnitřní rozhraní paralelního rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
