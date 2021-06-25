---
description: Objekt, který představuje data, která bude akce používat.
title: m_stateObject pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df510fafbfe3ed6e71e9b5290fb1df0b02ae1d39
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903954"
---
# <a name="m_stateobject-field"></a>m_stateObject pole
Objekt, který představuje data, která bude akce používat.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členu z .NET Framework, je následující syntaxe k dispozici v souboru Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Poznámky
 Toto je `state` parametr v <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktoru . Je to také zálohovací pole pro <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> vlastnost .

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
