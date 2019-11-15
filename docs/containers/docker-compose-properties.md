---
title: Nástroje kontejneru sady Visual Studio Docker Compose nastavení sestavení
author: ghogen
description: Přehled procesu sestavení nástrojů kontejneru
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: c2f96bcc9df16b5de7d7f3ff485431352800d27e
ms.sourcegitcommit: 9801fc66a14c0f855b9ff601fb981a9e5321819e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74072728"
---
# <a name="docker-compose-build-properties"></a>Docker Compose vlastnosti sestavení

Kromě vlastností, které řídí jednotlivé projekty Docker, popsaných v tématu [Vlastnosti sestavení nástrojů kontejneru](container-msbuild-properties.md), můžete také přizpůsobit způsob, jakým Visual Studio sestaví projekty Docker Compose nastavením vlastností Docker Compose, které MSBuild používá k sestavení řešení. Můžete také určit, jak bude ladicí program sady Visual Studio spouštět vaše aplikace Docker Compose nastavením popisků souborů v konfiguračních souborech Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Jak nastavit vlastnosti MSBuild

Chcete-li nastavit hodnotu vlastnosti, upravte soubor projektu. U Docker Compose vlastností je tento soubor projektu souborem s příponou. dcproj, pokud není uvedeno jinak v tabulce v další části. Předpokládejme například, že chcete určit, že chcete spustit prohlížeč při spuštění ladění. Můžete nastavit vlastnost `DockerLaunchAction` v souboru projektu. dcproj následujícím způsobem.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Nastavení vlastnosti můžete přidat do existujícího prvku `PropertyGroup`, nebo pokud není k dispozici, vytvořte nový prvek `PropertyGroup`.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose vlastnosti MSBuild

V následující tabulce jsou uvedeny vlastnosti MSBuild dostupné pro Docker Compose projekty.

| Název vlastnosti | Umístění | Popis | Výchozí hodnota  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFiles|dcproj|Určuje další soubory pro vytváření v seznamu středníkem oddělených souborů, které se budou odesílat do souboru Docker-Compose. exe pro všechny příkazy. Relativní cesty ze souboru projektu Docker-dcproj (sestavení) jsou povoleny.|-|
|DockerComposeBaseFilePath|dcproj|Určuje první část názvů souborů Docker-skládání souborů bez přípony *. yml* . Příklad: <br>1. DockerComposeBaseFilePath = null/Nedefinováno: použijte základní cestu k souboru *Docker-skládání*a soubory budou pojmenovány *Docker-Compose. yml* a *Docker-Compose. override. yml*<br>2. DockerComposeBaseFilePath = *mydockercompose*: soubory budou pojmenovány *mydockercompose. yml* a *mydockercompose. override. yml*<br> 3. DockerComposeBaseFilePath = *... \mydockercompose*: soubory budou o jednu úroveň výš. |Docker-Compose|
|DockerComposeBuildArguments|dcproj|Určuje nadbytečné parametry, které se mají předat příkazu `docker-compose build`. Třeba `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Určuje nadbytečné parametry, které se mají předat příkazu `docker-compose down`. Třeba `--timeout 500`.|-|  
|DockerComposeProjectPath|CSPROJ nebo VBPROJ|Relativní cesta k souboru dcproj (Docker-psací projekt). Tuto vlastnost nastavte při publikování projektu služby, aby bylo možné najít přidružená nastavení pro sestavení imagí uložená v souboru Docker-Compose. yml.|-|
|DockerComposeUpArguments|dcproj|Určuje nadbytečné parametry, které se mají předat příkazu `docker-compose up`. Třeba `--timeout 500`.|-|
|DockerLaunchAction| dcproj | Určuje akci spuštění, která se má provést na F5 nebo CTRL + F5.  Povolené hodnoty jsou None, LaunchBrowser a LaunchWCFTestClient.|Žádné|
|DockerLaunchBrowser| dcproj | Označuje, zda se má spustit prohlížeč. Ignoruje se, pokud je zadaný DockerLaunchAction. | False |
|DockerServiceName| dcproj|Pokud jsou zadány DockerLaunchAction nebo DockerLaunchBrowser, pak DockerServiceName je název služby, která se má spustit.  Tato vlastnost slouží k určení, který z potenciálně mnoho projektů, na který může odkazovat soubor Docker-na sestavení, se spustí.|-|
|DockerServiceUrl| dcproj | Adresa URL, která se má použít při spuštění prohlížeče.  Platné náhradní tokeny jsou {ServiceIPAddress}, {ServicePort} a {schéma}.  Příklad: {schéma}://{ServiceIPAddress}: {ServicePort}|-|
|DockerTargetOS| dcproj | Cílový operační systém, který se používá při vytváření image Docker.|-|

## <a name="example"></a>Příklad

Pokud změníte umístění souborů Docker, nastavením `DockerComposeBaseFilePath` na relativní cestu, musíte také zajistit, aby byl kontext sestavení změněn tak, aby odkazoval na složku řešení. Například, pokud je soubor s příznakem Docker složka s názvem *DockerComposeFiles*, musí soubor. Docker pro sestavení nastavit kontext buildu na ".." nebo ".. /.. ", v závislosti na tom, kde je relativní ke složce řešení.

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

Soubor *mydockercompose. yml* by měl vypadat takto, s kontextem sestavení nastaveným na relativní cestu ke složce řešení (v tomto případě `..`).

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

## <a name="docker-compose-file-labels"></a>Docker Compose popisky souborů

Můžete také přepsat určitá nastavení umístěním souboru s názvem *Docker-Compose. vs. Debug. yml* (pro konfiguraci **ladění** ) nebo *Docker-Compose. vs. Release. yml* (pro konfiguraci **vydané verze** ) ve stejném adresáři jako vaše  *soubor Docker-Compose. yml* .  V tomto souboru můžete zadat nastavení následujícím způsobem:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Použijte dvojité uvozovky kolem hodnot, jako v předchozím příkladu, a použijte zpětné lomítko jako řídicí znak pro zpětná lomítka v cestách.

|Název popisku|Popis|
|----------|-----------|
|com. Microsoft. VisualStudio. laděného procesu. arguments|Argumenty předávané programu při spuštění ladění. Pro aplikace .NET Core jsou tyto argumenty obvykle další cesty hledání balíčků NuGet následovaných cestou k výstupnímu sestavení projektu.|
|com. Microsoft. VisualStudio. laděného procesu. killprogram|Tento příkaz slouží k zastavení programu laděného procesu, který běží uvnitř kontejneru (v případě potřeby).|
|com. Microsoft. VisualStudio. laděného procesu. program|Program byl spuštěn při spuštění ladění. Pro aplikace .NET Core je toto nastavení obvykle **dotnet**.|
|com. Microsoft. VisualStudio. laděného procesu. WorkingDirectory|Adresář používaný jako spouštěcí adresář při spuštění ladění. Toto nastavení je obvykle */App* pro kontejnery Linux nebo *C:\app* pro kontejnery Windows.|

## <a name="next-steps"></a>Další kroky

Informace o vlastnostech MSBuildu obecně naleznete v tématu [vlastnosti MSBuild](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Viz také:

[Vlastnosti sestavení kontejnerových nástrojů](container-msbuild-properties.md)

[Nastavení spuštění nástrojů kontejneru](container-launch-settings.md)

[Rezervované a dobře známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
