---
title: Vlastnosti sestavení kontejnerů sady Visual Studio
author: ghogen
description: Přehled procesu sestavení nástrojů kontejneru
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 427a70d9bc4f6ef326ffb16e7d26df9d8fae2365
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283200"
---
# <a name="container-tools-build-properties"></a>Vlastnosti sestavení kontejnerových nástrojů

Můžete přizpůsobit způsob, jakým Visual Studio sestaví projekty kontejneru, nastavením vlastností, které nástroj MSBuild používá k sestavení projektu. Můžete například změnit název souboru Dockerfile, zadat značky a štítky pro obrázky, poskytnout další argumenty předané příkazům Docker a určit, zda aplikace Visual Studio provede určité optimalizace výkonu, jako je například sestavení mimo prostředí kontejneru. Můžete také nastavit vlastnosti ladění, jako je název spustitelného souboru, který se má spustit, a argumenty příkazového řádku, které mají být zadány.

Chcete-li nastavit hodnotu vlastnosti, upravte soubor projektu. Předpokládejme například, že vaše souboru Dockerfile má název *MyDockerfile*. Vlastnost můžete nastavit `DockerfileFile` v souboru projektu následujícím způsobem.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Nastavení vlastnosti můžete přidat do existujícího `PropertyGroup` prvku, nebo pokud není jedna, vytvořte nový `PropertyGroup` prvek.

V následující tabulce jsou uvedeny vlastnosti MSBuild dostupné pro projekty kontejnerů. Verze balíčku NuGet se vztahuje na [Microsoft. VisualStudio. Azure. containers. Tools. targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/).

| Název vlastnosti | Popis | Výchozí hodnota  | Verze balíčku NuGet|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | Určuje, jestli je povolená optimalizace optimalizace sestavení na úrovni hostitele (rychlý režim).  Povolené hodnoty jsou **rychlé** a **pravidelné**. | Rychlý |1.0.1872750 nebo novější|
| ContainerVsDbgPath | Cesta k ladicímu programu VSDBG | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 nebo novější|
| DockerDebuggeeArguments | Při ladění je ladicí program vyzván k předání těchto argumentů spuštěnému spustitelnému souboru. | Nedá se použít pro projekty ASP.NET .NET Framework. |1.7.8 nebo novější|
| DockerDebuggeeProgram | Při ladění je ladicí program vyzván ke spuštění tohoto spustitelného souboru. | Pro projekty .NET Core: dotnet, ASP.NET .NET Framework projekty: nejde použít (služba IIS se vždycky používá). |1.7.8 nebo novější|
| DockerDebuggeeKillProgram | Tento příkaz slouží k ukončení běžícího procesu v kontejneru. | Nedá se použít pro projekty ASP.NET .NET Framework. |1.7.8 nebo novější|
| DockerDebuggeeWorkingDirectory | Při ladění je ladicí program vyzván k použití této cesty jako pracovního adresáře. | C:\app (Windows) nebo/App (Linux) |1.7.8 nebo novější|
| DockerDefaultTargetOS | Výchozí cílový operační systém, který se používá při vytváření image Docker. | Nastaveno sadou Visual Studio. |1.0.1985401 nebo novější|
| DockerImageLabels | Výchozí sada popisků použitých pro bitovou kopii Docker. | com. Microsoft. Created-by = Visual-Studio; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |1.5.4 nebo novější|
| DockerFastModeProjectMountDirectory|V **rychlém režimu**Tato vlastnost řídí, kde je výstupní adresář projektu připojen ke svazku do běžícího kontejneru.|C:\app (Windows) nebo/App (Linux)|1.9.2 nebo novější|
| DockerfileBuildArguments | Do příkazu [Docker Build](https://docs.docker.com/engine/reference/commandline/build/) byly předány další argumenty. | Neužívá se. |1.0.1872750 nebo novější|
| DockerfileContext | Výchozí kontext použitý při vytváření image Docker jako cesta relativní k souboru Dockerfile. | Nastaveno sadou Visual Studio. |1.0.1872750 nebo novější|
| DockerfileFastModeStage | Fáze souboru Dockerfile (tj. Target), která se má použít při sestavování image v režimu ladění. | V souboru Dockerfile se našla první fáze (Base). |
| DockerfileFile | Popisuje výchozí souboru Dockerfile, který bude použit k sestavení nebo spuštění kontejneru pro projekt. Může to být i cesta. | Dockerfile |1.0.1872750 nebo novější|
| DockerfileRunArguments | Další argumenty předané příkazu [Docker Run](https://docs.docker.com/engine/reference/commandline/run/) . | Neužívá se. |1.0.1872750 nebo novější|
| DockerfileRunEnvironmentFiles | Středníky oddělený seznam souborů prostředí použitých při spuštění Docker. | Neužívá se. |1.0.1872750 nebo novější|
| DockerfileTag | Značka, která bude použita při sestavování image Docker. V ladění je k značce připojen ":d EV". | Název sestavení po odstranění nealfanumerických znaků pomocí následujících pravidel: <br/> Pokud je výsledná značka všechna číselná, pak se jako předpona vloží "image" (například image2314). <br/> Pokud je výsledná značka prázdným řetězcem, použije se jako značka "image". |1.0.1872750 nebo novější|

## <a name="example"></a>Příklad

Následující soubor projektu ukazuje příklady některých z těchto nastavení.

```xml
 <Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UserSecretsId>feae72bf-2368-4487-b6c6-546c19338cb1</UserSecretsId>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
    <!-- In CI/CD scenarios, you might need to change the context. By default, Visual Studio uses the
         folder above the Dockerfile. The path is relative to the Dockerfile, so here the context is
         set to the same folder as the Dockerfile. -->
    <DockerfileContext>.</DockerfileContext>
    <!-- Set `docker run` arguments to mount a volume -->
    <DockerfileRunArguments>-v $(pwd)/host-folder:/container-folder:ro</DockerfileRunArguments>
    <!-- Set `docker build` arguments to add a custom tag -->
    <DockerfileBuildArguments>-t contoso/front-end:v2.0</DockerfileBuildArguments>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.VisualStudio.Azure.Containers.Tools.Targets" Version="1.10.6" />
  </ItemGroup>

</Project>
```

## <a name="next-steps"></a>Další kroky

Informace o vlastnostech MSBuildu obecně naleznete v tématu [vlastnosti MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Viz také

[Docker Compose vlastnosti sestavení](docker-compose-properties.md)

[Nastavení spuštění nástrojů kontejneru](container-launch-settings.md)

[Vyhrazené a známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
