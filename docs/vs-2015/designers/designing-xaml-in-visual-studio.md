---
title: Navrhování XAML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c48e44e0488d61e3061d680962bf22e42935090
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664714"
---
# <a name="designing-xaml-in-visual-studio"></a>Návrh XAML v aplikaci Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio a Blend pro Visual Studio poskytují i vizuální nástroje pro vytváření poutavých uživatelských rozhraní a bohatých mediálních prostředí pro aplikace Windows Desktop, web, [Windows Phone](https://msdn.microsoft.com/library/windowsphone/develop/jj683071.aspx)a [Windows Store](https://msdn.microsoft.com/library/windows/apps/jj129478.aspx) založené na jazyce XAML. Nasdílejte společnou sadu oken návrh a nástroj a Editor XAML, ale Blend pro Visual Studio poskytují další vývojové nástroje pro pokročilejší úlohy, jako je například animace a chování.

## <a name="choosing-the-right-tool"></a>Výběr správného nástroje
 Vaše volba nástrojů pro návrh je převážně závislá na vaší sadě dovedností. Pokud máte více orientované na kód, můžete napsat kód XAML v aplikaci Visual Studio a provádět tak i pokročilé úkoly návrhu. Pokud pracujete podrobněji, Blend pro Visual Studio vám umožní provádět pokročilé úlohy bez psaní kódu.

 Můžete přepínat mezi Visual Studio a Blend pro Visual Studio a také můžete mít stejný projekt otevřený současně. Změny provedené v souborech XAML v jednom integrovaném vývojovém prostředí lze použít prostřednictvím automatického opětovného načtení při přepnutí na jiné integrované vývojové prostředí (IDE). Chování při opakovaném načítání můžete řídit prostřednictvím možností v dialogovém okně **nástroje**, **Možnosti** v obou IDE.

### <a name="shared-capabilities"></a>Sdílené možnosti
 Pro většinu základních úloh vývojové prostředí (IDE) pro Visual Studio a Blend pro Visual Studio sdílí stejnou sadu Windows a možností s některými drobnými rozdíly. Mezi nejdůležitější funkce patří:

- **Konzistentní uživatelské rozhraní:** Své aplikace můžete navrhovat v rámci známého kontextu uživatelského rozhraní sady Visual Studio, což usnadňuje přepínání mezi různými příjemnými a produktivními prostředími. Blend pro Visual Studio používá tmavý motiv sady Visual Studio, který vám pomůže soustředit se na obsah, který navrhujete, tím, že zlepšíte kontrast mezi obsahem a uživatelským rozhraním. Další informace najdete v tématu [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md).

     ![Blend pro Visual Studio IDE](../designers/media/blendide.png "BlendIDE")

- **IntelliSense XAML:** Obě tyto systémy podporují všechny běžné možnosti, které byste od IntelliSense očekávali, včetně dokončování příkazů, podpory běžných operací editoru, jako je přidávání komentářů a formátování kódu, navigace na zdroje, vazby a kód.

- **Základní možnosti ladění:** Nyní můžete ladit v Blendu, včetně nastavení zarážek v kódu, abyste mohli ladit spuštěnou aplikaci. Aby bylo možné zachovat konzistentní prostředí ladění pomocí sady Visual Studio, Blend pro Visual Studio zahrnuje většinu ladění oken a panelů nástrojů sady Visual Studio. Pokročilé možnosti ladění, jako jsou diagnostika a analýza kódu, jsou k dispozici pouze v aplikaci Visual Studio. Viz [ladění v aplikaci Visual Studio](../debugger/debugging-in-visual-studio.md).

- **Možnosti opětovného načtení souboru:** Soubory XAML můžete upravovat buď v Blend pro Visual Studio nebo v aplikaci Visual Studio, a při přepínání mezi nimi se automaticky načítají upravované soubory. Chcete-li minimalizovat přerušení pracovního postupu, můžete nyní nastavit předvolby opětovného načtení souborů v dialogovém okně znovu načíst soubor.

     ![Možnosti opětovného načtení souboru](../designers/media/blendfilereload.png "BlendFileReload")

