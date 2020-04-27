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
ms.openlocfilehash: 072d1b94c552b3aca34a1573e5d6545628f6568e
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167329"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler – úloha

`AspNetCompiler` Úkol zalomí *Aspnet_compiler. exe*, nástroj pro předkompilování aplikací ASP.NET.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `AspNetCompiler` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr,, sestavení se silným názvem umožní částečně důvěryhodné volající.|
|`Clean`|Volitelný `Boolean` parametr<br /><br /> Pokud je `true`tento parametr, předkompilovaná aplikace bude sestavena jako čistá. Všechny dříve kompilované součásti budou znovu zkompilovány. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-c** na *Aspnet_compiler. exe*.|
|`Debug`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr, ladicí informace (. Soubor PDB) je generován během kompilace. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-d** na *Aspnet_compiler. exe*.|
|`DelaySign`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr, sestavení není po vytvoření plně podepsáno.|
|`FixedNames`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr, zkompilované sestavení budou mít pevné názvy..|
|`Force`|Volitelný `Boolean` parametr<br /><br /> Pokud je `true`tento parametr, úloha přepíše cílový adresář, pokud již existuje. Existující obsah bude ztracen. Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-f** na *Aspnet_compiler. exe*.|
|`KeyContainer`|Volitelný `String` parametr.<br /><br /> Určuje kontejner klíče se silným názvem.|
|`KeyFile`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu k souboru klíče se silným názvem..|
|`MetabasePath`|Volitelný `String` parametr.<br /><br /> Určuje úplnou cestu metabáze služby IIS aplikace. Tento parametr nelze kombinovat s parametry `VirtualPath` nebo. `PhysicalPath` Tento parametr odpovídá přepínači **-m** na *Aspnet_compiler. exe*.|
|`PhysicalPath`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu aplikace, která má být zkompilována. Pokud tento parametr chybí, použije se k vyhledání aplikace metabáze IIS. Tento parametr odpovídá přepínači **-p** na *Aspnet_compiler. exe*.|
|`TargetFrameworkMoniker`|Volitelný `String` parametr.<br /><br /> Určuje TargetFrameworkMoniker, který označuje, která .NET Framework verze *Aspnet_compiler. exe* by se měla použít. Přijímá pouze .NET Framework monikery.|
|`TargetPath`|Volitelný `String` parametr.<br /><br /> Určuje fyzickou cestu, na kterou je aplikace kompilována. Pokud není zadán, aplikace je předkompilována místně.|
|`Updateable`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true`tento parametr, předkompilovaná aplikace bude aktualizovatelné.  Výchozí hodnota je `false`. Tento parametr odpovídá přepínači **-u** *Aspnet_compiler. exe*.|
|`VirtualPath`|Volitelný `String` parametr.<br /><br /> Virtuální cesta aplikace, která se má zkompilovat Je `PhysicalPath` -li tento parametr zadán, slouží k vyhledání aplikace fyzickou cestu. V opačném případě se použije metabáze IIS a předpokládá se, že se aplikace nachází ve výchozí lokalitě. Tento parametr odpovídá přepínači **-v** *Aspnet_compiler. exe*.|

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
* [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
