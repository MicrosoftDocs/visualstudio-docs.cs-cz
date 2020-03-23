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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79303020"
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Tipy a triky pro výkon visual studia

Visual Studio doporučení výkonu jsou určeny pro situace nedostatku paměti, které mohou nastat ve výjimečných případech. V těchto situacích můžete optimalizovat některé funkce sady Visual Studio, které pravděpodobně nepoužíváte. Následující tipy nejsou určeny jako obecná doporučení.

> [!NOTE]
> Pokud máte potíže s používáním produktu kvůli problémům s pamětí, dejte nám vědět prostřednictvím [nástroje pro zpětnou vazbu](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="use-a-64-bit-os"></a>Použití 64bitového operačního e-s

Pokud inovujete systém z 32bitové verze systému Windows na 64bitovou verzi, rozbalíte velikost virtuální paměti dostupné v sadě Visual Studio z 2 GB na 4 GB. To umožňuje Visual Studio zpracovat výrazně větší úlohy, i když je 32bitový proces.

Další informace naleznete v [tématu Omezení paměti](/windows/desktop/Memory/memory-limits-for-windows-releases) a [použití /LARGEADDRESSAWARE v 64bitovém systému Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="disable-automatic-file-restore"></a>Zakázat automatické obnovení souborů

Visual Studio automaticky znovu otevře dokumenty, které zůstaly otevřené v předchozí relaci. To může prodloužit dobu načtení řešení až o 30 % nebo více v závislosti na typu projektu a otevírání dokumentů. Návrháři jako Windows Forms a XAML a některé soubory JavaScriptu a psacího psa, může být pomalé otevřít.

Visual Studio vás upozorní ve žlutém pruhu při automatické obnovení dokumentu způsobuje řešení načíst výrazně pomalejší. Automatické znovuotevření souborů můžete zakázat následujícím postupem:

1. Vyberte**Možnosti** **nástrojů,** > chcete-li otevřít dialogové okno **Volby.**

1. Na stránce **Projekty a** > **Obecné** řešení zrušte výběr **možnosti Znovu otevřít dokumenty při načtení řešení**.

Pokud zakážete automatické obnovení souborů, rychlý způsob, jak přejít k souborům, které chcete otevřít, je pomocí jednoho z příkazů [Přejít na:](../ide/go-to.md)

- Chcete-li obecnou funkci **Přejít na,** vyberte **možnost Upravit** > **přejít** > **na vše**nebo stiskněte **kombinaci kláves Ctrl**+**T**.

- Přechod na poslední umístění úprav v řešení pomocí funkce **Upravit** > **přejít na** > **umístění poslední úpravy**nebo stisknutím **klávesy Ctrl**+**Shift**+**Backspace**.

- Pomocí **funkce Přejít** na poslední soubor zobrazíte seznam naposledy navštívených souborů v řešení. Vyberte **Možnost Upravit** > **přejít na** > **poslední soubor**nebo stiskněte **ctrl**+**1**, **Ctrl**+**R**.

## <a name="configure-debugging-options"></a>Konfigurace možností ladění

Pokud obvykle dochází paměť během ladění relací, můžete optimalizovat výkon provedením jedné nebo více změn konfigurace.

- **Povolit pouze můj kód**

    Nejjednodušší optimalizace je povolit funkci **Jen můj kód,** která načte pouze symboly pro váš projekt. Povolení této funkce může vést k významnému ukládání paměti pro ladění spravovaných aplikací (.NET). Tato možnost je již ve výchozím nastavení povolena v některých typech projektů.

    Chcete-li povolit **možnost Pouze můj kód**, zvolte **Možnosti** > **Options** > **ladění** > **nástrojů obecně**a pak vyberte **Povolit pouze můj kód**.

- **Určení symbolů, které se mají načíst**

    Pro nativní ladění je načítání souborů symbolů (*Pdb*) nákladné z hlediska paměťových prostředků. Nastavení symbolu ladicího programu můžete nakonfigurovat tak, aby šetřilo paměť. Obvykle nakonfigurujete řešení pouze načíst moduly z projektu.

    Chcete-li určit načítání symbolů, zvolte**Volby** >  **nástrojů** > **Ladění** > **symbolů**.

    Nastavte možnosti **pouze zadané moduly** namísto **všechny moduly** a pak určit, které moduly chcete načíst. Při ladění můžete také klepnout pravým tlačítkem myši na určité moduly v okně **Moduly** a explicitně zahrnout modul do zatížení symbolu. (Chcete-li otevřít okno při ladění, zvolte **Ladění** > **modulů systému****Windows** > .)

    Další informace naleznete v [tématu Understand symbol files](/visualstudio/ide/visual-studio-performance-tips-and-tricks?view=vs-2019).

- **Zakázat diagnostické nástroje**

    Doporučujeme po použití zakázat profilování procesoru. Tato funkce může spotřebovat velké množství prostředků. Jakmile je povoleno profilování procesoru, tento stav je trvalý v následujících ladicích relacích, takže stojí za to explicitně vypnout, když to hotovo. Můžete ušetřit některé prostředky zakázáním diagnostické nástroje při ladění, pokud nepotřebujete poskytované funkce.

    Chcete-li **diagnostické nástroje**zakázat , spusťte relaci ladění, zvolte**Možnosti** >  **nástroje** > **Povolit diagnostické nástroje**a odznačte tuto možnost.

    Další informace naleznete [v tématu Profilování nástroje](../profiling/profiling-feature-tour.md).

## <a name="disable-tools-and-extensions"></a>Zakázání nástrojů a rozšíření

Některé nástroje nebo rozšíření lze vypnout za účelem zvýšení výkonu.

> [!TIP]
> Často můžete izolovat problémy s výkonem vypnutím rozšíření jeden po druhém a opětovnou kontrolou výkonu.

### <a name="managed-language-service-roslyn"></a>Služba spravovaného jazyka (Roslyn)

Informace o aspekty výkonu platformy kompilátoru .NET ("Roslyn") naleznete v [tématu Důležité informace o výkonu pro velká řešení](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Zakázat úplnou analýzu řešení**

    Visual Studio provádí analýzu celého řešení s cílem poskytnout bohaté zkušenosti o chybách před vyvolání sestavení. Tato funkce je užitečná pro identifikaci chyb co nejdříve. Pro velká řešení však tato funkce může spotřebovat značné prostředky paměti. Pokud dochází k tlaku paměti nebo podobné problémy, můžete zakázat toto prostředí uvolnit tyto prostředky. Ve výchozím nastavení je tato možnost povolena pro jazyk Visual Basic a zakázána pro jazyk C#.

    Chcete-li zakázat **úplnou analýzu řešení**, zvolte**Textový editor****Možnosti** >  **nástroje** > a vyberte **možnost Visual Basic** nebo **C#**. Zvolte **Upřesnit** a zrušte výběr **možnosti Povolit úplnou analýzu řešení**.

- **Zakázat CodeLens**

    Visual Studio provádí **najít všechny odkazy úlohy** na každé metodě, jak je zobrazena. CodeLens poskytuje funkce, jako je například inline zobrazení počtu odkazů. Práce se provádí v samostatném procesu, jako je *ServiceHub.RoslynCodeAnalysisService32*. Ve velkých řešeních nebo v systémech s omezenými prostředky může mít tato funkce významný dopad na výkon. Pokud dochází k problémům s pamětí, například při načítání velkého řešení na počítači 4 GB nebo vysoké využití procesoru pro tento proces, můžete zakázat CodeLens uvolnit prostředky.

    Chcete-li zakázat **CodeLens**, zvolte**Možnosti** >  **nástroje** > **Textový editor** > **Všechny jazyky** > **CodeLens**a odznačte funkci.

    > [!NOTE]
    > CodeLens je k dispozici v edicích Professional a Enterprise v sadě Visual Studio.

### <a name="other-tools-and-extensions"></a>Další nástroje a rozšíření

- **Zakázat rozšíření**

    Rozšíření jsou další softwarové součásti přidané do sady Visual Studio, které poskytují nové funkce nebo rozšiřují stávající funkce. Rozšíření může být často zdrojem problémů s prostředky paměti. Pokud dochází k problémům s paměťovými prostředky, zkuste zakázat rozšíření jeden po druhém, abyste zjistili, jaký vliv má to na scénář nebo pracovní postup.

   ::: moniker range="vs-2017"

    Chcete-li rozšíření zakázat, přejděte na **rozšíření a aktualizace** **nástrojů** > a zakažte konkrétní rozšíření.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

    Chcete-li rozšíření zakázat, přejděte na **rozšíření** > **Spravovat rozšíření**a zakažte konkrétní rozšíření.

   ::: moniker-end

- **Zakázat návrháře XAML**

    Návrhář XAML je ve výchozím nastavení povolen, ale spotřebovává prostředky pouze v případě, že otevřete soubor *Xaml.* Pokud pracujete se soubory XAML, ale nechcete používat funkci návrháře, zakažte tuto funkci, abyste uvolnili některé paměti.

    Chcete-li zakázat **návrháře XAML**, přejděte na > **možnosti** >  **nástrojů:****Návrhář XAML** > **Povolit návrháře XAML**a tuto možnost odznačte.

- **Odebrání úloh**

    Instalační službu sady Visual Studio můžete použít k odebrání úloh, které se již nepoužívají. Tato akce může zjednodušit náklady na spuštění a běh za běhu přeskočením balíčků a sestavení, které již nejsou potřeba.

## <a name="force-a-garbage-collection"></a>Vynucení uvolňování paměti

CLR používá systém pro správu paměti uvolňování paměti. V tomto systému někdy paměť používá objekty, které již nejsou potřeba. Tento stav je dočasný; systém uvolňování paměti uvolní tuto paměť na základě její heuristiky výkonu a využití prostředků. Clr můžete vynutit shromažďování nevyužité paměti pomocí klávesové zkratky v sadě Visual Studio. Pokud je značné množství odpadků čekání na sběr a vynutit uvolňování paměti, měli byste vidět využití paměti procesu *devenv.exe* přetažení **ve Správci úloh**. Je zřídka nutné použít tuto metodu. Však po dokončení nákladné operace (například úplné sestavení, ladění relace nebo otevřené řešení události), může vám pomoci určit, kolik paměti je skutečně používá procesem. Vzhledem k tomu, že Visual Studio je smíšené (spravované & nativní), je občas možné pro nativní přidělování a uvolňování paměti soutěžit o omezené paměťové prostředky. Za podmínek vysoké využití paměti může pomoci vynutit spuštění systému uvolňování paměti.

Chcete-li vynutit uvolňování paměti, použijte klávesovou zkratku: **Ctrl**+**Alt**+**Shift**+**F12**, **Ctrl**+**Alt**+**Shift**+**F12** (stiskněte ji dvakrát).

Pokud vynucení uvolňování paměti spolehlivě provede váš scénář pracovat, soubor sestavy prostřednictvím nástroje zpětné vazby sady Visual Studio jako toto chování je pravděpodobně chyba.

Podrobný popis uvolňování CLR naleznete v [tématu Základy uvolňování paměti](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Viz také

- [Optimalizace výkonu sady Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Rychlejší načítání řešení (blog visual studia)](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
