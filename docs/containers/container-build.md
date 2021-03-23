---
title: Přehled sestavení a ladění nástrojů kontejnerů sady Visual Studio
author: ghogen
description: Přehled procesu sestavení a ladění nástrojů kontejneru
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 07ecc9a171cf6c0ca254ddbf284f116545ddd0f0
ms.sourcegitcommit: 20f546a0b13b56e7b0da21abab291d42a5ba5928
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2021
ms.locfileid: "104884080"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Jak Visual Studio vytváří kontejnerizované aplikace

Ať už vytváříte z integrovaného vývojového prostředí sady Visual Studio, nebo nastavíte sestavení příkazového řádku, musíte znát, jak Visual Studio používá souboru Dockerfile k sestavení vašich projektů.  Z důvodů výkonu aplikace Visual Studio dodržuje zvláštní proces pro kontejnerové aplikace. Porozumění způsobu sestavení projektů v aplikaci Visual Studio je obzvláště důležité při přizpůsobení procesu sestavení úpravou souboru Dockerfile.

Když aplikace Visual Studio vytvoří projekt, který nepoužívá kontejnery Docker, vyvolá nástroj MSBuild na místním počítači a vygeneruje výstupní soubory ve složce (obvykle) v `bin` místní složce řešení. Pro kontejnerový projekt ale proces sestavení vezme v úvahu pokyny souboru Dockerfile pro vytvoření kontejnerové aplikace. Souboru Dockerfile, který používá Visual Studio, je rozdělené do několika fází. Tento proces spoléhá na funkci *buildu s více fázemi* Docker.

## <a name="multistage-build"></a>Sestavení s více fázemi

Funkce buildu s více fázemi pomáhá zajistit efektivnější proces vytváření kontejnerů a zmenšuje kontejnery tím, že jim umožní obsahovat pouze bity, které vaše aplikace potřebuje v době běhu. Sestavení s více fázemi se používá pro projekty .NET Core, ne pro .NET Framework projekty.

Sestavení s více fázemi umožňuje vytváření imagí kontejnerů ve fázích, které vytvářejí mezilehlé image. Jako příklad zvažte typické souboru Dockerfile generované v rámci sady Visual Studio – první fáze `base` :

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Řádky v souboru Dockerfile začínají s imagí Debian z Microsoft Container Registry (mcr.microsoft.com) a vytvářejí mezilehlé image `base` , která zveřejňuje porty 80 a 443 a nastavuje pracovní adresář na `/app` .

Další fáze je `build` , která se zobrazí takto:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Můžete vidět, že `build` fáze začíná jinou původní bitovou kopií z registru ( `sdk` spíše než `aspnet` ), místo aby pokračovala od základny.  `sdk`Obrázek obsahuje všechny nástroje sestavení a z tohoto důvodu je to mnohem větší než Image ASPNET, která obsahuje pouze běhové komponenty. Důvod použití samostatné image se při pohledu na zbytek souboru Dockerfile bude jasný:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Poslední fáze se znovu spustí z `base` a obsahuje, kde `COPY --from=publish` zkopíruje publikovaný výstup do finální image. Tento proces umožňuje, aby poslední obrázek byl menší, protože nemusí zahrnovat všechny nástroje sestavení, které byly v `sdk` imagi.

## <a name="building-from-the-command-line"></a>Sestavování z příkazového řádku

Pokud chcete sestavit mimo sadu Visual Studio, můžete použít `docker build` nebo `MSBuild` k sestavení z příkazového řádku.

### <a name="docker-build"></a>docker build

Chcete-li vytvořit kontejnerové řešení z příkazového řádku, můžete obvykle použít příkaz `docker build <context>` pro každý projekt v řešení. Zadáte argument *kontextu sestavení* . *Kontext sestavení* pro souboru Dockerfile je složka v místním počítači, která se používá jako pracovní složka k vygenerování bitové kopie. Například složka, ze které kopírujete soubory při kopírování do kontejneru.  V projektech .NET Core použijte složku, která obsahuje soubor řešení (. sln).  Vyjádřeno jako relativní cesta, tento argument obvykle je ".." pro souboru Dockerfile ve složce projektu a soubor řešení v nadřazené složce.  Pro .NET Framework projekty je kontextem sestavení složka projektu, nikoli složka řešení.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Fázemi vytvořené pomocí sady Visual Studio pro projekty .NET Framework (a pro projekty .NET Core vytvořené ve verzích sady Visual Studio před aktualizací Visual Studio 2017 Update 4) nejsou fázemi s více fázemi.  Kroky v těchto fázemi nekompiluje váš kód.  Místo toho, když Visual Studio sestaví .NET Framework souboru Dockerfile, nejprve zkompiluje projekt pomocí nástroje MSBuild.  Po úspěšném sestavení Visual Studio sestaví souboru Dockerfile, který jednoduše zkopíruje výstup sestavení z MSBuild do výsledné image Docker.  Vzhledem k tomu, že kroky pro zkompilování kódu nejsou zahrnuty do souboru Dockerfile, nemůžete sestavit .NET Framework fázemi pomocí `docker build` z příkazového řádku. K sestavování těchto projektů byste měli použít MSBuild.

