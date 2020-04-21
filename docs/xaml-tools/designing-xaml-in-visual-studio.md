---
title: Návrh XAML v sadě Visual Studio a ve směsi pro Visual Studio
titleSuffix: ''
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: eb18a2face5d9f1831bec35379a423f272c3e6ce
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649823"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Návrh xaml v sadě Visual Studio a blend pro Visual Studio

Visual Studio a Blend for Visual Studio poskytují vizuální nástroje pro vytváření poutavých uživatelských rozhraní a multimediálních možností s XAML pro různé typy aplikací. Obě integrovaná vývojová prostředí (IDE) sdílejí společnou sadu funkcí, včetně vizuálního editoru XAML (návrháře). Blend pro Visual Studio, který podporuje platformy WPF a UPW, poskytuje další nástroje pro navrhování vizuálních stavů a vytváření animací.

Můžete přepínat tam a zpět mezi Visual Studio a Blend pro Visual Studio a můžete dokonce mít stejný projekt otevřený v obou INEŽ současně. Změny, které jsou uloženy do souborů XAML v jednom ide lze použít pomocí automatického opětovného načtení při přepnutí do jiného ide. Chování opětovného načtení můžete řídit přechodem na**dokumenty** **prostředí** >  **Tools** > **Options** > V obou ide.

## <a name="installation"></a>Instalace

