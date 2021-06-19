---
title: T4 – direktiva Import
description: V textové šabloně Visual Studio T4 zjistíte, že direktiva importu umožňuje odkazovat na elementy v jiném oboru názvů bez poskytnutí plně kvalifikovaného názvu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d0d441ec5a62dfa5266a17a06ac8fe33941136c6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386316"
---
# <a name="t4-import-directive"></a>T4 – direktiva Import

V blocích kódu textové Visual Studio T4 umožňuje direktiva odkazovat na prvky v jiném oboru názvů bez poskytnutí `import` plně kvalifikovaného názvu. Jedná se o ekvivalent v `using` jazyce C# nebo `imports` v [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] .

Obecný přehled psaní textových šablon T4 najdete v tématu [Zápis textové šablony T4.](../modeling/writing-a-t4-text-template.md)

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

- Obor názvů vašeho DSL

## <a name="see-also"></a>Viz také

- [T4 – direktiva Assembly](../modeling/t4-assembly-directive.md)
