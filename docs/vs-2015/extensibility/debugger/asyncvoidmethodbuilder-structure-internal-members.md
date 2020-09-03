---
title: AsyncVoidMethodBuilder struktura – interní členové | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 770e66c4136379a24cee349b04fcc06f5278a379
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201100"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Struktura AsyncVoidMethodBuilder – vnitřní členy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto téma popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> třídy. Obecné informace o této třídě naleznete v <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> referenčním tématu.  
  
 **Obor názvů:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v mscorlib.dll)  
  
 Vzhledem k tomu, že nemůžete získat přístup k těmto interním členům z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Interní členové  
  
|Název|Popis|  
|----------|-----------------|  
|[Vlastnost ObjectIdForDebugger –](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Získává objekt, který lze použít k jednoznačné identifikaci tohoto tvůrce do ladicího programu.|  
|[m_objectIdForDebugger pole](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Představuje inicializovaný objekt laxně vytvářená, který ladicí program používá k jednoznačné identifikaci tohoto tvůrce.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [Interní informace o paralelním rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
