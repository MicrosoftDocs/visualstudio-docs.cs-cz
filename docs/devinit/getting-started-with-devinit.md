---
title: Začínáme s devinit
description: Příručka Začínáme pro devinit.
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
ms.openlocfilehash: 660bb5a2c3d235a347e478d55ae8176e87c5d626
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672479"
---
# <a name="getting-started-with-devinit"></a>Začínáme s devinit

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

devinit je nástroj, který můžete použít k tomu, aby kdokoli mohl získat kód a zvýšit produktivitu vašeho úložiště spuštěním jednoduchého příkazu. Pomocí devinit můžete definovat všechny závislosti celého systému, které vaše úložiště potřebuje, jako je SQL Server, Node.js, Docker nebo IIS. Devinit může vyvolat další nástroje a správce balíčků a nainstalovat tak, co vaše úložiště potřebuje. Tyto závislosti definujete v souboru JSON s názvem [.devinit.jsv](devinit-json.md) a pak další osoba, která má vaše úložiště používat, stačí ke spuštění [`devinit init`](devinit-commands.md#init) instalace všech těchto závislostí. Takže místo toho, aby se do nového úložiště připojila polovina každodenního provozu, se to může udělat během několika minut.

devinit není správce balíčků ani konfigurační nástroj pro virtuální počítače (VM) v systému a sám na sobě. Jedná se o Spouštěč úloh pro soubor manifestu s názvem [.devinit.jsv](devinit-json.md), který definuje závislosti v celém systému, které vaše aplikace potřebuje. Pro instalaci těchto závislostí devinit využívá nástroje, které už možná používáte, například [čokolády](https://chocolatey.org). Dostupné nástroje můžete zkontrolovat v [úplném seznamu](devinit-tool-list.md). Díky tomu, že pomocí těchto nástrojů místo distribuce softwaru přímo distribuujete software, vám devinit poskytuje možnost použití nástroje podle vašeho výběru a umožní vám používat stávající konfigurace, například soubor [packages.config](https://chocolatey.org/docs/commands-install#packagesconfig) pro čokolády.  

## <a name="step-1-get-devinit"></a>Krok 1: získání devinit

devinit je v současné době k dispozici pouze jako součást GitHubu Codespaces při použití sady Visual Studio a je přístupná z integrovaného terminálu v aplikaci Visual Studio. V budoucnu bude devinit k dispozici jako součást sady Visual Studio.

## <a name="step-2-define-your-environment"></a>Krok 2: definování prostředí

Nejdůležitějším krokem je definování vývojového prostředí v [.devinit.jsv souboru](devinit-json.md). Tento soubor bude používat devinit k vytvoření prostředí při spuštění `devinit init` .

V tomto kroku si představte pokyny, které byste měli někomu poskytnout, aby mohli začít pracovat s úložištěm projektu. Například musí mít nainstalován SQL? Konkrétní verze .NET Core? A tak dále. Pak u každé z těchto závislostí vyhledejte odpovídající nástroj devinit v [seznamu nástrojů](devinit-tool-list.md) a přidejte ho do `.devinit.json` souboru úložiště.

Můžete si také prohlédnout výběr příkladů v [dokumentaci k ukázkám](sample-readme.md)nebo si přečtěte [kurz](tutorial.md).

## <a name="step-3-enjoy"></a>Krok 3: užívejte!

Teď je potřeba, aby se po klonování vašeho úložiště dokončila i každá osoba `devinit init` .

```console
devinit init
```

Pokud používáte [GitHub Codespaces](https://github.com/features/codespaces), můžete nakonfigurovat, aby se `devinit init` spouštěla automaticky, když se zřídí codespace. Další informace najdete v [dokumentaci k devinit a GitHub Codespaces](devinit-and-codespaces.md).
