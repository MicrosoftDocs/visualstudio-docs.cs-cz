---
title: Automatizace instalace pomocí souboru odpovědí.
description: Zjistěte, jak vytvořit soubor odpovědi JSON, která pomáhá automatizovat instalaci sady Visual Studio
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30e7af50259a2087a0a380b1fe2d0c96c0d83f9a
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158772"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Definování nastavení v souboru odpovědí.

Správci, kteří si nasadí sady Visual Studio můžete určit soubor odpovědí s použitím `--in` parametr, jako v následujícím příkladu:

```cmd
vs_enterprise.exe --in customInstall.json
```

Soubory odpovědí jsou [JSON](http://json-schema.org/) soubory, jejichž obsah zrcadlí argumenty příkazového řádku.  Obecně platí, že pokud parametr příkazového řádku nepřijímá žádné argumenty (například `--quiet`, `--passive`atd), hodnota v souboru odpovědí musí být true nebo false.  Pokud má argument (například `--installPath <dir>`), hodnota v souboru odpovědí by měl být řetězec.  Pokud má argument a může být více než jednou v příkazovém řádku (například `--add <id>`), měla by být pole řetězců.

Parametry, které jsou určeny na příkazový řádek přepsání nastavení ze souboru odpovědí s výjimkou při parametry trvat více vstupů (například `--add`). Pokud máte více vstupů, vstupy zadané na příkazovém řádku jsou sloučeny s nastavení ze souboru odpovědí.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Nastavuje se výchozí konfigurace pro sadu Visual Studio

Pokud jste vytvořili mezipaměť rozložení sítě se `--layout`, počáteční `response.json` soubor se vytvoří v rozložení. Pokud vytvoříte částečné rozložení, tento soubor odpovědí obsahuje úlohy a jazyky, které byly součástí rozložení.  Spuštění instalačního programu z tohoto rozložení automaticky používá tento soubor response.json vybere úlohy a komponenty, které jsou součástí rozložení.  Uživatelé mohou stále zaškrtněte nebo zrušte všechny úlohy v nastavení uživatelského rozhraní před instalací sady Visual Studio.

Správci, kteří vytvářejí rozložení můžete upravit `response.json` souboru v rozložení a výchozí nastavení, které jejich uživatelům zobrazit při instalaci sady Visual Studio z rozložení ovládacího prvku.  Například, pokud správce chce, aby se určité úlohy a komponenty, které jsou ve výchozím nastavení nainstalované, mohou nakonfigurovat `response.json` souboru je přidat.

Při spuštění instalačního programu sady Visual Studio ze složky rozložení, ho _automaticky_ používá soubor odpovědí ve složce rozložení.  Není nutné použít `--in` možnost.

Můžete aktualizovat `response.json` soubor, který je vytvořen ve složce aplikace offline rozložení pro definování výchozí nastavení pro uživatele, kteří si nainstalují z tohoto rozložení.

> [!WARNING]
> Je velmi důležité ponechat existující vlastnosti, která byla definována při vytváření rozložení.

Základní `response.json` soubor v rozložení by měl vypadat podobně jako v následujícím příkladu, s tím rozdílem, že by měl obsahovat hodnotu pro produkt a kanál, který chcete nainstalovat:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

Při vytvoření nebo aktualizaci rozložení, je také vytvoří soubor response.template.json.  Tento soubor obsahuje všechny úlohy, komponenty a jazyků, které lze použít.  Tento soubor je k dispozici jako šablona pro co může být součástí vlastní instalace.  Správci mohou používat tento soubor jako výchozí bod pro vlastní odpovědi souboru.  Odeberte ID pro takové věci, které nechcete k instalaci a uložit v souboru odpovědí.  Neupravujte soubor response.template.json nebo vaše změny budou ztraceny, jakmile dojde k aktualizaci rozložení.

## <a name="example-layout-response-file-content"></a>Obsah souboru odezvy příklad rozložení

Následující příklad nainstaluje Visual Studio Enterprise s šest běžné úlohy a komponenty a jazyky angličtinu a francouzštinu uživatelského rozhraní. V tomto příkladu můžete použít jako šablonu; Stačí změňte úlohy a komponenty na ty, které chcete nainstalovat:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [ID pracovního vytížení a komponenta Visual Studio 2017](workload-and-component-ids.md)
