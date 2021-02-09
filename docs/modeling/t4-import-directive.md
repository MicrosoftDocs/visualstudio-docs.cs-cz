---
title: T4 – direktiva Import
description: Seznamte se s tím, že v textové šabloně sady Visual Studio T4 umožňuje Direktiva Import odkazovat na prvky v jiném oboru názvů bez zadání plně kvalifikovaného názvu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9eb50261b346d8751a76817d97d59a798d17236
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899668"
---
# <a name="t4-import-directive"></a>T4 – direktiva Import

V blocích kódu textové šablony T4 sady Visual Studio `import` umožňuje direktivám odkazovat na prvky v jiném oboru názvů bez zadání plně kvalifikovaného názvu. Je ekvivalentem `using` v jazyce C# nebo `imports` v [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] .

Obecný přehled psaní textových šablon T4 naleznete v tématu [zápis textové šablony T4](../modeling/writing-a-t4-text-template.md).

## <a name="using-the-import-directive"></a>Použití direktivy importu

```
<#@ import namespace="namespace" #>
```

 V tomto příkladu se v kódu šablony může vynechat explicitní obor názvů pro členy System.IO:

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>Standardní importy
 Následující obor názvů se importuje automaticky, takže pro něj není nutné psát direktivu importu:

- `System`

  Pokud použijete vlastní direktivu, může navíc procesor direktiv importovat některé obory názvů automaticky.

  Pokud například píšete šablony pro jazyk domény (DSL), nemusíte psát direktivy importu pro následující obory názvů:

- `Microsoft.VisualStudio.Modeling`

- Obor názvů vaší DSL

## <a name="see-also"></a>Viz také

- [T4 – direktiva Assembly](../modeling/t4-assembly-directive.md)
