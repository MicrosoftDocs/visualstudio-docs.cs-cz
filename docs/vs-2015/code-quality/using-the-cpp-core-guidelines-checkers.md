---
title: Pomocí tyto moduly pro kontrolu podle dokumentu C++ Core Guidelines | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1153f7a32c26946fafb1230699c4afcae976cd9e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799558"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Pomocí podle dokumentu C++ Core Guidelines šachovnice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podle dokumentu C++ Core Guidelines jsou přenosná sadu pokynů, pravidla a osvědčenými postupy psaní kódu v jazyce C++ vytvořených odborníky C++ a návrháři.  Visual Studio teď podporuje balíčky, které nástroji pro analýzu kódu pro dodržování předpisů s podle dokumentu C++ Core Guidelines zkontrolujte a navrhněte vylepšení vytvořit další pravidla pro kód.  
  
## <a name="the-c-core-guidelines-project"></a>Projekt C++ Core Guidelines  
 Podle dokumentu C++ Core Guidelines vytvořeného Bjarne Stroustrup a jinými uživateli, jsou návod k použití moderním jazyce C++, bezpečně a efektivně. Pokyny zvýraznit statického typu bezpečnosti a bezpečný přístup z více zdrojů. Najít způsoby, jak vyloučit nebo minimalizovat nejvíce náchylné částí jazyk a navrhnout jak byl kód jednodušší a výkonnější spolehlivě. Tyto pokyny jsou udržovány základ standardu C++. Další informace najdete v dokumentaci, [podle dokumentu C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)a přístup k souborům projektu podle dokumentu C++ Core Guidelines dokumentaci na [Githubu](https://github.com/isocpp/CppCoreGuidelines).  
  
 Společnost Microsoft podporuje úsilí podle dokumentu C++ Core Guidelines tím, že C++ Core Check sad pravidel analýzy kódu, můžete přidat do vašich projektů pomocí balíčku Nuget. Balíček má název Microsoft.CppCoreCheck a je k dispozici na [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Tento balíček vyžaduje, že abyste měli aspoň nainstalovanou sadu Visual Studio 2015 s aktualizací Update 1.  
  
 Tento balíček nainstaluje taky jiný balíček jako závislost, pouze záhlaví obecné zásady podpory knihovny (GSL). GSL je také k dispozici na Githubu v [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Povolit C++ Core Check pravidla analýzy kódu  
 Pokud chcete povolit nástroji pro analýzu kódu C++ Core Check, nainstalujte balíček Microsoft.CppCoreCheck NuGet do jednotlivých projektů C++, který chcete zkontrolovat v sadě Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Chcete-li přidat balíček Microsoft.CppCoreCheck do projektu  
  
1. V **Průzkumníka řešení**, klikněte pravým tlačítkem a otevřete místní nabídku projektu v řešení, které chcete přidat balíček. Zvolte **spravovat balíčky NuGet** otevřít **Správce balíčků NuGet**.  
  
2. V **Správce balíčků NuGet** okna, vyhledejte Microsoft.CppCoreCheck.  
  
    ![Okno Správce balíčků Nuget zobrazuje CppCoreCheck balíčku](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Vyberte balíček Microsoft.CppCoreCheck a pak klikněte **nainstalovat** tlačítko pro přidání pravidel do projektu.  
  
   Balíček NuGet dalšího souboru .targets MSBuild přidá do projektu, která je volána, když povolit analýzu kódu na projektu. Tento soubor .targets přidá pravidel C++ Core Check jako další rozšíření pro nástroj pro analýzu kódu sady Visual Studio.  
  
   Můžete povolit analýzu kódu na projektu tak, že vyberete **povolit analýzu kódu na sestavení** zaškrtávací políčko ve **analýzy kódu** část **stránky vlastností** dialogové okno pro váš projekt.  
  
   ![Stránka vlastností pro nastavení obecné analýzy kódu](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Core Check pravidla se stanou součástí výchozí sady pravidel, které spustit, když je povolena analýza kódu. Vzhledem k tomu pravidel C++ Core Check ve vývoji, některá pravidla nemusí být připraven k použití na veškerý kód, ale může být informativní během vývoje. Tato pravidla jsou všeobecně dostupné jako experimentální. Můžete zvolit, jestli se má spustit vydané nebo experimentální pravidla ve vlastnostech projektu.  
  
   ![Stránka vlastností pro nastavení rozšířeními pro analýzu kódu](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Chcete-li povolit nebo zakázat sady pravidel C++ Core Check, otevřete **stránky vlastností** dialogové okno pro váš projekt. V části **vlastnosti konfigurace**, rozbalte **analýzy kódu**, **rozšíření**. V rozevíracím seznamu řízení vedle **povolit C++ Core Check (vydání)** nebo **povolit C++ Core Check (experimentální)**, zvolte **Ano** nebo **ne**. Zvolte **OK** nebo **použít** uložte provedené změny.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Zkontrolujte typy, hranice a životnosti  
 C++ Core Check balíček nyní obsahuje tyto moduly pro kontrolu pro [bezpečnost typů](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [vazeb bezpečnosti](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), a [životnost bezpečnosti](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) profily.  
  
 Tady je příklad takového typu, problémů, které můžete najít C++ Core Check pravidla:  
  
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
  
  **1 >---Sestavení začalo: projekt: CoreCheckExample, konfigurace: ladění Win32--**  
**----**  
**1 > CoreCheckExample.cpp**  
**1 > CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (úplný soubor PDB)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): upozornění C26494: uninitializ je proměnná "směrování žádostí na aplikace.**  
**vydání bude vždy inicializovat objekt. (type.5: http://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): upozornění C26485: výraz "směrování žádostí na aplikace": rozklad pole na**  
 **decay ukazatele. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**=== Sestavení: 1 úspěšné, 0 selhalo, 0 aktuálních, 0 vynecháno ===** The C++ Core Guidelines existují k pomoci psát lepší a bezpečnější kódu. Pokud máte instanci, kde by neměl použít pravidlo, nebo profil, je však snadné potlačit přímo v kódu. Můžete použít `gsl::suppress` atribut zabránit C++ Core Check zjišťování a vytváření sestav nedodržení pravidla v následující bloku kódu. Můžete označit jednotlivé příkazy můžete potlačit specifická pravidla. Můžete dokonce potlačit celý profil napsáním `[[gsl::suppress(bounds)]]` bez zahrnutí příslušné pravidlo číslo.  
  
## <a name="use-the-guideline-support-library"></a>Použití podpory knihovny obecných zásad  
 Balíček Microsoft.CppCoreCheck NuGet také nainstaluje balíček, který obsahuje implementaci společnosti Microsoft o podporu knihovny obecných zásad (GSL). Je také k dispozici v podobě samostatné na GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Tato knihovna je užitečné, pokud chcete postupovat podle pokynů Core. GSL obsahuje definice, které umožňují náchylné konstrukce nahraďte bezpečnějších alternativ. Například můžete nahradit `T*, length` dvojice parametrů s `span<T>` typu. GSL je open source, takže pokud se chcete podívat na komentář zdroje knihovny, nebo přispívat, projektu lze nalézt v [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).



