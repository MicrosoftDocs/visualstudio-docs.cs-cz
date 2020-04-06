---
title: m_stateObject pole | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fed70f2eda19ad96454a83217c20c046809f3034
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738372"
---
# <a name="m_stateobject-field"></a>m_stateObject pole
Objekt, který představuje data, která bude akce používat.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že k tomuto internímu členu nemáte přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Poznámky
 Toto `state` je parametr <xref:System.Threading.Tasks.Task.%23ctor%2A> v konstruktoru. Je také záložní pole <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> pro vlastnost.

## <a name="see-also"></a>Viz také
- [Třída úkolu](../../extensibility/debugger/task-class-internal-members.md)
