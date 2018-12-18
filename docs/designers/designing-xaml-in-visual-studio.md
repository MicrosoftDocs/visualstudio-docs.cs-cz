---
title: Použít XAML
ms.date: 07/17/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 40b2d37e5b416047aa8a6fecf8c2c9cca0c681ca
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062977"
---
# <a name="design-xaml-in-visual-studio"></a>Návrh XAML v sadě Visual Studio

Visual Studio a Blend for Visual Studio poskytují vizuální nástroje pro sestavování poutavější uživatelské rozhraní a bohatý mediální prostředí s XAML pro širokou škálu typů aplikací. Oba nástroje sdílejí společnou sadu funkcí, včetně o vizuální editor XAML, ale poskytuje program Blend pro Visual Studio další návrhové nástroje pro pokročilé úlohy, jako je animace a chování.

Proces návrhu aplikace závisí na nástroj, který zvolíte a cílovou platformu. Tento článek porovnává návrhové nástroje XAML v sadě Visual Studio a nástroje Blend for Visual Studio. Další podrobné návody pro používání nástroje naleznete v následujících tématech:

- [Vytvoření uživatelského rozhraní pomocí návrháře XAML v sadě Visual Studio](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)

## <a name="choose-the-right-tool"></a>Zvolte nejvhodnější nástroj

Návrh nástrojů podle vaší volby je do značné míry závisí na vašich dovednostech. Pokud jste více orientovaný na kód, můžete napsat kód XAML v sadě Visual Studio k provádění úloh pokročilý design. Pokud jste více orientovaný na návrh, Blend for Visual Studio umožňuje provádět pokročilé úlohy bez nutnosti psaní kódu.

Můžete přepínat vpřed a zpět mezi Visual Studio a nástroj Blend for Visual Studio a může probíhat dokonce na stejný projekt otevřít v obou ve stejnou dobu. Změny souborů XAML v jedné integrované vývojové prostředí můžete použít prostřednictvím automatické nové načtení přepnutím na jiné prostředí IDE. Můžete řídit chování opětovného načtení prostřednictvím možností v **nástroje** > **možnosti** dialogové okno v IDE.

### <a name="shared-capabilities"></a>Sdílené možnosti

Nejzákladnější úkoly integrovaném vývojovém prostředí sady Visual Studio a nástroje Blend for Visual Studio sdílet stejnou sadu windows a funkce, s nějaké drobné rozdíly. Mezi nejdůležitější funkce patří:

