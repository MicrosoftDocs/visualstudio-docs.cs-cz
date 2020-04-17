---
title: VSTest.Console.exe – možnosti příkazového řádku
ms.date: 07/12/2018
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40f8bc4847201d1bd0298bc91432996ecce58d65
ms.sourcegitcommit: 4bcd6abb89feff1cf8251e3ded73fdc30b67e347
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81615545"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe – možnosti příkazového řádku

*VSTest.Console.exe* je nástroj příkazového řádku pro spuštění testů. Na příkazovém řádku můžete zadat několik možností v libovolném pořadí. Tyto možnosti jsou uvedeny v seznamu [Obecné možnosti příkazového řádku](#general-command-line-options).

> [!NOTE]
> Adaptér MSTest v sadě Visual Studio funguje také ve starším režimu (ekvivalentní spuštění testů s *mstest.exe*) pro kompatibilitu. Ve starším režimu nelze využít funkce TestCaseFilter. Adaptér může přepnout do staršího režimu, když je zadán soubor *testsettings,* **forcelegacymode** je nastavena na **hodnotu true** v souboru *runsettings* nebo pomocí atributů, jako je **HostType**.
>
> Chcete-li spustit automatizované testy v počítači založeném na architektuře ARM, musíte použít *vstest.console.exe*.

Chcete-li použít nástroj příkazového řádku, otevřete [příkazový řádek pro vývojáře](/dotnet/framework/tools/developer-command-prompt-for-vs) nebo jej najdete v *%Program Files(x86)%\Microsoft Visual\\ Studio<verze\> \\<vydání\>\common7\ide\CommonExtensions\\<platformy | Microsoft>*.

## <a name="general-command-line-options"></a>Obecné možnosti příkazového řádku

V následující tabulce jsou uvedeny všechny možnosti nástroje *VSTest.Console.exe* a jejich krátké popisy. Podobný souhrn můžete zobrazit zadáním `VSTest.Console/?` na příkazovém řádku.

| Možnost | Popis |
|---|---|
|**[*názvy testovacích souborů*]**|Spusťte testy ze zadaných souborů. Oddělte více názvů testovacích souborů mezerami.<br />Příklady: `mytestproject.dll`,`mytestproject.dll myothertestproject.exe`|
|**/Settings:[*název souboru*]**|Spusťte testy s dalšími nastaveními, jako jsou například kolekce dat.<br />Příklad: `/Settings:Local.RunSettings`|
|**/Testy:[*název testu*]**|Spusťte testy s názvy, které obsahují zakalené hodnoty. Chcete-li zadat více hodnot, oddělte je čárky.<br />Příklad: `/Tests:TestMethod1,testMethod2`<br />Možnost příkazového řádku **/Tests** nelze použít s možností příkazového řádku **/TestCaseFilter.**|
|**/Paralelní**|Určuje, že testy budou prováděny paralelně. Ve výchozím nastavení lze použít až všechna dostupná jádra na stroji. Můžete nakonfigurovat počet jader, které chcete použít v souboru nastavení.|
|**/Enablecodecoverage**|Povolí diagnostický adaptér dat CodeCoverage v testovacím běhu.<br />Výchozí nastavení se použijí, pokud nejsou zadána pomocí souboru nastavení.|
|**/Izolace**|Spustí testy v izolovaném procesu.<br />Tato izolace umožňuje *vstest.console.exe* proces méně pravděpodobné, že bude zastaven a chyba v testech, ale testy mohou běžet pomaleji.|
|**/UseVsixRozšíření**|Tato možnost umožňuje *vstest.console.exe* proces použití nebo přeskočit Rozšíření VSIX nainstalován (pokud existuje) v testu spustit.<br />Tato možnost je zastaralá. Počínaje další hlavní verzí sady Visual Studio může být tato možnost odebrána. Přechod na náročné rozšíření k dispozici jako balíček NuGet.<br />Příklad: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*cesta*]**|Vynutí proces *ustest.console.exe* použít vlastní testovací adaptéry ze zadané cesty (pokud existuje) v testovacím běhu.<br />Příklad: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platforma:[*typ platformy*]**|Cílová architektura platformy, která se má použít pro spuštění testu.<br />Platné hodnoty jsou x86, x64 a ARM.|
|**/Framework: [*verze frameworku*]**|Cílová verze rozhraní .NET, která má být použita pro spuštění testu.<br />Příklady `Framework35`hodnot `Framework40` `Framework45`jsou `FrameworkUap10` `.NETCoreApp,Version=v1.1`, , , .<br />TargetFrameworkAttribute se používá k automatickému rozpoznání této `Framework40` možnosti z vašeho sestavení a výchozí, pokud atribut není k dispozici. Tuto možnost je nutné zadat explicitně, pokud odeberete [atribut TargetFrameworkAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.versioning.targetframeworkattribute) z sestavení jádra .NET.<br />Pokud je cílová architektura zadána jako **Framework35**, testy spustit v CLR 4.0 "režim kompatibility".<br />Příklad: `/Framework:framework40`|
|**/TestCaseFilter:[*výraz*]**|Spusťte testy, které odpovídají danému výrazu.<br /><\> Výraz je vlastnost\><formátu\>\| =\>hodnota<[<Expression ].<br />Příklad: `/TestCaseFilter:"Priority=1"`<br />Příklad: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />Možnost příkazového řádku **/TestCaseFilter** nelze použít s možností příkazového řádku **/Tests.** <br />Informace o vytváření a používání výrazů naleznete v [tématu TestCase filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Zobrazí informace o využití.|
|**/Logger:[*uri/friendlyname*]**|Zadejte protokolovací nástroj pro výsledky testů.<br />Příklad: Chcete-li protokolovat výsledky do souboru výsledků testů sady Visual Studio (TRX), použijte<br />**/Logger:trx**<br />**[; LogFileName=\<Výchozí je jedinečný název souboru>]**|
|**/ListTesty:[*název souboru*]**|Seznamy zjištěných testů z daného testovacího kontejneru.|
|**/ListObjevitelé**|Seznam nainstalovaných testovacích objevitelů.|
|**/SeznamExecutors**|Zobrazí seznam nainstalovaných vykonavatelů testů.|
|**/ListLoggery**|Seznam nainstalovaných testovacích záznamníků.|
|**/ListSettingsProviders**|Seznam nainstalovaných zprostředkovatelů nastavení testů.|
|**/Obviňování**|Sleduje testy při jejich provádění a pokud dojde k chybě procesu testovacího hostitele, vydává názvy testů v jejich pořadí provádění až do a včetně konkrétního testu, který byl spuštěn v době selhání. Tento výstup usnadňuje izolovat problematický test a dále diagnostikovat. [Více informací](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag:[*název souboru*]**|Zapíše protokoly diagnostických trasování do zadaného souboru.|
|**/ResultsDirectory:[*cesta*]**|Pokud neexistuje, bude adresář výsledků testu vytvořen v zadané cestě.<br />Příklad: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|ID procesu nadřazeného procesu odpovědného za spuštění aktuálního procesu.|
|**/Port:[*port*]**|Port pro připojení soketu a příjem zpráv o událostech.|
|**/Collect:[*dataCollector friendlyName*]**|Povolí sběr dat pro spuštění testu. [Více informací](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> Možnosti a hodnoty nejsou rozlišována malá a velká písmena.

## <a name="examples"></a>Příklady

Syntaxe pro spuštění *souboru VSTest.Console.exe* je:

`Vstest.console.exe [TestFileNames] [Options]`

Následující příkaz spustí *soubor VSTest.Console.exe* pro testovací knihovnu **myTestProject.dll**:

```cmd
vstest.console.exe myTestProject.dll
```

Následující příkaz spustí *soubor VSTest.Console.exe* s více testovacími soubory. Samostatné názvy testovacích souborů s mezerami:

```cmd
Vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Následující příkaz spustí *vstest.console.exe* s několika možnostmi. Spustí testy v souboru *myTestFile.dll* v izolovaném procesu a použije nastavení zadaná v souboru *Local.RunSettings.* Navíc spustí pouze testy označené "Priority= 1" a protokoly výsledky *.trx* souboru.

```cmd
vstest.console.exe  myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```
