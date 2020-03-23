---
title: Visual Studio Kontejner Nástroje Docker sestavení nastavení sestavení
author: ghogen
description: Přehled procesu sestavení kontejnerových nástrojů
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 85cb8745a14439cfb09036a1bc96e6bd0fa15ae4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988508"
---
# <a name="docker-compose-build-properties"></a>Vlastnosti sestavení dockeru

Kromě vlastností, které řídí jednotlivé projekty Dockeru, popsané ve [vlastnostech sestavení nástroje kontejneru](container-msbuild-properties.md), můžete také přizpůsobit způsob, jakým Visual Studio vytváří projekty Docker Compose nastavením vlastností Docker Compose, které MSBuild používá k sestavení vašeho řešení. Můžete také řídit, jak ladicí program Sady Visual Studio spouští aplikace Docker Compose nastavením popisků souborů v konfiguračních souborech Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Jak nastavit vlastnosti MSBuild

Chcete-li nastavit hodnotu vlastnosti, upravte soubor projektu. Pro vlastnosti Docker Compose je tento soubor projektu soubor s příponou .dcproj, pokud není v tabulce v další části uvedeno jinak. Předpokládejme například, že chcete zadat spuštění prohlížeče při spuštění ladění. Vlastnost v `DockerLaunchAction` souboru projektu .dcproj můžete nastavit následujícím způsobem.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Nastavení vlastnosti můžete přidat `PropertyGroup` do existujícího prvku, nebo pokud není, vytvořte nový `PropertyGroup` prvek.

## <a name="docker-compose-msbuild-properties"></a>Vlastnosti nástroje MSBuild pro Docker Compose

V následující tabulce jsou uvedeny vlastnosti MSBuild, které jsou k dispozici pro projekty Docker Compose.

