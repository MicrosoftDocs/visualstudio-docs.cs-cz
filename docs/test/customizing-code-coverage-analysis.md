---
title: Přizpůsobení analýzy pokrytí kódu
description: Naučte se používat atribut ExcludeFromCodeCoverageAttribute k vyloučení testovacího kódu z výsledků pokrytí. Můžete zahrnout sestavení mimo vaše řešení.
ms.custom: SEO-VS-2020
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 65044baf78e6f49e35f011a4853111063e82a192
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964404"
---
# <a name="customize-code-coverage-analysis"></a>Přizpůsobení analýzy pokrytí kódu

Ve výchozím nastavení pokrytí kódu analyzuje všechna sestavení řešení, která jsou načtena během testování částí. Doporučujeme, abyste používali toto výchozí chování, protože funguje dobře ve většině času. Další informace naleznete v tématu [Použití pokrytí kódu k určení, kolik kódu je testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Pro vyloučení testovacího kódu z výsledků pokrytí kódu a zahrnutí pouze kódu aplikace přidejte <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atribut do vaší třídy testu.

Chcete-li zahrnout sestavení, která nejsou součástí vašeho řešení, Získejte soubory *PDB* pro tato sestavení a zkopírujte je do stejné složky jako soubory Assembly *. dll* .

## <a name="run-settings-file"></a>Soubor parametrů běhu

[Soubor s parametry spuštění](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) je konfigurační soubor používaný nástroji pro testování částí. Rozšířené nastavení pokrytí kódu je určeno v souboru *. runsettings* .

Chcete-li přizpůsobit pokrytí kódu, postupujte podle následujících kroků:

1. Přidejte do svého řešení soubor s parametry spuštění. V **Průzkumník řešení** v místní nabídce řešení zvolte možnost **Přidat**  >  **novou položku** a vyberte **soubor XML**. Uložte soubor s názvem, například *CodeCoverage. runsettings*.

2. Přidejte obsah z ukázkového souboru na konci tohoto článku a pak ho Přizpůsobte podle svých potřeb, jak je popsáno v následujících částech.

::: moniker range="vs-2017"

3. Chcete-li vybrat soubor parametrů spuštění, v nabídce **test** zvolte možnost **nastavení testu**  >  **Vybrat soubor s nastavením testu**. Chcete-li zadat soubor parametrů běhu pro spuštění testů z příkazového řádku, přečtěte si téma [Konfigurace testování částí](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line).

::: moniker-end

::: moniker range=">=vs-2019"

3. Chcete-li vybrat soubor s parametry spuštění, v nabídce **test** zvolte **možnost soubor nastavení**. Chcete-li zadat soubor parametrů běhu pro spuštění testů z příkazového řádku, přečtěte si téma [Konfigurace testování částí](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line).

::: moniker-end

   Když vyberete možnost **Analyzovat pokrytí kódu**, informace o konfiguraci budou načteny ze souboru parametrů běhu.

   > [!TIP]
   > Všechny předchozí výsledky pokrytí kódu a barevné zvýraznění kódu nejsou automaticky skryty při spuštění testů nebo aktualizaci kódu.

::: moniker range="vs-2017"

Chcete-li vlastní nastavení vypnout a zapnout, zrušte výběr nebo vyberte soubor v nabídce  > **Nastavení** testu testu.

![Nabídka nastavení testu se souborem vlastního nastavení v aplikaci Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li vlastní nastavení vypnout a zapnout, zrušte výběr nebo vyberte soubor v nabídce **test** .

::: moniker-end

## <a name="symbol-search-paths"></a>Cesty pro hledání symbolů

Pokrytí kódu vyžaduje soubory symbolů (soubory *PDB* ) pro sestavení. Pro sestavení sestavená vaším řešením jsou soubory symbolů obvykle přítomny společně s binárními soubory a pokrytí kódu funguje automaticky. V některých případech může být vhodné zahrnout odkazovaná sestavení do analýzy pokrytí kódu. V takových případech soubory *. pdb* nemusí být sousedící s binárními soubory, ale můžete zadat cestu pro hledání symbolů v souboru *. runsettings* .

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Rozlišení symbolů může trvat čas, zejména při použití umístění vzdáleného souboru s mnoha sestaveními. Proto zvažte možnost zkopírovat soubory *. pdb* do stejného místního umístění jako binární soubory (*. dll* a *. exe*).

## <a name="include-or-exclude-assemblies-and-members"></a>Zahrnout nebo vyloučit sestavení a členy

Můžete zahrnout nebo vyloučit sestavení nebo konkrétní typy a členy z analýzy pokrytí kódu. Pokud je oddíl **include** prázdný nebo vynechán, jsou zahrnuta všechna sestavení, která jsou načtena a přidruženy soubory PDB. Pokud sestavení nebo člen souhlasí s klauzulí v oddílu **Exclude** , je vyloučen z pokrytí kódu. Oddíl **Exclude** má přednost před oddílem **include** : Pokud je sestavení uvedeno v **zahrnutí** i **vyloučení**, nebude zahrnuto do pokrytí kódu.

Například následující kód XML vyloučí jedno sestavení zadáním jeho názvu:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>.*Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Následující příklad určuje, že v pokrytí kódu by mělo být zahrnuto pouze jedno sestavení:

```xml
<ModulePaths>
  <Include>
   <ModulePath>.*Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Následující tabulka ukazuje různé způsoby, jak mohou být sestavení a členové spárovány s zahrnutím do nebo z pokrytí kódu.

| XML – element | Co odpovídá |
| - | - |
| ModulePath nastavte | Odpovídá sestavením určeným názvem sestavení nebo cestou k souboru. |
| CompanyName | Porovnává sestavení podle atributu **společnosti** . |
| PublicKeyToken | Odpovídá podepsaným sestavením tokenu veřejného klíče. |
| Zdroj | Porovná prvky podle názvu cesty zdrojového souboru, ve kterém jsou definovány. |
| Atribut | Porovná prvky, které mají zadaný atribut. Zadejte úplný název atributu, například `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>` .<br/><br/>Pokud atribut vyloučíte <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute> , kód, který používá funkce jazyka, jako jsou `async` , `await` , `yield return` a automaticky implementované vlastnosti, je vyloučen z analýzy pokrytí kódu. Chcete-li vyloučit skutečně generovaný kód, vylučte pouze <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> atribut. |
| Funkce | Porovná procedury, funkce nebo metody podle plně kvalifikovaného názvu, včetně seznamu parametrů. Můžete také porovnat část názvu pomocí [regulárního výrazu](#regular-expressions).<br/><br/>Příklady:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` Jazyk<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)` Volat |

### <a name="regular-expressions"></a>Regulární výrazy

Uzly include a Exclude používejte regulární výrazy, které nejsou stejné jako zástupné znaky. Ve shodách se nerozlišují velká a malá písmena. Tady je několik příkladů:

- **.\*** odpovídá řetězci libovolných znaků

- **\\.** odpovídá tečkě "."

- **\\ ( \\ )** odpovídá závorce "()"

- **\\\\** odpovídá oddělovači cesty souboru " \\ "

- **^** odpovídá začátku řetězce

- **$** odpovídá konci řetězce

Následující kód XML ukazuje, jak zahrnout a vyloučit konkrétní sestavení pomocí regulárních výrazů:

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

Následující kód XML ukazuje, jak zahrnout a vyloučit konkrétní funkce pomocí regulárních výrazů:

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>
```

> [!WARNING]
> Pokud je v regulárním výrazu Chyba, jako je například neuvozená nebo nespárovaná závorka, analýza pokrytí kódu se nespustí.

Další informace o regulárních výrazech naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="sample-runsettings-file"></a>Ukázkový soubor s příponou .runsettings

Zkopírujte tento kód a upravte jej tak, aby vyhovoval vašim potřebám.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See /visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler\.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis\.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->

            <!-- Set this to True to collect coverage information for functions marked with the "SecuritySafeCritical" attribute. Instead of writing directly into a memory location from such functions, code coverage inserts a probe that redirects to another function, which in turns writes into memory. -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <!-- When set to True, collects coverage information from child processes that are launched with low-level ACLs, for example, UWP apps. -->
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <!-- When set to True, collects coverage information from child processes that are launched by test or production code. -->
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <!-- When set to True, restarts the IIS process and collects coverage information from it. -->
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>Viz také

- [Konfigurace testů jednotek pomocí souboru parametrů běhu](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Použití pokrytí kódu k určení množství testovaného kódu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
