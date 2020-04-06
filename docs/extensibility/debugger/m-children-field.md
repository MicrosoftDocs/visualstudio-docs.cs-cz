---
title: m_children pole | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738422"
---
# <a name="m_children-field"></a>m_children pole
Seznam podřízených úkolů, které jsou registrovány s tímto úkolem.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v *mscorlib.dll*)

 Vzhledem k tomu, že k tomuto internímu členu nemáte přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Poznámky
 Při spuštění úlohy by měl přístup k tomuto poli přistupovat pouze vlákno, které úlohu provede.

 Pokud je úkol dokončen, ostatní vlákna mají přístup k tomuto poli, pokud k němu nic nepřidají ani z něj nic neodeberou.

## <a name="see-also"></a>Viz také
- [Třída ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
