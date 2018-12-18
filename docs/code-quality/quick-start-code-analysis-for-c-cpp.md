---
title: 'Rychlé zahájení: Analýza kódu pro C/C++'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 3aefc42e77c6ccaf14a426a26e12b81b49bb5632
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818760"
---
# <a name="quickstart-code-analysis-for-cc"></a>Rychlý start: Analýza kódu pro C/C++

Zlepšit kvalitu vaší aplikace při spuštění analýzy kódu pravidelně na kód jazyka C nebo C++. To může pomoct najít běžné problémy, porušování programovacím vhodné nebo chyb, které je obtížné vyhledat pomocí testování. Upozornění analýzy kódu se liší od kompilátoru chyby a upozornění, protože analýza kódu hledá vzory v konkrétním kódu, které jsou platné, ale přesto vytvořit problémy pro vy nebo ostatní uživatelé, kteří používají váš kód.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurace sady pravidel pro projekt

1. V **Průzkumníka řešení**, otevřete místní nabídku pro název projektu a klikněte na tlačítko **vlastnosti**.

2. Následující kroky jsou volitelné:

    1. V **konfigurace** a **platformy** seznamy, zvolte sestavení konfigurace a cílovou platformu.

    2. Ve výchozím nastavení analýza kódu sestavu upozornění z kódu, který je automaticky generován externí nástroje. Chcete-li zobrazit upozornění z generovaného kódu, zrušte **potlačit Výsledky generovaného kódu** zaškrtávací políčko.

        > [!NOTE]
        > Tato možnost není potlačit chyby analýzy kódu a upozornění z generovaného kódu při chyby a upozornění se zobrazí ve formulářích a šablony. Můžete jak zobrazit a spravovat zdrojový kód pro formuláře nebo šablony.

3. Chcete-li spustit nástroj Analýza kódu pokaždé, když se sestavení projektu použitím vybrané konfigurace, vyberte **povolit analýzu kódu pro C/C++ při sestavení** zaškrtávací políčko. Můžete také spustit analýzu kódu ručně tak, že otevřete **analyzovat** nabídky a následným výběrem možnosti **spustit analýzu kódu na** *ProjectName*.

4. V **spustit tuto sadu pravidel** seznamu, proveďte jednu z následujících akcí:

    - Vyberte sadu pravidel, kterou chcete použít.

    - Zvolte  **\<Procházet... >** zadat sadu existujících vlastních pravidel, která se nenachází v seznamu.

    - Definování [vlastní sady pravidel](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Sady pravidel standardním C/C++

Visual Studio obsahuje dvě standardní sady pravidel pro nativní kód:

|Sada pravidel|Popis|
|--------------|-----------------|
|Microsoft nativní Minimální doporučená pravidla|Tato sada pravidel se soustředí na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a selhání aplikace. Měli byste zahrnout tuto sadu pravidel v jakékoli vlastní sadě pravidel, že kterou vytvoříte pro vaše nativní projekty.|
|Microsoft nativní doporučená pravidla|Tato sada pravidel obsahuje celou řadu problémů. Obsahuje všechna pravidla v Microsoft nativní Minimální doporučená pravidla.|

## <a name="run-code-analysis"></a>Spuštění analýzy kódu

Na stránce analýzy kódu na stránkách vlastností projektu můžete konfigurovat analýzu kódu při každém spuštění sestavení projektu. Analýza kódu můžete spustit také ručně.

Spuštění analýzy kódu pro řešení:

- Na **sestavení** nabídce zvolte **spustit analýzu kódu na řešení**.

Chcete-li spustit analýzu kódu na projektu:

1. V Průzkumníku řešení vyberte název projektu.

2. Na **sestavení** nabídce zvolte **spustit analýzu kódu na** *název projektu*.

   Projekt nebo řešení je zkompilován a spuštění analýzy kódu. Výsledky se zobrazí v seznamu chyb.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analýza a řešení upozornění analýzy kódu

Pokud chcete analyzovat konkrétního upozornění, vyberte záhlaví upozornění v seznamu chyb. Upozornění rozšíří a zobrazte další informace o problému. Pokud je to možné, analýza kódu zobrazuje čísla řádků a analýzy logiku, která vedla k upozornění. Podrobné informace o upozornění, včetně možná řešení problému zvolte ID upozornění zobrazíte jeho odpovídající online téma nápovědy.

Při výběru upozornění na řádek kódu, který způsobil toto upozornění je zvýrazněn v editoru kódu sady Visual Studio.

Po zjištění problému ho mohli vyřešit ve vašem kódu. Potom znovu spusťte analýzu kódu, abyste měli jistotu, že upozornění již nezobrazuje v seznamu chyb a všechna nová upozornění, že jste kód opravili správně nebyla vyvolána.

## <a name="suppress-code-analysis-warnings"></a>Potlačení upozornění analýzy kódu

Existují situace, kdy byste se mohli rozhodnot Neopravovat upozornění analýzy kódu. Můžete se rozhodnout, že řešení upozornění vyžaduje příliš mnoho nahrávání ve vztahu k pravděpodobnost, že problém vzniknou v žádné Skutečná implementace kódu. Nebo může domnívat, že je nevhodná pro konkrétní kontext, který se používá v tomto upozornění analýzy. Jednotlivá upozornění můžete potlačit tak, aby se nebude zobrazovat v seznamu chyb.

Chcete-li potlačit upozornění:

1. Pokud se zobrazí podrobné informace, vyberte název upozornění a rozbalte ho.

2. Zvolte **akce** odkaz v dolní části upozornění.

3. Zvolte **potlačit zprávu** a klikněte na tlačítko **zdroje v**.

   Potlačení zprávy vloží `#pragma warning (disable:[warning ID])` , který potlačí případná upozornění pro řádek kódu.

## <a name="create-work-items-for-code-analysis-warnings"></a>Vytvoření pracovní položky pro kód upozornění analýzy

Funkce sledování pracovní položky můžete použít k protokolování chyb z Visual Studia. Chcete-li tuto funkci používat, musí připojit k instanci serveru Team Foundation Server.

**Chcete-li vytvořit pracovní položku pro jeden nebo více upozornění kódu C/C++**

1. V seznamu chyb rozbalte a vyberte upozornění

2. V místní nabídce pro upozornění, zvolte **vytvořit pracovní položku**a pak zvolte typ pracovní položky.

3. Visual Studio vytvoří jedné pracovní položky pro vybrané upozornění a pracovní položky se zobrazí v okně dokumentu rozhraní IDE.

4. Přidat žádné další informace a klikněte na tlačítko **uložit pracovní položku**.

## <a name="search-and-filter-code-analysis-results"></a>Vyhledávání a filtrování výsledků analýzy kódu

Můžete hledat dlouhé seznamy varovné zprávy a upozornění v řešení vícenásobného projektu můžete filtrovat.

- **Filtr upozornění podle názvu nebo id upozornění**: do vyhledávacího pole zadejte klíčové slovo.

- **Filtr upozornění podle závažnosti**: ve výchozím nastavení, zprávy analýzy kódu jsou přiřazeny závažnost **upozornění**. Můžete přiřadit závažnost jednu nebo více zpráv jako **chyba** sada vlastních pravidel. Na **závažnost** sloupec **seznam chyb**, zvolte šipku rozevíracího seznamu a klikněte na ikonu filtru. Zvolte **upozornění** nebo **chyba** zobrazíte jen zprávy, které jsou přiřazeny příslušných závažnosti. Zvolte **Vybrat vše** zobrazíte všechny zprávy.

## <a name="see-also"></a>Viz také:

[Analýza kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)