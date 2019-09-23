---
title: Nástroje kontejneru sady Visual Studio Docker Compose nastavení sestavení
author: ghogen
description: Přehled procesu sestavení nástrojů kontejneru
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 06a1c5b637ca2ed9306162ee1960c60d103e5843
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185978"
---
# <a name="docker-compose-build-properties"></a>Docker Compose vlastnosti sestavení

Kromě vlastností, které řídí jednotlivé projekty Docker, popsaných v tématu [Vlastnosti sestavení nástrojů kontejneru](container-msbuild-properties.md), můžete také přizpůsobit způsob, jakým Visual Studio sestaví projekty Docker Compose nastavením vlastností Docker Compose, které MSBuild používá k sestavení řešení. Můžete také určit, jak bude ladicí program sady Visual Studio spouštět vaše aplikace Docker Compose nastavením popisků souborů v konfiguračních souborech Docker Compose.

## <a name="how-to-set-the-msbuild-properties"></a>Jak nastavit vlastnosti MSBuild

Chcete-li nastavit hodnotu vlastnosti, upravte soubor projektu. U Docker Compose vlastností je tento soubor projektu souborem s příponou. dcproj, pokud není uvedeno jinak v tabulce v další části. Předpokládejme například, že chcete určit, že chcete spustit prohlížeč při spuštění ladění. `DockerLaunchAction` Vlastnost můžete nastavit v souboru projektu. dcproj následujícím způsobem.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Nastavení vlastnosti můžete přidat do existujícího `PropertyGroup` prvku, nebo pokud není jedna, vytvořte nový `PropertyGroup` prvek.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose vlastnosti MSBuild

V následující tabulce jsou uvedeny vlastnosti MSBuild dostupné pro Docker Compose projekty.

| Název vlastnosti | Umístění | Popis | Výchozí hodnota  |
|---------------|----------|-------------|----------------|
|DockerComposeBuildArguments|dcproj|Určuje další parametry, které se mají předat `docker-compose build` příkazu. Třeba `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Určuje další parametry, které se mají předat `docker-compose down` příkazu. Třeba `--timeout 500`.|-|  
|DockerComposeProjectPath|CSPROJ nebo VBPROJ|Relativní cesta k souboru dcproj (Docker-psací projekt). Tuto vlastnost nastavte při publikování projektu služby, aby bylo možné najít přidružená nastavení pro sestavení imagí uložená v souboru Docker-Compose. yml.|-|
|DockerComposeUpArguments|dcproj|Určuje další parametry, které se mají předat `docker-compose up` příkazu. Třeba `--timeout 500`.|-|
|DockerLaunchAction| dcproj | Určuje akci spuštění, která se má provést na F5 nebo CTRL + F5.  Povolené hodnoty jsou None, LaunchBrowser a LaunchWCFTestClient.|Žádné|
|DockerLaunchBrowser| dcproj | Označuje, zda se má spustit prohlížeč. Ignoruje se, pokud je zadaný DockerLaunchAction. | False |
|DockerServiceName| dcproj|Pokud jsou zadány DockerLaunchAction nebo DockerLaunchBrowser, pak DockerServiceName je název služby, která se má spustit.  Tato vlastnost slouží k určení, který z potenciálně mnoho projektů, na který může odkazovat soubor Docker-na sestavení, se spustí.|-|
|DockerServiceUrl| dcproj | Adresa URL, která se má použít při spuštění prohlížeče.  Platné náhradní tokeny jsou {ServiceIPAddress}, {ServicePort} a {schéma}.  Příklad: {schéma}://{ServiceIPAddress}: {ServicePort}|-|
|DockerTargetOS| dcproj | Cílový operační systém, který se používá při vytváření image Docker.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments a DockerComposeUpArguments jsou novinkou v aplikaci Visual Studio 2019 verze 16,3 Preview 3.

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
