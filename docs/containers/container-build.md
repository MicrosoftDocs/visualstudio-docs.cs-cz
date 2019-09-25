---
title: Přehled sestavení kontejnerových nástrojů sady Visual Studio
author: ghogen
description: Přehled procesu sestavení nástrojů kontejneru
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: edc4674e2468124ecb46b25a1411043ed4b66a2a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253120"
---
# <a name="building-containerized-apps-using-visual-studio-or-the-command-line"></a>Sestavování kontejnerových aplikací pomocí sady Visual Studio nebo příkazového řádku

Ať už vytváříte z integrovaného vývojového prostředí sady Visual Studio, nebo nastavíte sestavení příkazového řádku, musíte znát, jak sestavení sady Visual Studio používá souboru Dockerfile k sestavení vašich projektů.  Z důvodů výkonu aplikace Visual Studio dodržuje zvláštní proces pro kontejnerové aplikace. Porozumění způsobu sestavení projektů v aplikaci Visual Studio je obzvláště důležité při přizpůsobení procesu sestavení úpravou souboru Dockerfile.

Když aplikace Visual Studio vytvoří projekt, který nepoužívá kontejnery Docker, vyvolá nástroj MSBuild na místním počítači a vygeneruje výstupní soubory ve složce (obvykle `bin`) v místní složce řešení. Pro kontejnerový projekt ale proces sestavení vezme v úvahu pokyny souboru Dockerfile pro vytvoření kontejnerové aplikace. Souboru Dockerfile, který používá Visual Studio, je rozdělené do několika fází. Tento proces spoléhá na funkci *buildu s více fázemi* Docker.

## <a name="multistage-build"></a>Sestavení s více fázemi

Funkce buildu s více fázemi pomáhá zajistit efektivnější proces vytváření kontejnerů a zmenšuje kontejnery tím, že jim umožní obsahovat pouze bity, které vaše aplikace potřebuje v době běhu. Sestavení s více fázemi se používá pro projekty .NET Core, ne pro .NET Framework projekty.

Sestavení s více fázemi umožňuje vytváření imagí kontejnerů ve fázích, které vytvářejí mezilehlé image. Jako příklad zvažte typické souboru Dockerfile generované v rámci sady Visual Studio – první fáze `base`:

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Řádky v souboru Dockerfile začínají s imagí Nanoserver z Microsoft Container Registry (MCR.Microsoft.com) a vytvářejí mezilehlé image `base` , která zveřejňuje porty 80 a 443 a nastavuje pracovní adresář na. `/app`

Další fáze je `build`, která se zobrazí takto:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Můžete vidět, že `build` fáze začíná jinou původní bitovou kopií z registru (`sdk` spíše než `aspnet`), místo aby pokračovala od základny.  `sdk` Obrázek obsahuje všechny nástroje sestavení a z tohoto důvodu je to mnohem větší než Image ASPNET, která obsahuje pouze běhové komponenty. Důvod použití samostatné image se při pohledu na zbytek souboru Dockerfile bude jasný:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Poslední fáze se znovu spustí z `base`a `COPY --from=publish` obsahuje, kde zkopíruje publikovaný výstup do finální image. Tento proces umožňuje, aby poslední obrázek byl menší, protože nemusí zahrnovat všechny nástroje sestavení, které byly v `sdk` imagi.

## <a name="faster-builds-for-the-debug-configuration"></a>Rychlejší sestavení pro konfiguraci ladění

K dispozici je několik optimalizací, které aplikace Visual Studio provede s výkonem procesu sestavení pro kontejnerové projekty. Při spuštění ladění (F5) se znovu použije dříve sestavená bitová kopie, pokud je to možné. Pokud nechcete znovu použít předchozí kontejner, můžete použít příkazy pro opětovné **sestavení** nebo **Vyčištění** v aplikaci Visual Studio k vynucení použití nového kontejneru v aplikaci Visual Studio.

Pro zlepšení výkonu také proces sestavení pro aplikace s možností vytváření kontejnerů není jednoduchý, stejně jako v souladu s postupem popsaným v souboru Dockerfile. Sestavování v kontejneru je mnohem pomalejší než sestavování na místním počítači.  Takže když sestavíte v konfiguraci **ladění** , Visual Studio ve skutečnosti vytvoří vaše projekty na místním počítači a pak nasdílí výstupní složku do kontejneru pomocí připojení svazku. Sestavení s touto optimalizací povoleno se označuje jako sestavení *rychlého* režimu.

