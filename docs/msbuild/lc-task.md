---
title: LC Úkol | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633600"
---
# <a name="lc-task"></a>LC – úloha

Zabalí *soubor LC.exe*, který generuje soubor *.license* ze souboru *LICX.* Další informace o *souboru LC.exe*naleznete v [tématu Lc.exe (License Compiler).](/dotnet/framework/tools/lc-exe-license-compiler)

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `LC` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`LicenseTarget`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje spustitelný soubor, pro který jsou generovány soubory *.licenses.*|
|`NoLogo`|Volitelný `Boolean` parametr.<br /><br /> Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|`OutputDirectory`|Volitelný `String` parametr.<br /><br /> Určuje adresář, do kterého mají být výstupní soubory *.licenses* umístit.|
|`OutputLicense`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje název souboru *.licenses.* Pokud název nezadáte, bude použit název souboru *LICX* a soubor *.licenses* bude umístěn do adresáře, který obsahuje soubor *LICX.*|
|`ReferencedAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje odkazované součásti, které se mají načíst při generování souboru *.license.*|
|`SdkToolsPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, například *resgen.exe*.|
|`Sources`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje položky, které obsahují licencované součásti, které mají být zahrnuty do souboru *.licenses.* Další informace naleznete v dokumentaci k přepínači v `/complist` [souboru Lc.exe (License Compiler).](/dotnet/framework/tools/lc-exe-license-compiler)|

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.ToolTaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.ToolTask> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [ToolTaskExtension base class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad

Následující příklad používá `LC` úlohu ke kompilaci licencí.

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
