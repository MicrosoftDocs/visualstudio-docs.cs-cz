---
title: choco-install
description: devinit Tool Choco – instalace pro instalaci balíčků čokolády
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c1f5b1c587ea8d1d6335e19b2e7303cc12ad9783
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671656"
---
# <a name="choco-install"></a>choco-install

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

`choco-install`Nástroj lze použít k instalaci a aktualizaci [čokoládových](https://chocolatey.org/) balíčků.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj neprovede žádnou akci.

| Název                                             | Typ   | Vyžadováno  | Hodnota                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No        | Volitelná vlastnost komentářů Nepoužívá se.                                                                          |
| [**vstup**](#input)                              | řetězec | Yes       | Balíček, který se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .                                                 |
| [**additionalOptions**](#additional-options)     | řetězec | No        | Další možnosti, které se mají předat nástroji Podrobnosti najdete níže v části [Další možnosti](#additional-options) .       |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k zadání názvu balíčku, který má být nainstalován (například ' MongoDB ') nebo cesty ke konfiguračnímu souboru následujících formátů _packages.config_, _. nuspec_ a _. nupkg_. Hodnota `input` bude připojena k `choco install` příkazu (například `choco install mongodb` ) spolu s případnými argumenty, které jsou specifické v nástroji [`additionalOptions`](#additional-options) a integrovanými `choco` možnostmi (definované [níže](#built-in-options)). Balíčky jsou k dispozici v [galerii balíčků pro čokolády](https://chocolatey.org/packages). Při použití konfiguračního souboru můžete v této vlastnosti předat cestu k tomuto souboru `input` , například `"input":"packages.config"` .

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty jsou přímo Passthrough na argumenty používané [`choco install`](https://chocolatey.org/docs/commands-install) a jsou definovány v dokumentaci k čokoládě.

#### <a name="adding-new-feeds-to-chocolatey"></a>Přidání nových informačních kanálů k čokoládě
Pokud chcete přidat nový informační kanál k čokoládě, podobně jako `choco source add` příkaz, můžete `additionalOptions` k tomu předat. Příkladem [použití](#example-usage)je například přidání nového informačního kanálu. Pokud chcete přidat privátní kanál, doporučujeme spustit nástroj na příkazovém řádku, protože vyžaduje přihlašovací údaje. Například `devinit run -t choco-install -i {package} -s "{feed link}" -u {user} -p {password}` , kde,, `{package}` `{feed link}` `{user}` a `{password}` odkazují na konkrétní balíček, odkaz na informační kanál, uživatelské jméno a heslo. Další informace najdete v dokumentaci k čokoládě, na kterou se odkazuje výše. 

### <a name="built-in-options"></a>Předdefinované možnosti

`choco-install`Nástroj nastaví řadu `choco` argumentů příkazového řádku, aby bylo zajištěno, že `choco` může běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v [dokumentaci k čokoládě](https://chocolatey.org/docs/).

| Název                  | Description                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Ano**             | Potvrdit všechny výzvy – vybere kladnou odpověď místo výzvy. To `--accept-license.` |
| **--No-Progress**     | Nezobrazovat průběh – procento průběhu nebude zobrazeno.                                         |
| **--Skip-PowerShell** | Přeskočit PowerShell – chocolateyInstall.ps1 nebude spuštěná.                                              |

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `choco-install` nástroje je chyba, protože `input` vlastnost je povinná.

## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `choco-install` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-packages-listed-in-packagesconfig"></a>.devinit.js, které budou instalovat balíčky uvedené v packages.config:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-mongodb"></a>.devinit.js, které budou instalovat MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-mongodb"></a>.devinit.js, na které se nainstaluje konkrétní verze MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```

#### <a name="devinitjson-that-adds-a-new-feed-to-chocolatey"></a>.devinit.js, který přidá nový informační kanál k čokoládě:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-install",
            "input": "packages.config",
            "additionalOptions": "-s '{feed link}'"
        }
    ]
}
```