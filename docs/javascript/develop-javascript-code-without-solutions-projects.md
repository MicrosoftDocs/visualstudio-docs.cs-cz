---
title: Psaní kódu jazyka JavaScript v aplikaci Visual Studio bez řešení nebo projektu
titleSuffix: ''
description: Visual Studio poskytuje podporu pro vytváření kódu bez závislosti na souboru projektu nebo souboru řešení.
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 187ca5ea0d0232e0ca8b99165e77ee265b81e801
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285085"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Vývoj kódu v jazyce JavaScript a TypeScript v aplikaci Visual Studio bez řešení nebo projektů

Počínaje sadou Visual Studio 2017 můžete [vyvíjet kód bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), což umožňuje otevřít složku kódu a hned začít pracovat s bohatou podporou editoru, jako je IntelliSense, hledání, refaktoring, ladění a další. Kromě těchto funkcí nástroj Node.js Tools for Visual Studio přidává podporu pro vytváření souborů TypeScriptu, správu balíčků npm a spouštění skriptů npm.

Začněte tím, že na panelu nástrojů vyberete **soubor**  >  **otevřít**  >  **složku** . Průzkumník řešení zobrazí všechny soubory ve složce a můžete otevřít kterýkoli ze souborů, abyste mohli začít upravovat. Na pozadí aplikace Visual Studio indexuje soubory pro povolení funkcí NPM, Build a Debug.

> [!IMPORTANT]
> Mnohé z funkcí popsaných v tomto článku, včetně integrace npm, vyžadují Visual Studio 2017 verze 15,8 nebo novější. Je nutné nainstalovat úlohu vývoj sady Visual Studio **Node.js** .

## <a name="npm-integration"></a>integrace npm

Pokud složka, kterou otevřete, obsahuje *package.jsv* souboru, můžete kliknout pravým tlačítkem na *package.jsna* , aby se zobrazila kontextová nabídka (místní nabídka) specifická pro npm.

![NPM – nabídka v Průzkumník řešení](../javascript/media/solution-explorer-npm-ctx.png)

V místní nabídce můžete spravovat balíčky nainstalované nástrojem npm stejným způsobem jako při použití souboru projektu pro [správu balíčků npm](npm-package-management.md) .

Kromě toho nabídka také umožňuje spouštět skripty definované v `scripts` prvku *package.jsna*. Tyto skripty budou používat verzi Node.js, která je k dispozici v `PATH` proměnné prostředí. Skripty se spouštějí v novém okně. Toto je skvělý způsob, jak spustit skripty sestavení nebo spuštění.

## <a name="build-and-debug"></a>Sestavení a ladění

### <a name="packagejson"></a>package.json
Pokud *package.js* ve složce Určuje `main` prvek, příkaz **ladění** bude k dispozici v místní nabídce pravého tlačítka pro *package.jsna*.
Kliknutím se spustí *node.exe* se zadaným skriptem jako jeho argumentem.

### <a name="javascript-files"></a>Soubory JavaScriptu
Soubory JavaScriptu můžete ladit tak, že kliknete pravým tlačítkem na soubor a vyberete **ladění** z místní nabídky. Spustí se *node.exe* s tímto souborem JavaScriptu jako argumentem.

### <a name="typescript-files-and-tsconfigjson"></a>Soubory TypeScriptu a tsconfig.jsv
Pokud ve složce neexistuje žádná *tsconfig.js* , můžete kliknout pravým tlačítkem myši na soubor TypeScript a zobrazit příkazy místní nabídky pro sestavení a ladění tohoto souboru. Když použijete tyto příkazy, sestavíte nebo ladíte pomocí *tsc.exe* s výchozími možnostmi. (Před laděním musíte soubor sestavit.)

> [!NOTE]
> Při sestavování kódu TypeScript používáme nejnovější verzi nainstalovanou v `C:\Program Files (x86)\Microsoft SDKs\TypeScript` .

Pokud se ve složce nachází *tsconfig.js* souboru, můžete kliknout pravým tlačítkem na soubor TypeScript a zobrazit příkaz nabídky pro ladění tohoto souboru TypeScript. Možnost se zobrazí pouze v případě, že `outFile` v *tsconfig.js*není určena. Pokud `outFile` je zadaný, můžete tento soubor ladit tak, že kliknete pravým tlačítkem *tsconfig.jsna* a vyberete správnou možnost. `tsconfig.json`Soubor také poskytuje možnost sestavení, která umožňuje zadat možnosti kompilátoru.

> [!NOTE]
> Další informace o *tsconfig.jsnajdete na* [stráncetsconfig.jsna stránce příručka TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Testování částí
Můžete povolit integraci testu jednotek v aplikaci Visual Studio zadáním kořene testu v *package.jsv*:

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

Po otevření Průzkumníka testů (zvolit **test**  >  **Windows**  >  **Průzkumníka testů**systému Windows), Visual Studio zjistí a zobrazí testy.

> [!NOTE]
> Test Runner bude vytvářet výčet pouze souborů JavaScriptu v kořenu testu, pokud je vaše aplikace napsána v TypeScript, je třeba nejprve vytvořit.
