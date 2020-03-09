---
title: Tipy pro zlepšení výkonu
ms.date: 08/14/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3cd7fe9781048f6612ff6bd81c0bf0cbc00a30b
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409495"
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

1. Vyberte **nástroje** > **Možnosti** a otevřete dialogové okno **Možnosti** .

1. Na stránce **projekty a řešení** > **Obecné** zrušte výběr **znovu otevřít dokumenty při načtení řešení**.

Pokud automatické obnovení souborů zakážete, můžete rychlým způsobem navigace do souborů, které chcete otevřít, použít jeden z příkazů [Přejít na](../ide/go-to.md) :

- V části Obecné **přejděte na** možnost **Upravit** > **přejděte na** > **Přejít na vše**nebo stiskněte klávesovou **zkratku CTRL**+**t**.

- Přejděte do posledního umístění pro úpravy v řešení pomocí **edit** > **přejděte na** > **Přejít na poslední umístění úprav**nebo stiskněte **klávesu CTRL**+**SHIFT**+**BACKSPACE**.

- Pomocí **Přejít na poslední soubor** zobrazíte seznam nedávno navštívených souborů v řešení. Vyberte **upravit** > **Přejít na** > **Přejít na poslední soubor**nebo stiskněte **CTRL**+**1**, **CTRL**+**R**.

## <a name="configure-debugging-options"></a>Konfigurace možností ladění

Pokud obvykle dochází k nedostatku paměti během relace ladění, můžete optimalizovat výkon provedením jedné nebo více změn konfigurace.

- **Povolit Pouze můj kód**

    Nejjednodušší optimalizace je povolit funkci **pouze můj kód** , která načte jenom symboly pro váš projekt. Povolení této funkce může způsobit významné uložení paměti pro ladění spravovaných aplikací (.NET). Tato možnost je již ve výchozím nastavení povolena v některých typech projektů.

    Pokud chcete **povolit pouze můj kód**, zvolte **nástroje** > **Možnosti** > **ladění** > **Obecné**a pak vyberte **Povolit pouze můj kód**.

- **Zadejte symboly, které se mají načíst.**

    Pro nativní ladění je načítání souborů symbolů ( *. pdb*) nákladné z důvodu paměťových prostředků. Můžete nakonfigurovat nastavení symbolu ladicího programu pro zachování paměti. Obvykle můžete řešení nakonfigurovat tak, aby se načetly jenom moduly z vašeho projektu.

    Chcete-li určit načítání symbolů, zvolte **nástroje** > **možnosti** > **ladění** > **symboly**.

    Nastavte možnosti jenom na **zadané moduly** , a ne na **všechny moduly** a pak určete, které moduly si můžete načíst. Při ladění můžete také kliknout pravým tlačítkem myši na konkrétní moduly v okně **moduly** , aby explicitně zahrnovaly modul v načtení symbolu. (Chcete-li otevřít okno při ladění, vyberte možnost **ladit** > **moduly** **Windows** > .)

    Další informace najdete v tématu [Principy souborů symbolů](/visualstudio/ide/visual-studio-performance-tips-and-tricks?view=vs-2019).

