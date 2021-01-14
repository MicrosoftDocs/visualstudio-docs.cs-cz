---
title: VSTest.Console.exe – možnosti příkazového řádku
description: Přečtěte si o nástroji příkazového řádku VSTest.Console.exe, který spouští testy. Tento článek obsahuje obecné možnosti příkazového řádku.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0dc266b43d9a4634fe8cfbc05a3a070ae72cdaa9
ms.sourcegitcommit: 1ceb58e3a1afa80a3211911ada4e5adaa1b1d439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192860"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe – možnosti příkazového řádku

*VSTest.Console.exe* je nástroj příkazového řádku pro spouštění testů. Na příkazovém řádku můžete zadat několik možností v libovolném pořadí. Tyto možnosti jsou uvedeny v [obecných parametrech příkazového řádku](#general-command-line-options).

> [!NOTE]
> Adaptér MSTest v sadě Visual Studio funguje také v režimu starší verze (ekvivalent spuštění testů s *mstest.exe*) kvůli kompatibilitě. V režimu starší verze nemůže využít funkci TestCaseFilter. Adaptér může přepnout do režimu starší verze, pokud je zadán soubor *testsettings* , **forcelegacymode** je nastaven na **hodnotu true** v souboru *runsettings* nebo pomocí atributů jako **HostType**.
>
> Chcete-li spustit automatizované testy na počítači založeném na architektuře ARM, je nutné použít *VSTest.Console.exe*.

Otevřete [Developer Command Prompt](/dotnet/framework/tools/developer-command-prompt-for-vs) pro použití nástroje příkazového řádku nebo můžete najít tento nástroj v *% Program Files (x86)% \ Microsoft Visual Studio \\<verze \> \\<edice \> \common7\ide\CommonExtensions \\<Platform | Microsoft>*.

## <a name="general-command-line-options"></a>Obecné možnosti příkazového řádku

V následující tabulce jsou uvedeny všechny možnosti pro *VSTest.Console.exe* a krátké popisy. Podobný souhrn můžete zobrazit zadáním `VSTest.Console/?` na příkazovém řádku.

| Možnost | Popis |
|---|---|
|**[*názvy testovacích souborů*]**|Spustí testy ze zadaných souborů. Více názvů testovacích souborů oddělte mezerami.<br />Příklady: `mytestproject.dll` , `mytestproject.dll myothertestproject.exe`|
|**/Settings: [*název souboru*]**|Spusťte testy s dalšími nastaveními, jako jsou například sběrače dat. Další informace najdete v tématu [konfigurace testů jednotek pomocí souboru. runsettings.](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)<br />Příklad: `/Settings:local.runsettings`|
|**/Tests: [*název testu*]**|Spusťte testy s názvy, které obsahují zadané hodnoty. Chcete-li zadat více hodnot, oddělte je čárkami.<br />Příklad: `/Tests:TestMethod1,testMethod2`<br />Možnost příkazového řádku **/Tests** nelze použít s parametrem příkazového řádku **/TestCaseFilter** .|
|**/Parallel**|Určuje, že testy budou spuštěny paralelně. Ve výchozím nastavení je možné použít až všechna dostupná jádra v počítači. Počet jader, které se mají použít v souboru nastavení, můžete nakonfigurovat.|
|**/Enablecodecoverage**|Povolí adaptér diagnostiky dat CodeCoverage v testovacím běhu.<br />Výchozí nastavení se použijí, pokud není zadáno pomocí souboru nastavení.|
|**/Inisolation.**|Spustí testy v izolovaném procesu.<br />Díky této izolaci se *vstest.console.exe* proces méně pravděpodobně zastavil při chybě v testech, ale testy mohou běžet pomaleji.|
|**/UseVsixExtensions**|Tato možnost umožňuje procesu *vstest.console.exe* použít nebo přeskočit nainstalovaná rozšíření VSIX (pokud existují) v testovacím běhu.<br />Tato možnost je zastaralá. Od další hlavní verze sady Visual Studio může být tato možnost odebrána. Přejděte k využití rozšíření, která jsou zpřístupněna jako balíček NuGet.<br />Příklad: `/UseVsixExtensions:true`|
|**/TestAdapterPath: [*cesta*]**|Vynutí, aby proces *vstest.console.exe* používal vlastní testovací adaptéry ze zadané cesty (pokud existuje) v testovacím běhu.<br />Příklad: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform: [*typ platformy*]**|Vynutí použití dané platformy místo platformy zjištěné z aktuálního modulu runtime. Tato možnost je schopná vynutit jenom platformy x86 a x64 ve Windows. Možnost ARM je poškozená a výsledkem bude x64 ve většině systémů.<br />Nezadávejte tuto možnost, pokud chcete spustit v modulech runtime, které nejsou v seznamu platných hodnot, jako je ARM64.<br />Platné hodnoty jsou x86, x64 a ARM.<br /> 
|**/Framework: [*Framework – verze*]**|Cílová verze rozhraní .NET, která se má použít pro spuštění testu.<br />Příklady hodnot jsou `Framework35` , `Framework40` , `Framework45` , `FrameworkUap10` , `.NETCoreApp,Version=v1.1` .<br />TargetFrameworkAttribute slouží k automatické detekci této možnosti ze sestavení a výchozím nastavením, `Framework40` Pokud atribut není přítomen. Tuto možnost je nutné zadat explicitně, pokud chcete odebrat [TargetFrameworkAttribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) ze sestavení .NET Core.<br />Je-li cílové rozhraní určeno jako **Framework35**, testy jsou spouštěny v modulu CLR 4,0 "režim kompatibility".<br />Příklad: `/Framework:framework40`|
|**/TestCaseFilter: [*výraz*]**|Spustí testy, které odpovídají danému výrazu.<br />Výraz <\> má formát <vlastnost \> =<hodnota \> [ \|<ový výraz \> ].<br />Příklad: `/TestCaseFilter:"Priority=1"`<br />Příklad: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />Možnost příkazového řádku **/TestCaseFilter** nelze použít s parametrem příkazového řádku **/Tests** . <br />Informace o vytváření a používání výrazů najdete v tématu [testovací případ Filter](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).|
|**/?**|Zobrazí informace o použití.|
|**/Logger: [*URI/FriendlyName*]**|Zadejte protokolovací nástroj pro výsledky testů. Pokud chcete povolit více protokolovacích nástrojů, zadejte parametr víckrát.<br />Příklad: Chcete-li protokolovat výsledky do souboru sady Visual Studio Výsledky testů (TRX), použijte<br />**/Logger: TRX**<br />**[; LogFile = \<Defaults to unique file name> ]**|
|**/ListTests: [*název souboru*]**|Zobrazí seznam zjištěných testů z daného kontejneru testů.|
|**/ListDiscoverers**|Zobrazí seznam nainstalovaných zjišťování testů.|
|**/ListExecutors**|Zobrazí seznam nainstalovaných prováděcích modulů testů.|
|**/ListLoggers**|Zobrazí seznam nainstalovaných protokolovacích nástrojů testů.|
|**/ListSettingsProviders**|Zobrazí seznam nainstalovaných zprostředkovatelů nastavení testů.|
|**/Blame**|Spustí testy v režimu viny. Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu. Při zjištění chyby vytvoří soubor sekvence v `TestResults/<Guid>/<Guid>_Sequence.xml` , který zachytí pořadí testů, které byly spuštěny před selháním. Další informace najdete v tématu [viny data collector](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md).|
|**/Diag: [*název souboru*]**|Zapíše protokoly trasování diagnostiky do zadaného souboru.|
|**/ResultsDirectory: [*cesta*]**|Adresář výsledků testů bude vytvořen v zadané cestě, pokud neexistuje.<br />Příklad: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId: [*ParentProcessId*]**|ID procesu nadřazeného procesu zodpovědného za spuštění aktuálního procesu.|
|**/Port: [*port*]**|Port pro připojení soketu a příjem zpráv událostí.|
|**/Collect: [DataCollector *FriendlyName*]**|Povolí shromažďování dat pro testovací běh. [Další informace](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> V možnostech a hodnotách se nerozlišují velká a malá písmena.

## <a name="examples"></a>Příklady

Syntaxe pro spuštění *vstest.console.exe* je:

`vstest.console.exe [TestFileNames] [Options]`

Následující příkaz spustí *vstest.console.exe* pro *myTestProject.dll* knihovny testů:

```cmd
vstest.console.exe myTestProject.dll
```

Následující příkaz se spustí *vstest.console.exe* s více testovacími soubory. Názvy testovacích souborů oddělte mezerami:

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

Následující příkaz se spustí *vstest.console.exe* s několika možnostmi. Spustí testy v souboru *myTestFile.dll* v izolovaném procesu a použije nastavení zadané v *místním souboru. runsettings* . Kromě toho spustí pouze testy označené "Priorita = 1" a zaprotokoluje výsledky do souboru *. TRX* .

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

Následující příkaz se spustí *vstest.console.exe* s `/blame` možností pro *myTestProject.dll* knihovny testů:

```cmd
vstest.console.exe myTestFile.dll /blame
```

Pokud došlo k chybě hostitele testu, je vygenerován soubor *sequence.xml* . Soubor obsahuje plně kvalifikované názvy testů v pořadí spouštění až do a včetně konkrétního testu, který byl spuštěn v době selhání.

Pokud nedojde k žádné chybě hostitele testu, *sequence.xml* soubor nebude vygenerován.

Příklad vygenerovaného souboru *sequence.xml* : 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```
