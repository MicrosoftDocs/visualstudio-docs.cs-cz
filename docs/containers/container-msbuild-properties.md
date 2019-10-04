---
title: Vlastnosti sestavení kontejnerů sady Visual Studio
author: ghogen
description: Přehled procesu sestavení nástrojů kontejneru
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 987d358abcccadf36d15593722ff55ba4b879d03
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950687"
---
# <a name="container-tools-build-properties"></a>Vlastnosti sestavení kontejnerových nástrojů

Můžete přizpůsobit způsob, jakým Visual Studio sestaví projekty kontejneru, nastavením vlastností, které nástroj MSBuild používá k sestavení projektu. Můžete například změnit název souboru Dockerfile, zadat značky a štítky pro obrázky, poskytnout další argumenty předané příkazům Docker a určit, zda aplikace Visual Studio provede určité optimalizace výkonu, jako je například sestavování mimo prostředí kontejneru. Můžete také nastavit vlastnosti ladění, jako je název spustitelného souboru, který se má spustit, a argumenty příkazového řádku, které mají být zadány.

Chcete-li nastavit hodnotu vlastnosti, upravte soubor projektu. Předpokládejme například, že vaše souboru Dockerfile má název *MyDockerfile*. Vlastnost `DockerfileFile` v souboru projektu lze nastavit následujícím způsobem.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Nastavení vlastnosti můžete přidat do existujícího elementu `PropertyGroup`, nebo pokud není jedna, vytvořte nový prvek `PropertyGroup`.

V následující tabulce jsou uvedeny vlastnosti MSBuild dostupné pro projekty kontejnerů. Verze balíčku NuGet se vztahuje na [Microsoft. VisualStudio. Azure. containers. Tools. targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Název vlastnosti | Popis | Výchozí hodnota  | Verze balíčku NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Určuje, jestli je povolená optimalizace optimalizace sestavení na úrovni hostitele (rychlý režim).  Povolené hodnoty jsou **rychlé** a **pravidelné**. | Světl |1.0.1872750 nebo novější|
| ContainerVsDbgPath | Cesta k ladicímu programu VSDBG | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 nebo novější|
| DockerDebuggeeArguments | Při ladění je ladicí program vyzván k předání těchto argumentů spuštěnému spustitelnému souboru. | Nedá se použít pro projekty ASP.NET .NET Framework. |1.7.8 nebo novější|
| DockerDebuggeeProgram | Při ladění je ladicí program vyzván ke spuštění tohoto spustitelného souboru. | Pro projekty .NET Core: dotnet, ASP.NET .NET Framework projekty: Nejde použít (služba IIS se vždycky používá) |1.7.8 nebo novější|
| DockerDebuggeeKillProgram | Tento příkaz slouží k ukončení běžícího procesu v kontejneru. | Nedá se použít pro projekty ASP.NET .NET Framework. |1.7.8 nebo novější|
| DockerDebuggeeWorkingDirectory | Při ladění je ladicí program vyzván k použití této cesty jako pracovního adresáře. | C:\app (Windows) nebo/App (Linux) |1.7.8 nebo novější|
| DockerDefaultTargetOS | Výchozí cílový operační systém, který se používá při vytváření image Docker. | Nastaveno sadou Visual Studio. |1.0.1985401 nebo novější|
| DockerImageLabels | Výchozí sada popisků použitých pro bitovou kopii Docker. | com.microsoft.created-by=visual-studio;com.microsoft.visual-studio.project-name=$(MSBuildProjectName) |1.5.4 nebo novější|
| DockerFastModeProjectMountDirectory|V **rychlém režimu**Tato vlastnost řídí, kde je výstupní adresář projektu připojen ke svazku do běžícího kontejneru.|C:\app (Windows) nebo/App (Linux)|1.9.2 nebo novější|
| DockerfileBuildArguments | Do příkazu Docker Build byly předány další argumenty. | Není k dispozici. |1.0.1872750 nebo novější|
| DockerfileContext | Výchozí kontext použitý při vytváření image Docker. | Nastaveno sadou Visual Studio. |1.0.1872750 nebo novější|
| DockerfileFastModeStage | Fáze souboru Dockerfile (tj. Target), která se má použít při sestavování image v režimu ladění. | V souboru Dockerfile se našla první fáze (Base). |
| DockerfileFile | Popisuje výchozí souboru Dockerfile, který bude použit k sestavení nebo spuštění kontejneru pro projekt. Může to být i cesta. | Souboru Dockerfile |1.0.1872750 nebo novější|
| DockerfileRunArguments | Další argumenty předané příkazu Docker run. | Není k dispozici. |1.0.1872750 nebo novější|
| DockerfileRunEnvironmentFiles | Středníky oddělený seznam souborů prostředí použitých při spuštění Docker. | Není k dispozici. |1.0.1872750 nebo novější|
| DockerfileTag | Značka, která bude použita při sestavování image Docker. V ladění je k značce připojen ":d EV". | Název sestavení po odstranění nealfanumerických znaků pomocí následujících pravidel: <br/> Pokud je výsledná značka všechna číselná, pak se jako předpona vloží "image" (například image2314). <br/> Pokud je výsledná značka prázdným řetězcem, použije se jako značka "image". |1.0.1872750 nebo novější|

## <a name="next-steps"></a>Další kroky

Informace o vlastnostech MSBuildu obecně naleznete v tématu [vlastnosti MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Viz také:

[Docker Compose vlastnosti sestavení](docker-compose-properties.md)

[Nastavení spuštění nástrojů kontejneru](container-launch-settings.md)

[Rezervované a dobře známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
