---
title: 'Postup: Použití proměnných prostředí v sestavení | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environment variables, referencing
- projects [.NET Framework], environment variables
- MSBuild, environment variables
ms.assetid: 7f9e4469-8865-4b59-aab3-3ff26bd36e77
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afc679f9b782b8bc9ed3e04a2b8fb684cdbc1a20
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633782"
---
# <a name="how-to-use-environment-variables-in-a-build"></a>Postup: Použití proměnných prostředí v sestavení

Při vytváření projektů je často nutné nastavit možnosti sestavení pomocí informací, které nejsou v souboru projektu nebo soubory, které tvoří projekt. Tyto informace jsou obvykle uloženy v proměnných prostředí.

## <a name="reference-environment-variables"></a>Proměnné referenčního prostředí

 Všechny proměnné prostředí jsou k dispozici pro soubor projektu Microsoft Build Engine (MSBuild) jako vlastnosti.

> [!NOTE]
> Pokud soubor projektu obsahuje explicitní definici vlastnosti, která má stejný název jako proměnná prostředí, vlastnost v souboru projektu přepíše hodnotu proměnné prostředí.

#### <a name="to-use-an-environment-variable-in-an-msbuild-project"></a>Použití proměnné prostředí v projektu MSBuild

- Odkazna proměnnou prostředí stejným způsobem jako proměnná deklarovaná v souboru projektu. Například následující kód odkazuje na proměnnou prostředí BIN_PATH:

   `<FinalOutput>$(BIN_PATH)\MyAssembly.dll</FinalOutput>`

  `Condition` Atribut můžete použít k zadání výchozí hodnoty pro vlastnost, pokud proměnná prostředí nebyla nastavena.

#### <a name="to-provide-a-default-value-for-a-property"></a>Poskytnutí výchozí hodnoty pro vlastnost

- Pomocí `Condition` atributu vlastnosti nastavte hodnotu pouze v případě, že vlastnost nemá žádnou hodnotu. Například následující kód nastaví `ToolsPath` vlastnost *c:\tools* `ToolsPath` pouze v případě, že proměnná prostředí není nastavena:

     `<ToolsPath Condition="'$(TOOLSPATH)' == ''">c:\tools</ToolsPath>`

    > [!NOTE]
    > Názvy vlastností nejsou rozlišována malá a velká písmena, takže obě `$(ToolsPath)` a `$(TOOLSPATH)` odkazují na stejnou vlastnost nebo proměnnou prostředí.

## <a name="example"></a>Příklad

 Následující soubor projektu používá proměnné prostředí k určení umístění adresářů.

```xml
<Project DefaultTargets="FakeBuild">
    <PropertyGroup>
        <FinalOutput>$(BIN_PATH)\myassembly.dll</FinalOutput>
        <ToolsPath Condition=" '$(ToolsPath)' == '' ">
            C:\Tools
        </ToolsPath>
    </PropertyGroup>
    <Target Name="FakeBuild">
        <Message Text="Building $(FinalOutput) using the tools at $(ToolsPath)..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Msbuild](../msbuild/msbuild.md)
- [Vlastnosti MSBuild](../msbuild/msbuild-properties.md)
- [Postup: Vytvoření stejných zdrojových souborů s různými možnostmi](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
