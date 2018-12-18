---
title: T4 – direktivy textových šablon
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: c01bea709d551e970ed8c44ec861ff348c7081ad
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947843"
---
# <a name="t4-text-template-directives"></a>T4 – direktivy textových šablon
Direktivy poskytují pokyny stroji, který provádí transformace textových šablon.

 Direktivy mají následující syntaxi:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

 Všechny hodnoty atributů musejí být uzavřeny do dvojitých uvozovek. Pokud samotná hodnota obsahuje uvozovky, musejí být uvozeny znakem \.

 Direktivy jsou zpravidla prvním prvkem v souboru šablony nebo vkládaném souboru. Neměli umístěte je uvnitř bloku kódu `<#...#>`, ani po blok funkce třída `<#+...#>`.

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

 [T4 – direktiva CleanUpBehavior](../modeling/t4-cleanupbehavior-directive.md)
 ```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

 Navíc můžete vytvářet své vlastní direktivy. Další informace najdete v tématu [vytváření vlastní T4 Text šablony direktiva procesorů](../modeling/creating-custom-t4-text-template-directive-processors.md). Pokud pomocí sady Visualization and Modeling SDK vytvoříte jazyk domény (DSL), vygeneruje se procesor direktiv jako součást tohoto kódu DSL.