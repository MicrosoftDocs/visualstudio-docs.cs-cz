---
title: Testování jednotek v Node.js
description: Visual Studio poskytuje podporu testování kódu jazyka JavaScript pomocí Node.js Tools for Visual Studio
ms.custom: ''
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 071f64c4239441d3c3fd2c111d1b912175e23316
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766541"
---
# <a name="unit-testing-in-nodejs"></a>Testování jednotek v Node.js

Node.js Tools For Visual Studio umožňují psání a spouštění testování částí pomocí některé další oblíbené architektury JavaScriptu bez nutnosti přepínat do příkazového řádku.

Podporované architektury jsou:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Pásky ([github.com/substack/tape](https://github.com/substack/tape))
* Export Runner (toto rozhraní je specifická pro Node.js Tools for Visual Studio)

> [!WARNING]
> Problém v pásky aktuálně zabraňuje pásku testy spuštění. Pokud [žádosti o přijetí změn #361](https://github.com/substack/tape/pull/361) se sloučí, by měl být problém vyřešen.

Pokud vaše oblíbená architektura není podporovaná, najdete v článku [přidání podpory pro rozhraní testování částí](#addingFramework) informace o přidání podpory.

## <a name="write-unit-tests"></a>Zápis testů jednotek

Před přidáním do projektu testování částí, ujistěte se, že je rozhraní, které plánujete použít místně nainstalovaný ve vašem projektu. Je to snadné dosáhnout pomocí [okno instalace balíčku npm](npm-package-management.md#npmInstallWindow).

Preferovaný způsob, jak přidat do projektu testování částí je tak, že vytvoříte *testy* složky v projektu a nastavení, které jako testovací kořenové ve vlastnostech projektu. Musíte také vybrat, kterou chcete použít rozhraní pro testování.

![Nastavte testovací kořenové a testovací rozhraní](../javascript/media/unit-test-project-properties.png)

Jednoduché prázdné testů můžete přidat do projektu pomocí **přidat novou položku** dialogové okno. JavaScript a TypeScript jsou podporovány ve stejném projektu.

![Přidat nový test jednotek](../javascript/media/unit-test-add-new-item.png)

Pro test jednotek Moka použijte následující kód:

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

Pokud jste nenastavili jednotky možnosti testování ve vlastnostech projektu, musíte zajistit **Test Framework** vlastnost **vlastnosti** okno bude nastaveno na správné testovací rozhraní pro soubory testu jednotky. To se provádí automaticky šablony soubor testu jednotek.

![Rozhraní pro testování](../javascript/media/UnitTestsFrameworkMocha.png)

> [!Note]
> Možnosti testování částí převezme předvoleb nastavení pro jednotlivé soubory.

Po otevření Průzkumníka testů (zvolte **testovací** > **Windows** > **Průzkumník testů**), Visual Studio zjistí a zobrazí testy. Pokud testy nejsou zobrazeny původně, pak znovu sestavte projekt a aktualizujte seznam.

![Průzkumník testů](../javascript/media/UnitTestsDiscoveryMocha.png)

> [!NOTE]
> Nepoužívejte `outdir` nebo `outfile` možnost *tsconfig.json*, protože Průzkumník testů nebude moci najít testování částí v souborech TypeScript.

## <a name="run-tests"></a>Spouštění testů

Testy můžete spustit v sadě Visual Studio 2017 nebo z příkazového řádku.

### <a name="run-tests-in-visual-studio-2017"></a>Spuštění testů v sadě Visual Studio 2017

Testy můžete spustit kliknutím **spustit všechny** odkaz v Průzkumníku testů. Nebo testy můžete spustit tak, že vyberete jeden nebo více testů nebo skupiny, že kliknete pravým tlačítkem a vyberete **spustit vybrané testy** z místní nabídky. Spustit testy na pozadí a Průzkumník testů automaticky aktualizuje a zobrazí výsledky. Kromě toho můžete také ladit vybrané testy tak, že vyberete **ladit vybrané testy**.

> [!Warning]
> Ladění testů jednotek pomocí Node 8 + momentálně se podporuje jenom funguje pro jazyk JavaScript soubory testů, TypeScript, soubory testu se nezdaří pro dosažení zarážky. Jako alternativní řešení použít `debugger` – klíčové slovo.

> [!NOTE]
> Aktuálně nepodporujeme testy profilaci nebo pokrytí kódu.

### <a name="run-tests-from-the-command-line"></a>Spuštění testů z příkazového řádku

Můžete spouštět testy z [Developer Command Prompt](/dotnet/framework/tools/developer-command-prompt-for-vs) pro Visual Studio 2017 pomocí následujícího příkazu:

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
> Pokud dojde k chybě, což indikuje, že *vstest.console.exe* nemůže být nalezen, ujistěte se, že jste otevřeli Developer Command Prompt a nejsou pravidelně příkazový řádek.

## <a name="addingFramework"></a>Přidání podpory pro rozhraní testování částí

Přidání podpory pro další testovacích architektur díky implementaci zjišťování a spouštění logiky pomocí jazyka JavaScript. To provedete tak, že přidáte složku s názvem rozhraní pro testování v rámci:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks`

Tato složka musí obsahovat soubor jazyka JavaScript se stejným názvem, který exportuje tyto dvě funkce:

* `find_tests`
* `run_tests`

Pro dobré a příklad `find_tests` a `run_tests` implementace rozhraní v testování Mocha implementace, naleznete v tématu:

`<VisualStudioFolder>\Common7\IDE\Extensions\Microsoft\NodeJsTools\TestAdapter\TestFrameworks\mocha\mocha.js`

K dispozici testovacích architektur zjišťování dochází při spuštění sady Visual Studio. Pokud architektura se přidá, když běží Visual Studio, restartujte Visual Studio ke zjištění rozhraní framework. Ale není nutné restartovat při provádění změn pro implementaci.

## <a name="unit-tests-in-other-project-types"></a>Testování částí v jiné typy projektů
Nejste omezeni pouze do projektu Node.js zápis testů jednotek. Po přidání vlastnosti TestFramework a TestRoot k libovolnému C# nebo projektu jazyka Visual Basic, tyto testy se vytvořil výčet a ji můžete spustit pomocí okna Průzkumníka testů.

Chcete-li povolit, klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení, zvolte **uvolnit projekt**a klikněte na tlačítko **upravit projekt**. Potom v souboru projektu přidejte následující dva elementy do vlastností skupiny.

> [!NOTE]
> Ujistěte se, že vlastnost skupinu, kterou přidáváte prvky, které mají nemá podmínka uvedená.
> To může způsobit neočekávané chování.

```xml
<PropertyGroup>
    <JavaScriptTestRoot>tests\</JavaScriptTestRoot>
    <JavaScriptTestFramework>Tape</JavaScriptTestFramework>
</PropertyGroup>
```

V dalším kroku přidat testy do kořenové složky test, který jste zadali, a budou k dispozici ke spuštění v okně Průzkumníka testů. Pokud se zpočátku nezobrazí, budete muset projekt znovu sestavte.

> [!NOTE]
> To aktuálně nebude fungovat pro projekty .NET Standard a .NET Core.
