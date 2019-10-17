---
title: Návrh XAML v sadě Visual Studio a Blendu
titleSuffix: ''
ms.date: 08/05/2019
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 88e03307f9f72d50fb77818ffaf632debbd830f6
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451141"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Návrh XAML v aplikaci Visual Studio a Blend pro Visual Studio

Visual Studio a Blend pro Visual Studio poskytují i vizuální nástroje pro vytváření poutavých uživatelských rozhraní a bohatých mediálních prostředí pomocí XAML pro nejrůznější typy aplikací. Jak integrované vývojové prostředí (IDE) sdílí společnou sadu funkcí, včetně editoru Visual XAML (Designer). Blend pro Visual Studio, který podporuje platformy WPF a UWP, poskytuje další nástroje pro návrh vizuálních stavů a vytváření animací.

Můžete přepínat mezi Visual Studio a Blend pro Visual Studio a můžete dokonce i mít stejný projekt otevřený v obou prostředích ve stejnou dobu. Změny uložené do souborů XAML v jednom rozhraní IDE lze použít prostřednictvím automatického opětovného načtení při přepnutí na jiné integrované vývojové prostředí (IDE). Způsob opětovného načtení můžete řídit tak, že přejdete na **nástroje**@no__t**možnosti**-1  > **prostředí** > **dokumentů** v obou IDE.

## <a name="installation"></a>Instalace

- Pokud chcete vytvářet aplikace WPF, nainstalujte do sady Visual Studio úlohu **vývoj desktopových** aplikací pro .NET. Nainstaluje se taky Blend pro Visual Studio.
- Pokud chcete vytvářet aplikace pro UWP, nainstalujte **Univerzální platforma Windows vývojové** úlohy v aplikaci Visual Studio. Nainstaluje se taky Blend pro Visual Studio.
- K vytváření aplikací Xamarin. Forms nainstalujte **vývoj mobilních aplikací pomocí technologie .NET** v aplikaci Visual Studio. Blend pro Visual Studio není *nainstalováno* . Blend nepodporuje aplikace Xamarin. Forms.

## <a name="shared-capabilities"></a>Sdílené možnosti

Pro většinu základních úloh vývoje aplikace Visual Studio a Blend pro Visual Studio sdílí stejnou sadu Windows a možností s některými drobnými rozdíly. Mezi nejdůležitější funkce patří:

- **IntelliSense:** V obou prostředích podporuje funkce IntelliSense, jako je například dokončování příkazů.

- **Ladění:** Můžete ladit v [aplikaci Visual Studio](../debugger/inspect-xaml-properties-while-debugging.md) a [Blend pro Visual Studio](../xaml-tools/debug-xaml-in-blend.md), včetně nastavení zarážek v kódu pro ladění spuštěné aplikace a pomocí [horkého opětovného načtení](../xaml-tools/xaml-hot-reload.md) ke změně kódu XAML v době, kdy aplikace běží. Aby bylo možné zachovat konzistentní prostředí ladění pomocí sady Visual Studio, Blend pro Visual Studio zahrnuje většinu ladění oken a panelů nástrojů sady Visual Studio.

- **Opětovné načtení souboru:** Soubory XAML můžete upravovat buď v aplikaci Visual Studio, nebo v Blend pro Visual Studio. Upravené soubory, které byly uloženy, se automaticky znovu načítají při přepínání mezi prostředím IDEs. Způsob opětovného načtení můžete řídit tak, že přejdete na **nástroje**@no__t**možnosti**-1  > **prostředí** > **dokumentů** v obou IDE.

- **Synchronizovaná rozložení a nastavení:** Přizpůsobené rozložení a nastavení oken nástrojů pro Visual Studio nebo Blend pro Visual Studio se synchronizují napříč vašimi zařízeními a verzemi, když se přihlásíte pomocí stejného účtu přizpůsobení. Viz [synchronizace nastavení napříč více počítači](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Pokročilé možnosti v Blend pro Visual Studio

Pokud chcete zvýšit produktivitu, zvažte použití Blend pro Visual Studio pro následující úlohy. Jedná se o oblasti, kde Blend pro Visual Studio nabízí více funkcí, než je Návrhář sady Visual Studio nebo samotný kód.

| Úloha | Visual Studio | Blend for Visual Studio | Další informace |
| - | - | - | - |
| **Návrh vizuálních stavů** | Neexistuje žádný nástroj, který by vám mohl pomáhat s návrhem vizuálních stavů. je nutné je vytvořit programově. | Pomocí návrhových nástrojů můžete změnit vzhled ovládacího prvku na základě jeho stavu. | [Vizuální stavy](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Vytváření animací** |Pro animace není k dispozici žádný nástroj pro návrh; je nutné je vytvořit programově. To vyžaduje pochopení systému animace a časování v technologii WPF a rozsáhlé znalosti kódování.|Animace můžete vizuálně vytvářet a můžete je zobrazit ve Blend pro Visual Studio. To je rychlejší a přesnější než vytváření animací v kódu. Můžete přidat triggery pro zpracování interakce uživatele a můžete přepnout do kódu pro přidání obslužných rutin událostí a dalších funkcí.|[Animace objektů](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Změnit tvar a text na cesty pro snadnější manipulaci**|Není podporováno.|Můžete provádět drobné nebo výrazné změny tvarů (například obdélníky a elipsy) jejich převodem na cesty, které poskytují lepší ovládací prvek pro úpravy. Můžete přetvarovat nebo kombinovat cesty a vytvářet složené cesty z více tvarů.<br /><br />Můžete také převést textové bloky na cesty, abyste je mohli manipulovat jako vektorové obrázky.|[Kreslení tvarů a cest](../xaml-tools/draw-shapes-and-paths.md)|
|**Úpravy ovládacích prvků, šablon a stylů**|Vyžaduje kódování a znalosti stylů a šablon WPF.|Přepněte libovolný obrázek do ovládacího prvku.<br /><br />Pomocí nástrojů pro úpravu šablon můžete provádět změny ovládacích prvků, stylů a šablon pomocí několika kliknutí myší.<br /><br />Například můžete použít prostředky stylu Blend pro Visual Studio k implementaci běžných ovládacích prvků WPF (jako jsou tlačítka, seznamy, posuvníky, nabídky atd.) a změnit jejich barvu, styl nebo podkladovou šablonu přímo v Blend pro Visual Studio. V případě potřeby můžete přepnout na kód pro dokončení dotykového ovládání.|[Úpravy stylu objektů](../designers/modify-the-style-of-objects-in-blend.md)|
|**Připojení uživatelského rozhraní k datům**|Můžete vytvořit zdroj dat z prostředků, jako jsou SQL Server databáze, WCF nebo webová služba, objekt nebo SharePointový seznam, a pak vytvořit propojení zdroje dat s ovládacími prvky uživatelského rozhraní.<br /><br />Data v době návrhu se musí vytvořit ručně pro interaktivní prostředí návrhu.|Pro .NET Framework aplikace Vytvářejte ukázková data snadno pro vytváření prototypů a testování. Až budete připraveni, přepněte na živá data.<br /><br />Možnosti generování dat Blend pro Visual Studio jsou nedokončené (můžete rychle přidat názvy, čísla, adresy URL a fotky) a můžete si ušetřit spoustu času.<br /><br />Pro živá data můžete navazovat ovládací prvky uživatelského rozhraní k souboru XML nebo k jakémukoli zdroji dat CLR.|[Zobrazení dat](../designers/display-data-in-blend.md)|

Další informace o pokročilém návrhu jazyka XAML naleznete v tématu [Vytvoření uživatelského rozhraní pomocí Blend pro Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).
