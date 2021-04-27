---
title: Docker Compose nastavení sestavení
author: ghogen
description: Naučte se, jak upravit vlastnosti Docker Compose buildu a přizpůsobit tak, jak Visual Studio sestavuje a spouští aplikaci Docker Compose.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: ed4b2a0dc1dc7a0520bf8e83ab1968a3815196e0
ms.sourcegitcommit: e12d6cdaeb37564f05361965db2ec8ad0d4f21ad
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025862"
---
# <a name="docker-compose-build-properties"></a>Docker Compose vlastnosti sestavení

Kromě vlastností, které řídí jednotlivé projekty Docker, popsané v tématu [Vlastnosti sestavení nástrojů kontejneru](container-msbuild-properties.md), můžete také přizpůsobit způsob, jakým Visual Studio sestaví projekty Docker Compose nastavením vlastností Docker Compose, které nástroj MSBuild používá k sestavení vašeho řešení. Můžete také určit, jak bude ladicí program sady Visual Studio spouštět vaše aplikace Docker Compose nastavením popisků souborů v konfiguračních souborech Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Jak nastavit vlastnosti MSBuild

Chcete-li nastavit hodnotu vlastnosti, upravte soubor projektu. U Docker Compose vlastností je tento soubor projektu souborem s příponou. dcproj, pokud není uvedeno jinak v tabulce v další části. Předpokládejme například, že chcete určit, že chcete spustit prohlížeč při spuštění ladění. Vlastnost můžete nastavit `DockerLaunchAction` v souboru projektu. dcproj následujícím způsobem.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Nastavení vlastnosti můžete přidat do existujícího `PropertyGroup` prvku, nebo pokud není jedna, vytvořte nový `PropertyGroup` prvek.

## <a name="docker-compose-msbuild-properties"></a>Vlastnosti nástroje MSBuild pro Docker Compose

V následující tabulce jsou uvedeny vlastnosti MSBuild dostupné pro Docker Compose projekty.

