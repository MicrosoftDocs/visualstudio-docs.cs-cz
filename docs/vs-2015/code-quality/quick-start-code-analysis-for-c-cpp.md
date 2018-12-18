---
title: 'Rychlý Start: Analýza kódu pro C / C++ | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 56f14abab372a6a6e533675b070d420a4dfc7a5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758197"
---
# <a name="quick-start-code-analysis-for-cc"></a>Rychlé zahájení: Analýza kódu pro C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zlepšit kvalitu vaší aplikace při spuštění analýzy kódu pravidelně na kód jazyka C nebo C++. To může pomoct najít běžné problémy, porušování programovacím vhodné nebo chyb, které je obtížné vyhledat pomocí testování. Upozornění analýzy kódu se liší od kompilátoru chyby a upozornění, protože analýza kódu hledá vzory v konkrétním kódu, které jsou platné, ale přesto vytvořit problémy pro vy nebo ostatní uživatelé, kteří používají váš kód.  
  
## <a name="in-this-topic"></a>V tomto tématu  
  
-   [Konfigurace sady pravidel pro projekt](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
-   [Spuštění analýzy kódu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
-   [Analýza a řešení upozornění analýzy kódu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
-   [Potlačení upozornění analýzy kódu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
-   [Vytváření pracovních položek pro kód upozornění analýzy](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
-   [Vyhledávání a filtrování výsledků analýzy kódu](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
##  <a name="BKMK_ConfigureRuleSets"></a> Konfigurace sady pravidel pro projekt  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro název projektu a klikněte na tlačítko **vlastnosti**.  
  
2.  Následující kroky jsou volitelné:  
  
    1.  V **konfigurace** a **platformy** seznamy, zvolte sestavení konfigurace a cílovou platformu.  
  
    2.  Ve výchozím nastavení analýza kódu sestavu upozornění z kódu, který je automaticky generován externí nástroje. Chcete-li zobrazit upozornění z generovaného kódu, zrušte **potlačit Výsledky generovaného kódu** zaškrtávací políčko.  
  
        > [!NOTE]
        >  Tato možnost není potlačit chyby analýzy kódu a upozornění z generovaného kódu při chyby a upozornění se zobrazí ve formulářích a šablony. Můžete jak zobrazit a spravovat zdrojový kód pro formuláře nebo šablony.  
  
3.  Chcete-li spustit nástroj Analýza kódu pokaždé, když se sestavení projektu použitím vybrané konfigurace, vyberte **povolit analýzu kódu pro C/C++ při sestavení** zaškrtávací políčko. Můžete také spustit analýzu kódu ručně tak, že otevřete **analyzovat** nabídky a následným výběrem možnosti **spustit analýzu kódu na** *ProjectName*.  
  
4.  V **spustit tuto sadu pravidel** seznamu, proveďte jednu z následujících akcí:  
  
    -   Vyberte sadu pravidel, kterou chcete použít.  
  
    -   Zvolte  **\<Procházet... >** zadat sadu existujících vlastních pravidel, která se nenachází v seznamu.  
  
    -   Definujte vlastní sady pravidel.  
  
         Další informace najdete v tématu [vytvoření vlastní sady pravidel](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Sady pravidel standardním C/C++  
 Visual Studio obsahuje dvě standardní sady pravidel pro nativní kód:  
  
|Sada pravidel|Popis|  
|--------------|-----------------|  
|Microsoft nativní Minimální doporučená pravidla|Tato sada pravidel se soustředí na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a selhání aplikace. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše nativní projekty.|  
|Microsoft nativní doporučená pravidla|Tato sada pravidel obsahuje celou řadu problémů. Obsahuje všechna pravidla v Microsoft nativní Minimální doporučená pravidla.|  
  
##  <a name="BKMK_Run"></a> Spuštění analýzy kódu  
 Na stránce analýzy kódu na stránkách vlastností projektu můžete konfigurovat analýzu kódu při každém spuštění sestavení projektu. Analýza kódu můžete spustit také ručně.  
  
 Spuštění analýzy kódu pro řešení:  
  
- Na **sestavení** nabídce zvolte **spustit analýzu kódu na řešení**.  
  
  Chcete-li spustit analýzu kódu na projektu:  
  
- V Průzkumníku řešení vyberte název projektu.  
  
- Na **sestavení** nabídce zvolte **spustit analýzu kódu na** *název projektu*.  
  
  Projekt nebo řešení je zkompilován a spuštění analýzy kódu. Výsledky se zobrazí v okně analýzy kódu.  
  
##  <a name="BKMK_Analyze"></a> Analýza a řešení upozornění analýzy kódu  
 Pokud chcete analyzovat konkrétního upozornění, vyberte záhlaví upozornění v okně analýzy kódu. Upozornění rozšíří a zobrazte další informace o problému. Pokud je to možné, analýza kódu zobrazuje čísla řádků a analýzy logiku, která vedla k upozornění. Podrobné informace o upozornění, včetně možná řešení problému zvolte id upozornění chcete zobrazit téma nápovědy v knihovně MSND zprávy.  
  
 Při rozšiřování upozornění na řádek kódu, který způsobil toto upozornění je zvýrazněn v editoru kódu sady Visual Studio.  
  
 Po zjištění problému ho mohli vyřešit ve vašem kódu. Pak znovu spusťte analýzu kódu, abyste měli jistotu, že již nezobrazuje upozornění v okně analýzy kódu, a nová upozornění, že jste kód opravili správně nebyla vyvolána.  
  
> [!TIP]
>  Můžete znovu spustit analýzu kódu v okně analýzy kódu. Zvolte **analyzovat** tlačítko a zvolte obor analýzy. Můžete znovu spustit analýzu na celé řešení nebo vybraný projekt.  
  
##  <a name="BKMK_Suppress"></a> Potlačení upozornění analýzy kódu  
 Existují situace, kdy byste se mohli rozhodnot Neopravovat upozornění analýzy kódu. Můžete se rozhodnout, že řešení upozornění vyžaduje příliš mnoho nahrávání ve vztahu k pravděpodobnost, že problém vzniknou v žádné Skutečná implementace kódu. Nebo může domnívat, že je nevhodná pro konkrétní kontext, který se používá v tomto upozornění analýzy. Jednotlivá upozornění můžete potlačit tak, aby se nebude zobrazovat v okně analýzy kódu.  
  
 Chcete-li potlačit upozornění:  
  
1. Pokud se zobrazí podrobné informace, vyberte název upozornění a rozbalte ho.  
  
2. Zvolte **akce** odkaz v dolní části upozornění.  
  
3. Zvolte **potlačit zprávu** a klikněte na tlačítko **zdroje v**.  
  
   Potlačení zprávy vloží `#pragma warning (disable:` *WarningId* `)` , který potlačí případná upozornění pro řádek kódu.  
  
##  <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Vytváření pracovních položek pro kód upozornění analýzy  
 Funkce sledování pracovní položky můžete použít k protokolování chyb z Visual Studia. Chcete-li tuto funkci používat, musí připojit k instanci serveru Team Foundation Server.  
  
 **Chcete-li vytvořit pracovní položku pro jeden nebo více upozornění kódu C/C++**  
  
1.  V okně analýzy kódu rozbalte a vyberte upozornění  
  
2.  V místní nabídce pro upozornění, zvolte **vytvořit pracovní položku**a pak zvolte typ pracovní položky.  
  
3.  Visual Studio vytvoří jedné pracovní položky pro vybrané upozornění a pracovní položky se zobrazí v okně dokumentu rozhraní IDE.  
  
4.  Přidat žádné další informace a klikněte na tlačítko **uložit pracovní položku**.  
  
##  <a name="BKMK_Search"></a> Vyhledávání a filtrování výsledků analýzy kódu  
 Můžete hledat dlouhé seznamy varovné zprávy a upozornění v řešení vícenásobného projektu můžete filtrovat.  
  
1.  **Filtr upozornění podle názvu nebo id upozornění**: Zadejte klíčové slovo v **filtr** textového pole.  
  
2.  **Filtr upozornění projektem**: V řešení vícenásobného projektu, vyberte jeden nebo více projektů v seznamu v horní části napravo od v okně analýzy kódu. Zvolte název řešení Chcete-li zobrazit všechna upozornění.  
  
3.  **Filtr upozornění podle závažnosti**: ve výchozím nastavení, zprávy analýzy kódu jsou přiřazeny závažnost **upozornění**. Můžete přiřadit závažnost jednu nebo více zpráv jako **chyba** sada vlastních pravidel. Zvolte buď **upozornění** nebo **chyba** zobrazíte jen zprávy, které jsou přiřazeny příslušných závažnosti. Zvolte **všechny** zobrazíte všechny zprávy.