| Název vlastnosti | Umístění | Popis | Výchozí hodnota  |
|---------------|----------|-------------|----------------|
|Další composefilepaths|dcproj|Určuje další soubory pro skládání v seznamu odděleném středníkem, které mají být odeslány do docker-compose.exe pro všechny příkazy. Relativní cesty ze souboru projektu docker-compose (dcproj) jsou povoleny.|-|
|Cesta DockerComposeBaseFilePath|dcproj|Určuje první část názvů souborů docker-compose bez přípony *.yml.* Například: <br>1. DockerComposeBaseFilePath = null/undefined: použijte základní cestu *souboru docker-compose*a soubory budou pojmenovány *docker-compose.yml* a *docker-compose.override.yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*: soubory budou *pojmenovány mydockercompose.yml* a *mydockercompose.override.yml*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: soubory budou o jednu úroveň vyšší. |docker-compose|
|DockerComposeBuildArguments|dcproj|Určuje další parametry, které `docker-compose build` mají být příkazu předány. Například `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Určuje další parametry, které `docker-compose down` mají být příkazu předány. Například `--timeout 500`.|-|  
|Cesta dockercomposeprojektu|csproj nebo vbproj|Relativní cesta k souboru projektu docker-compose (dcproj). Nastavte tuto vlastnost při publikování projektu služby najít přidružené nastavení sestavení bitové kopie uložené v souboru docker-compose.yml.|-|
|DockerComposeUpArguments|dcproj|Určuje další parametry, které `docker-compose up` mají být příkazu předány. Například `--timeout 500`.|-|
|DockerDevelopmentMode|dcproj| Určuje, zda je povolena optimalizace "build-on-host" ("ladění rychlého režimu".  Povolené hodnoty jsou **rychlé** a **pravidelné**. | Rychle |
|DockerLaunchAction| dcproj | Určuje spouštěcí akci, která má být v yf5 nebo Ctrl+F5.  Povolené hodnoty jsou Žádný, LaunchBrowser a LaunchWCFTestClient|Žádný|
|DockerLaunchBrowser| dcproj | Označuje, zda se má spustit prohlížeč. Ignorováno, pokud je zadána akce DockerLaunchAction. | False |
|DockerServiceName| dcproj|Pokud jsou zadány DockerLaunchAction nebo DockerLaunchBrowser, pak DockerServiceName je název služby, která by měla být spuštěna.  Pomocí této vlastnosti můžete určit, které z potenciálně mnoho projektů, které docker-compose soubor může odkazovat bude spuštěna.|-|
|Adresa DockerServiceUrl| dcproj | Adresa URL, která se má použít při spuštění prohlížeče.  Platné náhradní tokeny jsou "{ServiceIPAddress}", "{ServicePort}" a {Scheme}.  Příklad: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|Dockertargetos| dcproj | Cílový operační systém použitý při vytváření image Dockeru.|-|

## <a name="example"></a>Příklad

Pokud změníte umístění docker ukládat soubory, `DockerComposeBaseFilePath` nastavením relativní cestu, pak je také nutné se ujistit, že kontext sestavení se změní tak, aby odkazuje na složku řešení. Pokud je například váš soubor docker compose složka s názvem *DockerComposeFiles*, pak by měl soubor compose dockeru nastavit kontext sestavení na ".." nebo ".. /..", v závislosti na tom, kde je relativní ke složce řešení.

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

Soubor *mydockercompose.yml* by měl vypadat takto, s kontextem sestavení nastaveným na `..`relativní cestu složky řešení (v tomto případě).

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
> DockerComposeBuildArguments, DockerComposeDownArguments a DockerComposeUpArguments jsou nové ve Visual Studiu 2019 verze 16.3.

## <a name="docker-compose-file-labels"></a>Popisky souborů Docker Compose

Určitá nastavení můžete také přepsat umístěním souboru s názvem *docker-compose.vs.debug.yml* (pro konfiguraci **ladění)** nebo *docker-compose.vs.release.yml* (pro konfiguraci **release)** do stejného adresáře jako soubor *docker-compose.yml.*  V tomto souboru můžete zadat nastavení takto:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Použijte dvojité uvozovky kolem hodnot, jako v předchozím příkladu, a použijte zpětné lomítko jako řídicí znak pro zpětná lomítka v cestách.

|Název popisku|Popis|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Argumenty předané programu při spuštění ladění. Pro aplikace .NET Core jsou tyto argumenty obvykle další cesty hledání pro balíčky NuGet následované cestou k výstupnímu sestavení projektu.|
|com.microsoft.visualstudio.debuggee.killprogram|Tento příkaz se používá k zastavení programu ladění, který je spuštěn uvnitř kontejneru (v případě potřeby).|
|com.microsoft.visualstudio.debuggee.program|Program byl spuštěn při spuštění ladění. U aplikací .NET Core je toto nastavení obvykle **dotnet**.|
|com.microsoft.visualstudio.debuggee.workingdirectory|Adresář použitý jako počáteční adresář při spuštění ladění. Toto nastavení je obvykle */app* pro linuxové kontejnery nebo *C:\app* pro kontejnery windows.|

## <a name="customize-the-app-startup-process"></a>Přizpůsobení procesu spuštění aplikace

Před spuštěním aplikace můžete spustit příkaz nebo `entrypoint` vlastní skript pomocí nastavení a jeho závislostí na konfiguraci. Například pokud potřebujete nastavit certifikát pouze **Debug** v režimu `update-ca-certificates`ladění spuštěním , ale ne v režimu **vydání,** můžete přidat následující kód pouze v *docker-compose.vs.debug.yml*:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

Pokud vynesete *docker-compose.vs.release.yml* nebo *docker-compose.vs.debug.yml* pak Visual Studio generuje jeden na základě výchozího nastavení.

## <a name="next-steps"></a>Další kroky

Informace o vlastnostech MSBuild obecně naleznete v tématu [Vlastnosti msbuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Viz také

[Kontejnerové nástroje sestavení vlastnosti](container-msbuild-properties.md)

[Nastavení spuštění nástrojů kontejneru](container-launch-settings.md)

[Vyhrazené a dobře známé vlastnosti msbuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
