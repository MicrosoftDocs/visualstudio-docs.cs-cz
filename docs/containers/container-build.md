---
title: Přehled sestavení a ladění nástrojů kontejneru sady Visual Studio
author: ghogen
description: Přehled procesu sestavení a ladění nástrojů kontejneru
ms.author: ghogen
ms.date: 11/20/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: d91dd01879ac3bb62b981109463f6762046382ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027264"
---
# <a name="how-visual-studio-builds-containerized-apps"></a>Jak Visual Studio vytváří kontejnerizované aplikace

Ať už vytváříte z ide Visual Studio nebo nastavujete sestavení příkazového řádku, potřebujete vědět, jak Visual Studio používá soubor Dockerfile k vytváření projektů.  Z důvodů výkonu Visual Studio sleduje speciální proces pro kontejnerizované aplikace. Pochopení toho, jak Visual Studio vytváří vaše projekty, je obzvláště důležité při přizpůsobení procesu sestavení úpravou souboru Dockerfile.

Když Visual Studio vytvoří projekt, který nepoužívá kontejnery Dockeru, vyvolá MSBuild v místním počítači a `bin`generuje výstupní soubory ve složce (obvykle) ve složce místního řešení. Pro kontejnerizovaný projekt však proces sestavení bere v úvahu pokyny Dockerfile pro vytváření kontejnerizované aplikace. Soubor Dockerfile, který používá Visual Studio je rozdělena do více fází. Tento proces závisí na *vícestupňové* funkci sestavení Dockeru.

## <a name="multistage-build"></a>Vícestupňové sestavení

Funkce vícestupňového sestavení pomáhá zefektivnit proces vytváření kontejnerů a zmenšuje kontejnery tím, že jim umožňuje obsahovat pouze bity, které vaše aplikace potřebuje za běhu. Vícestupňové sestavení se používá pro projekty .NET Core, nikoli pro projekty rozhraní .NET Framework.

Vícestupňové sestavení umožňuje vytváření iobrazek kontejneru ve fázích, které vytvářejí mezilehlé bitové kopie. Jako příklad zvažte typický soubor Dockerfile generovaný visual `base`studio - první fáze je :

```
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443
```

Řádky v Souboru Dockerfile začínají obrazem Debianu z Microsoft Container `base` Registry (mcr.microsoft.com) a vytvoří se mezilehlý `/app`obraz, který zpřístupní porty 80 a 443 a nastaví pracovní adresář na .

Další etapa `build`je , která se zobrazí takto:

```
FROM mcr.microsoft.com/dotnet/core/sdk:2.2-stretch AS build
WORKDIR /src
COPY ["WebApplication43/WebApplication43.csproj", "WebApplication43/"]
RUN dotnet restore "WebApplication43/WebApplication43.csproj"
COPY . .
WORKDIR "/src/WebApplication43"
RUN dotnet build "WebApplication43.csproj" -c Release -o /app
```

Můžete vidět, `build` že fáze začíná z jinépůvodní`sdk` bitové `aspnet`kopie z registru ( spíše než ), spíše než pokračovat od základny.  Obraz `sdk` má všechny nástroje sestavení a z tohoto důvodu je mnohem větší než bitová kopie aspnet, která obsahuje pouze součásti runtime. Důvod pro použití samostatného obrázku se vyjasní, když se podíváte na zbytek Dockerfile:

```
FROM build AS publish
RUN dotnet publish "WebApplication43.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication43.dll"]
```

Závěrečná fáze začíná `base`znovu od `COPY --from=publish` , a obsahuje zkopírovat publikovaný výstup do konečného obrazu. Tento proces umožňuje, aby konečný obrázek byl mnohem menší, protože nemusí obsahovat všechny nástroje `sdk` sestavení, které byly v obraze.

## <a name="building-from-the-command-line"></a>Budova z příkazového řádku

Pokud chcete vytvořit mimo Visual Studio, `docker build` můžete `MSBuild` použít nebo sestavit z příkazového řádku.

### <a name="docker-build"></a>docker build

