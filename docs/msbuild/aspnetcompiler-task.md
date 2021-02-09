---
title: Použití úlohy AspNetCompiler – k předkompilování ASP.NET
description: Použijte úlohu MSBuild AspNetCompiler – k zabalení aspnet_compiler.exe, nástroje pro předkompilování aplikací ASP.NET.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 504ea606994e06847c2e093bc1701b11ad92e278
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923880"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler – úloha

`AspNetCompiler`Úkol se zalomí *aspnet_compiler.exe*, což je nástroj pro předkompilování aplikací ASP.NET.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `AspNetCompiler` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Volitelný `Boolean` parametr.<br /><br /> Pokud je tento parametr `true` ,, sestavení se silným názvem umožní částečně důvěryhodné volající.|
|`Clean`|Volitelný `Boolean` parametr<br /><br /> Pokud je tento parametr `true` , předkompilovaná aplikace bude sestavena jako čistá. Všechny dříve kompilované součásti budou znovu zkompilovány. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-c** na *aspnet_compiler.exe*.|
|`Debug`|Volitelný `Boolean` parametr.<br /><br /> Pokud je tento parametr `true` , ladicí informace (. Soubor PDB) je generován během kompilace. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-d** na *aspnet_compiler.exe*.|
|`DelaySign`|Volitelný `Boolean` parametr.<br /><br /> Pokud je tento parametr `true` , sestavení není po vytvoření plně podepsáno.|
|`FixedNames`|Volitelný `Boolean` parametr.<br /><br /> Pokud je tento parametr `true` , zkompilované sestavení budou mít pevné názvy..|
|`Force`|Volitelný `Boolean` parametr<br /><br /> Pokud je tento parametr `true` , úloha přepíše cílový adresář, pokud již existuje. Existující obsah bude ztracen. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-f** na *aspnet_compiler.exe*.|
|`KeyContainer`|Volitelný `String` parametr.<br /><br /> Určuje kontejner klíče se silným názvem.|
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu k souboru klíče se silným názvem..|
|`MetabasePath`|Volitelný `String` parametr.<br /><br /> Určuje úplnou cestu metabáze služby IIS aplikace. Tento parametr nelze kombinovat s `VirtualPath` `PhysicalPath` parametry nebo. Tento parametr odpovídá přepínači **-m** na *aspnet_compiler.exe*.|
|`PhysicalPath`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu aplikace, která má být zkompilována. Pokud tento parametr chybí, použije se k vyhledání aplikace metabáze IIS. Tento parametr odpovídá přepínači **-p** na *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Volitelný `String` parametr.<br /><br /> Určuje TargetFrameworkMoniker, který označuje, která .NET Framework verze *aspnet_compiler.exe* by se měla použít. Přijímá pouze .NET Framework monikery.|
|`TargetPath`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu, na kterou je aplikace kompilována. Pokud není zadán, aplikace je předkompilována místně.|
|`Updateable`|Volitelný `Boolean` parametr.<br /><br /> Pokud je tento parametr `true` , předkompilovaná aplikace bude aktualizovatelné.  Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-u** *aspnet_compiler.exe*.|
|`VirtualPath`|Volitelný `String` parametr.<br /><br /> Virtuální cesta aplikace, která se má zkompilovat `PhysicalPath`Je-li tento parametr zadán, slouží k vyhledání aplikace fyzickou cestu. V opačném případě se použije metabáze IIS a předpokládá se, že se aplikace nachází ve výchozí lokalitě. Tento parametr odpovídá přepínači **-v** *aspnet_compiler.exe*.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Příklad

Následující příklad kódu používá `AspNetCompiler` úlohu k předkompilování aplikace ASP.NET.

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

## <a name="see-also"></a>Viz také

* [Úlohy](../msbuild/msbuild-tasks.md)
* [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
* [Nástroj pro kompilaci ASP.NET (aspnet_compiler.exe)](/previous-versions/ms229863(v=vs.100))
