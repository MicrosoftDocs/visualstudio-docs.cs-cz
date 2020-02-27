---
title: LC – úloha | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cea0ca4e6562ccc626bf52ad74dfa75b4f118f9
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633600"
---
# <a name="lc-task"></a>LC – úloha

Zabalí *LC. exe*, který generuje soubor *. License* ze souboru *. licx* . Další informace o *LC. exe*najdete v tématu [LC. exe (kompilátor licencí)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry pro úlohu `LC`.

|Parametr|Popis|
|---------------|-----------------|
|`LicenseTarget`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje spustitelný soubor, pro který jsou vygenerovány soubory *. licenses* .|
|`NoLogo`|Volitelný parametr `Boolean`.<br /><br /> Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|`OutputDirectory`|Volitelný parametr `String`.<br /><br /> Určuje adresář, do kterého se umístí výstup souborů *. licenses* .|
|`OutputLicense`|Volitelný výstupní parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje název souboru *. licenses* . Pokud název nezadáte, použije se název souboru *. licx* a soubor *. licenses* se umístí do adresáře, který obsahuje soubor *. licx* .|
|`ReferencedAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje odkazované součásti, které se mají načíst při vytváření souboru *. License* .|
|`SdkToolsPath`|Volitelný parametr `String`.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je *Resgen. exe*.|
|`Sources`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje položky, které obsahují licencované součásti, které mají být zahrnuty do souboru *. licenses* . Další informace najdete v dokumentaci k přepínači `/complist` v [LC. exe (kompilátor licencí)](/dotnet/framework/tools/lc-exe-license-compiler).|

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá úlohu `LC` ke kompilaci licencí.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
