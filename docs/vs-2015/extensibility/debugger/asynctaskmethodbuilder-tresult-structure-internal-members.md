---
title: AsyncTaskMethodBuilder &lt; TResult &gt; Struktura – interní členové | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e4999b71ae8f654aa3d362ba16c6cf5bc6574da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182270"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder &lt; TResult &gt; – Struktura – interní členové
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto téma popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> třídy. Obecné informace o této třídě naleznete v <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> referenčním tématu.  
  
 **Obor názvů:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v mscorlib.dll)  
  
 Vzhledem k tomu, že nemůžete získat přístup k těmto interním členům z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Interní členové  
  
|Název|Popis|  
|----------|-----------------|  
|[Vlastnost ObjectIdForDebugger –](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Získává objekt, který lze použít k jednoznačné identifikaci tohoto tvůrce do ladicího programu.|  
|[m_task pole](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Představuje inicializovaný vytvořenou úlohu laxně vytvářená.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [Interní informace o paralelním rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