Pokud chcete vytvořit image pro jeden projekt kontejneru Docker, můžete použít MSBuild s `/t:ContainerBuild` možností příkazu. Například:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Při sestavování řešení z integrovaného vývojového prostředí (IDE) sady Visual Studio uvidíte výstup podobný tomu, co vidíte v okně **výstup** . Vždy použít `/p:Configuration=Release` , protože v případech, kdy aplikace Visual Studio používá optimalizaci sestavení s více fázemi, výsledky při sestavování konfigurace **ladění** nemusí být očekávaným způsobem. Viz [ladění](#debugging).

Pokud používáte projekt Docker Compose, použijte tento příkaz k sestavení imagí:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Zahřívání projektu

*Zahřívání projektu* odkazuje na řadu kroků, ke kterým dochází, když je vybrán profil Docker pro projekt (tj. když je načten projekt nebo je přidána podpora Docker) za účelem zlepšení výkonu následných spuštění (**F5** nebo **CTRL** + **F5**). Tato možnost se dá **nakonfigurovat v nabídce nástroje**  >  **Možnosti**  >  **kontejnerů**. Zde jsou úkoly, které běží na pozadí:

- Ověřte, že je nainstalovaný a spuštěný dokovací počítač.
- Ujistěte se, že je Docker Desktop nastavený na stejný operační systém jako projekt.
- Napravte obrázky v první fázi souboru Dockerfile ( `base` fáze ve většině fázemi).  
- Sestavte souboru Dockerfile a spusťte kontejner.

Zahřívání bude k dispozici pouze v **rychlém** režimu, takže v běžícím kontejneru bude k dispozici složka aplikace připojená ke svazku. To znamená, že jakékoli změny aplikace nebudou mít za následek zrušení platnosti kontejneru. Tím se zlepší výkon ladění významně a zkrátí čekací doba pro dlouhotrvající úlohy, jako je například přijímání velkých imagí.

## <a name="volume-mapping"></a>Mapování svazků

Pro ladění pro práci v kontejnerech používá Visual Studio mapování svazků pro mapování ladicího programu a složek NuGet z hostitelského počítače. Mapování svazků je popsané [v dokumentaci k](https://docs.docker.com/storage/volumes/)Docker. Tady jsou svazky, které jsou připojené do vašeho kontejneru:

|Svazek|Popis|
|-|-|
| **Vzdálený ladicí program** | Obsahuje bity potřebné ke spuštění ladicího programu v kontejneru v závislosti na typu projektu. To je vysvětleno podrobněji v části [ladění](#debugging) .|
| **Složka aplikace** | Obsahuje složku projektu, kde se nachází souboru Dockerfile.|
| **Zdrojová složka** | Obsahuje kontext sestavení, který je předán příkazům Docker.|
| **Složky balíčků NuGet** | Obsahuje balíčky NuGet a záložní složky, které se čtou ze souboru *obj \{ projektu. csproj. NuGet. g. props* v projektu. |

Pro webové aplikace ASP.NET Core můžou existovat dvě další složky pro certifikát SSL a tajné klíče uživatelů, které jsou podrobněji vysvětleny v další části.

## <a name="ssl-enabled-aspnet-core-apps"></a>ASP.NET Core aplikace s povoleným protokolem SSL

Nástroje kontejneru v aplikaci Visual Studio podporují ladění aplikace ASP.NET Core s povoleným protokolem SSL pomocí vývojového certifikátu stejným způsobem, jako byste očekávali, že bude pracovat bez kontejnerů. Aby k tomu mohlo dojít, Visual Studio přidá několik dalších kroků pro Export certifikátu a zpřístupní ho kontejneru. Zde je tok, který aplikace Visual Studio zpracuje při ladění v kontejneru:

1. Zajistí, aby byl místní vývojový certifikát přítomen a důvěryhodný na hostitelském počítači prostřednictvím `dev-certs` nástroje.
2. Exportuje certifikát do%APPDATA%\ASP.NET\Https se zabezpečeným heslem uloženým v úložišti tajných klíčů uživatelů pro tuto konkrétní aplikaci.
3. Volume-připojí následující adresáře:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core vyhledá certifikát, který odpovídá názvu sestavení ve složce *https* , což je důvod, proč je namapován na kontejner v této cestě. Cestu k certifikátu a heslo lze případně definovat pomocí proměnných prostředí (tj `ASPNETCORE_Kestrel__Certificates__Default__Path` `ASPNETCORE_Kestrel__Certificates__Default__Password` . a) nebo v souboru JSON uživatelských tajných klíčů, například:

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "c:\\app\\mycert.pfx",
        "Password": "strongpassword"
      }
    }
  }
}
```

Pokud vaše konfigurace podporuje kontejnery i sestavení bez kontejnerů, měli byste použít proměnné prostředí, protože cesty jsou specifické pro prostředí kontejneru.

Další informace o použití protokolu SSL s ASP.NET Core aplikacemi v kontejnerech najdete v tématu [hostování ASP.NET Core imagí pomocí Docker přes HTTPS](/aspnet/core/security/docker-https)).

## <a name="debugging"></a>Ladění

Při sestavování konfigurace **ladění** je k dispozici několik optimalizací, které aplikace Visual Studio provede s výkonem procesu sestavení pro kontejnerové projekty. Proces sestavení pro aplikace s možností vytvoření kontejnerů není jednoduchý, stejně jako v souladu s postupem popsaným v souboru Dockerfile. Sestavování v kontejneru je mnohem pomalejší než sestavování na místním počítači.  Takže když sestavíte v konfiguraci **ladění** , Visual Studio ve skutečnosti vytvoří vaše projekty na místním počítači a pak nasdílí výstupní složku do kontejneru pomocí připojení svazku. Sestavení s touto optimalizací povoleno se označuje jako sestavení *rychlého* režimu.

V **rychlém** režimu volání Visual studia `docker build` s argumentem, který instruuje Docker pro sestavení pouze `base` fáze.  Visual Studio zpracovává zbytek procesu bez ohledu na obsah souboru Dockerfile. Takže při úpravách souboru Dockerfile, jako je například přizpůsobení prostředí kontejneru nebo instalace dalších závislostí, byste měli do první fáze umístit své změny.  Nespustí se žádné vlastní kroky, které jsou umístěné ve `build` `publish` fázích souboru Dockerfile, nebo `final` .

Tato optimalizace výkonu nastane pouze při sestavení v konfiguraci **ladění** . V konfiguraci **vydání** se sestavení objeví v kontejneru, jak je uvedeno v souboru Dockerfile.

Pokud chcete zakázat optimalizaci výkonu a sestavení jako souboru Dockerfile, pak nastavte vlastnost **ContainerDevelopmentMode** na hodnotu **Regular** v souboru projektu následujícím způsobem:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Chcete-li obnovit optimalizaci výkonu, odeberte vlastnost ze souboru projektu.

 Při spuštění ladění (**F5**) se znovu použije dřív spuštěný kontejner, pokud je to možné. Pokud nechcete znovu použít předchozí kontejner, můžete použít příkazy pro opětovné **sestavení** nebo **Vyčištění** v aplikaci Visual Studio k vynucení použití nového kontejneru v aplikaci Visual Studio.

Proces spuštění ladicího programu závisí na typu projektu a operačního systému kontejneru:

|Scenario|Proces ladicího programu|
|-|-|
| **Aplikace .NET Core (kontejnery platformy Linux)**| Visual Studio stáhne `vsdbg` a namapuje ho do kontejneru, potom se volá pomocí vašeho programu a argumentů (tj. `dotnet webapp.dll` ) a pak se ladicí program připojí k procesu. |
| **Aplikace .NET Core (kontejnery Windows)**| Visual Studio používá `onecoremsvsmon` a mapuje ho do kontejneru, spouští ho jako vstupní bod a pak se k němu připojí Visual Studio a připojí se k vašemu programu. To se podobá tomu, jak byste normálně nastavili vzdálené ladění na jiném počítači nebo virtuálním počítači.|
| **Aplikace .NET Framework** | Visual Studio používá `msvsmon` a mapuje ho do kontejneru, spouští ho jako součást vstupního bodu, ve kterém se k němu může připojit Visual Studio, a připojuje se k vašemu programu.|

Informace o naleznete v `vsdbg.exe` tématu [Offroad debugginging of .NET Core on Linux and OSX from Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Vstupní bod kontejneru

Visual Studio používá vlastní vstupní bod kontejneru v závislosti na typu projektu a operačním systému kontejneru. Jedná se o různé kombinace:

|Typ kontejneru|Vstupní bod|
|-|-|
| **Linuxové kontejnery** | Vstupním bodem je `tail -f /dev/null` , což je nekonečné čekání na chod kontejneru. Když se aplikace spustí prostřednictvím ladicího programu, je to ladicí program, který zodpovídá za spuštění aplikace (tj `dotnet webapp.dll` .). Pokud se spustí bez ladění, spouští se nástroj a spustí se `docker exec -i {containerId} dotnet webapp.dll` aplikace.|
| **Kontejnery Windows**| Vstupní bod je podobný jako při `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` spuštění ladicího programu, takže naslouchá připojení. Totéž platí, že ladicí program spustí aplikaci a `docker exec` příkaz při spuštění bez ladění. U .NET Frameworkch webových aplikací se vstupní bod mírně liší, kde `ServiceMonitor` se přidá do příkazu.|

Vstupní bod kontejneru lze upravit pouze v projektech Docker – vytváření, nikoli v projektech s jedním kontejnerem.

## <a name="next-steps"></a>Další kroky

Přečtěte si další informace o tom, jak upravit sestavení nastavením dalších vlastností MSBuild v souborech projektu. Přečtěte si téma [vlastnosti MSBuild pro projekty kontejnerů](container-msbuild-properties.md).

## <a name="see-also"></a>Viz také

Nástroj [MSBuild](../msbuild/msbuild.md) 
 [Souboru Dockerfile ve Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile) 
 [Kontejnery platformy Linux ve Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
