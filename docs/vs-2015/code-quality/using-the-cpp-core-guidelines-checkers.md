---
title: Použití hlavních C++ pokynů pro kontrolu | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 946b46bfb5101154832e10b61cd861b0c104dc14
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275297"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Použití kontrolních mechanismů C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Základní pokyny jsou přenosné sady pokynů, pravidel a osvědčených postupů pro kódování, které C++ C++ vytváří odborníci a návrháři.  Visual Studio teď podporuje balíčky doplňků, které vytvářejí další pravidla pro nástroje pro analýzu kódu, aby kontrolovaly dodržování C++ základních pokynů a navrhovat vylepšení.  
  
## <a name="the-c-core-guidelines-project"></a>C++ Základní projektové směrnice  
 C++ Základní pokyny, které vytvořila aplikace Bjarne Stroustrup a další, jsou návodem k C++ používání moderního a efektivního použití. Pokyny zdůrazňují zabezpečení statického typu a bezpečnost prostředků. Identifikují způsoby, jak eliminovat nebo minimalizovat největší možné části kódu náchylné k chybám, a navrhnout, jak zjednodušit a zajistit jednodušší a spolehlivější způsob provádění. Tyto pokyny jsou spravovány standardem C++ Foundation. Další informace najdete v dokumentaci, [ C++ základních pokynech](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)a v C++ dokumentaci k základním pokynům dokumentace k souborům projektu na [GitHubu](https://github.com/isocpp/CppCoreGuidelines).  
  
 Společnost Microsoft podporuje C++ základní pokyny při vytváření C++ základních kontrolních sad pravidel analýzy kódu, které můžete přidat do svých projektů pomocí balíčku NuGet. Balíček má název Microsoft. CppCoreCheck a je k dispozici na adrese [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Tento balíček vyžaduje aspoň sadu Visual Studio 2015 s nainstalovanou aktualizací Update 1.  
  
 Balíček také nainstaluje jiný balíček jako závislost, a to pouze v případě, že je k disřádku podpůrná knihovna zásad (GSL). GSL je také k dispozici na GitHubu na adrese [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Povolit C++ základní kontrolní pokyny při analýze kódu  
 Chcete-li C++ povolit nástroje pro analýzu kódu základní kontroly, nainstalujte balíček NuGet Microsoft. CppCoreCheck do C++ každého projektu, který chcete kontrolovat v rámci sady Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Přidání balíčku Microsoft. CppCoreCheck do projektu  
  
1. V **Průzkumník řešení**kliknutím pravým tlačítkem otevřete místní nabídku projektu v řešení, do kterého chcete balíček přidat. Zvolením **možnosti spravovat balíčky NuGet** otevřete **Správce balíčků NuGet**.  
  
2. V okně **Správce balíčků NuGet** vyhledejte Microsoft. CppCoreCheck.  
  
    ![Okno Správce balíčků NuGet zobrazuje balíček CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Vyberte balíček Microsoft. CppCoreCheck a pak kliknutím na tlačítko **nainstalovat** přidejte pravidla do projektu.  
  
   Balíček NuGet přidá další soubor MSBuild. targets do projektu, který je vyvolán při povolení analýzy kódu v projektu. Tento soubor. targets přidá C++ pravidla základní kontroly jako další rozšíření nástroje Visual Studio Code Analysis Tool.  
  
   Můžete povolit analýzu kódu v projektu zaškrtnutím políčka **Povolit analýzu kódu při sestavení** v části **Analýza kódu** dialogového okna **stránky vlastností** projektu.  
  
   ![Stránka vlastností pro obecné nastavení analýzy kódu](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Základní pravidla kontroly se stanou součástí výchozích sad pravidel, které jsou spuštěny, když je povolena analýza kódu. Vzhledem k C++ tomu, že základní pravidla kontrol jsou ve vývoji, některá pravidla nemusí být připravená na použití na veškerý kód, ale můžou být během vývoje informativní. Tato pravidla jsou vydaná jako experimentální. Můžete zvolit, zda chcete spustit vydaná nebo experimentální pravidla ve vlastnostech projektu.  
  
   ![Stránka vlastností pro nastavení rozšíření analýzy kódu](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Chcete-li povolit nebo C++ zakázat sadu pravidel kontroly základní kontroly, otevřete dialogové okno **stránky vlastností** projektu. V části **Vlastnosti konfigurace**rozbalte položku **Analýza kódu**, **rozšíření**. V ovládacím prvku rozevíracího seznamu **vedle C++ možnosti Povolit základní kontrolu (vydaná)** nebo **Povolit C++ základní kontrolu (experimentální)** vyberte **Ano** nebo **ne**. Změny uložte kliknutím na **OK** nebo **použít** .  
  
## <a name="check-types-bounds-and-lifetimes"></a>Kontroly typů, vazeb a životností  
 Balíček C++ Core check nyní obsahuje kontrolu [zabezpečení typů](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [zabezpečení hranic](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)a profily [zabezpečení životního cyklu](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Tady je příklad druhu problémů, které pravidla kontroly C++ jádra můžou najít:  
  
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
  
- C26481 je rozsahy pravidel. 1: Nepoužívejte aritmetický ukazatel. Místo toho použijte `span`.  
  
  Pokud je C++ při kompilování tohoto kódu nainstalována a povolená základní analýza kódu RuleSets, první dvě upozornění jsou výstup, ale třetí se potlačí. Zde je výstup sestavení z příkladu kódu:  
  
**1 >------sestavení bylo zahájeno: projekt: CoreCheckExample, konfigurace: ladění Win32--**  
**----**  
**1 > CoreCheckExample. cpp**  
**1 > CoreCheckExample. vcxproj – > C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample. vcxproj – > C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (úplný soubor PDB)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): upozornění C26494: Proměnná ' ARR ' je uninitializ**  
**Ed. vždy Inicializujte objekt. (typ. 5: https://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): upozornění C26485: výraz ' ARR ': žádné pole**  
**ukazatel Decay. (Bounds. 3: https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = = **Sestavení: 1 úspěšné, 0 selhalo, 0-k datu, 0 přeskočeno = =** = = = = = = = = C++ Základní pokyny jsou tam, kde vám pomůžou psát lepší a bezpečnější kód. Pokud však máte instanci, kde pravidlo nebo profil nepoužijete, je snadné ho potlačit přímo v kódu. Atribut `gsl::suppress` lze použít k zajištění C++ , že základní kontrolu před detekcí a vykazováním jakéhokoliv porušení pravidla v následujícím bloku kódu. Jednotlivé příkazy můžete označit pro potlačení specifických pravidel. Můžete dokonce potlačit celý profil s mezemi, a to tak, že zapíšete `[[gsl::suppress(bounds)]]` bez zahrnutí konkrétního čísla pravidla.  
  
## <a name="use-the-guideline-support-library"></a>Použití knihovny podpory zásad  
 Balíček NuGet Microsoft. CppCoreCheck nainstaluje také balíček, který obsahuje implementaci knihovny Support (GSL) od Microsoftu. GSL je také k dispozici v samostatné podobě na [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). Tato knihovna je užitečná, pokud chcete postupovat podle základních pokynů. GSL obsahuje definice, které umožňují nahradit konstrukce náchylné k chybám s bezpečnějšími alternativami. Můžete například nahradit dvojici `T*, length` parametrů s typem `span<T>`. GSL je open source, takže pokud se chcete podívat na zdroje knihovny, komentáře nebo Contribute, projekt najdete na adrese [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).
