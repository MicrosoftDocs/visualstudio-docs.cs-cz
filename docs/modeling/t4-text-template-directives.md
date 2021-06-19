---
title: T4 – direktivy textových šablon
description: Přečtěte si o direktivách testovací šablony T4 a o tom, jak poskytují pokyny modulu pro transformaci textových šablon.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d9b7ca189ced11eea57e175a06b81161090070b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388734"
---
# <a name="t4-text-template-directives"></a>T4 – direktivy textových šablon

Direktivy poskytují pokyny stroji, který provádí transformace textových šablon.

Direktivy mají následující syntaxi:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Všechny hodnoty atributů musejí být uzavřeny do dvojitých uvozovek. Pokud samotná hodnota obsahuje uvozovky, musejí být uvozeny znakem \.

Direktivy jsou zpravidla prvním prvkem v souboru šablony nebo vkládaném souboru. Neměli byste je umístit do bloku kódu `<#...#>` ani za blok funkce třídy `<#+...#>` .

[T4 – direktiva Template](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[T4 – direktiva Parameter](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[T4 – direktiva Output](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[T4 – direktiva Assembly](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[T4 – direktiva Import](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[T4 – direktiva Include](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[T4 CleanUpBehavior – direktiva](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Navíc můžete vytvářet své vlastní direktivy. Další informace najdete v tématu Vytváření vlastních procesorů direktiv textových šablon [T4.](../modeling/creating-custom-t4-text-template-directive-processors.md) Pokud pomocí sady Visualization and Modeling SDK vytvoříte jazyk domény (DSL), vygeneruje se procesor direktiv jako součást tohoto kódu DSL.