| Název vlastnosti | Umístění | Description | Výchozí hodnota  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Určuje další soubory pro vytváření v seznamu středníkem oddělených souborů, které se budou odesílat docker-compose.exe pro všechny příkazy. Relativní cesty ze souboru projektu Docker-dcproj (sestavení) jsou povoleny.|-|
|DockerComposeBaseFilePath|dcproj|Určuje první část názvů souborů Docker-skládání souborů bez přípony *. yml* . Například: <br>1. DockerComposeBaseFilePath = null/Nedefinováno: použijte základní cestu k souboru *Docker-skládání* a soubory budou pojmenované *Docker-Compose. yml* a *Docker-Compose. override. yml*.<br>2. DockerComposeBaseFilePath = *mydockercompose*: soubory budou pojmenovány *mydockercompose. yml* a *mydockercompose. override. yml*.<br> 3. DockerComposeBaseFilePath = *... \mydockercompose*: soubory budou o jednu úroveň výš. |Docker-Compose|
|DockerComposeBuildArguments|dcproj|Určuje další parametry, které se mají předat `docker-compose build` příkazu. Například, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Určuje další parametry, které se mají předat `docker-compose down` příkazu. Například, `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | Když se tato parametr zadá, přepíše název projektu pro projekt Docker-pro vytváření. | "dockercompose" + automaticky generovaná hodnota hash |
|DockerComposeProjectPath|CSPROJ nebo VBPROJ|Relativní cesta k souboru dcproj (Docker-psací projekt). Tuto vlastnost nastavte při publikování projektu služby, aby bylo možné najít přidružená nastavení pro sestavení imagí uložená v souboru Docker-Compose. yml.|-|
|DockerComposeProjectsToIgnore|dcproj| Určuje projekty, které mají být během ladění ignorovány pomocí nástrojů pro vytváření Docker. Tuto vlastnost lze použít pro libovolný projekt. Cesty k souborům lze zadat jedním ze dvou způsobů: <br> 1. relativní vzhledem k dcproj. Například, `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. absolutní cesty.<br> **Poznámka**: cesty by měly být odděleny znakem oddělovače `;` .|-|
|DockerComposeUpArguments|dcproj|Určuje další parametry, které se mají předat `docker-compose up` příkazu. Například, `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Určuje, zda je projekt uživatele sestaven v kontejneru. Povolené hodnoty **rychlého** nebo **normálního** řízení [, které fáze jsou sestaveny](https://aka.ms/containerfastmode) v souboru Dockerfile. Konfigurace ladění je rychlý režim ve výchozím nastavení a v normálním režimu. | Rychlý |
|DockerLaunchAction| dcproj | Určuje akci spuštění, která se má provést na F5 nebo CTRL + F5.  Povolené hodnoty jsou None, LaunchBrowser a LaunchWCFTestClient. | Žádné |
|DockerLaunchBrowser| dcproj | Označuje, zda se má spustit prohlížeč. Ignoruje se, pokud je zadaný DockerLaunchAction. | Ne |
|DockerServiceName| dcproj| Pokud jsou zadány DockerLaunchAction nebo DockerLaunchBrowser, pak DockerServiceName určuje, která služba je odkazována v souboru Docker-skládání.|-|
|DockerServiceUrl| dcproj | Adresa URL, která se má použít při spuštění prohlížeče.  Platné náhradní tokeny jsou {ServiceIPAddress}, {ServicePort} a {schéma}.  Příklad: {schéma}://{ServiceIPAddress}: {ServicePort}|-|
|DockerTargetOS| dcproj | Cílový operační systém, který se používá při vytváření image Docker.|-|

## <a name="example"></a>Příklad

Pokud změníte umístění souborů Docker pro sestavení nastavením `DockerComposeBaseFilePath` na relativní cestu, musíte také zajistit, aby byl kontext sestavení změněn tak, aby odkazoval na složku řešení. Například, pokud je soubor s příznakem Docker složka s názvem *DockerComposeFiles*, musí soubor. Docker pro sestavení nastavit kontext buildu na ".." nebo ".. /.. ", v závislosti na tom, kde je relativní ke složce řešení.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

Soubor *mydockercompose. yml* by měl vypadat takto, s kontextem sestavení nastaveným na relativní cestu ke složce řešení (v tomto případě `..` ).

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments a DockerComposeUpArguments jsou v systému Visual Studio 2019 verze 16,3 novinkou.

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Přepsání konfigurace Docker Compose sady Visual Studio

Určitá nastavení můžete přepsat umístěním souboru s názvem *Docker-Compose. vs. Debug. yml* (pro **rychlý** režim) nebo *Docker-Compose. vs. Release. yml* (pro **běžný** režim) ve stejném adresáři jako soubor *Docker-Compose. yml* . 

>[!TIP] 
>Pokud chcete zjistit výchozí hodnoty pro některá z těchto nastavení, podívejte se do *Docker-Compose. vs. Debug. g. yml* nebo *Docker-Compose. vs. Release. g. yml*.

### <a name="docker-compose-file-labels"></a>Docker Compose popisky souborů

 V *Docker-Compose. vs. Debug. yml* nebo *Docker-Compose. vs. Release. yml* můžete definovat popisky specifické pro přepsání následujícím způsobem:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Použijte dvojité uvozovky kolem hodnot, jako v předchozím příkladu, a použijte zpětné lomítko jako řídicí znak pro zpětná lomítka v cestách.

|Název popisku|Description|
|----------|-----------|
|com. Microsoft. VisualStudio. laděného procesu. arguments|Argumenty předávané programu při spuštění ladění. Pro aplikace .NET Core jsou tyto argumenty obvykle další cesty hledání balíčků NuGet následovaných cestou k výstupnímu sestavení projektu.|
|com. Microsoft. VisualStudio. laděného procesu. program|Program byl spuštěn při spuštění ladění. Pro aplikace .NET Core je toto nastavení obvykle **dotnet**.|
|com. Microsoft. VisualStudio. laděného procesu. WorkingDirectory|Adresář používaný jako spouštěcí adresář při spuštění ladění. Toto nastavení je obvykle */App* pro kontejnery Linux nebo *C:\app* pro kontejnery Windows.|
|com. Microsoft. VisualStudio. laděného procesu. killprogram|Tento příkaz slouží k zastavení programu laděného procesu, který běží uvnitř kontejneru (v případě potřeby).|

### <a name="customize-the-docker-build-process"></a>Přizpůsobení procesu sestavení Docker

Můžete deklarovat, kterou fázi sestavit v souboru Dockerfile pomocí `target` nastavení ve `build` Vlastnosti. Toto přepsání lze použít pouze v *Docker-Compose. vs. Debug. yml* nebo *Docker-Compose. vs. Release. yml* 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Přizpůsobení procesu spuštění aplikace

Můžete spustit příkaz nebo vlastní skript před spuštěním aplikace pomocí `entrypoint` nastavení a tím, že bude závislý na `DockerDevelopmentMode` . Například pokud potřebujete nastavit certifikát pouze v **rychlém** režimu spuštěním `update-ca-certificates` , ale ne v **normálním** režimu, můžete přidat následující kód **pouze** do *Docker-Compose. vs. Debug. yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Další kroky

Informace o vlastnostech MSBuildu obecně naleznete v tématu [vlastnosti MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Viz také

[Vlastnosti sestavení kontejnerových nástrojů](container-msbuild-properties.md)

[Nastavení spuštění nástrojů kontejneru](container-launch-settings.md)

[Vyhrazené a známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
