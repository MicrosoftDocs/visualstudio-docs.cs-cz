---
title: Použití kontrolních mechanismů C++ Core Guidelines
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
dev_langs:
- CPP
ms.openlocfilehash: 762ba639c1443bb737087233d04c9e3753f2f455
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807082"
---
# <a name="use-the-c-core-guidelines-checkers"></a>Použití kontrolních mechanismů C++ Core Guidelines

C++ Základní pokyny jsou přenosné sady pokynů, pravidel a osvědčených postupů pro kódování, které C++ C++ vytváří odborníci a návrháři. Sada Visual Studio aktuálně podporuje podmnožinu těchto pravidel jako součást nástrojů pro analýzu kódu pro C++. Základní kontrolní prvky jsou nainstalovány ve výchozím nastavení v aplikaci Visual Studio 2017 a Visual Studio 2019 a jsou [k dispozici jako balíček NuGet pro sadu Visual studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>C++ Základní projektové směrnice

C++ Základní pokyny, které vytvořila aplikace Bjarne Stroustrup a další, jsou návodem k C++ používání moderního a efektivního použití. Pokyny zdůrazňují zabezpečení statického typu a bezpečnost prostředků. Identifikují způsoby, jak eliminovat nebo minimalizovat největší možné části kódu náchylné k chybám, a navrhnout, jak zjednodušit a zajistit jednodušší a spolehlivější způsob provádění. Tyto pokyny jsou spravovány standardem C++ Foundation. Další informace najdete v dokumentaci, [ C++ základních pokynech](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)a v C++ dokumentaci k základním pokynům dokumentace k souborům projektu na [GitHubu](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Povolit C++ základní kontrolní pokyny při analýze kódu
Můžete povolit analýzu kódu v projektu zaškrtnutím políčka **Povolit analýzu kódu při sestavení** v části **Analýza kódu** dialogového okna **stránky vlastností** projektu.

![Stránka vlastností pro obecné nastavení analýzy kódu](media/cppcorecheck_codeanalysis_general.png)

Podmnožina C++ základních pravidel kontroly je obsažena v nativní Doporučené sadě pravidel společnosti Microsoft, která je ve výchozím nastavení spuštěna, pokud je povolena analýza kódu. Pokud chcete povolit další základní pravidla kontroly, klikněte na rozevírací seznam a vyberte, které sady pravidel chcete zahrnout:

![Rozevírací seznam pro C++ další sady pravidel základní kontroly](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Příklady
Tady je příklad některých problémů, které pravidla kontroly C++ jádra můžou najít:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

Tento příklad ukazuje několik upozornění, která mohou C++ základní pravidla kontroly najít:

- C26494 je typ pravidla. 5: vždy Inicializujte objekt.

- C26485 je vázáno na pravidlo. 3: žádné Decay pole na ukazatel.

- C26481 je rozsahy pravidel. 1: Nepoužívejte aritmetický ukazatel. Místo nich se používá `span`.

Pokud je C++ při kompilování tohoto kódu nainstalována a povolená základní analýza kódu RuleSets, první dvě upozornění jsou výstup, ale třetí se potlačí. Zde je výstup sestavení z příkladu kódu:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

C++ Základní pokyny jsou tam, kde vám pomůžou psát lepší a bezpečnější kód. Pokud však máte instanci, kde pravidlo nebo profil nepoužijete, je snadné ho potlačit přímo v kódu. Můžete použít atribut `gsl::suppress`, chcete-li C++ , aby základní kontroly zjistily a nahlášeny jakékoli porušení pravidla v následujícím bloku kódu. Jednotlivé příkazy můžete označit pro potlačení specifických pravidel. Můžete dokonce potlačit celý profil s mezemi, a to tak, že zapíšete `[[gsl::suppress(bounds)]]` bez zahrnutí konkrétního čísla pravidla.

## <a name="supported-rule-sets"></a>Podporované sady pravidel
Při přidání nových pravidel do nástroje pro C++ kontrolu základních pokynů se může zvýšit počet upozornění vytvořených pro stávající kód. Předdefinované sady pravidel můžete použít k filtrování, které typy pravidel se mají povolit.
Referenční témata pro většinu pravidel najdete v části [základní C++ informace o kontrole sady Visual Studio](code-analysis-for-cpp-corecheck.md).

Od verze Visual Studio 2017 verze 15,3 jsou podporované sady pravidel:
- **Pravidla ukazatele vlastníka** vynutila [kontroly správy prostředků související s vlastníkem\<t > v C++ základních pokynech](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Konstantní pravidla** vynutila [kontroly související s const podle C++ základních pokynů](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **Pravidla nezpracovaných ukazatelů** vynutila [kontroly správy prostředků související s nezpracovanými ukazateli podle C++ základních pokynů](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Pravidla jedinečných ukazatelů** vynutila [kontroly správy prostředků související s typy se sémantikou jedinečných C++ ukazatelů z hlavních pokynů](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Pravidla vazeb** vynutily [profil mezí C++ základních pokynů](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Pravidla typu** vynutily [profil typu C++ základních pokynů](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Visual Studio 2017 verze 15,5**:

- **Pravidla třídy** Několik pravidel, která se zaměřují na správné používání speciálních členských funkcí a virtuálních specifikací. Toto je podmnožina kontrol doporučených pro [třídy a hierarchie tříd](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **Pravidla souběžnosti** Jediné pravidlo, které zachycuje nesprávně deklarované objekty Guard. Další informace najdete v tématu [pokyny týkající se souběžnosti](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Pravidla deklarace** Několik pravidel z [pokynů rozhraní](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) , které se zaměřují na to, jak jsou deklarovány globální proměnné.
- **Pravidla funkcí** Dvě kontroly, které vám pomůžou s přijetím specifikátoru `noexcept`. Toto je součást pokynů pro [vymazání návrhu a implementace funkcí](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Pravidla sdílených ukazatelů** V rámci vynucování pokynů [pro správu prostředků](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) jsme přidali několik pravidel, která jsou specifická pro to, jak se sdílené ukazatele předávají do funkcí nebo se používají místně.
- **Pravidla stylu** Jedna jednoduchá, ale důležitá kontrolu, která zakazuje používání příkazu [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Toto je první krok při vylepšení stylu kódování a použití výrazů a příkazů v C++.

**Visual Studio 2017 verze 15,6**:

- **Aritmetická pravidla** Pravidla pro detekci aritmetického [přetečení](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [podepsaných a nepodepsaných operací](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) a [manipulace s přenosem](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Můžete omezit upozornění jenom na jednu nebo několik skupin. **Nativní minimální** a **nativní Doporučené** sady pravidel zahrnují C++ kromě dalších předrychlých kontrol i základní pravidla kontroly. Chcete-li zobrazit dostupné sady pravidel, otevřete dialogové okno Vlastnosti projektu, vyberte možnost **Code Analysis\General**, otevřete rozevírací nabídku v poli se seznamem **sady pravidel** a vyberte **možnost zvolit více sad pravidel**. Další informace o použití sad pravidel v sadě Visual Studio najdete v tématu [použití sad pravidel k seskupení pravidel analýzy kódu](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makra

Kontrola C++ základních pokynů se dodává se souborem hlaviček, který definuje makra, která usnadňují potlačení celé kategorie upozornění v kódu:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Tato makra odpovídají sadám pravidel a rozšiřují seznam čísel upozornění oddělených mezerami. Pomocí příslušných konstrukcí pragma můžete nakonfigurovat efektivní sadu pravidel, která jsou zajímavá pro projekt nebo část kódu. V následujícím příkladu analýza kódu upozorňuje pouze na chybějící modifikátory konstant:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atributy

Kompilátor společnosti C++ Microsoft má omezené podpory pro atribut GSL potlačit. Dá se použít k potlačení upozornění na výrazy a příkazy bloku uvnitř funkce.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppress-analysis-by-using-command-line-options"></a>Potlačit analýzu pomocí možností příkazového řádku

Místo #pragmas můžete použít možnosti příkazového řádku na stránce vlastností souboru, chcete-li potlačit upozornění pro projekt nebo jeden soubor. Pokud například chcete zakázat upozornění 26400 pro soubor:

1. Pravým tlačítkem myši klikněte na soubor v **Průzkumník řešení**

2. Zvolit **vlastnosti | C/C++| Příkazový řádek**

3. V okně **Další možnosti** přidejte `/wd26400`.

Pomocí možnosti příkazového řádku můžete dočasně zakázat veškerou analýzu kódu pro soubor zadáním `/analyze-`. Tím dojde k tomu, že upozornění *D9025 Přepisuje "/analyze" pomocí "/analyze-"* , který vás později upozorní na opětovné povolení analýzy kódu.

## <a name="corecheck_per_file"></a>Povolit kontrolu C++ základních pokynů pro konkrétní soubory projektu

V některých případech může být užitečné provádět analýzu kódu a dál používat Visual Studio IDE. Následující vzorový scénář lze použít pro velké projekty pro uložení času sestavení a pro snadnější filtrování výsledků:

1. V příkazovém prostředí nastavte proměnné prostředí `esp.extension` a `esp.annotationbuildlevel`.
2. Chcete-li tyto proměnné zdědit, otevřete aplikaci Visual Studio z příkazového prostředí.
3. Načtěte projekt a otevřete jeho vlastnosti.
4. Povolte analýzu kódu, vyberte příslušné sady pravidel, ale nepovolujte rozšíření pro analýzu kódu.
5. Do souboru, který chcete analyzovat, použijte kontrolu C++ základních pokynů a otevřete jeho vlastnosti.
6. Zvolit **možnostiC++\command čáry** a přidat `/analyze:plugin EspXEngine.dll`
7. Zakázat použití předkompilované hlavičky (**hlavičky C/C++\Precompiled**). To je nezbytné, protože modul rozšíření se může pokusit přečíst své interní informace z předkompilované hlavičky (PCH); Pokud se soubor PCH zkompiluje s výchozími možnostmi projektu, nebude kompatibilní.
8. Znovu sestavte projekt. Společné kontroly před rychlým spuštěním by se měly spouštět na všech souborech. Vzhledem k C++ tomu, že kontrola základních pokynů není ve výchozím nastavení povolená, měla by běžet jenom pro soubor, který je nakonfigurovaný tak, aby ho používal.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Jak používat C++ základní pokyny pro kontrolu mimo Visual Studio

V automatizovaných sestaveních můžete použít C++ základní pokyny kontroly.

### <a name="msbuild"></a>MSBuild
Nástroj pro kontrolu nativních analýz kódu (PREfast) je integrován do prostředí MSBuild pomocí vlastních souborů cílů. K povolení můžete použít vlastnosti projektu a přidat kontrolu C++ základních pokynů (která je založená na předrychlou):

```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Nezapomeňte tyto vlastnosti přidat před importem souboru Microsoft. cpp. targets. Můžete vybrat konkrétní sady pravidel nebo vytvořit vlastní sadu pravidel nebo použít výchozí sadu pravidel, která zahrnuje další kontroly.

C++ Základní kontrolu můžete spustit pouze pro zadané soubory pomocí stejného přístupu, jak je [popsáno výše](#corecheck_per_file), ale pomocí souborů MSBuild. Proměnné prostředí lze nastavit pomocí `BuildMacro` položky:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Pokud nechcete upravovat soubor projektu, můžete předat vlastnosti na příkazovém řádku:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projekty jiné než MSBuild

Použijete-li systém sestavení, který nespoléhá na nástroj MSBuild, můžete přesto spustit kontrolu, ale je nutné se seznámit s některými interními konfiguracemi modulu Code Analysis. V budoucnu není zaručeno, že tyto interní součásti budou podporovány.

Je nutné nastavit několik proměnných prostředí a použít pro kompilátor správné možnosti příkazového řádku. Je lepší pracovat v prostředí "nativní nástroje" příkazového řádku, takže nemusíte hledat konkrétní cesty pro kompilátor, zahrnout adresáře atd.

1. **Proměnné prostředí**
   - `set esp.extensions=cppcorecheck.dll` znamená to, že modul načte C++ základní pokyny.
   - `set esp.annotationbuildlevel=ignore` tím zakážete logiku, která zpracovává poznámky SAL. Poznámky neovlivňují analýzu kódu v nástroji C++ kontrola základních pokynů, jejich zpracování ale trvá čas (někdy dlouhou dobu). Toto nastavení je volitelné, ale důrazně se doporučuje.
   - `set caexcludepath=%include%` důrazně doporučujeme, abyste zakázali upozornění, která se aktivují ve standardních hlavičkách. Sem můžete přidat další cesty, například cestu k běžným hlavičkám v projektu.
2. **Možnosti příkazového řádku**
   - `/analyze` povolí analýzu kódu (Zvažte také použití/analyze: Only a/analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` Tato možnost načte modul rozšíření analýzy kódu do rychlého režimu. Tento modul zase načte základní pokyny pro C++ kontrolu.

## <a name="use-the-guideline-support-library"></a>Použití knihovny podpory zásad
Knihovna podpory směrnic je navržená tak, aby vám pomohla postupovat podle základních pokynů. GSL obsahuje definice, které umožňují nahradit konstrukce náchylné k chybám s bezpečnějšími alternativami. Můžete například nahradit pár parametrů `T*, length` pomocí typu `span<T>`. GSL je k dispozici na adrese [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). Knihovna je open source, takže můžete zobrazit zdroje, vytvářet komentáře nebo přispívat. Projekt najdete na adrese [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a>Použití C++ základních pokynů pro kontrolu v projektech sady Visual Studio 2015

Pokud používáte sadu Visual Studio 2015, není C++ standardně nainstalována sada pravidel analýzy kódu základní kontroly. Než budete moci povolit C++ základní nástroje pro analýzu kódu v aplikaci Visual Studio 2015, je nutné provést některé další kroky. Společnost Microsoft poskytuje podporu pro projekty sady Visual Studio 2015 pomocí balíčku NuGet. Balíček má název Microsoft. CppCoreCheck a je k dispozici na adrese [http://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Tento balíček vyžaduje aspoň sadu Visual Studio 2015 s nainstalovanou aktualizací Update 1.

Balíček také nainstaluje jiný balíček jako závislost, a to pouze v případě, že je k disřádku podpůrná knihovna zásad (GSL). GSL je také k dispozici na GitHubu na adrese [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

Z důvodu způsobu, jakým jsou načtena pravidla analýzy kódu, je nutné nainstalovat balíček NuGet Microsoft. CppCoreCheck do C++ každého projektu, který chcete kontrolovat v rámci sady Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Přidání balíčku Microsoft. CppCoreCheck do projektu v aplikaci Visual Studio 2015

1. V **Průzkumník řešení**kliknutím pravým tlačítkem otevřete místní nabídku projektu v řešení, do kterého chcete balíček přidat. Zvolením **možnosti spravovat balíčky NuGet** otevřete **Správce balíčků NuGet**.

2. V okně **Správce balíčků NuGet** vyhledejte Microsoft. CppCoreCheck.

    ![Okno Správce balíčků NuGet zobrazuje balíček CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Vyberte balíček Microsoft. CppCoreCheck a pak kliknutím na tlačítko **nainstalovat** přidejte pravidla do projektu.

   Balíček NuGet přidá další soubor MSBuild *. targets* do projektu, který je vyvolán při povolení analýzy kódu v projektu. Tento soubor *. targets* přidá C++ pravidla základní kontroly jako další rozšíření nástroje Visual Studio Code Analysis Tool. Po instalaci balíčku můžete použít dialogové okno stránky vlastností k povolení nebo zakázání vydaných a experimentálních pravidel.

## <a name="see-also"></a>Viz také:

- [Základní informace C++ o kontrole sady Visual Studio](code-analysis-for-cpp-corecheck.md)
