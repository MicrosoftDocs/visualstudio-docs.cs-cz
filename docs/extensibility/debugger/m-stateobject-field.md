---
description: Objekt, který představuje data, která bude akce používat.
title: m_stateObject pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92fdad68506c62440c7f3e130caee49b4fe780da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158758"
---
# <a name="m_stateobject-field"></a>m_stateObject pole
Objekt, který představuje data, která bude akce používat.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Poznámky
 Toto je `state` parametr v <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktoru. Je to také pole zálohování pro <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> vlastnost.

## <a name="see-also"></a>Viz také
- [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
