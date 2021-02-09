---
title: T4 – direktivy textových šablon
description: Přečtěte si o direktivách šablon testů T4 a o tom, jak poskytují pokyny pro modul transformace textových šablon.
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ba13cbd31d41e656533aa5b13cf2a09503e58e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924597"
---
# <a name="t4-text-template-directives"></a>T4 – direktivy textových šablon

Direktivy poskytují pokyny stroji, který provádí transformace textových šablon.

Direktivy mají následující syntaxi:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Všechny hodnoty atributů musejí být uzavřeny do dvojitých uvozovek. Pokud samotná hodnota obsahuje uvozovky, musejí být uvozeny znakem \.

Direktivy jsou zpravidla prvním prvkem v souboru šablony nebo vkládaném souboru. Neměli byste je umístit uvnitř bloku kódu `<#...#>` ani po bloku funkcí třídy `<#+...#>` .

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

Navíc můžete vytvářet své vlastní direktivy. Další informace najdete v tématu [vytváření vlastních procesorů pro direktivy textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md). Pokud pomocí sady Visualization and Modeling SDK vytvoříte jazyk domény (DSL), vygeneruje se procesor direktiv jako součást tohoto kódu DSL.
