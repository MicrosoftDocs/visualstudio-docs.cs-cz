---
title: T4 – direktiva Import
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a28bedd01e3a4f6a7a87b025ac9a9a6184da9b2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591863"
---
# <a name="t4-import-directive"></a>T4 – direktiva Import

V blocích kódu textové šablony T4 sady Visual Studio umožňuje direktiva `import` odkazovat na prvky v jiném oboru názvů bez zadání plně kvalifikovaného názvu. Je ekvivalentem `using` v C# nebo `imports` v [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

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

## <a name="see-also"></a>Viz také:

- [T4 – direktiva Assembly](../modeling/t4-assembly-directive.md)