Chcete-li vytvořit kontejnerizované řešení z příkazového řádku, můžete obvykle použít příkaz `docker build <context>` pro každý projekt v řešení. Zadáte kontext *sestavení* argument. *Kontext sestavení* pro soubor Dockerfile je složka v místním počítači, která se používá jako pracovní složka pro generování bitové kopie. Například je to složka, ze které kopírujete soubory při kopírování do kontejneru.  V projektech .NET Core použijte složku, která obsahuje soubor řešení (.sln).  Vyjádřeno jako relativní cesta, tento argument je obvykle ".." pro soubor Dockerfile ve složce projektu a soubor řešení v nadřazené složce.  U projektů rozhraní .NET Framework je kontext sestavení složka projektu, nikoli složka řešení.

```cmd
docker build -f Dockerfile ..
```

### <a name="msbuild"></a>MSBuild

Dockerfiles vytvořené Visual Studio pro projekty rozhraní .NET Framework (a pro projekty .NET Core vytvořené pomocí verzí sady Visual Studio před Visual Studio 2017 Update 4) nejsou vícestupňové Dockerfiles.  Kroky v těchto Dockerfiles nekompilují váš kód.  Místo toho při Visual Studio vytvoří soubor .NET Framework Dockerfile, nejprve zkompiluje váš projekt pomocí MSBuild.  Když se to podaří, Visual Studio pak vytvoří Dockerfile, který jednoduše zkopíruje výstup sestavení z MSBuild do výsledné image Dockeru.  Vzhledem k tomu, že kroky ke kompilaci kódu nejsou zahrnuty v souboru Dockerfile, nelze vytvořit soubory .NET Framework Dockerfiles pomocí `docker build` z příkazového řádku. Měli byste použít MSBuild k vytvoření těchto projektů.

Chcete-li vytvořit image pro projekt kontejneru jednoho `/t:ContainerBuild` dockeru, můžete použít MSBuild s možností příkazu. Například:

```cmd
MSBuild MyProject.csproj /t:ContainerBuild /p:Configuration=Release
```

