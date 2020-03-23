---
title: XslTransformační úloha | Dokumenty společnosti Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d23799e5ce5bf391915ac459c69c27b990211f0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094541"
---
# <a name="xsltransformation-task"></a>XslTransformation – úloha

Transformuje vstup XML pomocí XSLT nebo kompilované XSLT a výstupy do výstupního zařízení nebo souboru.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `XslTransformation` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`OutputPaths`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje výstupní soubory pro transformaci XML.|
|`Parameters`|Volitelný `String` parametr.<br /><br /> Určuje parametry vstupního dokumentu XSLT.  Zadejte nezpracovaný kód XML, který obsahuje každý parametr jako `<Parameter Name="" Value="" Namespace="" />`.|
|`XmlContent`|Volitelný `String` parametr.<br /><br /> Určuje vstup XML jako řetězec.|
|`XmlInputPaths`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje vstupní soubory XML.|
|`XslCompiledDllPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje zkompilovaný XSLT.|
|`XslContent`|Volitelný `String` parametr.<br /><br /> Určuje vstup XSLT jako řetězec.|
|`XslInputPath`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje vstupní soubor XSLT.|

## <a name="remarks"></a>Poznámky

 Kromě parametrů, které jsou uvedeny v tabulce, tato úloha <xref:Microsoft.Build.Tasks.TaskExtension> dědí parametry z <xref:Microsoft.Build.Utilities.Task> třídy, která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

V následujícím příkladu se k úpravě souboru `$(XmlInputFileName)`XML používá transformační soubor *XSL.* Transformovaný kód XML `$(IntermediateOutputPath)output.xml`je zapsán do aplikace . Transformace XSL `$(Parameter1)` bere jako vstupní parametr.

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>Viz také

- [Parametry XSLT](/dotnet/standard/data/xml/xslt-parameters)
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