- **Synchronizovaná rozložení a nastavení:** Vlastní rozložení umožňují uložit a použít přizpůsobení rozložení oken nástrojů. Visual Studio bude synchronizovat tyto vlastní nastavení a předvolby pro Visual Studio i Blend pro Visual Studio v různých počítačích, když se přihlásíte se stejným účet Microsoft. Viz [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

- **Běžné Průzkumník řešení:** Průzkumník řešení poskytuje uspořádané zobrazení vašich projektů a jejich souborů a také připravený přístup k příkazům, které jsou k nim přidruženy. S Průzkumník řešení je snazší pracovat s velkými podnikovými projekty. Viz [řešení a projekty](../ide/solutions-and-projects-in-visual-studio.md).

- **Team Explorer:** Pomocí Team Explorer můžete spravovat své projekty pomocí úložišť GIT nebo TFS, abyste usnadnili týmovou spolupráci. Viz [work in Team Explorer](https://msdn.microsoft.com/library/fd7a5cf7-7916-4fa0-b5e6-5a83cf377a02).

- **NuGet:** Balíčky NuGet můžete spravovat jak v aplikaci Visual Studio, tak i v Blend pro Visual Studio. NuGet je správce balíčků pro .NET Framework, který zjednodušuje instalaci a odebrání balíčků z řešení.

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Pokročilé možnosti v Blend pro Visual Studio
 Pokud chcete zvýšit produktivitu, zvažte použití Blend pro Visual Studio pro následující úlohy. Jedná se o oblasti, kde Blend pro Visual Studio nabízí větší rychlost a funkčnost než Návrhář sady Visual Studio nebo samotný kód.

|Chcete-li|Visual Studio|Blend for Visual Studio|Další informace|
|--------|-------------------|-----------------------------|----------------------|
|**Vytváření animací**|Pro animace není k dispozici žádný nástroj pro návrh; je nutné je vytvořit programově. To vyžaduje pochopení systému animace a časování v technologii WPF a rozsáhlé znalosti kódování.|Animace můžete vizuálně vytvářet a můžete je zobrazit ve Blend pro Visual Studio. To je rychlejší a přesnější než vytváření animací v kódu. Můžete přidat triggery pro zpracování interakce uživatele a můžete přepnout do kódu pro přidání obslužných rutin událostí a dalších funkcí.|[Animace objektů](../designers/animate-objects-in-xaml-designer.md)|
|**Změnit tvar a text na cesty pro snadnější manipulaci**|Není podporováno.|Můžete provádět drobné nebo výrazné změny tvarů (například obdélníky a elipsy) jejich převodem na cesty, které poskytují lepší ovládací prvek pro úpravy.  Můžete přetvarovat nebo kombinovat cesty a vytvářet složené cesty z více tvarů.<br /><br /> Můžete také převést textové bloky na cesty, abyste je mohli manipulovat jako vektorové obrázky.|[Kreslení tvarů a cest](../designers/draw-shapes-and-paths.md)|
|**Přidání interaktivity k návrhům uživatelského rozhraní**|Vyžaduje C#, Visual Basic nebo C++ kód.|Přetáhněte chování na ovládací prvky a přidejte do svých statických návrhů interaktivitu. Chování jsou fragmenty kódu připravené k použití, které zapouzdřují funkce, jako jsou například přetahování, přiblížení a vizuální změny stavu. Existuje rostoucí sada chování, ze kterých si můžete vybrat, a můžete si vytvořit svoje vlastní.<br /><br /> Pak můžete přizpůsobit každé chování změnou jeho vlastností v Blend pro Visual Studio nebo přidáním obslužných rutin událostí v kódu.|[Vložení ovládacích prvků a změna jejich chování](../designers/insert-controls-and-modify-their-behavior-in-xaml-designer.md)|
|**Použití Adobe kreseb**|Není podporováno.|Importujte kresby Adobe FXG, PhotoShop nebo Illustrator a implementujte uživatelské rozhraní v Blend pro Visual Studio.|[Vložení obrázků, videí a zvukových klipů](../designers/insert-images-videos-and-audio-clips-in-xaml-designer.md)|
|**Úpravy ovládacích prvků, šablon a stylů**|Vyžaduje kódování a znalosti stylů a šablon WPF.|Přepněte libovolný obrázek do ovládacího prvku.<br /><br /> Pomocí nástrojů pro úpravu šablon můžete provádět změny ovládacích prvků, stylů a šablon pomocí několika kliknutí myší.<br /><br /> Například můžete použít prostředky stylu Blend pro Visual Studio k implementaci běžných ovládacích prvků WPF (jako jsou tlačítka, seznamy, posuvníky, nabídky atd.) a změnit jejich barvu, styl nebo podkladovou šablonu přímo v Blend pro Visual Studio. V případě potřeby můžete přepnout na kód pro dokončení dotykového ovládání.|[Úpravy stylu objektů](../designers/modify-the-style-of-objects-in-blend.md)|
|**Připojení uživatelského rozhraní k datům**|Můžete vytvořit zdroj dat z prostředků, jako jsou SQL Server databáze, WCF nebo webové služby, objekty nebo SharePointové seznamy, a vytvořit navázání zdroje dat na ovládací prvky uživatelského rozhraní.<br /><br /> Data v době návrhu se musí vytvořit ručně pro interaktivní prostředí návrhu.|Vytvářejte ukázková data snadno pro vytváření prototypů a testování. Až budete připraveni, přepněte na živá data.<br /><br /> Možnosti generování dat Blend pro Visual Studio jsou nedokončené (můžete přidávat názvy, čísla, adresy URL a fotky snadno v průběhu) a můžete si ušetřit spoustu času.<br /><br /> Pro živá data můžete navazovat ovládací prvky uživatelského rozhraní k souboru XML nebo k jakémukoli zdroji dat CLR.|[Zobrazení dat](../designers/display-data-in-blend.md)|

 Další informace o pokročilém návrhu jazyka XAML naleznete v tématu. [Vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
