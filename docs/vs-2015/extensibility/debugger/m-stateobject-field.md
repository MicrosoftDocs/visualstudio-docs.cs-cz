---
title: m_stateObject pole | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e9cfc6f689504bef2a8366f90282641d1e9e105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149044"
---
# <a name="m_stateobject-field"></a>m_stateObject – pole
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Objekt, který představuje data, která bude akce používat.  
  
 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v mscorlib.dll)  
  
 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).  
  
## <a name="syntax"></a>Syntax  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Poznámky  
 Toto je `state` parametr v <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktoru. Je to také pole zálohování pro <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
