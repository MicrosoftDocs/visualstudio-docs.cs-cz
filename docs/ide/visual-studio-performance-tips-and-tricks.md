---
title: Tipy pro zvýšení výkonu
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1c4e55fe6275d750d3bc3b03fb8f0ac5eec2751
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672922"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Tipy k výkonu sady Visual Studio a triky

Doporučení ohledně výkonu pro Visual Studio jsou určeny pro situace nedostatku paměti, které mohou nastat v ojedinělých případech. V těchto situacích můžete optimalizovat některé funkce sady Visual Studio, které nepoužíváte. Následující tipy nepředstavují obecná doporučení.

> [!NOTE]
> Pokud máte potíže s používáním produktu z důvodu problémů s pamětí, dejte nám vědět prostřednictvím [nástroj pro zpětnou vazbu](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="use-a-64-bit-os"></a>Použít 64bitová verze OS

Pokud upgradujete váš systém z 32bitové verze Windows na 64bitovou verzi, rozbalte velikost virtuální paměti, které jsou k dispozici se sadou Visual Studio z 2 GB až 4 GB. Díky sadě Visual Studio pro zpracování výrazně větší úlohy, i když je 32bitový proces.

Další informace najdete v tématu [limity paměti](/windows/desktop/Memory/memory-limits-for-windows-releases#memory_limits) a [použijte parametr/LARGEADDRESSAWARE na Windows 64-bit](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Zakázat automatické obnovení

Visual Studio automaticky znovu neotevře dokumenty, které byly ponechány otevřené v předchozí relaci. To může prodloužit čas potřebný k načtení řešení až 30 % a víc, v závislosti na typu projektu a dokumenty jsou otevřené. Návrháře, jako jsou Windows Forms a XAML a některé soubory jazyka JavaScript a typescript může trvat dlouho.

Visual Studio vás upozorní žlutě panelu při obnovení automatické dokumentů způsobuje řešení načtení výrazně pomalejší. Můžete zakázat automatickou znovu otevřít pomocí následujících kroků:

1. Vyberte **nástroje** > **možnosti** otevřít **možnosti** dialogové okno.

1. Na **projekty a řešení** > **Obecné** stránce, zrušte zaškrtnutí možnosti **dokumentů u načtení řešení znovu otevřít**.

Pokud zakážete automatické obnovení, přejděte k souborům, který chcete spustit rychlý způsob je pomocí jedné z [přejít na](../ide/go-to.md) příkazy:

- Obecnou **přejít na** funkce, vyberte **upravit** > **přejít na** > **přejít na vše**, nebo stiskněte klávesu  **CTRL**+**T**.

- V sadě Visual Studio 2017 verze 15,8 a novější, můžete přeskočit na poslední úpravy umístění v řešení pomocí **upravit** > **přejít na** > **přejít na poslední upravit umístění**, nebo stisknutím klávesy **Ctrl**+**Shift**+**Backspace**.

- V sadě Visual Studio 2017 verze 15,8 a novější, použijte **přejít na poslední soubor** zobrazíte seznam naposledy navštívený souborů v řešení. Vyberte **upravit** > **přejít na** > **přejít na poslední soubor**, nebo stiskněte klávesu **Ctrl** + **1**, **Ctrl**+**R**.

## <a name="configure-debugging-options"></a>Konfigurovat možnosti ladění

Pokud je obvykle dochází v paměti během relace ladění, můžete optimalizovat výkon tím, že jedna nebo více změn konfigurace.

- **Povolit volbu pouze vlastní kód**

    Nejjednodušší optimalizace je umožnit **pouze můj kód** funkci, která pouze načte symboly pro váš projekt. Povolení této funkce může způsobit velké paměti ukládá pro ladění spravované aplikace (.NET). Tato možnost je už povolená ve výchozím nastavení v některých typech projektů.

    Chcete-li povolit **pouze můj kód**, zvolte **nástroje** > **možnosti** > **ladění**  >   **Obecné**a pak vyberte **povolit volbu pouze vlastní kód**.

- **Zadejte symboly, které chcete načíst**

    Pro nativní ladění, načítají se soubory symbolů (*PDB*) je nákladný z hlediska paměťových prostředků. Můžete nakonfigurovat nastavení symbolu ladicího programu pro konzervaci paměti. Obvykle konfigurovat řešení tak, aby moduly načíst jenom z projektu.

    Chcete-li zadat načítání symbolů, zvolte **nástroje** > **možnosti** > **ladění** > **symboly**.

    Nastavit na **pouze určité moduly** místo **všechny moduly** a pak zadejte které moduly, které jsou pro vás k načtení. Při ladění, je můžete také kliknout pravým tlačítkem konkrétní moduly v **moduly** okno explicitně zahrnout symbol zatížení modulu. (Chcete-li otevřít okno při ladění, zvolte **ladění** > **Windows** > **moduly**.)

    Další informace najdete v tématu [pochopit soubory symbolů](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Zakázat diagnostické nástroje**

    Doporučuje se zakázat profilaci procesoru po použití. Tato funkce může spotřebovat velké množství prostředků. Po povolení profilace procesoru tento stav se uchovávají napříč dalších ladicích relací, takže je vhodné explicitně vypnutí, až budete hotovi. Některé prostředky můžou uložit zakázáním diagnostických nástrojů při ladění, pokud zadaná funkce není nutné.

    Zakázat **diagnostické nástroje**, spustíte relaci ladění, zvolte **nástroje** > **možnosti** > **povolení diagnostiky Nástroje**a zrušte výběr možnosti.

    Další informace najdete v tématu [nástrojů pro profilaci sady](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Zakázat nástroje a rozšíření

Některé nástroje nebo rozšíření lze vypnout pro zvýšení výkonu.

> [!TIP]
> Vypnutím rozšíření jeden po druhém a opětná kontrola výkonu často izolovat problémy s výkonem.

### <a name="managed-language-service-roslyn"></a>Spravovaná služba jazyka (Roslyn)

Informace o aspektech týkajících se výkonu .NET Compiler Platform ("Roslyn"), najdete v části [faktory ovlivňující výkon u velkých řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Zákaz úplné analýzy řešení**

    Visual Studio provádí analýzu na celé řešení s cílem poskytují bohaté uživatelské prostředí před vyvoláním sestavení o chybách. Tato funkce je užitečná k identifikaci chyby co nejdříve. Pro velká řešení, ale tato funkce může spotřebovat významné paměťových prostředků. Pokud dojde k přetížení paměti nebo podobné problémy, můžete zakázat toto prostředí k uvolnění těchto prostředků. Ve výchozím nastavení tato možnost je povolená v jazyce Visual Basic a zakázané pro jazyk C#.

    Chcete-li zakázat **úplné analýzy řešení**, zvolte **nástroje** > **možnosti** > **textový Editor**a pak vyberte buď **jazyka Visual Basic** nebo **jazyka C#**. Zvolte **Upřesnit** a zrušte zaškrtnutí možnosti **povolení úplné analýzy řešení**.

- **Zakázat funkci CodeLens**

    Visual Studio provede **najít všechny odkazy** úloh na jednotlivé metody, který se zobrazí. Funkce CodeLens nabízí funkce, jako je vloženým zobrazením počet odkazů. Práce se provádí v samostatném procesu, jako *ServiceHub.RoslynCodeAnalysisService32*. V rozsáhlých řešeních, nebo v systémech s omezenými zdroji tato funkce může mít významný dopad na výkon. Pokud máte problémy paměti, například při načítání velkých řešení na 4 GB, nebo vysoké využití procesoru pro tento proces můžete zakázat CodeLens a uvolnit tak prostředky.

    Chcete-li zakázat **CodeLens**, zvolte **nástroje** > **možnosti** > **textový Editor**  >   **Všechny jazyky** > **CodeLens**a zrušte zaškrtnutí možnosti funkce.

    > [!NOTE]
    > CodeLens je k dispozici v edicích sady Visual Studio Professional a Enterprise.

### <a name="other-tools-and-extensions"></a>Další nástroje a rozšíření

- **Zakázat rozšíření**

    Rozšíření jsou další softwarové komponenty se přidali do sady Visual Studio, které přinášejí nové funkce nebo rozšířit stávající funkce. Rozšíření lze často příčiny problémů s pamětí prostředků. Pokud máte problémy paměti prostředku, zkuste zakázat rozšíření jeden najednou zobrazit, jak to ovlivní scénáře nebo pracovních postupů.

    Pokud chcete zakázat rozšíření, přejděte na **nástroje** > **rozšíření a aktualizace**a konkrétní rozšíření zakázat.

- **Zakázat návrháře XAML**

    Návrhář XAML je ve výchozím nastavení povolené, ale pouze využívá prostředky, pokud otevřete *.xaml* souboru. Je-li pracovat se soubory XAML, ale nechcete použít funkci návrháře, zakažte tuto funkci pro uvolnění paměti.

    Chcete-li zakázat **návrháře XAML**, přejděte na stránku **nástroje** > **možnosti** > **návrháře XAML**  >  **Povolit návrhář XAML**a zrušte výběr možnosti.

- **Odebrat úlohy**

    Instalační program sady Visual Studio můžete použít k odebrání úlohy, které se již nepoužívají. Tato akce může zjednodušit náklady na spuštění a modulu runtime přeskočením balíčky a sestavení, které už nejsou potřeba.

## <a name="force-a-garbage-collection"></a>Vynutit uvolňování paměti

Systém uvolňování paměti kolekce paměti správy používá modul CLR. V tomto systému je někdy paměti používá objekty, které už nejsou potřeba. Tento stav je dočasné. uvolňování vydá tuto paměť založené na jeho výkon a využití prostředků heuristické metody. Můžete vynutit CLR shromažďovat všechny nevyužité paměti pomocí klávesové zkratky v sadě Visual Studio. Pokud je značné množství paměti čekání na kolekci a vynutit uvolnění paměti, měli byste vidět využití paměti *devenv.exe* procesu pokles **Správce úloh**. Je zřídka nezbytné při použití této metody. Ale po dokončení nákladné operace (například úplná sestavení, relace ladění nebo otevřít událost řešení), může vám pomoct zjistit, kolik paměti skutečně používá proces. Protože Visual Studio je smíšený (spravovaný a nativní), je někdy možné nativní přidělování a uvolňování soutěží o prostředky omezenou pamětí. Za podmínek vysoké využití paměti může pomoct vynutit systému uvolňování paměti ke spuštění.

Chcete-li vynutit uvolnění paměti, použijte klávesová zkratka: **Ctrl**+**Alt**+**Shift**+**F12**, **Ctrl**+**Alt**+**Shift**+**F12** (ji stiskněte dvakrát klávesu).

Pokud vynucení uvolnění paměti spolehlivě provede váš scénář fungovat, soubor sestavy prostřednictvím nástroje pro zpětnou vazbu Visual Studio, jak toto chování je pravděpodobně chyba.

Podrobný popis systému uvolňování paměti modulu CLR najdete v tématu [základy kolekce paměti](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu sady Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Načíst řešení rychleji (blog sady Visual Studio)](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)