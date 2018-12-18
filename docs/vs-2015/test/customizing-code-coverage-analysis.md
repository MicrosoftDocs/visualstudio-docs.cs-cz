---
title: Přizpůsobení analýzy pokrytí kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f6337c35-acae-4c5f-b5d9-ac5ff687ef18
caps.latest.revision: 18
ms.author: gewarren
manager: douge
ms.openlocfilehash: d8a0b09bf2e67813548865b6ed56fee0b0170cc5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890163"
---
# <a name="customizing-code-coverage-analysis"></a>Přizpůsobení analýzy pokrytí kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení analyzuje nástroj pokrytí kódu Visual Studio všechna sestavení řešení (.exe/.dll), která jsou načtena během testování částí. Doporučujeme zachovat toto výchozí nastavení, protože ve většině případů funguje dobře. Další informace najdete v tématu [pomocí pokrytí kódu k určení jak mnohem kódu je právě testováno](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Před přizpůsobením chování pokrytí kódu je třeba zvážit některé alternativy:  
  
- *Chci vyloučit testovací kód z výsledků pokrytí kódu a obsahovat pouze kód aplikace.*  
  
   Přidat `ExcludeFromCodeCoverage Attribute` do vaší testovací třídy.  
  
- *Chci zahrnout sestavení, které nejsou součástí skupiny Moje řešení.*  
  
   Získejte soubory s příponou .pdb pro tato sestavení a zkopírujte je do stejné složky jako soubory sestavení s příponou .dll.  
  
  Chcete-li přizpůsobit chování pokrytí kódu, zkopírujte [ukázku na konci tohoto tématu](#sample) a přidejte ji do vašeho řešení pomocí souboru s příponou .runsettings. Upravit pro vaše konkrétní potřeby a potom na **testovací** nabídce zvolte **nastavení testu**, **vyberte nastavení testu** souboru. Zbývající část tohoto tématu popisuje tento postup podrobněji.  
  
## <a name="the-runsettings-file"></a>Soubor s příponou .runsettings  
 V souboru s příponou .runsettings jsou uvedena upřesňující nastavení pokrytí kódu. Jedná se o konfigurační soubor používaný nástroji pro testování částí. Doporučujeme vám zkopírovat [ukázku na konci tohoto tématu](#sample) a upravte jej podle svých potřeb.  
  
- *Co se stalo s soubor .testsettings, který jsem používal v sadě Visual Studio 2010?*  
  
   V sadě Visual Studio 2010 se soubor s příponou .testsettings používá pouze při testování částí založeném na rozhraní MSTest. V sadě Visual Studio 2012 se testovací nástroje používají nejen u rozhraní MSTest, ale také u jiných rozhraní, jako například NUnit a xUnit.net. Soubor s příponou .testsettings nebude s těmito rozhraními fungovat. Soubor s příponou .runsettings je určen k provádění úprav testovacích nástrojů takovým způsobem, který je kompatibilní se všemi testovacími rozhraními.  
  
  Chcete-li přizpůsobit pokrytí kódu, je nutné přidat soubor s příponou .runsettings do vašeho řešení:  
  
1. Přidání souboru .xml jako položku řešení s příponou `.runsettings`:  
  
    V Průzkumníku řešení zvolte v místní nabídce vašeho řešení a **přidat**, **nová položka**a vyberte **soubor XML**. Uložte soubor s názvem, jako například `CodeCoverage.runsettings`  
  
2. Přidejte obsah uvedený v ukázce kódu na konci tohoto tématu a potom jej přizpůsobte svým potřebám tak, jak je popsáno v následujících částech.  
  
3. Na **testovací** nabídce zvolte **nastavení testu**, **vybrat soubor nastavení testu** a vyberte soubor.  
  
4. Pokud nyní spustíte **analyzovat pokrytí kódu**tento `.runsettings` souboru bude kontrolovat své chování. Nezapomeňte, že musíte spustit pokrytí kódu znovu: předchozí výsledky pokrytí a barevné zvýraznění kódu nejsou při spuštění testů nebo aktualizaci kódu automaticky skryty.  
  
5. Vlastní nastavení vypnutí a zapnutí, zrušte výběr nebo vyberte soubor v **testovací**, **nastavení testu** nabídky.  
  
   ![Nabídka nastavení testu se soubor s vlastním nastavením](../test/media/codecoverage-settingsfile.png "Soubor_nastavení CodeCoverage")  
  
   Další aspekty testování částí lze nakonfigurovat ve stejném souboru s příponou .runsettings. Další informace najdete v tématu [svůj kód testu jednotek](../test/unit-test-your-code.md).  
  
### <a name="specifying-symbol-search-paths"></a>Určení cest pro hledání symbolů  
 Pokrytí kódu vyžaduje, aby byly pro sestavení k dispozici symboly (soubory s příponou .pdb). V případě sestavení vytvořených vaším řešením jsou soubory symbolů obvykle k dispozici spolu s binárními soubory a pokrytí kódu pracuje automaticky. Ale v některých případech můžete chtít zahrnout odkazovaná sestavení do analýzy pokrytí kódu. V takových případech se nemusí soubory s příponou .pdb nacházet u binárních souborů, ale můžete zadat cestu pro hledání symbolů v souboru s příponou .runsettings.  
  
```xml  
<SymbolSearchPaths>                
      <Path>\\mybuildshare\builds\ProjectX</Path>  
      <!--More paths if required-->  
</SymbolSearchPaths>  
  
```  
  
> [!WARNING]
>  Vyhodnocování symbolů může trvat dobu, zvláště při použití vzdáleného umístění souborů s velkým množstvím sestavení. Zvažte proto možnost zkopírování vzdálených souborů s příponou .pdb do stejného umístění jako binární soubory (.dll a .exe).  
  
### <a name="excluding-and-including"></a>Vyloučení a zahrnutí  
 Vybraná sestavení lze vyloučit z analýzy pokrytí kódu. Příklad:  
  
```minterastlib  
<ModulePaths>  
  <Exclude>  
   <ModulePath>Fabrikam.Math.UnitTest.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Exclude>  
</ModulePaths>  
```  
  
 Nebo naopak můžete vybrat sestavení, která chcete do analýzy zahrnout. Tento přístup má tu nevýhodu, že při přidání více sestavení k řešení je nesmíte zapomenout přidat do seznamu:  
  
```minterastlib  
<ModulePaths>  
  <Include>  
   <ModulePath>Fabrikam.Math.dll</ModulePath>  
   <!-- Add more ModulePath nodes here. -->  
  </Include>  
</ModulePaths>  
```  
  
 Pokud `<Include>` je prázdný, pak zpracování pokrytí kódu zahrne všechna sestavení (soubory .dll a .exe), která jsou načtena a pro kterou **PDB** nalezeny soubory, s výjimkou položky, které odpovídají klauzuli v `<Exclude>` seznamu.  
  
 `Include` je zpracován před atributem `Exclude`.  
  
### <a name="regular-expressions"></a>Regulární výrazy  
 Pomocí regulárních výrazů můžete zahrnout a vyloučit uzly. Další informace najdete v tématu [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md). Regulární výrazy nejsou stejné jako zástupné znaky. Zejména:  
  
1. **\.\\*** odpovídá řetězci libovolných znaků  
  
2. **\\.** odpovídá tečce ".")  
  
3. **\\( \\)** odpovídá závorkám ""  
  
4. **\\\\** odpovídá oddělovači cesty k souboru "\\"  
  
5. **^** odpovídá začátku řetězce  
  
6. **$** odpovídá konci řetězce  
  
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
>  Pokud je v regulárním výrazu chyba, jako například neřídící a nesprávně umístěné závorky, analýza pokrytí kódu se nespustí.  
  
### <a name="other-ways-to-include-or-exclude-elements"></a>Další způsoby zahrnutí nebo vyloučení prvků  
 Zobrazit [ukázku na konci tohoto tématu](#sample) příklady.  
  
- `ModulePath` – Sestavení určená cestou k souboru sestavení.  
  
- `CompanyName` – Porovná sestavení podle atributu společnost.  
  
- `PublicKeyToken` – Porovná podepsaná sestavení podle tokenu veřejného klíče. Například porovnat všechny součásti sady Visual Studio a rozšíření, použijte `<PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>`.  
  
- `Source` – Porovná prvky podle názvu cesty zdrojového souboru, ve kterém jsou definovány.  
  
- `Attribute` – Porovná prvky, ke kterým je připojen určitý atribut. Zadejte úplný název atributu včetně výrazu „Atribut“ na konci názvu.  
  
- `Function` – Porovná procedury, funkce nebo metody podle plně kvalifikovaného názvu.  
  
  **Porovnání názvu funkce**  
  
  Regulární výraz musí odpovídat plně kvalifikovanému názvu funkce včetně oboru názvů, názvu třídy, názvu metody a seznamu parametrů. Například  
  
- C# nebo Visual Basic: `Fabrikam.Math.LocalMath.SquareRoot(double)`  
  
- JAZYK C++:  `Fabrikam::Math::LocalMath::SquareRoot(double)`  
  
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
  
## <a name="how-to-specify-runsettings-files-while-running-tests"></a>Jak určit soubory s příponou .runsettings při spouštění testů  
  
### <a name="to-customize-runsettings-in-visual-studio-tests"></a>Přizpůsobení souboru s příponou .runsettings v testech sady Visual Studio  
 Zvolte **testovací**, **nastavení testu**, **vybrat soubor nastavení testu** a vyberte soubor s příponou .runsettings. Soubor se zobrazí v nabídce Nastavení testu a můžete jej vybrat nebo zrušit. Po výběru souboru s příponou .runsettings použije při každém použití **analyzovat pokrytí kódu**.  
  
### <a name="to-customize-run-settings-in-a-command-line-test"></a>Přizpůsobení parametrů spuštění v testu příkazového řádku  
 Pro spuštění testů z příkazového řádku se používá příkaz vstest.console.exe. Soubor nastavení je parametr tohoto nástroje. Další informace najdete v tématu [použití konzole VSTest.console z příkazového řádku](http://msdn.microsoft.com/library/852812d8-b3bb-407e-bc43-04d511fcb27a).  
  
1.  Spusťte příkazový řádek pro vývojáře v sadě Visual Studio:  
  
     Na Windows **Start**, zvolte **všechny programy**, **sady Microsoft Visual Studio**, **Visual Studio Tools**, **pro vývojáře Příkazový řádek**.  
  
2.  Spusťte:  
  
     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage /Settings:CodeCoverage.runsettings`  
  
### <a name="to-customize-run-settings-in-a-build-definition"></a>Přizpůsobení parametrů spuštění v definici sestavení  
 Data pokrytí kódu můžete získat ze sestavení týmu.  
  
 ![Určení runsettings v definici sestavení](../test/media/codecoverage-buildrunsettings.png "CodeCoverage buildRunsettings")  
  
1. Zkontrolujte, zda byl soubor s příponou .runsettings vrácen se změnami.  
  
2. V Průzkumníku týmových projektů otevřete **sestavení**a poté přidejte nebo upravte definici sestavení.  
  
3. Na **procesu** stránce, rozbalte **automatizované testy**, **zdroj testu**, **parametrů běhu**. Vyberte vaše **s příponou .runsettings** souboru.  
  
   - <em>Ale **sestavení testu</em>* se zobrazí místo **zdroj testu**. Při pokusu o nastavení **parametrů běhu** pole, lze vybrat pouze soubory .testsettings.*  
  
      V části **automatizované testy**vyberte **sestavení testu**a zvolte **[...]**  na konci řádku. V **přidat/upravit testovací běh** dialogové okno, nastavte **nástroj Test Runner** k **Visual Studio Test Runner**.  
  
   Výsledky jsou zobrazeny v souhrnné části zprávy o sestavení.  
  
##  <a name="sample"></a> Ukázkový soubor s příponou .runsettings  
 Zkopírujte tento kód a upravte jej podle svých potřeb. Toto je výchozí soubor s příponou .runsettings.  
  
 (Pro jiné účely soubor s příponou .runsettings naleznete v tématu [konfigurace testů jednotek s použitím souboru .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).)  
  
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
Each element in the list is a regular expression (ECMAScript syntax). See http://msdn.microsoft.com/library/2k3te2cs.aspx.  
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
                <!—Don't forget "Attribute" at the end of the name -->  
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
  
## <a name="see-also"></a>Viz také  
 [Použití pokrytí kódu k určení jak mnohem kódu je testována](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)   
 [Testování částí kódu](../test/unit-test-your-code.md)



