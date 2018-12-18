---
title: Struktura AsyncTaskMethodBuilder – vnitřní členy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 130a3236752fba85c611619fb3cae70e00c76ec9
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39150963"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Struktura AsyncTaskMethodBuilder – vnitřní členy
Toto téma popisuje interní členy <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> třídy. Obecné informace o této třídy, najdete v článku <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> téma referenčních informací.  
  
 **Namespace:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v knihovně mscorlib.dll)  
  
 Protože tyto vnitřní členy nemůže získat přístup z rozhraní .NET Framework, je k dispozici v Common Intermediate Language (CIL) následující syntaxi.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>Vnitřní členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Vlastnost ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Získá objekt, který slouží k jednoznačné identifikaci tohoto Tvůrce ladicímu programu.|  
|[m_builder pole](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Reprezentuje obecný tvůrce objektu, ke kterému tato instance neobecných delegátů.|  
  
## <a name="see-also"></a>Viz také:  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [Interní informace o paralelním rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)