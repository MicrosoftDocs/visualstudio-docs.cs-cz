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
ms.openlocfilehash: 62c31dcb72735304f7b28e7dfd817f6647187bc9
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022627"
---
# <a name="getting-started-with-devinit"></a>Začínáme s devinit

## <a name="step-1-get-devinit"></a>Krok 1: získání devinit

devinit je v současné době k dispozici pouze jako součást GitHubu Codespaces při použití sady Visual Studio a je přístupná z integrovaného terminálu v aplikaci Visual Studio. V budoucnu bude devinit k dispozici jako součást sady Visual Studio.

## <a name="step-2-define-your-environment"></a>Krok 2: definování prostředí

Nejdůležitějším krokem je definování prostředí pro vývojáře v [ _.devinit.js_ souboru](devinit-json.md). Tento soubor bude používat devinit k vytvoření prostředí při spuštění `devinit init` .

V tomto kroku si představte pokyny, které byste měli někomu poskytnout, aby mohli začít pracovat s úložištěm projektu. Například musí mít nainstalován SQL? Konkrétní verze .NET Core? atd. Pak u každé z těchto závislostí vyhledejte odpovídající nástroj devinit v [seznamu nástrojů](devinit-tool-list.md) a přidejte ho do _.devinit.jsúložiště v_ souboru.

## <a name="step-3-enjoy"></a>Krok 3: užívejte!

Teď je potřeba, aby se po klonování vašeho úložiště dokončila i každá osoba `devinit init` .

```console
> devinit init
```

Pokud používáte [GitHub Codespaces](https://github.com/features/codespaces), můžete nakonfigurovat, aby se `devinit init` spouštěla automaticky, když se zřídí codespace. Další informace najdete v [dokumentaci k devinit a GitHub Codespaces](devinit-and-codespaces.md).
