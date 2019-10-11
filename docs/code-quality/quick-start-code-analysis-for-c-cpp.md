---
title: 'Rychlý start: Analýza kódu pro C/C++'
description: Spusťte statickou analýzu C++ kódu v aplikaci Visual Studio a zjistěte běžné problémy s kódováním a vady.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 2c68bb94a66be2c9fc1da4365cb77adf8d1330a1
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163022"
---
# <a name="quickstart-code-analysis-for-cc"></a>Rychlý start: Analýza kódu pro C/C++

Kvalitu aplikace můžete zlepšit spuštěním analýzy kódu pravidelně na jazyku C nebo C++ kódu. To vám může pomáhat najít běžné problémy, porušení dobrého programovacího postupu nebo vady, které se obtížně zjišťují prostřednictvím testování. Upozornění analýzy kódu se liší od kompilátoru chyby a upozornění, protože analýza kódu hledá vzory v konkrétním kódu, které jsou platné, ale přesto vytvořit problémy pro vy nebo ostatní uživatelé, kteří používají váš kód.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurace sad pravidel pro projekt

1. V **Průzkumník řešení**otevřete místní nabídku pro název projektu a pak zvolte možnost **vlastnosti**.

2. Volitelně můžete v seznamech **Konfigurace** a **platforma** zvolit konfigurace sestavení a cílovou platformu.

3. Chcete-li spustit nástroj Analýza kódu pokaždé, když se sestavení projektu použitím vybrané konfigurace, vyberte **povolit analýzu kódu na sestavení** zaškrtávací políčko. Můžete také spustit analýzu kódu ručně otevřením nabídky **analyzovat** a následným výběrem možnosti **Spustit analýzu kódu v** *ProjectName* nebo **Spustit analýzu kódu v souboru**.

4. Vyberte [sadu pravidel](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md) , kterou chcete použít, nebo vytvořte [vlastní sadu pravidel](../code-quality/how-to-create-a-custom-rule-set.md). Pokud používáte LLVM/Clang-CL, přečtěte si téma [použití Clang-uklizený v aplikaci Visual Studio](../code-quality/clang-tidy.md) ke konfiguraci možností analýzy Clang-uklizený.

### <a name="standard-cc-rule-sets"></a>Standardní sady CC++ /pravidla

Sada Visual Studio obsahuje dvě standardní sady pravidel pro nativní kód:

|Sada pravidel|Popis|
|--------------|-----------------|
|Nativní minimální doporučená pravidla společnosti Microsoft|Tato sada pravidel se zaměřuje na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a chyb aplikací. Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro vaše nativní projekty.|
|Nativní doporučená pravidla společnosti Microsoft|Tato sada pravidel se zabývá širokou škálou problémů. Obsahuje všechna pravidla pro nativní minimální doporučená pravidla společnosti Microsoft.|

## <a name="run-code-analysis"></a>Spustit analýzu kódu

Na stránce Analýza kódu stránky vlastností projektu lze konfigurovat analýzu kódu pro spuštění při každém sestavení projektu. Můžete také spustit analýzu kódu ručně.

Spuštění analýzy kódu v řešení:

- V nabídce **sestavení** vyberte možnost **Spustit analýzu kódu v řešení**.

Spuštění analýzy kódu v projektu:

1. V Průzkumník řešení vyberte název projektu.

2. V nabídce **sestavení** vyberte možnost **Spustit analýzu kódu pro** *název projektu*.

Spuštění analýzy kódu v souboru:

1. V Průzkumník řešení vyberte název souboru.

2. V nabídce **sestavení** zvolte možnost **Spustit analýzu kódu v souboru** nebo stiskněte **kombinaci kláves CTRL + SHIFT + ALT + F7**.

   Projekt nebo řešení jsou kompilovány a je spuštěna analýza kódu. Výsledky se zobrazí v Seznam chyb.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Analyzovat a vyřešit upozornění analýzy kódu

Chcete-li analyzovat konkrétní upozornění, vyberte název upozornění v Seznam chyb. Upozornění se rozbalí, aby se zobrazily další informace o problému. Pokud je to možné, analýza kódu zobrazuje čísla řádků a logiku analýzy, která vedla k upozornění. Chcete-li získat podrobné informace o upozornění, včetně možných řešení problému, vyberte ID upozornění, abyste zobrazili příslušné téma online nápovědy.

Když vyberete upozornění, zvýrazní se řádek kódu, který způsobil upozornění, v editoru kódu sady Visual Studio.

Po zjištění problému ho mohli vyřešit ve vašem kódu. Pak znovu spusťte analýzu kódu, abyste se ujistili, že se už nezobrazuje v Seznam chyb a že vaše oprava nevyvolala žádná nová upozornění.

## <a name="suppress-code-analysis-warnings"></a>Potlačit upozornění analýzy kódu

Existují situace, kdy byste se mohli rozhodnot Neopravovat upozornění analýzy kódu. Můžete se rozhodnout, že řešení upozornění vyžaduje příliš mnoho nahrávání ve vztahu k pravděpodobnost, že problém vzniknou v žádné Skutečná implementace kódu. Nebo může domnívat, že je nevhodná pro konkrétní kontext, který se používá v tomto upozornění analýzy. Jednotlivá upozornění můžete potlačit, aby se už nezobrazovala v Seznam chyb.

Chcete-li potlačit upozornění:

1. Pokud se nezobrazují podrobné informace, vyberte název upozornění a rozbalte ho.

2. Zvolte **akce** odkaz v dolní části upozornění.

3. Zvolte možnost **potlačit zprávu** a pak zvolte možnost **zdroj**.

   Potlačení vložení zprávy `#pragma warning (disable:[warning ID])`, které potlačí upozornění na řádek kódu.

## <a name="create-work-items-for-code-analysis-warnings"></a>Vytváření pracovních položek pro upozornění analýzy kódu

Funkci sledování pracovní položky můžete použít k protokolování chyb z aplikace Visual Studio. Chcete-li použít tuto funkci, je nutné se připojit k instanci Team Foundation Server.

**Vytvoření pracovní položky pro jedno nebo více upozornění C/C++ kódu**

1. V Seznam chyb rozbalte a vyberte upozornění.

2. V místní nabídce pro upozornění zvolte **vytvořit pracovní položku**a pak zvolte typ pracovní položky.

3. Visual Studio vytvoří jednu pracovní položku pro vybraná upozornění a zobrazí pracovní položku v okně dokumentu integrovaného vývojového prostředí (IDE).

4. Přidejte další informace a pak zvolte **Uložit pracovní položku**.

## <a name="search-and-filter-code-analysis-results"></a>Hledání a filtrování výsledků analýzy kódu

Můžete hledat dlouhé seznamy varovné zprávy a upozornění v řešení vícenásobného projektu můžete filtrovat.

- **Filtrování upozornění podle názvu nebo ID upozornění**: Do vyhledávacího pole zadejte klíčové slovo.

- **Filtrování upozornění podle závažnosti**: Ve výchozím nastavení jsou zprávy nástroje Code Analysis přiřazeny závažnost **Upozornění**. Závažnost jedné nebo více zpráv můžete přiřadit jako **chybu** v sadě vlastních pravidel. Ve sloupci **závažnost** **Seznam chyb**klikněte na šipku rozevíracího seznamu a pak na ikonu filtru. Chcete-li zobrazit pouze zprávy, které jsou přiřazeny příslušné závažnosti, vyberte možnost **Upozornění** nebo **Chyba** . Zvolte **možnost Vybrat vše** , chcete-li zobrazit všechny zprávy.

## <a name="see-also"></a>Viz také:

- [Analýza kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)