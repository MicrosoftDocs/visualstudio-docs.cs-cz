---
title: Zápis kódu JavaScriptu v Sadě Visual Studio bez řešení nebo projektu
titleSuffix: ''
description: Visual Studio poskytuje podporu pro vytváření kódu bez závislosti na souboru projektu nebo souboru řešení
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
ms.openlocfilehash: ae8b6fd52cd2469cf7562a199b952d388b463089
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549935"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Vývoj kódu JavaScriptu a jazyka V auvisual u sady Visual Studio bez řešení nebo projektů

Počínaje Visual Studio 2017, můžete [vyvíjet kód bez projektů nebo řešení](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), který umožňuje otevřít složku kódu a okamžitě začít pracovat s podporou rich editor, jako je IntelliSense, vyhledávání, refaktoring, ladění a další. Kromě těchto funkcí přidává Nástrojy Node.js pro visual studio podporu pro vytváření souborů Typu TypeScript, správu balíčků npm a spouštění skriptů npm.

Chcete-li začít, vyberte na panelu nástrojů**položku Složka** **otevření** >  **souboru.** >  Průzkumník řešení zobrazí všechny soubory ve složce a můžete otevřít libovolný soubor a začít upravovat. Na pozadí Visual Studio indexuje soubory povolit npm, sestavení a ladění funkce.

> [!IMPORTANT]
> Mnoho funkcí popsaných v tomto článku, včetně integrace npm, vyžadují Visual Studio 2017 verze 15.8 nebo novější verze. Úloha vývoje aplikace Visual Studio **Node.js** musí být nainstalována.

## <a name="npm-integration"></a>npm integrace

Pokud složka, kterou otevřete, obsahuje soubor *package.json,* můžete klepnout pravým tlačítkem myši na *soubor package.json* a zobrazit místní nabídku (místní nabídku) specifickou pro npm.

![nabídka npm v Průzkumníku řešení](../javascript/media/solution-explorer-npm-ctx.png)

V místní nabídce můžete spravovat balíčky nainstalované npm stejným způsobem, jakým [spravujete balíčky npm](npm-package-management.md) při použití souboru projektu.

Kromě toho menu také umožňuje spouštět skripty definované v elementu `scripts` v *package.json*. Tyto skripty budou používat verzi souboru Node.js, která je k dispozici v `PATH` proměnné prostředí. Skripty jsou spuštěny v novém okně. To to je skvělý způsob, jak spustit sestavení nebo spustit skripty.

## <a name="build-and-debug"></a>Sestavení a ladění

### <a name="packagejson"></a>package.json
Pokud *soubor package.json* ve složce určuje `main` prvek, bude příkaz **Ladění** k dispozici v místní nabídce pravým tlačítkem myši pro soubor *package.json*.
Klepnutím na toto tlačítko spustíte *node.exe* se zadaným skriptem jako argumentem.

### <a name="javascript-files"></a>Soubory JavaScriptu
Soubory JavaScriptu můžete ladit klepnutím pravým tlačítkem myši na soubor a výběrem **možnosti Ladění** v místní nabídce. Tím spustí *node.exe* s tímto souborem JavaScript jako jeho argument.

### <a name="typescript-files-and-tsconfigjson"></a>Soubory typescriptu a tsconfig.json
Pokud ve složce není k dispozici žádný soubor *tsconfig.json,* můžete klepnout pravým tlačítkem myši na soubor jazyka TypeScript a zobrazit příkazy místní nabídky pro sestavení a ladění tohoto souboru. Při použití těchto příkazů, sestavení nebo ladění pomocí *tsc.exe* s výchozími možnostmi. (Před laděním je třeba soubor vytvořit.)

> [!NOTE]
> Při vytváření kódu TypeScript používáme nejnovější `C:\Program Files (x86)\Microsoft SDKs\TypeScript`verzi nainstalovanou v aplikaci .

Pokud je ve složce soubor *tsconfig.json,* můžete klepnutím pravým tlačítkem myši na soubor typu TypeScript zobrazit příkaz nabídky pro ladění tohoto souboru TypeScript. Tato možnost se zobrazí `outFile` pouze v případě, že v *souboru tsconfig.json*není zadánžádný . Pokud `outFile` je zadán soubor, můžete tento soubor ladit klepnutím pravým tlačítkem myši na *soubor tsconfig.json* a výběrem správné možnosti. Soubor `tsconfig.json` také poskytuje možnost sestavení, která vám umožní určit možnosti kompilátoru.

> [!NOTE]
> Další informace o *souboru tsconfig.json* naleznete na [stránce tsconfig.json TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Jednotkové testy
Integraci testování částí můžete povolit v sadě Visual Studio zadáním kořenového adresáře testu v *souboru package.json*:

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Testovací běžec vyjmenovává místně nainstalované balíčky k určení, které testovací rozhraní použít.
Pokud není rozpoznán žádný z podporovaných rámců, zkušební běžec výchozí *ExportRunner*. Dalšími podporovanými rámci jsou:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmín[(Jasmine.github.io](https://jasmine.github.io/))
* Páska ([github.com/substack/tape](https://github.com/substack/tape))
* Žert ([jestjs.io](https://jestjs.io/))

Po otevření Průzkumníka testů (zvolte **Testovat** > **Průzkumníka testů systému****Windows** > ) Visual Studio zjišťuje a zobrazuje testy.

> [!NOTE]
> Testovací běžec bude pouze výčet souborů JavaScript v kořenovém adresáři testu, pokud je vaše aplikace zapsána v TypeScriptu, musíte je nejprve vytvořit.
