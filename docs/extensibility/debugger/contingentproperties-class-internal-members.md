---
title: ContingentProperties třída – interní členové | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3f332c715c8a182b30191cd96c8f1d1438cbdefd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930483"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties třída – interní členy
Obsahuje další vlastnosti <xref:System.Threading.Tasks.Task> objektu.

 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Sestavení:** mscorlib (v mscorlib.dll)

 Vzhledem k tomu, že nemůžete získat přístup k těmto interním členům z .NET Framework, je k dispozici následující syntaxe v Common Intermediate Language (CIL).

## <a name="syntax"></a>Syntax

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Členové

### <a name="fields"></a>Pole

|Název|Description|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Seznam podřízených úloh, které jsou registrovány s touto úlohou.|

## <a name="remarks"></a>Poznámky
 .NET Framework inicializuje pole této třídy pouze v případě potřeby.

## <a name="see-also"></a>Viz také
- [Vnitřní rozšíření pro .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
