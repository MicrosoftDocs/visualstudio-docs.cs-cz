---
title: Přizpůsobení analýzy pokrytí kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 09af57ca64524dafa506d57d486e9385a4c35a93
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53054934"
---
# <a name="customize-code-coverage-analysis"></a>Přizpůsobení analýzy pokrytí kódu

Ve výchozím nastavení pokrytí kódu analyzuje všechna sestavení řešení, která jsou načtena během testování částí. Vzhledem k tomu, že to funguje dobře ve většině případů doporučujeme použít toto výchozí chování. Další informace najdete v tématu [použití pokrytí kódu k určení, kolik kódu je testována](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

Chcete-li vyloučit testovací kód z výsledků pokrytí kódu a obsahovat jenom kód aplikace, přidejte <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> atribut do vaší testovací třídy.

Chcete-li zahrnout sestavení, které nejsou součástí vašeho řešení, získat *PDB* soubory pro tato sestavení a zkopírujte je do stejné složky jako sestavení *.dll* soubory.

## <a name="run-settings-file"></a>Soubor parametrů běhu

[Soubor parametrů běhu](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) je konfigurační soubor používaný nástroji pro testování jednotky. Upřesňující nastavení pokrytí kódu jsou určené v *s příponou .runsettings* souboru.

Chcete-li přizpůsobit pokrytí kódu, postupujte podle těchto kroků:

1. Přidejte soubor parametrů běhu do vašeho řešení. V **Průzkumníka řešení**, v místní nabídce řešení zvolte **přidat** > **nová položka**a vyberte **soubor XML**. Uložte soubor s názvem, jako *CodeCoverage.runsettings*.

1. Přidejte obsah ze souboru příkladu na konci tohoto článku a jak je popsáno v následující části jeho úprava podle vašich potřeb.

1. Vyberte soubor parametrů běhu na **testovací** nabídky, zvolte **nastavení testu** > **vybrat soubor nastavení testu**. Zadejte soubor parametrů běhu pro spouštění testů z příkazového řádku nebo v pracovním postupu sestavení, najdete v článku [konfigurace testů jednotek s použitím *s příponou .runsettings* souboru](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file).

   Když vyberete **analyzovat pokrytí kódu**, informace o konfiguraci je pro čtení ze souboru parametrů běhu.

   > [!TIP]
   > Předchozí výsledky pokrytí kódu a barevné zvýraznění kódu nejsou zakryty automaticky při spuštění testů nebo aktualizujte svůj kód.

Vlastní nastavení vypnutí a zapnutí, zrušte výběr nebo vyberte soubor v **testovací** > **nastavení testu** nabídky.

![Nabídka nastavení testu se soubor s vlastním nastavením](../test/media/codecoverage-settingsfile.png)

### <a name="specify-symbol-search-paths"></a>Určení cest pro hledání symbolů

Pokrytí kódu vyžaduje soubory symbolů (*PDB* soubory) pro sestavení. Pro sestavení vytvořených vaším řešením jsou soubory symbolů obvykle k dispozici spolu s binární soubory a pokrytí kódu pracuje automaticky. Ale v některých případech můžete chtít zahrnout odkazovaná sestavení do analýzy pokrytí kódu. V takovém případě *PDB* soubory nemusí být vedle binární soubory, ale můžete zadat cestu pro hledání symbolů v *s příponou .runsettings* souboru.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> Vyhodnocování symbolů může trvat dobu, zvláště při použití vzdáleného umístění souborů s mnoha sestavení. Zvažte proto možnost zkopírování *PDB* soubory do stejného umístění jako binární soubor (*.dll* a *.exe*) soubory.

### <a name="exclude-and-include"></a>Vyloučení a zahrnutí

Vybraná sestavení lze vyloučit z analýzy pokrytí kódu. Příklad:

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

Nebo naopak můžete vybrat sestavení, která chcete do analýzy zahrnout. Tento přístup má tu nevýhodu, že při přidání více sestavení k řešení je nesmíte zapomenout přidat do seznamu:

```xml
<ModulePaths>
  <Include>
   <ModulePath>Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

Pokud **zahrnout** je prázdný, pak zpracování pokrytí kódu zahrne všechna sestavení, která jsou načtena a pro kterou *PDB* soubory lze nalézt. Pokrytí kódu neobsahuje položky, které odpovídají klauzuli v **vyloučit** seznamu.

**Zahrnout** je zpracován před atributem **vyloučit**.

### <a name="regular-expressions"></a>Regulární výrazy

Pomocí regulárních výrazů můžete zahrnout a vyloučit uzly. Další informace najdete v tématu [použití regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Regulární výrazy nejsou stejné jako zástupné znaky. Zejména:

- **. \\** * odpovídá řetězci libovolných znaků

- **\\.** odpovídá tečce ".")

- **\\( \\)** odpovídá závorkám ""

- **\\\\** odpovídá oddělovači cesty k souboru "\\"

- **^** odpovídá začátku řetězce

- **$** odpovídá konci řetězce

Ve shodách se nerozlišují velká a malá písmena.

Příklad:

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

> [!WARNING]
> Pokud dojde k chybě v regulárním výrazu, jako je například znakem nebo nespárované závorky, analýza pokrytí kódu se nespustí.

### <a name="other-ways-to-include-or-exclude-elements"></a>Další způsoby zahrnutí nebo vyloučení prvků

- **ModulePath** – porovná sestavení určená cestou k souboru sestavení.

- **CompanyName** – porovná sestavení podle **společnosti** atribut.

- **PublicKeyToken** – porovná podepsaná sestavení podle tokenu veřejného klíče.

- **Zdroj** – porovná prvky podle názvu cesty zdrojového souboru, ve kterém jsou definovány.

- **Atribut** – porovná prvky, ke kterým je připojen určitý atribut. Zadejte úplný název atributu a zahrnují "Atribut" na konci názvu.

- **Funkce** – porovná procedury, funkce nebo metody podle plně kvalifikovaného názvu. Tak, aby odpovídaly názvu funkce, musí odpovídat regulárnímu výrazu plně kvalifikovaný název funkce včetně oboru názvů, název třídy, názvu metody a seznamu parametrů. Příklad:

   ```csharp
   Fabrikam.Math.LocalMath.SquareRoot(double);
   ```

   ```cpp
   Fabrikam::Math::LocalMath::SquareRoot(double)
   ```

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
Each element in the list is a regular expression (ECMAScript syntax). See https://docs.microsoft.com/visualstudio/ide/using-regular-expressions-in-visual-studio.
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
                <Attribute>^System\.Runtime\.CompilerServices.CompilerGeneratedAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis.ExcludeFromCodeCoverageAttribute$</Attribute>
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
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
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