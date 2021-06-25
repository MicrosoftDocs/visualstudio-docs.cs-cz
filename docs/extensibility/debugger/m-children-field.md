---
description: Seznam podřízených úloh, které jsou zaregistrovány v rámci této úlohy.
title: m_children pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 311ab164551e46fbe1c30b5a6045a7993a900a67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901367"
---
# <a name="m_children-field"></a>m_children pole
Seznam podřízených úloh, které jsou zaregistrovány v rámci této úlohy.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že nemůžete získat přístup k tomuto internímu členu z .NET Framework, je následující syntaxe k dispozici v souboru Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Poznámky
 Zatímco je úloha spuštěná, k tomuto poli by mělo přistupovat pouze vlákno, které úlohu provádí.

 Pokud je úloha dokončena, mají k tomuto poli přístup jiná vlákna, pokud do něj nic nesčítá nebo z něj nic neodebere.

## <a name="see-also"></a>Viz také
- [ContingentProperties – třída](../../extensibility/debugger/contingentproperties-class-internal-members.md)
