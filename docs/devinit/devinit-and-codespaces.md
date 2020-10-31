---
title: Codespaces devinit a GitHub
description: Naučte se, jak přizpůsobit codespace pro Visual Studio pomocí devinit.
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
ms.openlocfilehash: a9731469f6725c0a4b9118c4e41235974a19c473
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134383"
---
# <a name="devinit-and-github-codespaces"></a>Codespaces devinit a GitHub

devinit je skvělý bezplatný [Codespaces](https://github.com/features/codespaces) a devinit se dá použít k získání codespace nastavení, takže přispěvatelé můžou hned sestavovat, spouštět a ladit.

Pro integraci s Codespaces GitHubu je `devinit` potřeba volat z `postCreateCommand` definovaného v `.devcontainer.json` souboru umístěném v kořenovém adresáři úložiště. Řetězce v `postCreateCommand` jsou spouštěny ve výchozím prostředí po naklonování úložiště v codespace. Další informace najdete `postCreateCommand` v [dokumentaci pro přizpůsobení](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)Codespaces GitHubu. Chcete-li přidat `devinit` příkaz, můžete přidat `devinit init` do, `postCreateCommand` jak je znázorněno v níže uvedených příkladech.

Můžete se také spouštět `devinit init -f <path to .devinit.json>` z integrovaného terminálu sady Visual Studio, jakmile se připojíte k vašemu codespace.

## <a name="examples"></a>Příklady

### <a name="with-a-devinitjson-file"></a>S .devinit.jsem v souboru
V tomto příkladu se _.devcontainer.js_ v souboru nachází v kořenovém adresáři úložiště vedle _.devinit.jsv_ souboru. Soubory mohou být také umístěny v adresáři _. devcontainer_ .

```json
{
  "postCreateCommand": "devinit init"
}
```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

### <a name="as-commands"></a>Jako příkazy
V tomto příkladu _.devcontainer.jsv_ souboru níže je umístěn v kořenovém adresáři úložiště a `devinit run` je volán programově pro spuštění nástroje.  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Z výzvy terminálu

Když aktuální pracovní adresář obsahuje _.devinit.jsv_ souboru.

```console
devinit init
```

Když je _.devinit.js_ v jiném adresáři.

```console
devinit init -f path/to/.devinit.json
```
