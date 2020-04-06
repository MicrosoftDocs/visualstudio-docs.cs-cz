---
title: Třída ContingentProperties - Interní členové | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6441cafcc34a06464061b41691ea5faa32fc359
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739099"
---
# <a name="contingentproperties-class---internal-members"></a>Třída ContingentProperties - interní členy
Obsahuje další vlastnosti objektu. <xref:System.Threading.Tasks.Task>

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestava:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že k těmto interním členům nelze získat přístup z rozhraní .NET Framework, je ve společném zprostředkujícím jazyce (CIL) k dispozici následující syntaxe.

## <a name="syntax"></a>Syntaxe

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Členové

### <a name="fields"></a>Fields (Pole)

|Name (Název)|Popis|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Seznam podřízených úkolů, které jsou registrovány s tímto úkolem.|

## <a name="remarks"></a>Poznámky
 Rozhraní .NET Framework inicializuje pole této třídy pouze v případě, že jsou potřeba.

## <a name="see-also"></a>Viz také
- [Vnitřní rozhraní paralelního rozšíření pro rozhraní .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
