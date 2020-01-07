---
title: Použití úlohy AspNetCompiler – k předkompilování aplikací ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6535dbec7c09f0888d0fb29a2e6b801632da22f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593457"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler – úloha
`AspNetCompiler` úkol zalomí *Aspnet_compiler. exe*, což je nástroj pro předkompilování [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikací.

## <a name="task-parameters"></a>Parametry úlohy
Následující tabulka popisuje parametry úlohy `AspNetCompiler`.

|Parametr|Popis|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Volitelný parametr `Boolean`.<br /><br /> Pokud je tento parametr `true`, bude sestavení se silným názvem umožňovat částečně důvěryhodné volající.|
|`Clean`|Volitelný parametr `Boolean`<br /><br /> Pokud je tento parametr `true`, předkompilovaná aplikace bude sestavena jako čistá. Všechny dříve kompilované součásti budou znovu zkompilovány. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-c** na *Aspnet_compiler. exe*.|
|`Debug`|Volitelný parametr `Boolean`.<br /><br /> Pokud je tento parametr `true`, ladicí informace (. Soubor PDB) je generován během kompilace. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-d** na *Aspnet_compiler. exe*.|
|`DelaySign`|Volitelný parametr `Boolean`.<br /><br /> Pokud je tento parametr `true`, sestavení není po vytvoření plně podepsáno.|
|`FixedNames`|Volitelný parametr `Boolean`.<br /><br /> Pokud je tento parametr `true`, zkompilované sestavení budou mít pevné názvy..|
|`Force`|Volitelný parametr `Boolean`<br /><br /> Pokud je tento parametr `true`, úloha přepíše cílový adresář, pokud již existuje. Existující obsah bude ztracen. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-f** na *Aspnet_compiler. exe*.|
|`KeyContainer`|Volitelný parametr `String`.<br /><br /> Určuje kontejner klíče se silným názvem.|
|`KeyFile`|Volitelný parametr `String`.<br /><br /> Určuje fyzickou cestu k souboru klíče se silným názvem..|
|`MetabasePath`|Volitelný parametr `String`.<br /><br /> Určuje úplnou cestu metabáze služby IIS aplikace. Tento parametr nelze kombinovat s parametry `VirtualPath` nebo `PhysicalPath`. Tento parametr odpovídá přepínači **-m** na *Aspnet_compiler. exe*.|
|`PhysicalPath`|Volitelný parametr `String`.<br /><br /> Určuje fyzickou cestu aplikace, která má být zkompilována. Pokud tento parametr chybí, použije se k vyhledání aplikace metabáze IIS. Tento parametr odpovídá přepínači **-p** na *Aspnet_compiler. exe*.|
|`TargetFrameworkMoniker`|Volitelný parametr `String`.<br /><br /> Určuje TargetFrameworkMoniker, který označuje, která .NET Framework verze *Aspnet_compiler. exe* by se měla použít. Přijímá pouze .NET Framework monikery.|
|`TargetPath`|Volitelný parametr `String`.<br /><br /> Určuje fyzickou cestu, na kterou je aplikace kompilována. Pokud není zadán, aplikace je předkompilována místně.|
|`Updateable`|Volitelný parametr `Boolean`.<br /><br /> Pokud je tento parametr `true`, předkompilovaná aplikace bude aktualizovatelné.  Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-u** *Aspnet_compiler. exe*.|
|`VirtualPath`|Volitelný parametr `String`.<br /><br /> Virtuální cesta aplikace, která se má zkompilovat Pokud `PhysicalPath` zadáno, použije se k vyhledání aplikace fyzická cesta. V opačném případě se použije metabáze IIS a předpokládá se, že se aplikace nachází ve výchozí lokalitě. Tento parametr odpovídá přepínači **-v** *Aspnet_compiler. exe*.|

## <a name="remarks"></a>Poznámky
Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.ToolTask> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [ToolTaskExtension – Base Class](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Příklad
Následující příklad kódu používá úlohu `AspNetCompiler` k předkompilování [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="PrecompileWeb">
        <AspNetCompiler
            VirtualPath="/MyWebSite"
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"
            TargetPath="c:\precompiledweb\MyWebSite\"
            Force="true"
            Debug="true"
        />
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také:
* [Úlohy](../msbuild/msbuild-tasks.md)
* [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
