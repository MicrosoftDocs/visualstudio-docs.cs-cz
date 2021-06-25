---
description: Delegát, který představuje kód pro spuštění v objektu System.Threading.Tasks.Task.
title: m_action pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 838494eb612ffaa18931e42227619b22bc297b4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901471"
---
# <a name="m_action-field"></a>m_action pole
Delegát, který představuje kód, který má být proveden v <xref:System.Threading.Tasks.Task> objektu.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členu z .NET Framework, je následující syntaxe k dispozici v souboru Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Poznámky
 Toto je `action` parametr v <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktoru .

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
