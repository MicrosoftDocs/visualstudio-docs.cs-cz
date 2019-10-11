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
ms.openlocfilehash: b14737c09cf7ff2b14eda1f61408b531b9c22c14
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018367"
---
# <a name="quickstart-code-analysis-for-cc"></a>Rychlý start: Analýza kódu pro C/C++

Kvalitu aplikace můžete zlepšit spuštěním analýzy kódu pravidelně na jazyku C nebo C++ kódu. To vám může pomáhat najít běžné problémy, porušení dobrého programovacího postupu nebo vady, které se obtížně zjišťují prostřednictvím testování. Upozornění analýzy kódu se liší od kompilátoru chyby a upozornění, protože analýza kódu hledá vzory v konkrétním kódu, které jsou platné, ale přesto vytvořit problémy pro vy nebo ostatní uživatelé, kteří používají váš kód.

## <a name="configure-rule-sets-for-a-project"></a>Konfigurace sad pravidel pro projekt

1. V **Průzkumník řešení**otevřete místní nabídku pro název projektu a pak zvolte možnost **vlastnosti**.

2. Následující kroky jsou volitelné:

    1. V seznamech **Konfigurace** a **platforma** vyberte konfigurace sestavení a cílová platforma.

    2. Ve výchozím nastavení analýza kódu sestavu upozornění z kódu, který je automaticky generován externí nástroje. Chcete-li zobrazit upozornění z generovaného kódu, zrušte **potlačit Výsledky generovaného kódu** zaškrtávací políčko.

        > [!NOTE]
        > Tato možnost není potlačit chyby analýzy kódu a upozornění z generovaného kódu při chyby a upozornění se zobrazí ve formulářích a šablony. Zdrojový kód formuláře nebo šablony můžete zobrazit a spravovat.

3. Chcete-li spustit analýzu kódu pokaždé, když je projekt sestaven pomocí vybrané konfigurace, zaškrtněte políčko **Povolit analýzu kódu proC++ sestavení C/on** . Analýzu kódu lze také spustit ručně otevřením nabídky **analyzovat** a následným výběrem možnosti **Spustit analýzu kódu v** *ProjectName*.

4. V **spustit tuto sadu pravidel** seznamu, proveďte jednu z následujících akcí:

    - Vyberte sadu pravidel, kterou chcete použít.

    - Zvolte **\<Browse >** a zadejte existující vlastní sadu pravidel, která není v seznamu.

    - Definování [vlastní sady pravidel](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Standardní sady CC++ /pravidla

Sada Visual Studio obsahuje dvě standardní sady pravidel pro nativní kód:

|Sada pravidel|Popis|
|--------------|-----------------|
|Nativní minimální doporučená pravidla společnosti Microsoft|Tato sada pravidel se zaměřuje na nejdůležitější problémy v nativním kódu, včetně možných bezpečnostních děr a chyb aplikací. Tuto sadu pravidel byste měli zahrnout v jakékoli vlastní sadě pravidel, kterou vytvoříte pro vaše nativní projekty.|
|Nativní doporučená pravidla společnosti Microsoft|Tato sada pravidel se zabývá širokou škálou problémů. Obsahuje všechna pravidla pro nativní minimální doporučená pravidla společnosti Microsoft.|

## <a name="run-code-analysis"></a>Spustit analýzu kódu

Na stránce Analýza kódu na stránkách vlastností projektu můžete nakonfigurovat analýzu kódu, která se spustí při každém sestavení projektu. Můžete také spustit analýzu kódu ručně.

Spuštění analýzy kódu v řešení:

- Na **sestavení** nabídce zvolte **spustit analýzu kódu na řešení**.

Spuštění analýzy kódu v projektu:

1. V Průzkumník řešení vyberte název projektu.

2. V nabídce **sestavení** vyberte možnost **Spustit analýzu kódu pro** *název projektu*.

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

[Analýza kódu pro C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)