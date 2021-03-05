---
description: Seznam podřízených úloh, které jsou registrovány s touto úlohou.
title: m_children pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5aaf29d76a7bbd81a416c86360f315bc5c09b76c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158866"
---
# <a name="m_children-field"></a>m_children pole
Seznam podřízených úloh, které jsou registrovány s touto úlohou.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členovi z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Poznámky
 Když je úloha spuštěná, měl by k tomuto poli přistupovat jenom vlákno, které úlohu spustí.

 Pokud je úloha dokončena, budou mít k tomuto poli přístup další vlákna, pokud k nim nepřidáte nic nebo z něj neodeberete nic.

## <a name="see-also"></a>Viz také
- [ContingentProperties – třída](../../extensibility/debugger/contingentproperties-class-internal-members.md)
