---
title: Tipy pro zlepšení výkonu
description: Naučte se optimalizovat některé funkce sady Visual Studio, které nemusíte používat, aby bylo možné lépe vylepšit výkon.
ms.custom: SEO-VS-2020
ms.date: 08/13/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f4c36987e198be576d843b984be14ddea824919
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479612"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Tipy a triky pro výkon sady Visual Studio

Doporučení k výkonu sady Visual Studio jsou určená pro situace s nedostatkem paměti, ke kterým může dojít ve výjimečných případech. V těchto situacích můžete optimalizovat některé funkce sady Visual Studio, které nemusíte používat. Následující tipy nejsou určeny jako obecná doporučení.

> [!NOTE]
> Pokud máte potíže s používáním produktu z důvodu problémů s pamětí, dejte nám vědět prostřednictvím [Nástroje pro zpětnou vazbu](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="use-a-64-bit-os"></a>Použití 64. bitového operačního systému

Pokud upgradujete systém z 32 verze Windows na 64 verzi, rozšíříte velikost virtuální paměti dostupné pro sadu Visual Studio ze 2 GB na 4 GB. Díky tomu může Visual Studio zpracovávat výrazně větší úlohy, i když je to 32 proces.

Další informace najdete v tématu [omezení paměti](/windows/desktop/Memory/memory-limits-for-windows-releases) a [použití/LARGEADDRESSAWARE v 64-bitových oknech](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Zakázat automatické obnovení souborů

Visual Studio automaticky znovu otevře dokumenty, které zůstaly otevřené v předchozí relaci. To může prodloužit dobu potřebnou k načtení řešení až o 30% nebo více, v závislosti na typu projektu a otevíraných dokumentech. Návrháře, jako jsou model Windows Forms a XAML a některé soubory jazyka JavaScript a TypeScript, mohou být pomalé pro otevření.

Pokud automatické obnovení dokumentů způsobuje výrazné zpomalení řešení, Visual Studio vás upozorní na žlutou čáru. Automatické opětovné otevření souboru můžete zakázat pomocí následujících kroků:

1. Výběrem **Tools**  >  **Možnosti** nástroje otevřete dialogové okno **Možnosti** .

1. Na stránce **projekty a**  >  **Obecné** řešení zrušte výběr **znovu otevřít dokumenty při načtení řešení**.

Pokud automatické obnovení souborů zakážete, můžete rychlým způsobem navigace do souborů, které chcete otevřít, použít jeden z příkazů [Přejít na](../ide/go-to.md) :

- V části Obecné **přejděte na** funkce vyberte **Upravit**  >  **Přejít na**  >  **vše** nebo stiskněte **CTRL** + **T**.

- Přejděte do posledního umístění pro úpravy v řešení pomocí možnosti **Upravit**  >  **Přejít na**  >  **Přejít na poslední umístění úprav** nebo stiskněte **klávesovou zkratku CTRL** + **SHIFT** + **BACKSPACE**.

- Pomocí **Přejít na poslední soubor** zobrazíte seznam nedávno navštívených souborů v řešení. Vyberte **Upravit**  >  **Přejít** na  >  **Poslední soubor** nebo stiskněte **CTRL** + **1**, **CTRL** + **R**.

## <a name="configure-debugging-options"></a>Konfigurace možností ladění

Pokud obvykle dochází k nedostatku paměti během relace ladění, můžete optimalizovat výkon provedením jedné nebo více změn konfigurace.

- **Povolit Pouze můj kód**

    Nejjednodušší optimalizace je povolit funkci **pouze můj kód** , která načte jenom symboly pro váš projekt. Povolení této funkce může způsobit významné uložení paměti pro ladění spravovaných aplikací (.NET). Tato možnost je již ve výchozím nastavení povolena v některých typech projektů.

    Pokud chcete povolit **pouze můj kód**, zvolte **nástroje**  >  **Možnosti**  >  **ladění**  >  **Obecné** a potom vyberte **Povolit pouze můj kód**.

- **Zadejte symboly, které se mají načíst.**

    Pro nativní ladění je načítání souborů symbolů (*. pdb*) nákladné z důvodu paměťových prostředků. Můžete nakonfigurovat nastavení symbolu ladicího programu pro zachování paměti. Obvykle můžete řešení nakonfigurovat tak, aby se načetly jenom moduly z vašeho projektu.

    Chcete-li určit načítání symbolů, zvolte **nástroje**  >  **Možnosti**  >  **ladění**  >  **symboly**.

    Nastavte možnosti jenom na **zadané moduly** , a ne na **všechny moduly** a pak určete, které moduly si můžete načíst. Při ladění můžete také kliknout pravým tlačítkem myši na konkrétní moduly v okně **moduly** , aby explicitně zahrnovaly modul v načtení symbolu. (Chcete-li otevřít okno během ladění, klikněte na tlačítko **ladit**  >  **Systém Windows**  >  **Moduly**.)

    Další informace najdete v tématu [Principy souborů symbolů](?view=vs-2019&preserve-view=true).

- **Zakázat Diagnostické nástroje**

    Doporučuje se, abyste po použití zakázali profilaci procesoru. Tato funkce může využívat velké množství prostředků. Po povolení profilace procesoru je tento stav trvale v následných ladicích relacích, takže je po dokončení potřeba ho explicitně zapnout. Můžete uložit některé prostředky zakázáním diagnostických nástrojů během ladění, pokud nepotřebujete poskytované funkce.

    Pokud chcete **diagnostické nástroje** zakázat, spusťte ladicí relaci, zvolte možnosti **nástrojů**  >  **Options**  >  **Povolit diagnostické nástroje** a zrušte výběr možnosti.

    Další informace najdete v tématu [Nástroje pro profilaci](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Zakázat nástroje a rozšíření

Některé nástroje nebo rozšíření je možné vypnout, aby se zlepšil výkon.

> [!TIP]
> Problémy s výkonem často můžete izolovat vypnutím rozšíření po jednom a dalším zkontrolováním výkonu.

### <a name="managed-language-service-roslyn"></a>Služba spravovaného jazyka (Roslyn)

Informace o požadavcích na výkon .NET Compiler Platform (Roslyn) najdete v tématu [požadavky na výkon pro velká řešení](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

- **Zakázat kompletní analýzu řešení**

    Visual Studio provede analýzu celého řešení, aby před vyvoláním sestavení poskytovala bohatou zkušenost s chybami. Tato funkce je užitečná k identifikaci chyb co nejdříve. U velkých řešení ale tato funkce může využívat významné paměťové prostředky. Pokud se setkáváte s tlakem na paměť nebo podobnými problémy, můžete toto prostředí zakázat a uvolnit tak tyto prostředky. Ve výchozím nastavení je tato možnost povolená pro Visual Basic a zakázaná pro C#.

    Chcete-li zakázat **kompletní analýzu řešení**, zvolte možnost **nástroje**  >  **Options**  >  **textový editor** a pak vyberte možnost **Visual Basic** nebo **C#**. Zvolte **Upřesnit** a zrušte výběr možnosti **Povolit úplnou analýzu řešení**.

- **Zakázat CodeLens**

    Visual Studio provede úlohu **Najít všechny odkazy** na každé metodě, která je zobrazena. CodeLens poskytuje funkce, jako je vložené zobrazení počtu odkazů. Práce se provádí v samostatném procesu, jako je *ServiceHub. RoslynCodeAnalysisService32*. Ve velkých řešeních nebo v systémech s omezením prostředků může mít tato funkce výrazný dopad na výkon. Pokud máte problémy s pamětí, například při načítání velkého řešení na 4 GB počítače nebo vysokém využití procesoru pro tento proces, můžete CodeLens vypnout a uvolnit tak prostředky.

    Chcete-li zakázat **CodeLens**, zvolte **nástroje**  >  **Možnosti**  >  **textový editor**  >  **všechny jazyky**  >  **CodeLens** a zrušte výběr funkce.

    > [!NOTE]
    > CodeLens je k dispozici v edicích Professional a Enterprise sady Visual Studio.

### <a name="other-tools-and-extensions"></a>Další nástroje a rozšíření

- **Zakázat rozšíření**

    Rozšíření jsou další softwarové komponenty přidané do sady Visual Studio, které poskytují nové funkce nebo zvyšují stávající funkce. Rozšíření mohou být často zdrojem potíží s prostředky paměti. Pokud dochází k potížím s prostředky paměti, zkuste zakázat rozšíření po jednom, abyste viděli, jak má dopad na scénář nebo pracovní postup.

   ::: moniker range="vs-2017"

    Pokud chcete rozšíření zakázat, použijte **Možnosti** > **rozšíření a aktualizace** nástrojů a zakažte konkrétní rozšíření.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Chcete-li zakázat rozšíření, použijte příkaz **rozšíření** > **Správa rozšíření** a zakažte konkrétní rozšíření.

   ::: moniker-end

- **Zakázat režim mapování**

    V [**režimu mapy**](how-to-track-your-code-by-customizing-the-scrollbar.md#display-modes) se na posuvníku zobrazují řádky kódu v miniaturách. Režim mapování je ve výchozím nastavení povolen.

    Chcete-li zakázat režim mapování, přejděte do části **nástroje**  >  **Možnosti**  >  **Editor textu**  >  **všechny jazyky**  >  **posuvníky** a v části **chování** zrušte výběr **možnosti použít režim mapy pro svislou lištu posuvníku** .

- **Vypnout zalamování řádků**

    [**Zalamování**](./reference/how-to-manage-word-wrap-in-the-editor.md) řádků zobrazí část dlouhého řádku kódu, který překračuje aktuální šířku okna editoru kódu. Zalamování řádků je ve výchozím nastavení zapnuté.

    Chcete-li vypnout zalamování řádků pro projekt, na kterém aktuálně pracujete, přejdete na **Upravit**  >  **Rozšířené**  >  **zalamování řádků**. (Toto nastavení můžete přepínat pomocí stejných příkazů nabídky.)

    Chcete-li vypnout zalamování řádků pro všechny projekty, použijte možnost **nástroje**  >  **Možnosti**  >  **Obecné**  >  **textový editor**  >  **Obecné**  >  **General** a v části **Nastavení** zrušte výběr možnosti **zalamování řádků** .

- **Zakázat Návrhář XAML**

    Návrhář XAML je ve výchozím nastavení povolen, ale spotřebovává prostředky pouze v případě, že otevřete soubor *. XAML* . Pokud pracujete se soubory XAML, ale nechcete používat funkci návrháře, zakažte tuto funkci, aby uvolnila nějakou paměť.

    Návrhář XAML zakážete tak, že přejdete na možnosti **nástroje**  >  **Options**  >  **Návrhář XAML**  >  **Povolit Návrhář XAML** a odškrtnete políčko.

- **Odebrat úlohy**

    Pomocí Instalační program pro Visual Studio můžete odebrat úlohy, které se už nepoužívají. Tato akce může zjednodušit náklady na spuštění a za běhu tím, že přeskočí balíčky a sestavení, které už nepotřebujete.

## <a name="force-a-garbage-collection"></a>Vynutit uvolňování paměti

CLR používá systém správy paměti pro uvolňování paměti. V tomto systému se někdy paměť používá v objektech, které už nejsou potřeba. Tento stav je dočasný. systém uvolňování paměti uvolní tuto paměť na základě jeho heuristiky výkonu a využití prostředků. Můžete vynutit, aby CLR shromáždil veškerou nepoužitou paměť pomocí klávesových zkratek v aplikaci Visual Studio. Pokud se pro shromažďování dat a vynucení uvolňování paměti vyskytne velký objem paměti, měli byste vidět využití paměti při vyřazení procesu *devenv.exe* ve **Správci úloh**. Tuto metodu je zřídka nutné použít. Po dokončení náročné operace (například úplné sestavení, relace ladění nebo otevřené události řešení) vám však může usnadnit určení množství paměti, které tento proces skutečně používá. Vzhledem k tomu, že je sada Visual Studio smíšená (spravovaná & nativní), je možné, že nativní přidělování a uvolňování paměti můžou být v případě omezeného počtu paměťových prostředků konkurenční. V podmínkách vysokého využití paměti může pomáhat vynutit spouštění uvolňování paměti.

Chcete-li vynutit uvolňování paměti, použijte klávesovou zkratku **CTRL** + **ALT** + **SHIFT** + **F12**, **CTRL** + **ALT** + **SHIFT** + **F12** (stiskněte dvakrát).

Pokud vynucené uvolňování paměti zajistí spolehlivou práci, zaznamenejte zprávu prostřednictvím nástroje pro zpětnou vazbu sady Visual Studio, protože toto chování je pravděpodobně chyba.

Podrobný popis systému uvolňování paměti CLR najdete v tématu [základní informace o uvolňování paměti](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Viz také

- [Optimalizace výkonu sady Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Rychlejší načítání řešení (blog sady Visual Studio)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)