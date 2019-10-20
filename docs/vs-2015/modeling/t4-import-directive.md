---
title: T4 – direktiva importu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4a931ca05f8b12175deded8b316d0177d8f8c74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661822"
---
# <a name="t4-import-directive"></a>T4 – direktiva Import
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V blocích kódu textové šablony [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4, direktiva `import` umožňuje odkazování na prvky v jiném oboru názvů bez zadání plně kvalifikovaného názvu. Je ekvivalentem `using` v C# nebo `imports` v [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].

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

- Obor názvů vašeho kódu DSL

## <a name="see-also"></a>Viz také
 [T4 – direktiva Assembly](../modeling/t4-assembly-directive.md)
