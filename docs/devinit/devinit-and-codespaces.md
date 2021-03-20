---
title: Codespaces devinit a GitHub
description: Naučte se, jak přizpůsobit codespace pro Visual Studio pomocí devinit.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c98c00e0b62d3a2a755790b07621d717abcb41c1
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672219"
---
# <a name="devinit-and-github-codespaces"></a>Codespaces devinit a GitHub

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

devinit je skvělý doplněk k [GitHubu Codespaces](https://github.com/features/codespaces) a devinit se dá použít k získání codespace nastavení, takže přispěvatelé můžou hned sestavovat, spouštět a ladit.

> [!IMPORTANT]
> Před integrací devinit s vaším codespace musíte nejdřív zkontrolovat, že máte `.devinit.json` soubor, který definuje vaše závislosti. Další informace o tom, jak vytvořit `.devinit.json` , najdete v [dokumentaci Začínáme](getting-started-with-devinit.md).

V rámci Codespace GitHubu je vaše aplikace sestavená a spuštěná v cloudu. V cloudu znamená, že vaše aplikace nemá přístup k místním prostředkům na vašich počítačích. Patří mezi ně nástroje nebo programy, které jste nainstalovali místně. Pokud vaše aplikace potřebuje nainstalovat nebo nakonfigurovat systémové závislosti, je nutné ji provést na všech codespace. Nejjednodušší způsob, jak toho dosáhnout, je použít `.devinit.json` soubor.

Aby se zajistilo, že se vytvoří codespace se závislostmi, které vaše aplikace potřebuje, `devinit` musí se spustit při vytvoření codespace. To lze provést voláním `devinit init` z `postCreateCommand` definovaného v `.devcontainer.json` souboru umístěném v kořenovém adresáři úložiště. Řetězce v `postCreateCommand` jsou spouštěny ve výchozím prostředí po naklonování úložiště v codespace. Další informace najdete `postCreateCommand` v [dokumentaci pro přizpůsobení](https://docs.github.com/github/developing-online-with-codespaces/configuring-codespaces-for-your-project)Codespaces GitHubu. Chcete-li přidat `devinit` příkaz, můžete přidat `devinit init` do, `postCreateCommand` jak je znázorněno v níže uvedených příkladech.

Můžete se také spouštět `devinit init -f <path to .devinit.json>` z integrovaného terminálu sady Visual Studio, jakmile se připojíte k vašemu codespace.

## <a name="examples"></a>Příklady

V obou příkladech níže se `.devinit.json` nachází v kořenovém adresáři úložiště společně `.devcontainer.json` .

### <a name="with-a-devcontainerjson-file"></a>S .devcontainer.jsem v souboru

V tomto příkladu `.devcontainer.json` je soubor umístěný níže v kořenu úložiště společně se `.devinit.json` souborem. Soubory mohou být také umístěny v `.devcontainer` adresáři.

```json
{
  "postCreateCommand": "devinit init"
}
```

Pokud `.devinit.json` je v jiném adresáři, může být použit příznak-f.

```json
{
  "postCreateCommand": "devinit init -f path\\to\\.devinit.json"
}

```

```json
{
  "postCreateCommand": ["<some other command>", "devinit init"]
}
```

Další příklady použití devinit najdete v naší [dokumentaci](sample-all-tool.md) a na GitHubu v [příkladu .NET Core](https://github.com/microsoft/devinit-example-dotnet-core) a v [Node.js ukázkových](https://github.com/microsoft/devinit-example-nodejs) úložištích.

### <a name="as-commands"></a>Jako příkazy

V tomto příkladu `.devcontainer.json` je soubor níže umístěn v kořenu úložiště a `devinit run` je volán přímo z příkazového řádku pro spuštění jednotlivého nástroje.  

```json
{
  "postCreateCommand": ["devinit run –t require-dotnetcoresdk"]
}
```

### <a name="from-a-terminal-prompt"></a>Z výzvy terminálu

Když aktuální pracovní adresář obsahuje `.devinit.json` soubor.

```console
devinit init
```

Když `.devinit.json` je v jiném adresáři.

```console
devinit init -f path/to/.devinit.json
```
