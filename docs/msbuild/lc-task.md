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
ms.openlocfilehash: 865167b9182ca1f2264900a3e71ddeb4983e25ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "82167394"
---
# <a name="lc-task"></a>LC – úloha

Zalomí *LC.exe*, který generuje soubor *. License* ze souboru *. licx* . Další informace o *LC.exe*najdete v tématu [Lc.exe (kompilátor licencí)](/dotnet/framework/tools/lc-exe-license-compiler).

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry pro `LC` úlohu.

|Parametr|Popis|
|---------------|-----------------|
|`LicenseTarget`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje spustitelný soubor, pro který jsou vygenerovány soubory *. licenses* .|
|`NoLogo`|Volitelný `Boolean` parametr.<br /><br /> Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|`OutputDirectory`|Volitelný `String` parametr.<br /><br /> Určuje adresář, do kterého se umístí výstup souborů *. licenses* .|
|`OutputLicense`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> výstupní parametr.<br /><br /> Určuje název souboru *. licenses* . Pokud název nezadáte, použije se název souboru *. licx* a soubor *. licenses* se umístí do adresáře, který obsahuje soubor *. licx* .|
|`ReferencedAssemblies`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje odkazované součásti, které se mají načíst při vytváření souboru *. License* .|
|`SdkToolsPath`|Volitelný `String` parametr.<br /><br /> Určuje cestu k nástrojům sady SDK, jako je například *resgen.exe*.|
|`Sources`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje položky, které obsahují licencované součásti, které mají být zahrnuty do souboru *. licenses* . Další informace najdete v dokumentaci k `/complist` přepínači v [Lc.exe (kompilátor licencí)](/dotnet/framework/tools/lc-exe-license-compiler).|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Příklad

Následující příklad používá `LC` úlohu k sestavení licencí.

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
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