- Chcete-li vytvořit aplikace WPF, nainstalujte **úlohu vývoje plochy .NET** ve Visual Studiu. Blend pro Visual Studio bude také nainstalován.

     ![Snímek obrazovky s úlohou vývoje plochy .NET z Instalační služby sady Visual Studio](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Chcete-li vytvořit aplikace UPW, nainstalujte **úlohu vývoje univerzální platformy Windows** ve Visual Studiu. Blend pro Visual Studio bude také nainstalován.

     ![Snímek obrazovky s úlohou vývoje univerzální platformy Windows z Instalační služby Sady Visual Studio](../xaml-tools/media/uwp-workload.png)

- Chcete-li vytvořit aplikace Xamarin.Forms, nainstalujte vývoj Mobile s zatížením **.NET** ve Visual Studiu. Blend pro Visual Studio *není* nainstalován; Blend nepodporuje aplikace Xamarin.Forms.

     ![Snímek obrazovky s vývojem mobilních zařízení s úlohami rozhraní .NET z Instalační služby sady Visual Studio](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Sdílené možnosti

Pro většinu základních vývojových úloh Visual Studio a Blend pro Visual Studio sdílet stejnou sadu oken a možností, s některé jemné rozdíly. Mezi nejdůležitější funkce patří:

- **Technologie IntelliSense:** Obě idcy podporují funkce Technologie IntelliSense, jako je například dokončení příkazu.

- **Ladění:** Můžete ladit v [Sadě Visual Studio](inspect-xaml-properties-while-debugging.md) a Blend pro Visual [Studio](../xaml-tools/debug-xaml-in-blend.md), včetně nastavení zarážek v kódu pro ladění spuštěné aplikace a pomocí [Hot Reload](../xaml-tools/xaml-hot-reload.md) změnit kód XAML, když je aplikace spuštěná. Chcete-li zachovat konzistentní ladění prostředí s Visual Studio, Blend pro Visual Studio zahrnuje většinu ladění sady Visual Studio okna a panely nástrojů.

- **Znovu načíst soubor:** Soubory XAML můžete upravit v sadě Visual Studio nebo Blend for Visual Studio. Upravené soubory, které byly uloženy, se při přepínání mezi IDS automaticky načítají. Chování opětovného načtení můžete řídit přechodem na**dokumenty** **prostředí** >  **Tools** > **Options** > V obou ide.

- **Synchronizovaná rozložení a nastavení:** Rozložení okna nástroje přizpůsobení návrhu a předvolby nastavení pro Visual Studio nebo Blend for Visual Studio jsou synchronizovány mezi vašimi zařízeními a verzemi při přihlášení pomocí stejného účtu individuálního nastavení. Viz [Synchronizace nastavení ve více počítačích](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Pokročilé funkce ve blendu pro Visual Studio

Chcete-li zvýšit produktivitu, zvažte použití blendu pro visual studio pro následující úkoly. Jedná se o oblasti, kde blend pro Visual Studio nabízí více funkcí než návrháře sady Visual Studio nebo samotný kód.

| Úkol | Visual Studio | Blend for Visual Studio | Další informace |
| - | - | - | - |
| **Návrh vizuálních stavů** | Neexistuje žádný nástroj, který by vám pomohl navrhnout vizuální stavy; je nutné je vytvořit programově. | Pomocí návrhových nástrojů můžete změnit vzhled ovládacího prvku na základě jeho stavu. | [Vizuální stavy](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Vytváření animací** |Neexistuje žádný návrhový nástroj pro animace; musíte je vytvořit programově. To vyžaduje pochopení animací a časování systému wpf a rozsáhlé znalosti kódování.|Animace můžete vytvářet vizuálně a zobrazit jejich náhled v blendu pro Visual Studio. To je rychlejší a přesnější než vytváření animací v kódu. Můžete přidat aktivační události pro zpracování interakce uživatele a můžete přepnout na kód a přidat obslužné rutiny událostí a další funkce.|[Animace objektů](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Proměňte tvary a text na cesty pro snadnější manipulaci**|Není podporováno.|Můžete provést jemné nebo dramatické změny obrazců (například obdélníků a elips) jejich převedením na cesty, které poskytují lepší kontrolu úprav. Můžete změnit tvar nebo zkombinovat cesty a vytvořit složené cesty z více tvarů.<br /><br />Textové bloky můžete také převést na cesty a manipulovat s nimi jako s vektorovými obrazy.|[Kreslení tvarů a cest](../xaml-tools/draw-shapes-and-paths.md)|
|**Úpravy ovládacích prvků, šablon a stylů**|Vyžaduje kódování a znalost stylů a šablon WPF.|Přeměňte libovolný obrázek na ovládací prvek.<br /><br />Pomocí nástrojů pro úpravy šablony můžete provádět změny ovládacích prvků, stylů a šablon pouhými několika kliknutími myši.<br /><br />Můžete například použít blend pro visual studio styl prostředky k implementaci běžných ovládacích prvků WPF (jako jsou tlačítka, seznamy, posuvníky, nabídky, atd.) a změnit jejich barvu, styl nebo základní šablony přímo v Blend for Visual Studio. Pak můžete přepnout na kód pro dokončovací úpravy, pokud chcete.|[Úpravy stylu objektů](modify-the-style-of-objects-in-blend.md)|
|**Připojení ui k datům**|Zdroj dat můžete vytvořit z prostředků, jako je například databáze serveru SQL Server, WCF nebo seznam webové služby, objekt u nebo sharepoint, a potom svázat zdroj dat s ovládacími prvky uživatelského rozhraní.<br /><br />Data návrhu musí být vytvořena ručně pro interaktivní návrh.|Pro aplikace rozhraní .NET Framework snadno vytvořte ukázková data pro vytváření prototypů a testování. Až budete připraveni, přepněte na živá data.<br /><br />Blend pro visual studio je generování dat možnosti jsou vynikající (můžete přidat jména, čísla, adresy URL a fotografie snadno za běhu), a můžete ušetřit spoustu času.<br /><br />U živých dat můžete svázat ovládací prvky ui se souborem XML nebo s libovolným zdrojem dat CLR.|[Zobrazení dat](display-data-in-blend.md)|

Další informace o pokročilém návrhu XAML naleznete [v tématu Vytvoření uživatelského rozhraní pomocí blendu pro Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Přehled XAML](xaml-overview.md)
- [Přehled prolnutí pro Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