V **rychlém** režimu volání `docker build` Visual studia s argumentem, který instruuje Docker `base` pro sestavení pouze fáze.  Visual Studio zpracovává zbytek procesu bez ohledu na obsah souboru Dockerfile. Takže při úpravách souboru Dockerfile, jako je například přizpůsobení prostředí kontejneru nebo instalace dalších závislostí, byste měli do první fáze umístit své změny.  Nespustí se žádné vlastní kroky `build`, které jsou umístěné ve fázích souboru Dockerfile, `publish`nebo `final` .

Tato optimalizace výkonu nastane pouze při sestavení v konfiguraci **ladění** . V konfiguraci **vydání** se sestavení objeví v kontejneru, jak je uvedeno v souboru Dockerfile.

Pokud chcete zakázat optimalizaci výkonu a sestavení jako souboru Dockerfile, pak nastavte vlastnost **ContainerDevelopmentMode** na hodnotu **Regular** v souboru projektu následujícím způsobem:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Chcete-li obnovit optimalizaci výkonu, odeberte vlastnost ze souboru projektu.

## <a name="building-from-the-command-line"></a>Sestavování z příkazového řádku

Můžete použít `docker build` nebo `MSBuild` k sestavení z příkazového řádku.

### <a name="docker-build"></a>sestavení Docker

Chcete-li vytvořit kontejnerové řešení z příkazového řádku, můžete obvykle použít příkaz `docker build <context>` pro každý projekt v řešení. Zadáte argument *kontextu sestavení* . *Kontext sestavení* pro souboru Dockerfile je složka v místním počítači, která se používá jako pracovní složka k vygenerování bitové kopie. Například složka, ze které kopírujete soubory při kopírování do kontejneru.  V projektech .NET Core použijte složku, která obsahuje soubor řešení (. sln).  Vyjádřeno jako relativní cesta, tento argument obvykle je ".." pro souboru Dockerfile ve složce projektu a soubor řešení v nadřazené složce.  Pro .NET Framework projekty je kontextem sestavení složka projektu, nikoli složka řešení.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Fázemi vytvořené pomocí sady Visual Studio pro projekty .NET Framework (a pro projekty .NET Core vytvořené ve verzích sady Visual Studio před aktualizací Visual Studio 2017 Update 4) nejsou fázemi s více fázemi.  Kroky v těchto fázemi nekompiluje váš kód.  Místo toho, když Visual Studio sestaví .NET Framework souboru Dockerfile, nejprve zkompiluje projekt pomocí nástroje MSBuild.  Po úspěšném sestavení Visual Studio sestaví souboru Dockerfile, který jednoduše zkopíruje výstup sestavení z MSBuild do výsledné image Docker.  Vzhledem k tomu, že kroky pro zkompilování kódu nejsou zahrnuty do souboru Dockerfile, nemůžete sestavit `docker build` .NET Framework fázemi pomocí z příkazového řádku. K sestavování těchto projektů byste měli použít MSBuild.

Pokud chcete vytvořit image pro jeden projekt kontejneru Docker, můžete použít MSBuild s `/t:ContainerBuild` možností příkazu. Příklad:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Při sestavování řešení z integrovaného vývojového prostředí (IDE) sady Visual Studio uvidíte výstup podobný tomu, co vidíte v okně **výstup** . Vždy použít `/p:Configuration=Release`, protože v případech, kdy aplikace Visual Studio používá optimalizaci sestavení s více fázemi, výsledky při sestavování konfigurace **ladění** nemusí být očekávaným způsobem.

Pokud používáte projekt Docker Compose, použijte příkaz k sestavení imagí:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="next-steps"></a>Další kroky

Přečtěte si další informace o tom, jak upravit sestavení nastavením dalších vlastností MSBuild v souborech projektu. Přečtěte si téma [vlastnosti MSBuild pro projekty kontejnerů](container-msbuild-properties.md).

## <a name="see-also"></a>Viz také:

[MSBuild](../msbuild/msbuild.md)[](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
[souboru Dockerfile na kontejnerech systému Windows Linux ve Windows](/virtualization/windowscontainers/deploy-containers/linux-containers) 

