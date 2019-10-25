---
title: Psaní kódu jazyka JavaScript v aplikaci Visual Studio bez řešení nebo projektu
titleSuffix: ''
description: Visual Studio poskytuje podporu pro vytváření kódu bez závislosti na souboru projektu nebo souboru řešení.
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 288cb11d3e6ae3917f5fcc6ec9ed242549908576
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888644"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Vývoj kódu v jazyce JavaScript a TypeScript v aplikaci Visual Studio bez řešení nebo projektů

Počínaje sadou Visual Studio 2017 můžete [vyvíjet kód bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), což umožňuje otevřít složku kódu a hned začít pracovat s bohatou podporou editoru, jako je IntelliSense, hledání, refaktoring, ladění a další. Kromě těchto funkcí Node.js Tools for Visual Studio přidává podporu pro vytváření souborů TypeScriptu, správu balíčků npm a spouštění skriptů npm.

Chcete-li začít, vyberte **soubor** > **otevřete** > **složce** z panelu nástrojů. Průzkumník řešení zobrazí všechny soubory ve složce a můžete otevřít kterýkoli ze souborů, abyste mohli začít upravovat. Na pozadí aplikace Visual Studio indexuje soubory pro povolení funkcí NPM, Build a Debug.

> [!IMPORTANT]
> Mnohé z funkcí popsaných v tomto článku, včetně integrace npm, vyžadují Visual Studio 2017 verze 15,8 nebo novější.

## <a name="npm-integration"></a>integrace npm

Pokud složka, kterou otevřete, obsahuje soubor *Package. JSON* , můžete kliknout pravým tlačítkem na soubor *Package. JSON* a zobrazit kontextovou nabídku (místní nabídka) specifickou pro npm.

![NPM – nabídka v Průzkumník řešení](../javascript/media/solution-explorer-npm-ctx.png)

V místní nabídce můžete spravovat balíčky nainstalované nástrojem npm stejným způsobem jako při použití souboru projektu pro [správu balíčků npm](npm-package-management.md) .

Kromě toho tato nabídka umožňuje spouštět skripty definované v prvku `scripts` v *balíčku Package. JSON*. Tyto skripty budou používat verzi Node. js dostupnou v proměnné prostředí `PATH`. Skripty se spouštějí v novém okně. Toto je skvělý způsob, jak spustit skripty sestavení nebo spuštění.

## <a name="build-and-debug"></a>Sestavení a ladění

### <a name="packagejson"></a>Package. JSON
Pokud soubor *Package. JSON* ve složce určuje `main` element, příkaz **ladění** bude k dispozici v místní nabídce, která se zobrazí v *balíčku Package. JSON*.
Kliknutím se spustí *Node. exe* se zadaným skriptem jako jeho argument.

### <a name="javascript-files"></a>Soubory JavaScriptu
Soubory JavaScriptu můžete ladit tak, že kliknete pravým tlačítkem na soubor a vyberete **ladění** z místní nabídky. Tím se jako argument spustí *Node. exe* s tímto souborem JavaScriptu.

### <a name="typescript-files-and-tsconfigjson"></a>Soubory TypeScriptu a tsconfig. JSON
Pokud ve složce neexistuje *tsconfig. JSON* , můžete kliknout pravým tlačítkem na soubor TypeScript a zobrazit příkazy místní nabídky pro sestavení a ladění tohoto souboru. Když použijete tyto příkazy, sestavíte nebo ladíte pomocí nástroje *TSC. exe* s výchozími možnostmi. (Před laděním musíte soubor sestavit.)

> [!NOTE]
> Při sestavování kódu TypeScript používáme nejnovější verzi nainstalovanou v `C:\Program Files (x86)\Microsoft SDKs\TypeScript`.

Pokud se ve složce nachází soubor *tsconfig. JSON* , můžete kliknout pravým tlačítkem na soubor TypeScript a zobrazit příkaz nabídky pro ladění tohoto souboru TypeScript. Možnost se zobrazí pouze v případě, že v *tsconfig. JSON*není zadána žádná `outFile`. Je-li zadán `outFile`, můžete tento soubor ladit kliknutím pravým tlačítkem na *tsconfig. JSON* a výběrem správné možnosti. Soubor `tsconfig.json` také poskytuje možnost sestavení, která umožňuje zadat možnosti kompilátoru.

> [!NOTE]
> Další informace o *tsconfig. JSON* najdete na [stránce příručka tsconfig. JSON TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Testování částí
Můžete povolit integraci testů jednotek v aplikaci Visual Studio zadáním kořene testu ve vašem *balíčku. JSON*:

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Test Runner vytvoří výčet místně nainstalovaných balíčků, aby určil, který testovací rozhraní se má použít.
Pokud není rozpoznán žádný z podporovaných platforem, je Test Runner nastaven na výchozí hodnotu *ExportRunner*. Ostatní podporované architektury:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jednotek Jasmine ([Jasmine.GitHub.IO](https://jasmine.github.io/))
* Páska ([GitHub.com/substack/Tape](https://github.com/substack/tape))
* Jest ([jestjs.IO](https://jestjs.io/))

Po otevření Průzkumníka testů (zvolit **test** > **Windows** > **Průzkumník testů**), Visual Studio zjistí a zobrazí testy.

> [!NOTE]
> Test Runner bude vytvářet výčet pouze souborů JavaScriptu v kořenu testu, pokud je vaše aplikace napsána v TypeScript, je třeba nejprve vytvořit.