Zobrazí se výstup podobný tomu, co vidíte v okně **Výstup** při vytváření řešení z IDE Visual Studio. Vždy `/p:Configuration=Release`používejte , protože v případech, kdy Visual Studio používá optimalizace vícestupňového sestavení, výsledky při vytváření konfigurace **ladění** nemusí být podle očekávání. Viz [Ladění](#debugging).

Pokud používáte projekt Docker Compose, použijte tento příkaz k vytvoření bitových kopií:

```cmd
msbuild /p:SolutionPath=<solution-name>.sln /p:Configuration=Release docker-compose.dcproj
```

## <a name="project-warmup"></a>Zahřívání projektu

*Zahřívání projektu* odkazuje na řadu kroků, ke kterým dojde, když je pro projekt vybrán profil Dockeru (to znamená, když je projekt načten nebo je přidána podpora Dockeru) za účelem zlepšení výkonu následných spuštění **(F5** nebo **Ctrl**+**F5**). To je konfigurovatelné v části **Nástroje** > **Možnosti** > **Kontejner Tools Tools Tools**. Zde jsou úkoly, které běží na pozadí:

- Zkontrolujte, zda je dockerová plocha nainstalovaná a spuštěná.
- Ujistěte se, že Docker Desktop je nastaven na stejný operační systém jako projekt.
- Vytáhněte obrázky v první fázi Dockerfile `base` (fáze ve většině Dockerfiles).  
- Vytvořte Dockerfile a spusťte kontejner.

Zahřívání se stane pouze v **režimu rychlé,** takže spuštěný kontejner bude mít namontovat složky aplikace. To znamená, že žádné změny v aplikaci nezruší platnost kontejneru. To proto výrazně zlepšuje výkon ladění a zkracovaní čekací doba pro dlouho běžící úlohy, jako je například vytahování velkých bitových kopií.

## <a name="volume-mapping"></a>Mapování svazků

Pro ladění pracovat v kontejnerech, Visual Studio používá mapování svazku mapovat ladicí program a NuGet složky z hostitelského počítače. Mapování svazků je popsáno v dokumentaci [Dockeru zde](https://docs.docker.com/storage/volumes/). Zde jsou svazky, které jsou namontovány v kontejneru:

|||
|-|-|
| **Vzdálený ladicí program** | Obsahuje bity potřebné ke spuštění ladicího programu v kontejneru v závislosti na typu projektu. To je vysvětleno ve více |podrobnosti v části [Ladění.](#debugging)
| **Složka aplikace** | Obsahuje složku projektu, kde je umístěn Dockerfile.|
| **Zdrojová složka** | Obsahuje kontext sestavení, který je předán příkazům Dockeru.|
| **Složky balíčků NuGet** | Obsahuje balíčky NuGet a záložní složky, které se čtou ze souboru *\{obj project}.csproj.nuget.g.props* v projektu. |

Pro ASP.NET základní webové aplikace mohou existovat dvě další složky pro certifikát SSL a tajné klíče uživatelů, což je podrobněji vysvětleno v další části.

## <a name="ssl-enabled-aspnet-core-apps"></a>Základní aplikace s podporou ASP.NET ssl

Nástroje kontejnerů v sadě Visual Studio podporují ladění základní aplikace s podporou ssl ASP.NET s dev certifikátem, stejným způsobem, jakým byste očekávali, že bude fungovat bez kontejnerů. Aby k tomu došlo, Visual Studio přidá několik dalších kroků k exportu certifikátu a zpřístupnit jej do kontejneru. Tady je tok, který visual studio zpracovává pro vás při ladění v kontejneru:

1. Zajišťuje, že certifikát místního vývoje je přítomen `dev-certs` a důvěryhodný v hostitelském počítači prostřednictvím nástroje.
2. Exportuje certifikát do %APPDATA%\ASP.NET\Https se zabezpečeným heslem uloženým v úložišti uživatelských tajných klíčů pro tuto konkrétní aplikaci.
3. Svazek připojí následující adresáře:

   - *%APPDATA%\Microsoft\UserSecrets*
   - *%APPDATA%\ASP.NET\Https*

ASP.NET Core hledá certifikát, který odpovídá názvu sestavení ve složce *Https,* což je důvod, proč je mapován na kontejner v této cestě. Cestu k certifikátu a heslo lze alternativně definovat `ASPNETCORE_Kestrel__Certificates__Default__Path` pomocí `ASPNETCORE_Kestrel__Certificates__Default__Password`proměnných prostředí (tj. a ) nebo v souboru json uživatelských tajných kódů, například:

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

Pokud vaše konfigurace podporuje kontejnerizované i nekontejnerizované sestavení, měli byste použít proměnné prostředí, protože cesty jsou specifické pro prostředí kontejneru.

Další informace o používání protokolu SSL s aplikacemi ASP.NET Core v kontejnerech najdete v [tématu Hostování ASP.NET image jádra s Dockerem přes HTTPS](/aspnet/core/security/docker-https)).

## <a name="debugging"></a>ladění

Při vytváření konfigurace **ladění** existuje několik optimalizací, které Visual Studio provádí, které pomáhají s výkonem procesu sestavení pro kontejnerizované projekty. Proces sestavení pro kontejnerizované aplikace není tak jednoduché, jak jednoduše postupujte podle kroků popsaných v Dockerfile. Stavba v kontejneru je mnohem pomalejší než stavba na místním stroji.  Takže při vytváření konfigurace **ladění** Visual Studio ve skutečnosti vytvoří vaše projekty v místním počítači a potom sdílí výstupní složku do kontejneru pomocí připojení svazku. Sestavení s touto povolenou optimalizací se nazývá sestavení *rychlého* režimu.

V **Fast** rychlém režimu `docker build` Visual Studio volá s argumentem, který říká Docker sestavit pouze `base` fázi.  Visual Studio zpracovává zbytek procesu bez ohledu na obsah Dockerfile. Takže při úpravě souboru Dockerfile, jako je například přizpůsobit prostředí kontejneru nebo nainstalovat další závislosti, měli byste umístit změny v první fázi.  Žádné vlastní kroky umístěné v `build`Dockerfile `publish` `final` , , nebo fáze nebudou provedeny.

K této optimalizaci výkonu dochází pouze při sestavení v konfiguraci **ladění.** V konfiguraci **verze** sestavení dochází v kontejneru, jak je uvedeno v Dockerfile.

Pokud chcete zakázat optimalizaci výkonu a sestavení podle určuje Dockerfile, nastavte **ContainerDevelopmentMode** vlastnost **Regular** v souboru projektu takto:

```xml
<PropertyGroup>
   <ContainerDevelopmentMode>Regular</ContainerDevelopmentMode>
</PropertyGroup>
```

Chcete-li obnovit optimalizaci výkonu, odeberte vlastnost ze souboru projektu.

 Při spuštění ladění (**F5**), dříve spuštěnkontejner je znovu použít, pokud je to možné. Pokud nechcete znovu použít předchozí kontejner, můžete použít **příkazy Znovu sestavit** nebo **Vyčistit** v sadě Visual Studio a vynutit Visual Studio použít nový kontejner.

Proces spuštění ladicího programu závisí na typu operačního systému projektu a kontejneru:

|||
|-|-|
| **Aplikace .NET Core (linuxové kontejnery)**| Visual Studio `vsdbg` stáhne a mapuje do kontejneru, pak se zavolá s `dotnet webapp.dll`programem a argumenty (to znamená), a pak ladicí program připojí k procesu. |
| **Aplikace .NET Core (kontejnery Windows)**| Visual Studio `onecoremsvsmon` používá a mapuje do kontejneru, spustí jej jako vstupní bod a potom Visual Studio připojí k němu a připojí k programu. To je podobné, jak byste normálně nastavit vzdálené ladění v jiném počítači nebo virtuálním počítači.|
| **Aplikace rozhraní .NET Framework** | Visual Studio `msvsmon` používá a mapuje do kontejneru, spustí jej jako součást vstupního bodu, kde visual studio můžete připojit k němu a připojí k programu.|

Informace o `vsdbg.exe`tématu naleznete [v tématu Offroad ladění .NET Core na Linuxu a OSX z Visual Studia](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio).

## <a name="container-entry-point"></a>Vstupní bod kontejneru

Visual Studio používá vlastní vstupní bod kontejneru v závislosti na typu projektu a operačního systému kontejneru, zde jsou různé kombinace:

|||
|-|-|
| **Linuxové kontejnery** | Vstupní bod `tail -f /dev/null`je , což je nekonečné čekání, aby kontejner spuštěn. Když je aplikace spuštěna prostřednictvím ladicího programu, je ladicí program, `dotnet webapp.dll`který je zodpovědný za spuštění aplikace (to znamená). Pokud je spuštěnbez ladění, nástroj spustí `docker exec -i {containerId} dotnet webapp.dll` aplikaci.|
| **Kontejnery Windows**| Vstupní bod je `C:\remote_debugger\x64\msvsmon.exe /noauth /anyuser /silent /nostatus` něco jako který běží ladicí program, takže naslouchá připojení. Totéž platí, že ladicí program `docker exec` spustí aplikaci a příkaz při spuštění bez ladění. Pro webové aplikace rozhraní .NET Framework se `ServiceMonitor` vstupní bod mírně liší, kde je přidán do příkazu.|

Vstupní bod kontejneru lze upravit pouze v projektech docker-compose, nikoli v projektech s jedním kontejnerem.

## <a name="next-steps"></a>Další kroky

Zjistěte, jak dále přizpůsobit sestavení nastavením dalších vlastností MSBuild v souborech projektu. Viz [Vlastnosti MSBuild pro kontejnerové projekty](container-msbuild-properties.md).

## <a name="see-also"></a>Viz také

[MSBuild](../msbuild/msbuild.md)
[Dockerfile v](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
kontejnerech Windows[Linux u Windows ve Windows](/virtualization/windowscontainers/deploy-containers/linux-containers)
