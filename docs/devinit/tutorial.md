---
title: Kurz
description: Kurz pro devinit.
ms.date: 11/18/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 5fc53a534b592b4f6a4799100ce16b1d45049457
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671796"
---
# <a name="tutorial"></a>Kurz

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

V tomto kurzu se podíváme na nastavení [úložiště eShopOnWeb](https://github.com/andysterland/eShopOnWeb) s využitím Devinit a Codespaces. V tomto kurzu se předpokládá, že devinit je již k dispozici, jak je popsáno na [stránce Začínáme](getting-started-with-devinit.md).

## <a name="step-1-determining-setup-steps"></a>Krok 1: určení kroků instalace

Jak je uvedeno na [stránce Začínáme](getting-started-with-devinit.md), prvním krokem je vždy určit závislosti a instalační kroky projektu. To se bude lišit v závislosti na konkrétním projektu, ale existuje několik otázek, které je třeba vzít v úvahu:

- Jaké běhové moduly a sady SDK závisí na tom, jak váš projekt funguje?
- Vyžaduje váš projekt jakékoli balíčky (například z čokolády)?
- Vyžaduje proces instalace všechny akce (například spuštění skriptu)?
- Má váš projekt implicitní závislosti na cokoli, co je nainstalováno společně se systémem Visual Studio?
  - Pokud ano, je vhodné je zahrnout i do instalace devinit. Tímto způsobem se můžete vyhnout propojení s instalací sady Visual Studio.

Jedním z nejlepších způsobů, jak tyto informace zjistit, je prozkoumat postup ručního nastavení, který v současnosti máte k dispozici pro vaše úložiště. V případě eShopOnWeb je potřeba zvládnout několik věcí:

- Instalace nejnovější verze .NET Core SDK
- Instalace nejnovější verze rozhraní příkazového řádku nástroje .NET Entity Framework Core
- Instalace SQL Server 2019 Express
- Použití rozhraní příkazového řádku .NET Entity Framework k aktualizaci místní databáze na nejnovější migraci

V dalším kroku se podíváme, jak to udělat v kontextu devinit.

## <a name="step-2-the-devinitjson"></a>Krok 2: .devinit.jsv

Nejdřív budeme chtít vytvořit [.devinit.jsna soubor](devinit-json.md) a umístit ho do kořenového adresáře našeho úložiště. Tento soubor bude obsahovat řadu kroků, které budou provedeny později jako součást `devinit init` příkazu. Pokud chcete zjistit, co by mělo být součástí `.devinit.json` souboru, můžeme si seznam kroků instalace a porovnat se seznamem [nástrojů pro devinit](devinit-tool-list.md). Pojďme to udělat s kroky pro instalaci výše.

| Krok                                                              | Může to devinit zvládnout pro nás?                                                                        |
| :---------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------  |
| Nainstalovat nejnovější .NET Core SDK                                      | **Ano**! [ `require-dotnetcoresdk` Nástroj](tool-require-dotnetcoresdk.md) můžeme použít                  |
| Nainstalovat rozhraní příkazového řádku nástroje .NET Entity Framework Core                      | **Ano**! [ `dotnet-toolinstall` Nástroj](tool-dotnet-toolinstall.md) můžeme použít                        |
| Instalace SQL Server 2019 Express                                   | **Ano**! [ `choco-install` Nástroj](tool-choco-install.md) můžeme použít                                  |
| Aktualizace místní databáze pomocí Entity Framework .NET                 | **Ne**, ale přesto to provedeme kombinováním devinit se skriptem!                               |

Teď, když jsme to udělali, můžeme začít se základními `.devinit.json` . Zahrneme odkaz na [ `.devinit.json` schéma](https://json.schemastore.org/devinit.schema-2.0)a prázdný `run` oddíl:

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": []
}
```

Teď přidáme některé nástroje!

Nejprve přidáme [`require-dotnetcoresdk`](tool-require-dotnetcoresdk.md) . V dokumentaci k tomuto nástroji můžeme vidět, že výchozím chováním je instalace nejnovější verze sady SDK. To je přesně to, co chceme, a Pojďme ho přidat do naší `.devinit.json` :

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

Za druhé přidáme [`dotnet-toolinstall`](tool-dotnet-toolinstall.md) k instalaci `dotnet-ef` nástroje globálně. V dokumentaci vidíte, že můžeme použít `input` pole k zadání názvu nástroje a `additionalOptions` pole pro určení globálního rozsahu:

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    }
  ]
}
```

Nakonec přidáme [`choco-install`](tool-choco-install.md) k instalaci `sql-server-express` balíčku.

```json
{
  "run": [
    {
      "comments": "Install the latest version of the .NET Core SDK.",
      "tool": "require-dotnetcoresdk"
    },
    {
      "comments": "Install latest version of the .NET Entity Framework Core Tools CLI.",
      "tool": "dotnet-toolinstall",
      "input": "dotnet-ef",
      "additionalOptions": "--global"
    },
    {
      "comments": "Install SQL Server 2019 Express",
      "tool": "choco-install",
      "input": "sql-server-express"
    }
  ]
}
```

Teď, když `.devinit.json` je naše část hotová, můžeme pracovat na instalačním skriptu, který bude postarat o spuštění devinit a aktualizaci místní databáze.

## <a name="step-3-the-setup-script"></a>Krok 3: skript pro instalaci

Abychom mohli zpracovávat spuštěné devinit a aktualizovat místní databázi, vytvoříme skript, který provede potřebné příkazy. Pojďme vytvořit prázdný skript PowerShellu v našem kořenovém adresáři úložiště s názvem `PostCloneSetup.ps1` . Nejprve přidáme volání do `devinit init` :

```powershell
devinit init
```

Po spuštění spustí `devinit init` všechny nástroje definované v `run` části našeho `.devinit.json` .

Nakonec chceme vyvolat `dotnet ef database update` aktualizaci místní databáze:

```powershell
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

Po dokončení našeho skriptu instalace musíme přidat `.devcontainer.json` soubor, který se spustí během instalace codespace.

## <a name="step-4-the-devcontainerjson"></a>Krok 4: .devcontainer.jsv

Abychom zajistili, že se náš instalační skript spustí během vytváření našeho codespace, použijeme `.devcontainer.json` soubor. Podobně jako u ostatních souborů by měl být umístěn v kořenovém adresáři úložiště.

V `.devcontainer.json` souboru musíme jenom volat náš instalační skript jako součást `postCreateCommand` . Tato akce bude provedena v rámci procesu vytváření codespace:

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```

A to je vše!

## <a name="step-5-trying-it-out"></a>Krok 5: pokus o vyzkoušení

Teď, když jsou uvedené kroky pro instalaci, Pojďme si to vyzkoušet v Live codespace pomocí [reálného úložiště](https://github.com/andysterland/eShopOnWeb).

Nejprve vytvoříme codespace pomocí sady Visual Studio:

:::image type="content" source="media/eshoponweb-github-codespaces-prompt.png" alt-text="Vytvoření codespace":::

Po zahájení vytváření codespace můžeme sledovat průběh našeho procesu instalace v nástroji `C:\.vsonline\.vsoshared\vmTerminal.dat` :

:::image type="content" source="media/eshoponweb-watching-progress.png" alt-text="Sledování průběhu instalace":::

Až to bude hotové, spusťte aplikaci pomocí nástroje a ujistěte se, `Web.csproj` že vše funguje správně:

:::image type="content" source="media/eshoponweb-csproj.png" alt-text="Spuštění projektu":::

Jakmile aplikace sestaví a začne, můžeme se podívat na náš webový prohlížeč:

:::image type="content" source="media/eshoponweb-live.png" alt-text="Zobrazení webu":::

Proto náš proces nastavení správně pracoval a teď jsme připraveni na vývoj v projektu eShopOnWeb!
