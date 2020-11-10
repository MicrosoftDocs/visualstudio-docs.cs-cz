---
title: Začínáme s devinit
description: Příručka Začínáme pro devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 1f66f691bd92c6cc9d315c58225b9345198fe96d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435764"
---
# <a name="getting-started-with-devinit"></a>Začínáme s devinit

devinit je nástroj, který můžete použít k tomu, aby kdokoli mohl získat kód a zvýšit produktivitu vašeho úložiště spuštěním jednoduchého příkazu. Pomocí devinit můžete definovat všechny závislosti celého systému, které vaše úložiště potřebuje, jako je SQL Server, Node.js, Docker nebo IIS. Devinit může vyvolat další nástroje a správce balíčků a nainstalovat tak, co vaše úložiště potřebuje. Tyto závislosti definujete v souboru JSON s názvem [.devinit.jsv](devinit-json.md) a pak další osoba, která má vaše úložiště používat, stačí ke spuštění [`devinit init`](devinit-commands.md#init) instalace všech těchto závislostí. Takže místo toho, aby se do nového úložiště připojila polovina každodenního provozu, se to může udělat během několika minut.

devinit není správce balíčků ani konfigurační nástroj pro virtuální počítače (VM) v systému a sám na sobě. Jedná se o Spouštěč úloh pro soubor manifestu s názvem [.devinit.jsv](devinit-json.md), který definuje závislosti v celém systému, které vaše aplikace potřebuje. Pro instalaci těchto závislostí devinit využívá nástroje, které už možná používáte, například [čokolády](https://chocolatey.org). Dostupné nástroje můžete zkontrolovat v [úplném seznamu](devinit-tool-list.md). Díky tomu, že pomocí těchto nástrojů místo distribuce softwaru přímo distribuujete software, vám devinit poskytuje možnost použití nástroje podle vašeho výběru a umožní vám používat stávající konfigurace, například soubor [packages.config](https://chocolatey.org/docs/commands-install#packagesconfig) pro čokolády.  

## <a name="step-1-get-devinit"></a>Krok 1: získání devinit

devinit je v současné době k dispozici pouze jako součást GitHubu Codespaces při použití sady Visual Studio a je přístupná z integrovaného terminálu v aplikaci Visual Studio. V budoucnu bude devinit k dispozici jako součást sady Visual Studio.

## <a name="step-2-define-your-environment"></a>Krok 2: definování prostředí

Nejdůležitějším krokem je definování vývojového prostředí v [.devinit.jsv souboru](devinit-json.md). Tento soubor bude používat devinit k vytvoření prostředí při spuštění `devinit init` .

V tomto kroku si představte pokyny, které byste měli někomu poskytnout, aby mohli začít pracovat s úložištěm projektu. Například musí mít nainstalován SQL? Konkrétní verze .NET Core? A tak dále. Pak u každé z těchto závislostí vyhledejte odpovídající nástroj devinit v [seznamu nástrojů](devinit-tool-list.md) a přidejte ho do `.devinit.json` souboru úložiště. Můžete si také prohlédnout výběr příkladů v [dokumentaci k ukázkám](sample-readme.md).

## <a name="step-3-enjoy"></a>Krok 3: užívejte!

Teď je potřeba, aby se po klonování vašeho úložiště dokončila i každá osoba `devinit init` .

```console
devinit init
```

Pokud používáte [GitHub Codespaces](https://github.com/features/codespaces), můžete nakonfigurovat, aby se `devinit init` spouštěla automaticky, když se zřídí codespace. Další informace najdete v [dokumentaci k devinit a GitHub Codespaces](devinit-and-codespaces.md).