- **Konzistentní uživatelské rozhraní:** můžete navrhnout vaše aplikace v rámci kontextu známé uživatelské rozhraní sady Visual Studio, díky přepínání mezi integrovanými vývojovými prostředími příjemný a produktivní prostředí. Blend pro Visual Studio používá Visual Studio tmavý motiv, který vám pomůže soustředit na obsah, který při návrhu kontrast mezi vaším obsahem a uživatelské rozhraní, což zlepšuje. Zobrazit [vytvoření uživatelského rozhraní pomocí návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     ![Blend for Visual Studio IDE](../designers/media/blendide.png)

- **XAML IntelliSense:** obě Integrovaná vývojová prostředí podporují všechny běžné možnosti, které očekáváte od technologie IntelliSense, dokončování příkazů, podpora pro běžné operace editoru, například přidávání poznámek a formátování kódu a navigace k prostředkům, včetně vazby a kódu.

- **Základní možnosti ladění:** teď můžete ladit v Blendu, včetně nastavení zarážek v kódu k ladění vaší běžící aplikaci. Zachování konzistentní možnosti ladění pomocí sady Visual Studio, nástroje Blend for Visual Studio obsahuje většinu ladění systému windows a panelů nástrojů sady Visual Studio. Pokročilé funkce ladění, jako diagnostiku a analýzy kódu jsou pouze k dispozici v sadě Visual Studio. Zobrazit [ladit v sadě Visual Studio](../debugger/debugging-in-visual-studio.md).

- **Soubor znovu načíst prostředí:** souborů XAML v obou Blend for Visual Studio nebo Visual Studio můžete upravit, a mít vašich upravených souborů znovu načíst automaticky jak mezi nimi přepínat. K minimalizuje přerušení pracovních postupů, teď můžete nastavit váš soubor znovu načíst předvolby v dialogovém okně soubor znovu načíst.

     ![Opětovné načítání souborů](../designers/media/blendfilereload.png)

- **Synchronizovat nastavení a rozložení:** vlastní rozložení umožňuje uložit a použít vlastní nastavení rozložení okna nástroje. Když se přihlásíte pomocí stejného účtu Microsoft synchronizaci Visual Studia tato vlastní nastavení a předvolby pro Visual Studio i programu Blend for Visual Studio napříč počítači. Zobrazit [synchronizaci nastavení mezi více počítači](../ide/synchronized-settings-in-visual-studio.md).

- **Průzkumník řešení common:** **Průzkumníka řešení** vám poskytne uspořádaný náhled vašich projektů a jejich soubory, jakož i přístup k příkazů přidružených s nimi. Pomocí Průzkumníka řešení je snazší pracovat s velkými objemy podnikových projektů. Zobrazit [řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md).

- **Team Explorer:** pomocí Průzkumníku týmových projektů můžete spravovat vaše projekty s úložišti GIT nebo TFS usnadňuje spolupráci mezi týmy. Zobrazit [práci v Průzkumníku týmových projektů](/azure/devops/user-guide/work-team-explorer).

- **NuGet:** můžete spravovat balíčky NuGet v sadě Visual Studio i programu Blend for Visual Studio. Správce balíčků NuGet je Správce balíčků pro rozhraní .NET Framework, která zjednodušuje instalace a odebrání balíčků z řešení.

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Pokročilé funkce v programu Blend for Visual Studio

Pokud chcete zvýšit vaši produktivitu, vezměte v úvahu pomocí nástroje Blend for Visual Studio pro následující úlohy. Jedná se o oblasti, kde Blend for Visual Studio nabízí další rychlost a funkce než návrháře aplikace Visual Studio nebo samotný kód.

|Chcete-li|Visual Studio|Blend for Visual Studio|Další informace|
|--------|-------------------| - | - |
|**Vytváření animací**|Neexistuje žádná návrhářský nástroj pro animace; je nutné je vytvořit prostřednictvím kódu programu. To vyžaduje pochopení animace a časování systému v projektech WPF a rozsáhlé znalosti kódování.|Vizuálně vytvářet animace a můžete si zobrazte jejich náhled v programu Blend for Visual Studio. Toto je rychlejší a přesnější, než vytváření animace v kódu. Můžete přidat aktivační události na zpracovávají interakci s uživatelem, a můžete přepnout na kód pro přidání obslužné rutiny událostí a další funkce.|[Animace objektů](../designers/animate-objects-in-xaml-designer.md)|
|**Proměňte cesty ke snadnější práci s tvary a text**|Není podporováno.|Drobné nebo výrazné změny můžete provádět obrazce (například obdélníky a tři tečky) převedením na cesty, které poskytují lepší úprav ovládacího prvku. Můžete změnit tvar nebo kombinace cesty a vytvořit složené cesty z více tvarů.<br /><br /> Bloky textu můžete také převést do cesty k manipulaci s nimi jako vektorové obrázky.|[Kreslení tvarů a cest](../designers/draw-shapes-and-paths.md)|
|**Přidání interaktivity návrhů uživatelského rozhraní**|Vyžaduje kódu C#, Visual Basic nebo C++.|Přetáhnout myší na ovládací prvky k přidání interaktivity do statické návrhy chování. Chování jsou připravené k použití kódu, které zapouzdřují funkce, jako je například přetažení, Lupa a změnám vizuálního stavu. Je stále početnější sadu chování, ze kterých můžete použít, a můžete vytvořit svoje vlastní.<br /><br /> Každý chování potom můžete přizpůsobit změnou jeho vlastností v programu Blend for Visual Studio nebo přidáním obslužných rutin událostí v kódu.|[Vložení ovládacích prvků a změna jejich chování](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|
|**Použití kresby Adobe**|Není podporováno.|Importovat aplikace Adobe FXG aplikace PhotoShop a Illustrator kresby a implementují uživatelské rozhraní v programu Blend for Visual Studio.|[Vložení obrázků, videí a zvukových klipů](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|
|**Upravit ovládací prvky, šablony a styly**|Vyžaduje kódování a znalost WPF – styly a šablony.|Zapněte všechny bitové kopie do ovládacího prvku.<br /><br /> Pomocí nástroje pro úpravy šablon provádět změny na ovládací prvky, styly a šablony pomocí několika kliknutí myší.<br /><br /> Například můžete použít nástroj Blend for Visual Studio prostředků stylu k implementaci běžných ovládacích prvků WPF (například tlačítka, seznamy, posuvníky, nabídkách atd.) a změnit jejich barva, styl nebo základní šablony přímo v programu Blend for Visual Studio. Pokud chcete, můžete kód pro doladění poté přejděte.|[Úpravy stylu objektů](../designers/modify-the-style-of-objects-in-blend.md)|
|**Vaše uživatelské rozhraní se připojit k datům**|Můžete vytvořit zdroj dat z prostředků, jako jsou databáze systému SQL Server, WCF webové služby, objekty nebo Sharepointové seznamy a vytvoření vazby zdroje dat pro vaše ovládací prvky uživatelského rozhraní.<br /><br /> Dat doby návrhu musí být vytvořeny ručně pro interaktivní návrhové prostředí.|Vytvořte ukázková data u vytváření prototypů a testování. Přepnout na živá data, jakmile budete připraveni.<br /><br /> Blend pro vytvoření datové sady Visual Studio možnosti nejsou vyřízeny (můžete přidat názvy, čísla, adresy URL a fotografie snadno za chodu) a ušetřit spoustu času.<br /><br /> Pro dynamická data můžete svázat ovládací prvky uživatelského rozhraní do souboru XML nebo k libovolnému zdroji dat CLR.|[Zobrazení dat](../designers/display-data-in-blend.md)|

Další informace o pokročilý design XAML najdete v tématu [vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).
