---
description: Obsahuje další vlastnosti pro objekt System.Threading.Tasks.Task.
title: Třída ContingentProperties – vnitřní | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8fca0bf68de4493d0165f9e66e251945ba6168b2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905680"
---
# <a name="contingentproperties-class---internal-members"></a>Třída ContingentProperties – interní členy
Obsahuje další vlastnosti <xref:System.Threading.Tasks.Task> objektu.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že nemůžete přistupovat k těmto interním členům z .NET Framework, je následující syntaxe k dispozici v souboru Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Členové

### <a name="fields"></a>Pole

|Název|Description|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Seznam podřízených úloh, které jsou zaregistrovány v rámci této úlohy.|

## <a name="remarks"></a>Poznámky
 Třída .NET Framework inicializuje pole této třídy pouze v případě, že jsou potřebná.

## <a name="see-also"></a>Viz také
- [Interní informace o paralelním rozšíření pro .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
