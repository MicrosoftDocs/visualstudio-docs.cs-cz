---
title: Úloha XslTransformation – | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu XslTransformation – k transformaci vstupu XML pomocí XSLT a výstupu do výstupního zařízení nebo souboru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f779fc5d222fdd0985adef203f0bb20fc601a429
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847943"
---
# <a name="xsltransformation-task"></a>XslTransformation – úloha

Transformuje vstup XML pomocí XSLT nebo zkompilovaného souboru XSLT a výstupy na výstupní zařízení nebo soubor.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `XslTransformation` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`OutputPaths`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje výstupní soubory pro transformaci XML.|
|`Parameters`|Volitelný `String` parametr.<br /><br /> Určuje parametry pro vstupní dokument XSLT.  Poskytněte nezpracovaný kód XML, který obsahuje každý parametr jako `<Parameter Name="" Value="" Namespace="" />` .|
|`XmlContent`|Volitelný `String` parametr.<br /><br /> Určuje vstup XML jako řetězec.|
|`XmlInputPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje vstupní soubory XML.|
|`XslCompiledDllPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje kompilovaný soubor XSLT.|
|`XslContent`|Volitelný `String` parametr.<br /><br /> Určuje vstup XSLT jako řetězec.|
|`XslInputPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje vstupní soubor XSLT.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

V následujícím příkladu se transformační soubor XSL *transformuje. XSLT* slouží k úpravě souboru XML `$(XmlInputFileName)` . Transformovaný kód XML je zapsán do `$(IntermediateOutputPath)output.xml` . Transformace XSL přebírá `$(Parameter1)` jako vstupní parametr.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Viz také

- [Parametry XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
