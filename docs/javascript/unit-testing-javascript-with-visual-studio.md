---
title: Testování částí JavaScript a TypeScript
description: Visual Studio poskytuje podporu testování částí JavaScriptu a kódu TypeScript pomocí nástrojů Node.js pro Visual Studio.
ms.date: 07/06/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 04ef9834fdc66256b601ecdcf156e4d290447ce3
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171315"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Testování částí JavaScriptu a TypeScript v aplikaci Visual Studio

Nástroje Node.js pro Visual Studio umožňují psát a spouštět testy jednotek pomocí některých z oblíbených rozhraní JavaScript, aniž by bylo nutné přepnout na příkazový řádek.

Podporované architektury:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jednotek Jasmine ([Jasmine.GitHub.IO](https://jasmine.github.io/))
* Páska ([GitHub.com/substack/Tape](https://github.com/substack/tape))
* Jest ([jestjs.IO](https://jestjs.io/))
* Exportovat Runner (Toto rozhraní je specifické pro Node.js nástroje pro Visual Studio)

Pokud vaše oblíbené rozhraní není podporováno, přečtěte si téma [Přidání podpory pro testovací prostředí jednotky](#addingFramework) , kde najdete informace o přidání podpory.

## <a name="write-unit-tests"></a>Zápis testů jednotek

Než do svého projektu přidáte testy jednotek, ujistěte se, že je v projektu nainstalováno rozhraní, které plánujete použít. To se dá snadno udělat pomocí [okna instalace balíčku npm](npm-package-management.md#npmInstallWindow).

Upřednostňovaným způsobem, jak přidat testy jednotek do projektu, je vytvoření složky *testů* v projektu a nastavení, které jako kořen testu ve vlastnostech projektu. Také je nutné vybrat testovací rozhraní, které chcete použít.

![Nastavit testovací kořen a testovací rozhraní](../javascript/media/unit-test-project-properties.png)

Do projektu můžete přidat jednoduché prázdné testy pomocí dialogového okna **Přidat novou položku** . Jazyk JavaScript i TypeScript jsou podporovány ve stejném projektu.

![Přidat nový test jednotek](../javascript/media/unit-test-add-new-item.png)

Pro test jednotky Mocha použijte následující kód:

```javascript
var assert = require('assert');

describe('Test Suite 1', function() {
    it('Test 1', function() {
        assert.ok(true, "This shouldn't fail");
    })

    it('Test 2', function() {
        assert.ok(1 === 1, "This shouldn't fail");
        assert.ok(false, "This should fail");
    })
})
```

Pokud jste nenastavili možnosti testu jednotek ve vlastnostech projektu, je nutné zajistit, aby vlastnost **testovacího rozhraní** v okně **vlastnosti** byla nastavena na správné testovací rozhraní pro soubory testů jednotek. To se provádí automaticky pomocí šablon souborů testu jednotek.

![Testovací rozhraní](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Možnosti testu jednotek budou mít přednost před nastaveními pro jednotlivé soubory.

Po otevření Průzkumníka testů (zvolit **test**  >    >  **Průzkumníka testů** systému Windows), Visual Studio zjistí a zobrazí testy. Pokud testy nejsou zpočátku zobrazeny, pak znovu sestavte projekt, aby se seznam aktualizoval.

![Průzkumník testů](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> V případě TypeScript Nepoužívejte `outdir` `outfile` možnost nebo v *tsconfig.jsna*, protože Průzkumník testů nebude moci nalézt testy jednotek.

## <a name="run-tests"></a>Spouštění testů

Můžete spouštět testy v aplikaci Visual Studio nebo z příkazového řádku.

### <a name="run-tests-in-visual-studio"></a>Spuštění testů v aplikaci Visual Studio

::: moniker range=">=vs-2019"
Testy můžete spustit kliknutím na odkaz **Spustit vše** v Průzkumníku testů. Nebo můžete spustit testy tak, že vyberete jeden nebo více testů nebo skupin, kliknete pravým tlačítkem myši a vyberete **Spustit** z místní nabídky. Testy běží na pozadí a Průzkumník testů automaticky aktualizuje a zobrazí výsledky. Kromě toho můžete také ladit vybrané testy kliknutím pravým tlačítkem a výběrem možnosti **ladit**.
::: moniker-end
::: moniker range="vs-2017"
Testy můžete spustit kliknutím na odkaz **Spustit vše** v Průzkumníku testů. Nebo můžete spustit testy tak, že vyberete jeden nebo více testů nebo skupin, kliknete pravým tlačítkem myši a vyberete možnost **Spustit vybrané testy** z místní nabídky. Testy běží na pozadí a Průzkumník testů automaticky aktualizuje a zobrazí výsledky. Kromě toho můžete také ladit vybrané testy výběrem možnosti **ladit vybrané testy**.
::: moniker-end

V případě TypeScript jsou testy jednotek spouštěny proti vygenerovanému kódu JavaScriptu.

> [!NOTE]
> Ve většině scénářů TypeScriptu můžete ladit test jednotek nastavením zarážky v kódu TypeScript, kliknutím pravým tlačítkem myši na test v Průzkumníku testů a výběrem možnosti **ladit**. Ve složitějších scénářích, například ve scénářích používajících zdrojové mapy, můžete mít potíže se zarážkami v kódu TypeScript. Jako alternativní řešení zkuste použít `debugger` klíčové slovo.

> [!NOTE]
> V současné době nepodporujeme testy profilování nebo pokrytí kódu.

### <a name="run-tests-from-the-command-line"></a>Spuštění testů z příkazového řádku

Testy můžete spustit z [Developer Command Prompt pro Visual Studio](../ide/reference/command-prompt-powershell.md) pomocí následujícího příkazu:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Tento příkaz zobrazí výstup podobný následujícímu:

```
Microsoft (R) Test Execution Command Line Tool Version 15.5.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
Processing: NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 1::mocha
  Creating TestCase:NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js::Test Suite 1 Test 2::mocha
Processing finished for framework of Mocha
Passed   Test Suite 1 Test 1
Standard Output Messages:
 Using default Mocha settings
 1..2
 ok 1 Test Suite 1 Test 1

Failed   Test Suite 1 Test 2
Standard Output Messages:
 not ok 1 Test Suite 1 Test 2
   AssertionError [ERR_ASSERTION]: This should fail
       at Context.<anonymous> (NodejsConsoleApp23\NodejsConsoleApp23\UnitTest1.js:10:16)

Total tests: 2. Passed: 1. Failed: 1. Skipped: 0.
Test Run Failed.
Test execution time: 1.5731 Seconds
```

> [!NOTE]
> Pokud se zobrazí chyba s oznámením, že *vstest.console.exe* nejde najít, ujistěte se, že jste otevřeli Developer Command Prompt a ne běžný příkazový řádek.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Přidání podpory pro systém testů jednotek

Můžete přidat podporu pro další testovací architektury implementací logiky zjišťování a spouštění pomocí JavaScriptu. To provedete tak, že přidáte složku s názvem testovacího rozhraní pod:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Tato složka musí obsahovat soubor JavaScriptu se stejným názvem, který vyexportuje tyto dvě funkce:

* `find_tests`
* `run_tests`

Dobrý příklad `find_tests` a `run_tests` implementace naleznete v tématu implementace pro rozhraní Mocha pro testování částí v:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Zjišťování dostupných testovacích rozhraní probíhá při spuštění sady Visual Studio. Pokud se při spuštění sady Visual Studio přidá rozhraní, restartujte Visual Studio, aby se zjistilo rozhraní. Při provádění změn v implementaci ale nemusíte nic restartovat.

## <a name="unit-tests-in-other-project-types"></a>Testování částí v jiných typech projektů

Nejste omezeni na psaní testů jednotek pouze v projektech Node.js. Když přidáte vlastnosti TestFramework a TestRoot do jakéhokoli projektu C# nebo Visual Basic, tyto testy budou vyčísleny a lze je spustit pomocí okna Průzkumník testů.

Pokud to chcete povolit, klikněte pravým tlačítkem myši na uzel projektu v Průzkumník řešení, zvolte **Uvolnit projekt** a pak zvolte **upravit projekt**. Poté v souboru projektu přidejte následující dva prvky do skupiny vlastností.

> [!IMPORTANT]
> Ujistěte se, že skupina vlastností, na kterou přidáváte prvky, nemá zadanou podmínku.
> To může způsobit neočekávané chování.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Dále přidejte testy do kořenové složky testu, kterou jste zadali, a budou k dispozici pro spuštění v okně Průzkumník testů. Pokud se nezobrazují, může být nutné projekt znovu sestavit.

### <a name="unit-test-net-core-and-net-standard"></a>Test jednotek .NET Core a .NET Standard

Kromě výše uvedených vlastností také budete muset nainstalovat balíček NuGet [Microsoft. JavaScript. UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) a nastavit vlastnost:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Některé testovací architektury mohou vyžadovat další balíčky npm pro detekci testů. Například jest vyžaduje balíček npm podpory jest-Editor. V případě potřeby si přečtěte dokumentaci pro konkrétní rozhraní.
