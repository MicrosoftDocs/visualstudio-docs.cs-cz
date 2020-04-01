---
title: Vlastnosti sestavení nástrojů kontejnerů sady Visual Studio
author: ghogen
description: Přehled procesu sestavení kontejnerových nástrojů
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 3caa8a76f461515c0d2265590383861b6e10d0a1
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472667"
---
# <a name="container-tools-build-properties"></a>Kontejnerové nástroje sestavení vlastnosti

Můžete přizpůsobit, jak Visual Studio staví projekty kontejnerů nastavením vlastností, které MSBuild používá k sestavení projektu. Můžete například změnit název souboru Dockerfile, zadat značky a popisky pro vaše image, poskytnout další argumenty předané příkazům Dockeru a určit, zda Visual Studio provádí určité optimalizace výkonu, jako je vytváření mimo prostředí kontejneru. Můžete také nastavit vlastnosti ladění, jako je například název spustitelného souboru ke spuštění a argumenty příkazového řádku, které chcete poskytnout.

Chcete-li nastavit hodnotu vlastnosti, upravte soubor projektu. Předpokládejme například, že váš dockerfile se nazývá *MyDockerfile*. Vlastnost v `DockerfileFile` souboru projektu můžete nastavit následujícím způsobem.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Nastavení vlastnosti můžete přidat `PropertyGroup` do existujícího prvku, nebo pokud není, vytvořte nový `PropertyGroup` prvek.

V následující tabulce jsou uvedeny vlastnosti MSBuild, které jsou k dispozici pro projekty kontejnerů. Verze balíčku NuGet se vztahuje na [Microsoft.VisualStudio.Azure.Containers.Tools.Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Název vlastnosti | Popis | Výchozí hodnota  | Verze balíčku NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Určuje, zda je povolena optimalizace "build-on-host" ("ladění rychlého režimu".  Povolené hodnoty jsou **rychlé** a **pravidelné**. | Rychle |1.0.1872750 nebo novější|
| KontejnerVsDbgPath | Cesta pro ladicí program VSDBG. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 nebo novější|
| DockerDebuggeeArguments | Při ladění ladicí program je pokyn předat tyto argumenty spustitelného souboru. | Nevztahuje se na projekty ASP.NET rozhraní .NET Framework |1.7.8 nebo novější|
| Program DockerDebuggeeProgram | Při ladění je ladicí program instruován ke spuštění tohoto spustitelného souboru. | Pro základní projekty .NET: dotnet, ASP.NET .NET Framework projekty: Není použitelné (IIS se vždy používá) |1.7.8 nebo novější|
| Program DockerDebuggeeKillProgram | Tento příkaz se používá k usmrcení spuštěného procesu v kontejneru. | Nevztahuje se na projekty ASP.NET rozhraní .NET Framework |1.7.8 nebo novější|
| DockerDebuggeeWorkingDirectory | Při ladění je ladicí program instruován k použití této cesty jako pracovního adresáře. | C:\app (Windows) nebo /app (Linux) |1.7.8 nebo novější|
| DockerDefaultTargetOS | Výchozí cílový operační systém používaný při vytváření image Dockeru. | Sada visual studio. |1.0.1985401 nebo novější|
| DockerImageLabels | Výchozí sada popisků aplikovaných na image Dockeru. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 nebo novější|
| DockerFastModeProjectMountDirectory|V **rychlém režimu**tato vlastnost určuje, kde je výstupní adresář projektu připojen ke svazku do spuštěného kontejneru.|C:\app (Windows) nebo /app (Linux)|1.9.2 nebo novější|
| DockerfileBuildArguments | Další argumenty předané příkazu sestavení Dockeru. | Neužívá se. |1.0.1872750 nebo novější|
| DockerfileContext | Výchozí kontext používaný při vytváření image Dockeru jako cesta vzhledem k dockerfile. | Sada visual studio. |1.0.1872750 nebo novější|
| DockerfileFastModeStage | Fáze Dockerfile (to znamená cíl), která se má použít při vytváření bitové kopie v režimu ladění. | První fáze nalezená v Dockerfile (základna) |
| Soubor dockeru | Popisuje výchozí soubor Dockerfile, který bude použit k sestavení nebo spuštění kontejneru pro projekt. To může být také cesta. | Soubor dockeru |1.0.1872750 nebo novější|
| DockerfileRunArguments | Další argumenty předané příkazu spuštění Dockeru. | Neužívá se. |1.0.1872750 nebo novější|
| DockerfileRunEnvironmentFiles | Seznam souborů prostředí oddělených středníkem použitýběhem spuštění Dockeru. | Neužívá se. |1.0.1872750 nebo novější|
| Značka DockerfileTag | Značka, která se použije při vytváření image Dockeru. V ladění ":dev" je připojen ke značce. | Název sestavy po odstranění nealfanumerických znaků pomocí následujících pravidel: <br/> Pokud je výsledná značka celá číselná, pak je jako předpona vložen "image" (například image2314). <br/> Pokud je výsledná značka prázdný řetězec, pak se jako značka používá "image". |1.0.1872750 nebo novější|

## <a name="next-steps"></a>Další kroky

Informace o vlastnostech MSBuild obecně naleznete v tématu [Vlastnosti msbuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Viz také

[Vlastnosti sestavení dockeru](docker-compose-properties.md)

[Nastavení spuštění nástrojů kontejneru](container-launch-settings.md)

[Vyhrazené a dobře známé vlastnosti msbuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