- **Zakázat Diagnostické nástroje**

    Doporučuje se, abyste po použití zakázali profilaci procesoru. Tato funkce může využívat velké množství prostředků. Po povolení profilace procesoru je tento stav trvale v následných ladicích relacích, takže je po dokončení potřeba ho explicitně zapnout. Můžete uložit některé prostředky zakázáním diagnostických nástrojů během ladění, pokud nepotřebujete poskytované funkce.

    Pokud chcete **diagnostické nástroje**zakázat, spusťte ladicí relaci, zvolte **nástroje** > **Možnosti** > **Povolit diagnostické nástroje**a zrušte výběr možnosti.

    Další informace najdete v tématu [Nástroje pro profilaci](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Zakázat nástroje a rozšíření

Některé nástroje nebo rozšíření je možné vypnout, aby se zlepšil výkon.

> [!TIP]
> Problémy s výkonem často můžete izolovat vypnutím rozšíření po jednom a dalším zkontrolováním výkonu.

### <a name="managed-language-service-roslyn"></a>Služba spravovaného jazyka (Roslyn)

Informace o požadavcích na výkon .NET Compiler Platform (Roslyn) najdete v tématu [požadavky na výkon pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Zakázat kompletní analýzu řešení**

    Visual Studio provede analýzu celého řešení, aby před vyvoláním sestavení poskytovala bohatou zkušenost s chybami. Tato funkce je užitečná k identifikaci chyb co nejdříve. U velkých řešení ale tato funkce může využívat významné paměťové prostředky. Pokud se setkáváte s tlakem na paměť nebo podobnými problémy, můžete toto prostředí zakázat a uvolnit tak tyto prostředky. Ve výchozím nastavení je tato možnost povolená pro Visual Basic a zakázaná pro C#.

    Chcete-li zakázat **kompletní analýzu řešení**, zvolte **nástroje** > **Možnosti** > **textový editor**a pak vyberte buď **C#** **Visual Basic** , nebo. Zvolte **Upřesnit** a zrušte výběr možnosti **Povolit úplnou analýzu řešení**.

- **Zakázat CodeLens**

    Visual Studio provede úlohu **Najít všechny odkazy** na každé metodě, která je zobrazena. CodeLens poskytuje funkce, jako je vložené zobrazení počtu odkazů. Práce se provádí v samostatném procesu, jako je *ServiceHub. RoslynCodeAnalysisService32*. Ve velkých řešeních nebo v systémech s omezením prostředků může mít tato funkce výrazný dopad na výkon. Pokud máte problémy s pamětí, například při načítání velkého řešení na 4 GB počítače nebo vysokém využití procesoru pro tento proces, můžete CodeLens vypnout a uvolnit tak prostředky.

    Chcete-li zakázat **CodeLens**, zvolte **nástroje** > **Možnosti** > **textový editor** > **všechny jazyky** > **CodeLens**a zrušte výběr funkce.

    > [!NOTE]
    > CodeLens je k dispozici v edicích Professional a Enterprise sady Visual Studio.

### <a name="other-tools-and-extensions"></a>Další nástroje a rozšíření

- **Zakázat rozšíření**

    Rozšíření jsou další softwarové komponenty přidané do sady Visual Studio, které poskytují nové funkce nebo zvyšují stávající funkce. Rozšíření mohou být často zdrojem potíží s prostředky paměti. Pokud dochází k potížím s prostředky paměti, zkuste zakázat rozšíření po jednom, abyste viděli, jak má dopad na scénář nebo pracovní postup.

   ::: moniker range="vs-2017"

    Pokud chcete rozšíření zakázat, v nabídce **nástroje** > **rozšíření a aktualizace**a zakažte konkrétní rozšíření.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Pokud chcete rozšíření zakázat, můžete přejít na **rozšíření** > **Spravovat rozšíření**a zakázat konkrétní rozšíření.

   ::: moniker-end

- **Zakázat Návrhář XAML**

    Návrhář XAML je ve výchozím nastavení povolen, ale spotřebovává prostředky pouze v případě, že otevřete soubor *. XAML* . Pokud pracujete se soubory XAML, ale nechcete používat funkci návrháře, zakažte tuto funkci, aby uvolnila nějakou paměť.

    Pokud chcete **Návrhář XAML**zakázat, v nabídce **nástroje** > **možnosti** > **Návrhář XAML** > **Povolit Návrhář XAML**a zrušte výběr možnosti.

- **Odebrat úlohy**

    Pomocí Instalační program pro Visual Studio můžete odebrat úlohy, které se už nepoužívají. Tato akce může zjednodušit náklady na spuštění a za běhu tím, že přeskočí balíčky a sestavení, které už nepotřebujete.

## <a name="force-a-garbage-collection"></a>Vynutit uvolňování paměti

CLR používá systém správy paměti pro uvolňování paměti. V tomto systému se někdy paměť používá v objektech, které už nejsou potřeba. Tento stav je dočasný. systém uvolňování paměti uvolní tuto paměť na základě jeho heuristiky výkonu a využití prostředků. Můžete vynutit, aby CLR shromáždil veškerou nepoužitou paměť pomocí klávesových zkratek v aplikaci Visual Studio. Pokud dojde k výraznému čekání na uvolnění paměti pro shromažďování a vynutíte uvolňování paměti, měli byste vidět využití paměti při zrušení procesu *devenv. exe* ve **Správci úloh**. Tuto metodu je zřídka nutné použít. Po dokončení náročné operace (například úplné sestavení, relace ladění nebo otevřené události řešení) vám však může usnadnit určení množství paměti, které tento proces skutečně používá. Vzhledem k tomu, že je sada Visual Studio smíšená (spravovaná & nativní), je možné, že nativní přidělování a uvolňování paměti můžou být v případě omezeného počtu paměťových prostředků konkurenční. V podmínkách vysokého využití paměti může pomáhat vynutit spouštění uvolňování paměti.

Chcete-li vynutit uvolňování paměti, použijte klávesovou zkratku **ctrl**+**Alt**+**Shift**+**F12**, **CTRL**+**ALT**+**SHIFT**+**F12** (stiskněte dvakrát).

Pokud vynucené uvolňování paměti zajistí spolehlivou práci, zaznamenejte zprávu prostřednictvím nástroje pro zpětnou vazbu sady Visual Studio, protože toto chování je pravděpodobně chyba.

Podrobný popis systému uvolňování paměti CLR najdete v tématu [základní informace o uvolňování paměti](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Viz také

- [Optimalizace výkonu sady Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Rychlejší načítání řešení (blog sady Visual Studio)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
