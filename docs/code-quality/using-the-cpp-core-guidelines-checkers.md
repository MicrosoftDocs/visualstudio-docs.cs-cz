---
title: Pomocí podle dokumentu C++ Core Guidelines šachovnice
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 6595e8990dece15e88e07a6c8eefabd3f543bbb7
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143460"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Pomocí podle dokumentu C++ Core Guidelines šachovnice
Podle dokumentu C++ Core Guidelines jsou přenosná sadu pokynů, pravidla a osvědčenými postupy psaní kódu v jazyce C++ vytvořených odborníky C++ a návrháři. Visual Studio aktuálně podporuje podmnožinu těchto pravidel jako součást své nástroje analýzy kódu pro jazyk C++. Tyto moduly pro kontrolu příručka core jsou nainstalované ve výchozím nastavení v sadě Visual Studio 2017 a jsou [k dispozici jako balíček NuGet pro Visual Studio 2015](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Projekt C++ Core Guidelines
 Podle dokumentu C++ Core Guidelines vytvořeného Bjarne Stroustrup a jinými uživateli, jsou návod k použití moderním jazyce C++, bezpečně a efektivně. Pokyny zvýraznit statického typu bezpečnosti a bezpečný přístup z více zdrojů. Najít způsoby, jak vyloučit nebo minimalizovat nejvíce náchylné částí jazyk a navrhnout jak byl kód jednodušší a výkonnější spolehlivě. Tyto pokyny jsou udržovány základ standardu C++. Další informace najdete v dokumentaci, [podle dokumentu C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)a přístup k souborům projektu podle dokumentu C++ Core Guidelines dokumentaci na [Githubu](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Povolit C++ Core Check pravidla analýzy kódu
 Můžete povolit analýzu kódu na projektu tak, že vyberete **povolit analýzu kódu na sestavení** zaškrtávací políčko ve **analýzy kódu** část **stránky vlastností** dialogové okno pro váš projekt.

 ![Stránka vlastností pro nastavení obecné analýzy kódu](media/cppcorecheck_codeanalysis_general.png)

 Podmnožina pravidel C++ Core Check je zahrnuta v sadě Microsoft nativní doporučená pravidla, na kterém běží ve výchozím nastavení při zapnuté funkci analýzy kódu. Povolit další pravidla Core Check, klikněte na rozevírací seznam a zvolte který sady pravidel, které chcete zahrnout:

 ![Rozevírací seznam pro další sady pravidel C++ Core Check](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Příklady
 Tady je příklad některých problémech, které můžete najít C++ Core Check pravidla:

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

Tento příklad ukazuje několik upozornění, která pravidla C++ Core Check najdete:

- C26494 je pravidlo Type.5: objekt vždy inicializujte.

- C26485 je pravidlo Bounds.3: žádné decay pole na ukazatel.

- C26481 je pravidlo Bounds.1: Nepoužívejte aritmetiku ukazatele. Místo nich se používá `span`.

Pokud je nainstalované a povolené při kompilaci tohoto kódu, jsou první dva upozornění výstup, ale je potlačeno třetí pravidel C++ Core Check analýzy kódu. Zde je výstup sestavení z ukázkového kódu:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Podle dokumentu C++ Core Guidelines existují k pomoci psát lepší a bezpečnější kódu. Pokud máte instanci, kde by neměl použít pravidlo, nebo profil, je však snadné potlačit přímo v kódu. Můžete použít `gsl::suppress` atribut zabránit C++ Core Check zjišťování a vytváření sestav nedodržení pravidla v následující bloku kódu. Můžete označit jednotlivé příkazy můžete potlačit specifická pravidla. Můžete dokonce potlačit celý profil napsáním `[[gsl::suppress(bounds)]]` bez zahrnutí příslušné pravidlo číslo.

## <a name="supported-rule-sets"></a>Podporované sady pravidel
Nová pravidla přidávání na kontrola C++ Core pokyny, kdykoliv zvýšit počet upozornění, které jsou vytvářeny pro již existující kód. Sady předdefinovaných pravidel můžete použít k filtrování, které druhy pravidla povolit.
Referenční témata pro většinu pravidel jsou v rámci [Visual Studio C++ Core zkontrolujte Reference](code-analysis-for-cpp-corecheck.md).

Od verze Visual Studio 2017 verze 15.3 sady podporované pravidel jsou:
- **– Pravidla ukazatelů vlastníka** vynutit [kontroly správy prostředků související s owner<T> podle dokumentu C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **– Pravidla konstant** vynutit [kontroly podle dokumentu C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **– Pravidla nezpracovaných ukazatelů** vynutit [kontroly správy prostředků související s nezpracovaných ukazatelů podle dokumentu C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **– Pravidla jedinečných ukazatelů** vynutit [kontroly správy prostředků související s typy se sémantikou jedinečných ukazatelů podle dokumentu C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **– Pravidla vazeb** vynutit [vazeb profil podle dokumentu C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Zadejte pravidla** vynutit [zadejte profil podle dokumentu C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Visual Studio 2017 verze 15.5**:

- **Třída pravidla** několik pravidel, která se soustřeďují na správné použití operátoru zvláštní členské funkce a virtuální specifikací. Toto je podmnožinou kontroly doporučuje pro [třídy a třídy hierarchie](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **– Pravidla souběžnosti** jediné pravidlo, které zachytí objekty chybně deklarované ochrany. Další informace najdete v tématu [pokyny související se souběžností](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Pravidla deklarace** několik pravidel z [rozhraní pokyny](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) ty se zaměřují na tom, jak globální proměnné jsou deklarovány.
- **Funkce pravidla** dvě kontroly, které pomáhají s přijetí `noexcept` specifikátor. Toto je část pokyny pro [vymazat funkce návrhu a implementace](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **– Pravidla sdílených ukazatelů** jako součást [správy prostředků](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) pokyny k vynucení, přidali jsme několik pravidel, které jsou specifické pro zobrazení sdílených ukazatelů jsou předány do funkcí nebo používané lokálně.
- **Pravidla stylu** jeden jednoduchý, ale důležité zaškrtnutí, která zakáže použití [goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Toto je prvním krokem při vylepšování kódování styl a používat výrazy a příkazy v jazyce C++.

**Visual Studio 2017 verze 15.6**:

- **Aritmetické pravidla** pravidla, která zjistí aritmetický [přetečení](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [podepsané bez znaménka operace](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) a [bit manipulaci s](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Můžete omezit upozornění jenom v jednom nebo několika skupin. **Nativní minimální** a **nativní doporučená** pravidlo sady zahrnují C++ Core Check pravidla kromě jiných PREfast kontroly. Pokud chcete zobrazit dostupné sady pravidel, otevřete dialogové okno Vlastnosti projektu, vyberte **kód Analysis\General**, otevřete rozevírací seznam v **sad pravidel** pole se seznamem a výběru **zvolte více sad pravidel** . Další informace o použití sad pravidel v sadě Visual Studio najdete v tématu [pomocí sad pravidel k seskupování pravidel analýzy kódu](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makra

Kontrola C++ Core pokyny obsahuje soubor hlaviček, který definuje makra, které usnadňují potlačit celé kategorie upozornění v kódu:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Tato makra odpovídají sady pravidel a rozšířit místo oddělený seznam čísel upozornění. Pomocí konstrukce odpovídající – Direktiva pragma, můžete nakonfigurovat efektivní sadu pravidel, která je zajímavé pro projekt nebo části kódu. V následujícím příkladu analýza kódu upozorňuje pouze konstantní modifikátory chybí:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Atributy

Kompilátor jazyka Microsoft Visual C++ má omezenou podporu pro GSL potlačení atributu. Slouží k potlačení upozornění na výrazu a příkazy bloku uvnitř funkce.

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

## <a name="suppressing-analysis-by-using-command-line-options"></a>Potlačení analýzy pomocí možnosti příkazového řádku

Místo #pragmas vám pomůže možnosti příkazového řádku na stránce vlastností v souboru potlačení upozornění pro projekt nebo jeden soubor. Například toto upozornění zakážete 26400 pro soubor:

1. Klikněte pravým tlačítkem na soubor v **Průzkumníka řešení**

2. Zvolte **vlastnosti | C / C ++ | Příkazový řádek**

3. V **další možnosti** okně Přidat `/wd26400`.

Možnost příkazového řádku můžete dočasně zakázat všechny analýzy kódu pro soubor tak, že zadáte `/analyze-`. Tím dojde k upozornění *D9025 přepsání parametr / analyze' pomocí "/ analyze-"*, která upozorní, chcete-li znovu povolit analýzu kódu.

## <a name="corecheck_per_file"></a> Povolení kontrola C++ Core pokyny na konkrétní projektových souborů

V některých případech může být užitečné pro analýzu kódu do, zaměřuje a stále použití integrovaného vývojového prostředí sady Visual Studio. Následující ukázkový scénář lze použít pro velké projekty, můžete ušetřit čas sestavení a aby bylo snazší, abyste vyfiltrovali výsledky:

1. V příkazovém prostředí služby nastaven `esp.extension` a `esp.annotationbuildlevel` proměnné prostředí.
2. Dědí tyto proměnné, spusťte Visual Studio z příkazového řádku.
3. Načtení projektu a otevřete její vlastnosti.
4. Povolit analýzu kódu, vyberte příslušné pravidlo sady, ale není doporučeno zapínat rozšířeními pro analýzu kódu.
5. Přejděte k souboru, který chcete analyzovat pomocí kontrola C++ Core pokyny a otevřete její vlastnosti.
6. Zvolte **C / C ++ \Command možnosti řádku** a přidat `/analyze:plugin EspXEngine.dll`
7. Zakázat použití předkompilované hlavičky (**C / C ++ \Precompiled záhlaví**). To je nezbytné, protože modul rozšíření můžou snažit přečíst jeho interních informací z předkompilované hlavičky (PCH); Pokud soubor PCH zkompilován s výchozími možnostmi projektu, nebudou kompatibilní.
8. Sestavte projekt znovu. Běžné PREFast kontroly by měl spustit na všechny soubory. Protože kontrola C++ Core pokyny není povolená ve výchozím nastavení, by měl spustit pouze v souboru, který je konfigurován pro použití.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Jak používat nástroj pro kontrolu jádra pokyny C++ mimo sadu Visual Studio

Kontrola C++ Core Guidelines můžete použít v automatizovaných sestaveních.

### <a name="msbuild"></a>MSBuild
 Nástroj pro kontrolu nativní analýzu kódu (nástroj PREfast) je integrované do prostředí nástroje MSBuild soubory vlastní cíle. Můžete použít vlastnosti projektu, aby je a přidat kontrola C++ Core pokyny, (která je založena na nástroj PREfast):

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Ujistěte se, že přidáte tyto vlastnosti před importem souboru Microsoft.Cpp.targets. Můžete vybrat konkrétní pravidlo sady nebo vytvořit vlastní sady pravidel nebo použít výchozí sadu pravidel, která obsahuje další PREfast kontroly.

Nástroje C++ Core Checker lze použít pouze v zadané soubory s využitím stejným způsobem jako [bylo popsáno dříve](#corecheck_per_file), ale pomocí nástroje MSBuild souborů. Proměnné prostředí můžete nastavit pomocí `BuildMacro` položky:

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

Pokud nechcete úpravu souboru projektu, můžete předat vlastnosti na příkazovém řádku:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Projekty MSBuild bez

Pokud používáte systém sestavení, který se nemusí spoléhat na MSBuild můžete spustit nástroj pro kontrolu, ale potřebujete, abyste věděli některé interní informace z konfigurace modulu analýzy kódu. Tyto interní informace nemusí podporovat v budoucnu.

Budete muset nastavit pár proměnné prostředí a použijte vhodné možnosti příkazového řádku pro kompilátor. Je lepší práce v části "Native Tools Command Prompt" prostředí, takže nemusíte hledat konkrétní cesty pro kompilátor, zahrnout adresáře atd.

1. **Proměnné prostředí**
   - `set esp.extensions=cppcorecheck.dll` To říká modul načíst modul podle dokumentu C++ Core Guidelines.
   - `set esp.annotationbuildlevel=ignore` Zakáže logiku, která zpracovává poznámky SAL. Poznámky nemají vliv na analýzu kódu v kontrola C++ Core pokyny, ale jejich zpracování trvá určitou dobu (v některých případech dlouhý čas). Toto nastavení je volitelné, ale důrazně ho doporučujeme.
   - `set caexcludepath=%include%` Důrazně doporučujeme zakázat varování, které na standardní záhlaví. Můžete přidat další cesty, třeba cestu k společné hlavičky ve vašem projektu.
2. **Možnosti příkazového řádku**
   - `/analyze`  Povolí analýzu kódu (zvažte také použití / analyze: pouze a / analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` Tato možnost načte modul rozšířeními pro analýzu kódu do nástroje PREfast. Tento modul, pak načte kontrola C++ Core pokyny.

## <a name="use-the-guideline-support-library"></a>Použití podpory knihovny obecných zásad
 Obecné zásady Support Library usnadňuje postupujte podle pokynů na jádro. GSL obsahuje definice, které umožňují náchylné konstrukce nahraďte bezpečnějších alternativ. Například můžete nahradit `T*, length` dvojice parametrů s `span<T>` typu. Je k dispozici na GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Knihovna je open source, můžete zobrazit zdroje, ujistěte se, komentáře nebo přispívat. Projekt lze nalézt v [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a> Postupujte podle pokynů C++ Core Check v projektech Visual Studio 2015

Pokud používáte Visual Studio 2015, se ve výchozím nastavení nenainstalují sad pravidel analýzy kódu C++ Core Check. Je nutné provést některé další kroky předtím, než můžete povolit C++ Core Check nástroje Analýza kódu v sadě Visual Studio 2015. Microsoft poskytuje podporu pro projekty Visual Studio 2015 s použitím balíčku Nuget. Balíček má název Microsoft.CppCoreCheck a je k dispozici na [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Tento balíček vyžaduje, že abyste měli aspoň nainstalovanou sadu Visual Studio 2015 s aktualizací Update 1.

Tento balíček nainstaluje taky jiný balíček jako závislost, pouze záhlaví obecné zásady podpory knihovny (GSL). GSL je také k dispozici na Githubu v [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

Kvůli způsobu, jakým jsou načteny pravidel analýzy kódu musíte nainstalovat balíček Microsoft.CppCoreCheck NuGet do jednotlivých projektů C++, který chcete zkontrolovat v rámci sady Visual Studio 2015.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Chcete-li přidat balíček Microsoft.CppCoreCheck do projektu v sadě Visual Studio 2015

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem a otevřete místní nabídku projektu v řešení, které chcete přidat balíček. Zvolte **spravovat balíčky NuGet** otevřít **Správce balíčků NuGet**.

2. V **Správce balíčků NuGet** okna, vyhledejte Microsoft.CppCoreCheck.

    ![Okno Správce balíčků Nuget zobrazuje balíček CppCoreCheck](../code-quality/media/cppcorecheck_nuget_window.png)

3. Vyberte balíček Microsoft.CppCoreCheck a pak klikněte **nainstalovat** tlačítko pro přidání pravidel do projektu.

   Balíček NuGet přidá další MSBuild *.targets* souboru projektu, která je volána, když povolit analýzu kódu na projektu. To *.targets* přidá soubor pravidel C++ Core Check jako další rozšíření pro nástroj pro analýzu kódu sady Visual Studio. Pokud je balíček nainstalován, můžete použít dialogové okno stránky vlastností k povolení nebo zakázání pravidla bylo uvolněno a experimentální.

## <a name="see-also"></a>Viz také

- [Odkaz Kontrola C++ Core sady Visual Studio](code-analysis-for-cpp-corecheck.md)