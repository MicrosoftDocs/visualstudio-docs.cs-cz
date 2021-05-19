---
title: Docker Compose nastavení sestavení
author: ghogen
description: Naučte se, jak upravit vlastnosti Docker Compose buildu a přizpůsobit tak, jak Visual Studio sestavuje a spouští aplikaci Docker Compose.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: b3744640aada798179c86cc60d2c8ce7b02ccfaa
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973476"
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
|DockerComposeBaseFilePath|dcproj|Určuje první část názvů souborů Docker-skládání souborů bez přípony *. yml* . Například: <br>1. DockerComposeBaseFilePath = null/Nedefinováno: použijte základní cestu k souboru *Docker-skládání* a soubory budou pojmenované *Docker-Compose. yml* a *Docker-Compose. override. yml*.<br>2. DockerComposeBaseFilePath = *mydockercompose:* files will be *named mydockercompose.yml* *and mydockercompose.override.yml*.<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose:* Soubory budou o jednu úroveň výše. |docker-compose|
|DockerComposeBuildArguments|dcproj|Určuje dodatečné parametry, které se mají předat `docker-compose build` příkazu. Například, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Určuje dodatečné parametry, které se mají předat `docker-compose down` příkazu. Například, `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | Pokud je zadaný, přepíše název projektu pro projekt docker-compose. | dockercompose + automaticky vygenerovaná hodnota hash |
|DockerComposeProjectPath|csproj nebo vbproj|Relativní cesta k souboru projektu docker-compose (dcproj). Tuto vlastnost nastavte při publikování projektu služby, abyste našli přidružená nastavení sestavení image uložená v souboru docker-compose.yml.|-|
|DockerComposeProjectsToIgnore|dcproj| Určuje projekty, které mají být během ladění ignorovány nástroji docker-compose. Tuto vlastnost lze použít pro libovolný projekt. Cesty k souborům lze zadat jedním ze dvou způsobů: <br> 1. relativní vzhledem k dcproj. Například, `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. absolutní cesty.<br> **Poznámka**: cesty by měly být odděleny znakem oddělovače `;` .|-|
|DockerComposeUpArguments|dcproj|Určuje další parametry, které se mají předat `docker-compose up` příkazu. Například, `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Určuje, zda je projekt uživatele sestaven v kontejneru. Povolené hodnoty **rychlého** nebo **normálního** řízení [, které fáze jsou sestaveny](https://aka.ms/containerfastmode) v souboru Dockerfile. Konfigurace ladění je rychlý režim ve výchozím nastavení a v normálním režimu. | Rychlý |
|DockerLaunchAction| dcproj | Určuje akci spuštění, která se má provést na F5 nebo CTRL + F5.  Povolené hodnoty jsou None, LaunchBrowser a LaunchWCFTestClient. | Žádná |
|DockerLaunchBrowser| dcproj | Označuje, zda se má spustit prohlížeč. Pokud je zadaná akce DockerLaunchAction, ignoruje se. | Ne |
|DockerServiceName| dcproj| Pokud jsou zadané DockerLaunchAction nebo DockerLaunchBrowser, pak DockerServiceName určuje, na kterou službu se odkazuje v souboru docker-compose.|-|
|DockerServiceUrl| dcproj | Adresa URL, která se má použít při spuštění prohlížeče.  Platné nahrazovací tokeny jsou {ServiceIPAddress}, {ServicePort} a {Scheme}.  Příklad: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Cílový operační systém použitý při sestavování image Dockeru.|-|

## <a name="example"></a>Příklad

Pokud změníte umístění souborů docker compose nastavením na relativní cestu, musíte se také ujistit, že se kontext sestavení změnil tak, aby odkazl na `DockerComposeBaseFilePath` složku řešení. Pokud je například soubor docker compose složka s názvem *DockerComposeFiles,* měl by soubor docker compose nastavit kontext sestavení na ".." nebo ".". /..", v závislosti na tom, kde je relativní vzhledem ke složce řešení.

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

Soubor *mydockercompose.yml* by měl vypadat takhle a kontext sestavení by měl být nastavený na relativní cestu ke složce řešení (v tomto případě `..` ).

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
> DockerComposeBuildArguments, DockerComposeDownArguments a DockerComposeUpArguments jsou v Visual Studio 2019 verze 16.3 nové.

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Přepsání Visual Studio konfigurace Docker Compose dat

Určitá nastavení můžete přepsat tak, že soubor s názvem *docker-compose.vs.debug.yml* (pro rychlý režim) nebo *docker-compose.vs.release.yml* (pro běžný režim) umístíte do stejného adresáře jako soubor   *docker-compose.yml.* 

>[!TIP] 
>Pokud chcete zjistit výchozí hodnoty pro kterékoli z těchto nastavení, podívejte se na *docker-compose.vs.debug.g.yml* nebo *docker-compose.vs.release.g.yml*.

### <a name="docker-compose-file-labels"></a>Docker Compose popisky souborů

 V *souboru docker-compose.vs.debug.yml* nebo *docker-compose.vs.release.yml* můžete definovat popisky specifické pro přepsání následujícím způsobem:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Hodnoty můžete obcházet dvojitými uvozovkami jako v předchozím příkladu a zpětné lomítko použijte jako řídicí znak pro zpětná lomítka v cestách.

|Název popisku|Description|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Argumenty předané programu při spuštění ladění. U aplikací .NET Core jsou tyto argumenty obvykle další cesty hledání pro balíčky NuGet následované cestou k výstupnímu sestavení projektu.|
|com.microsoft.visualstudio.debuggee.program|Program se spustí při spuštění ladění. Pro aplikace .NET Core je toto nastavení obvykle **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Adresář, který se používá jako počáteční adresář při spuštění ladění. Toto nastavení je obvykle */app pro* kontejnery Linuxu nebo *C:\app* pro kontejnery Windows.|
|com.microsoft.visualstudio.debuggee.killprogram|Tento příkaz slouží k zastavení programu debuggee spuštěného uvnitř kontejneru (v případě potřeby).|

### <a name="customize-the-docker-build-process"></a>Přizpůsobení procesu sestavení Dockeru

Pomocí nastavení ve vlastnosti můžete deklarovat, která fáze se má sestavit v souboru `target` `build` Dockerfile. Toto přepsání lze použít pouze v souboru *docker-compose.vs.debug.yml* nebo *docker-compose.vs.release.yml.* 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Přizpůsobení procesu spuštění aplikace

Příkaz nebo vlastní skript můžete spustit před spuštěním aplikace pomocí nastavení a jeho `entrypoint` závislostí na `DockerDevelopmentMode` . Pokud například potřebujete nastavit certifikát pouze v  rychlém režimu spuštěním příkazu , ale ne v normálním režimu, můžete přidat následující kód pouze v `update-ca-certificates` souboru  *docker-compose.vs.debug.yml:* 

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

[Správa profilů spuštění pro Docker Compose v aplikaci Visual Studio](launch-profiles.md)

[Vyhrazené a známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
