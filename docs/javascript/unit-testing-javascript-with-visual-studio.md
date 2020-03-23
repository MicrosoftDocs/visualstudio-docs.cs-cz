---
title: Testování částí JavaScript a TypeScript
description: Visual Studio poskytuje podporu testování částí JavaScript a kód Jazyka pomocí Node.js Tools for Visual Studio
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 792c74a3b5da5ed6528fa3919a0c60625d1a38ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77071944"
---
# <a name="unit-testing-javascript-and-typescript-in-visual-studio"></a>Testování částí JavaScript a TypeScript v sadě Visual Studio

Nástroje Node.js pro visual studio umožňují psát a spouštět testy částí pomocí některých nejoblíbenějších rozhraní JavaScript bez nutnosti přepnutí do příkazového řádku.

Podporované rámce jsou:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jasmín[(Jasmine.github.io](https://jasmine.github.io/))
* Páska ([github.com/substack/tape](https://github.com/substack/tape))
* Žert ([jestjs.io](https://jestjs.io/))
* Export Runner (tento rámec je specifický pro Node.js Nástroje pro Visual Studio)

> [!WARNING]
> Problém v pásku aktuálně brání páskové testy spuštění. Pokud [pr #361](https://github.com/substack/tape/pull/361) je sloučena, problém by měl být vyřešen.

Pokud vaše oblíbené rozhraní není podporováno, najdete [v tématu Přidání podpory pro rozhraní testování částí](#addingFramework) pro informace o přidání podpory.

## <a name="write-unit-tests"></a>Zapsat testy částí

Před přidáním testování částí do projektu, ujistěte se, že rámec, který chcete použít, je nainstalován místně v projektu. To je snadné pomocí [instalačního okna balíčku npm](npm-package-management.md#npmInstallWindow).

Upřednostňovaným způsobem přidání testů částí do projektu je vytvoření složky *testů* v projektu a nastavení jako kořen testu ve vlastnostech projektu. Je také nutné vybrat testovací rámec, který chcete použít.

![Nastavení kořenového a testovacího rámce testu](../javascript/media/unit-test-project-properties.png)

Jednoduché prázdné testy můžete do projektu přidat pomocí dialogového okna **Přidat novou položku.** JavaScript i TypeScript jsou podporovány ve stejném projektu.

![Přidat nový test částí](../javascript/media/unit-test-add-new-item.png)

Pro testování částí Mocha použijte následující kód:

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

Pokud jste nenastavili možnosti testování částí ve vlastnostech projektu, musíte zajistit, aby vlastnost **Test Framework** v okně **Vlastnosti** byla nastavena na správnou testovací architekturu pro soubory testování částí. To se provádí automaticky šablonami testovacích souborů jednotky.

![Testovací rámec](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Možnosti testování částí budou mít přednost před nastavením pro jednotlivé soubory.

Po otevření Průzkumníka testů (zvolte **Testovat** > **Průzkumníka testů systému****Windows** > ) Visual Studio zjišťuje a zobrazuje testy. Pokud testy nejsou zobrazeny zpočátku, znovu sestavit projekt aktualizovat seznam.

![Průzkumník testů](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Nepoužívejte možnost `outdir` `outfile` nebo v *souboru tsconfig.json*, protože Průzkumník testů nebude moci najít testy částí v souborech typescriptu.

## <a name="run-tests"></a>Spouštění testů

Testy můžete spustit v sadě Visual Studio 2017 nebo z příkazového řádku.

### <a name="run-tests-in-visual-studio-2017"></a>Spuštění testů ve Visual Studiu 2017

Testy můžete spustit kliknutím na odkaz **Spustit vše** v Průzkumníku testů. Nebo můžete spustit testy výběrem jednoho nebo více testů nebo skupin, kliknutím pravým tlačítkem myši a výběrem **spustit vybrané testy** z místní nabídky. Testy spustit na pozadí a Průzkumník testů automaticky aktualizuje a zobrazí výsledky. Kromě toho můžete také ladit vybrané testy výběrem **ladění vybrané testy**.

> [!Warning]
> Ladění testů jednotek pomocí uzlu 8 + v současné době funguje pouze pro testovací soubory JavaScript, testovací soubory Typu Script se nezdaří zasáhnout zarážky. Jako řešení použijte `debugger` klíčové slovo.

> [!NOTE]
> V současné době nepodporujeme profilovací testy ani pokrytí kódu.

### <a name="run-tests-from-the-command-line"></a>Spuštění testů z příkazového řádku

Testy můžete spustit z [příkazového řádku pro vývojáře](/dotnet/framework/tools/developer-command-prompt-for-vs) pro Visual Studio 2017 pomocí následujícího příkazu:

```
vstest.console.exe <path to project file>\NodejsConsoleApp23.njsproj /TestAdapterPath:<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter
```

Tento příkaz zobrazuje výstup podobný následujícímu:

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
> Pokud se zobrazí chyba označující, že *vstest.console.exe* nelze najít, zkontrolujte, zda jste otevřeli příkazový řádek pro vývojáře a ne pravidelný příkazový řádek.

## <a name="add-support-for-a-unit-test-framework"></a><a name="addingFramework"></a>Přidání podpory pro rozhraní testování částí

Můžete přidat podporu pro další testovací architektury implementací logiky zjišťování a spuštění pomocí JavaScriptu. To provést přidáním složky s názvem testovací ho rozhraní pod:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Tato složka musí obsahovat soubor JavaScript se stejným názvem, který exportuje následující dvě funkce:

* `find_tests`
* `run_tests`

Dobrý příklad `find_tests` a `run_tests` implementace, naleznete v implementaci pro testování jednotky Mocha rámce v:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

Zjišťování dostupných testovacích rozhraní dochází při spuštění sady Visual Studio. Pokud je přidána architektura, zatímco Visual Studio běží, restartujte Visual Studio ke zjištění rozhraní. Při provádění změn v implementaci však není nutné restartovat počítač.

## <a name="unit-tests-in-other-project-types"></a>Jednotkové testy v jiných typech projektů
Nejste omezeni na psaní testů částí pouze v projektech Node.js. Když přidáte Vlastnosti TestFramework a TestRoot do libovolného projektu jazyka C# nebo Visual Basic, tyto testy budou uvedeny ve výčtu a můžete je spustit pomocí okna Průzkumníka testů.

Chcete-li to povolit, klepněte pravým tlačítkem myši na uzel projektu v Průzkumníku řešení, zvolte **Uvolnit Projekt**a pak zvolte **Upravit project**. Potom v souboru projektu přidejte následující dva prvky do skupiny vlastností.

> [!NOTE]
> Ujistěte se, že skupina vlastností, do které přidáváte prvky, nemá zadanou podmínku.
> To může způsobit neočekávané chování.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

Dále přidejte testy do zadanou testovací kořenové složky a budou k dispozici ke spuštění v okně Průzkumníka testů. Pokud se zpočátku nezobrazí, bude pravděpodobně nutné znovu vytvořit projekt.

### <a name="unit-test-net-core-and-net-standard"></a>Testování částí .NET Core a standard .NET
Kromě výše uvedených vlastností budete také muset nainstalovat balíček NuGet [Microsoft.JavaScript.UnitTest](https://www.nuget.org/packages/Microsoft.JavaScript.UnitTest/) a nastavit vlastnost:

```xml
<PropertyGroup>
    <GenerateProgramFile>false</GenerateProgramFile>
</PropertyGroup>
```

Některé testovací architektury mohou vyžadovat další balíčky npm pro detekci testů. Například žert vyžaduje balíček npm pro podporu žertu-editor. V případě potřeby zkontrolujte dokumentaci pro konkrétní rámec.
