---
title: Přizpůsobení analýzy pokrytí kódu
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: bce7a6b9369f33e6fa5248821f58d9903172415c
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918651"
---
# <a name="customize-code-coverage-analysis"></a>Přizpůsobení analýzy pokrytí kódu

Ve výchozím nastavení pokrytí kódu analyzuje všechna sestavení řešení, která jsou načtena během testování částí. Vzhledem k tomu, že to funguje dobře ve většině případů doporučujeme použít toto výchozí chování. Další informace najdete v tématu [použití pokrytí kódu k určení, kolik kódu je testována](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Chcete-li vyloučit testovací kód z výsledků pokrytí kódu a obsahovat jenom kód aplikace, přidejte <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atribut do vaší testovací třídy.

Chcete-li zahrnout sestavení, které nejsou součástí vašeho řešení, získat *PDB* soubory pro tato sestavení a zkopírujte je do stejné složky jako sestavení *.dll* soubory.

## <a name="run-settings-file"></a>Soubor parametrů běhu

[Soubor parametrů běhu](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) je konfigurační soubor používaný nástroji pro testování jednotky. Upřesňující nastavení pokrytí kódu jsou určené v *s příponou .runsettings* souboru.

Chcete-li přizpůsobit pokrytí kódu, postupujte podle těchto kroků:

1. Přidejte soubor parametrů běhu do vašeho řešení. V **Průzkumníka řešení**, v místní nabídce řešení zvolte **přidat** > **nová položka**a vyberte **soubor XML**. Uložte soubor s názvem, jako *CodeCoverage.runsettings*.

2. Přidejte obsah ze souboru příkladu na konci tohoto článku a jak je popsáno v následující části jeho úprava podle vašich potřeb.

::: moniker range="vs-2017"

3. Vyberte soubor parametrů běhu na **testovací** nabídky, zvolte **nastavení testu** > **vybrat soubor nastavení testu**. Chcete-li zadat soubor parametrů běhu pro spuštění testů z příkazového řádku, přečtěte si téma [Konfigurace testování částí](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line).

::: moniker-end

::: moniker range=">=vs-2019"

3. Chcete-li vybrat soubor s parametry spuštění, v nabídce **test** zvolte **možnost soubor nastavení**. Chcete-li zadat soubor parametrů běhu pro spuštění testů z příkazového řádku, přečtěte si téma [Konfigurace testování částí](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#command-line).

::: moniker-end

   Když vyberete **analyzovat pokrytí kódu**, informace o konfiguraci je pro čtení ze souboru parametrů běhu.

   > [!TIP]
   > Všechny předchozí výsledky pokrytí kódu a barevné zvýraznění kódu nejsou automaticky skryty při spuštění testů nebo aktualizaci kódu.

::: moniker range="vs-2017"

Chcete-li vlastní nastavení vypnout a zapnout, zrušte výběr nebo vyberte soubor v nabídce **Nastavení** **testu > test** .

![Nabídka nastavení testu se souborem vlastního nastavení v aplikaci Visual Studio 2017](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

Chcete-li vlastní nastavení vypnout a zapnout, zrušte výběr nebo vyberte soubor v nabídce **test** .

::: moniker-end

## <a name="symbol-search-paths"></a>Cesty pro hledání symbolů

Pokrytí kódu vyžaduje soubory symbolů (*PDB* soubory) pro sestavení. Pro sestavení sestavená vaším řešením jsou soubory symbolů obvykle přítomny společně s binárními soubory a pokrytí kódu funguje automaticky. V některých případech může být vhodné zahrnout odkazovaná sestavení do analýzy pokrytí kódu. V takovém případě *PDB* soubory nemusí být vedle binární soubory, ale můžete zadat cestu pro hledání symbolů v *s příponou .runsettings* souboru.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Vyhodnocování symbolů může trvat dobu, zvláště při použití vzdáleného umístění souborů s mnoha sestavení. Zvažte proto možnost zkopírování *PDB* soubory do stejného umístění jako binární soubor ( *.dll* a *.exe*) soubory.

## <a name="include-or-exclude-assemblies-and-members"></a>Zahrnout nebo vyloučit sestavení a členy

Můžete zahrnout nebo vyloučit sestavení nebo konkrétní typy a členy z analýzy pokrytí kódu. Pokud je oddíl **include** prázdný nebo vynechán, jsou zahrnuta všechna sestavení, která jsou načtena a přidruženy soubory PDB. Pokud sestavení nebo člen souhlasí s klauzulí v oddílu **Exclude** , je vyloučen z pokrytí kódu. Oddíl **Exclude** má přednost před oddílem **include** : Pokud je sestavení uvedeno v **zahrnutí** i **vyloučení**, nebude zahrnuto do pokrytí kódu.

Například následující kód XML vyloučí jedno sestavení zadáním jeho názvu:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Následující příklad určuje, že v pokrytí kódu by mělo být zahrnuto pouze jedno sestavení:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
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
| Atribut | Porovná prvky, které mají zadaný atribut. Zadejte úplný název atributu, například `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`.<br/><br/>Pokud vyloučíte atribut <xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute>, kód, který používá funkce jazyka, jako jsou `async`, `await`, `yield return`a automaticky implementované vlastnosti, je vyloučen z analýzy pokrytí kódu. Chcete-li vyloučit skutečně generovaný kód, vylučte pouze atribut <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. |
| Funkce | Porovná procedury, funkce nebo metody podle plně kvalifikovaného názvu, včetně seznamu parametrů. Můžete také porovnat část názvu pomocí [regulárního výrazu](#regular-expressions).<br/><br/>Příklady:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` (C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)` (C++) |

### <a name="regular-expressions"></a>Regulární výrazy

Uzly include a Exclude používejte regulární výrazy, které nejsou stejné jako zástupné znaky. Ve shodách se nerozlišují velká a malá písmena. Tady je pár příkladů:

- **.\*** odpovídá řetězci libovolných znaků.

- **\\.** odpovídá tečkě "."

- **\\( \\)** odpovídá závorkám ""

- **\\\\** odpovídá oddělovači cesty k souboru "\\"

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
> Pokud dojde k chybě v regulárním výrazu, jako je například znakem nebo nespárované závorky, analýza pokrytí kódu se nespustí.

Další informace o regulárních výrazech naleznete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

## <a name="sample-runsettings-file"></a>Ukázkový soubor s příponou .runsettings

Zkopírujte tento kód a upravte jej tak, aby odpovídala vašim potřebám.

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

## <a name="see-also"></a>Viz také:

- [Konfigurace testů jednotek s použitím souboru parametrů běhu](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Použití pokrytí kódu k určení, kolik kódu je testována.](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
