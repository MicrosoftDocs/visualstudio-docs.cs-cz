---
title: Struktura asyncvoidmethodbuilder Structure – vnitřní členy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 414e505f033914302edc9e3f89880ede4823ddca
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150874"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Struktura asyncvoidmethodbuilder Structure – vnitřní členy
Toto téma popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> třídy. Obecné informace o této třídy, najdete v článku <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> téma referenčních informací.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v knihovně mscorlib.dll)  
  
 Protože tyto vnitřní členy nemůže získat přístup z rozhraní .NET Framework, je k dispozici v Common Intermediate Language (CIL) následující syntaxi.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Vnitřní členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Vlastnost ObjectIdForDebugger](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Získá objekt, který slouží k jednoznačné identifikaci tohoto Tvůrce ladicímu programu.|  
|[m_objectIdForDebugger pole](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Představuje laxně inicializovaný objekt použitý objektem ladicí program k jednoznačné identifikaci tohoto Tvůrce.|  
  
## <a name="see-also"></a>Viz také:  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Interní informace o paralelním rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)