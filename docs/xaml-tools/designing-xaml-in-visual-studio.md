---
title: Návrh XAML v aplikaci Visual Studio a v Blend pro Visual Studio
titleSuffix: ''
description: Seznamte se s možnostmi nástrojů pro vizuální návrh v aplikaci Visual Studio a Blend pro Visual Studio pro sestavování uživatelského rozhraní a prostředí v jazyce XAML.
ms.custom: SEO-VS-2020
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: fc6c05b925c8dac5c488ce3eea79ca683b590b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876417"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Návrh XAML v aplikaci Visual Studio a Blend pro Visual Studio

Visual Studio a Blend pro Visual Studio poskytují i vizuální nástroje pro vytváření poutavých uživatelských rozhraní a bohatých mediálních prostředí pomocí XAML pro nejrůznější typy aplikací. Jak integrované vývojové prostředí (IDE) sdílí společnou sadu funkcí, včetně editoru Visual XAML (Designer). Blend pro Visual Studio, který podporuje platformy WPF a UWP, poskytuje další nástroje pro návrh vizuálních stavů a vytváření animací.

Můžete přepínat mezi Visual Studio a Blend pro Visual Studio a můžete dokonce i mít stejný projekt otevřený v obou prostředích ve stejnou dobu. Změny uložené do souborů XAML v jednom rozhraní IDE lze použít prostřednictvím automatického opětovného načtení při přepnutí na jiné integrované vývojové prostředí (IDE). Způsob opětovného načtení můžete řídit tak, že přejdete na **nástroje**  >  **Možnosti** pro  >    >  **dokumenty** prostředí v obou IDE.

## <a name="installation"></a>Instalace

- Pokud chcete vytvářet aplikace WPF, nainstalujte do sady Visual Studio úlohu **vývoj desktopových** aplikací pro .NET. Nainstaluje se taky Blend pro Visual Studio.

     ![Snímek úlohy vývoj desktopových aplikací pro .NET z Instalační program pro Visual Studio](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Pokud chcete vytvářet aplikace pro UWP, nainstalujte **Univerzální platforma Windows vývojové** úlohy v aplikaci Visual Studio. Nainstaluje se taky Blend pro Visual Studio.

     ![Snímek obrazovky Univerzální platforma Windows úlohy vývoje z Instalační program pro Visual Studio](../xaml-tools/media/uwp-workload.png)

- K vytváření aplikací Xamarin. Forms nainstalujte **vývoj mobilních aplikací pomocí technologie .NET** v aplikaci Visual Studio. Blend pro Visual Studio není *nainstalováno* . Blend nepodporuje aplikace Xamarin. Forms.

     ![Snímek obrazovky vývoje mobilních aplikací s využitím úlohy .NET z Instalační program pro Visual Studio](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Sdílené možnosti

Pro většinu základních úloh vývoje aplikace Visual Studio a Blend pro Visual Studio sdílí stejnou sadu Windows a možností s některými drobnými rozdíly. Mezi nejdůležitější funkce patří:

- **IntelliSense:** V obou prostředích podporuje funkce IntelliSense, jako je například dokončování příkazů.

- **Ladění:** Můžete ladit v [aplikaci Visual Studio](inspect-xaml-properties-while-debugging.md) a [Blend pro Visual Studio](../xaml-tools/debug-xaml-in-blend.md), včetně nastavení zarážek v kódu pro ladění spuštěné aplikace a pomocí [horkého opětovného načtení](../xaml-tools/xaml-hot-reload.md) ke změně kódu XAML v době, kdy aplikace běží. Aby bylo možné zachovat konzistentní prostředí ladění pomocí sady Visual Studio, Blend pro Visual Studio zahrnuje většinu ladění oken a panelů nástrojů sady Visual Studio.

- **Opětovné načtení souboru:** Soubory XAML můžete upravovat buď v aplikaci Visual Studio, nebo v Blend pro Visual Studio. Upravené soubory, které byly uloženy, se automaticky znovu načítají při přepínání mezi prostředím IDEs. Způsob opětovného načtení můžete řídit tak, že přejdete na **nástroje**  >  **Možnosti** pro  >    >  **dokumenty** prostředí v obou IDE.

- **Synchronizovaná rozložení a nastavení:** Vzhledy oken a nastavení nástroje pro přizpůsobení návrhu pro Visual Studio nebo Blend pro Visual Studio se synchronizují napříč vašimi zařízeními a verzemi, když se přihlásíte pomocí stejného účtu přizpůsobení. Viz [synchronizace nastavení napříč více počítači](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Pokročilé možnosti v Blend pro Visual Studio

Pokud chcete zvýšit produktivitu, zvažte použití Blend pro Visual Studio pro následující úlohy. Jedná se o oblasti, kde Blend pro Visual Studio nabízí více funkcí, než je Návrhář sady Visual Studio nebo samotný kód.

| Úkol | Visual Studio | Blend for Visual Studio | Další informace |
| - | - | - | - |
| **Návrh vizuálních stavů** | Neexistuje žádný nástroj, který by vám mohl pomáhat s návrhem vizuálních stavů. je nutné je vytvořit programově. | Pomocí návrhových nástrojů můžete změnit vzhled ovládacího prvku na základě jeho stavu. | [Vizuální stavy](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Vytváření animací** |Pro animace není k dispozici žádný nástroj pro návrh; je nutné je vytvořit programově. To vyžaduje pochopení systému animace a časování v technologii WPF a rozsáhlé znalosti kódování.|Animace můžete vizuálně vytvářet a můžete je zobrazit ve Blend pro Visual Studio. To je rychlejší a přesnější než vytváření animací v kódu. Můžete přidat triggery pro zpracování interakce uživatele a můžete přepnout do kódu pro přidání obslužných rutin událostí a dalších funkcí.|[Animace objektů](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Změnit tvar a text na cesty pro snadnější manipulaci**|Nepodporováno|Můžete provádět drobné nebo výrazné změny tvarů (například obdélníky a elipsy) jejich převodem na cesty, které poskytují lepší ovládací prvek pro úpravy. Můžete přetvarovat nebo kombinovat cesty a vytvářet složené cesty z více tvarů.<br /><br />Můžete také převést textové bloky na cesty, abyste je mohli manipulovat jako vektorové obrázky.|[Kreslení tvarů a cest](../xaml-tools/draw-shapes-and-paths.md)|
|**Úpravy ovládacích prvků, šablon a stylů**|Vyžaduje kódování a znalosti stylů a šablon WPF.|Přepněte libovolný obrázek do ovládacího prvku.<br /><br />Pomocí nástrojů pro úpravu šablon můžete provádět změny ovládacích prvků, stylů a šablon pomocí několika kliknutí myší.<br /><br />Například můžete použít prostředky stylu Blend pro Visual Studio k implementaci běžných ovládacích prvků WPF (jako jsou tlačítka, seznamy, posuvníky, nabídky atd.) a změnit jejich barvu, styl nebo podkladovou šablonu přímo v Blend pro Visual Studio. V případě potřeby můžete přepnout na kód pro dokončení dotykového ovládání.|[Úpravy stylu objektů](modify-the-style-of-objects-in-blend.md)|
|**Připojení uživatelského rozhraní k datům**|Můžete vytvořit zdroj dat z prostředků, jako jsou SQL Server databáze, WCF nebo webová služba, objekt nebo SharePointový seznam, a pak vytvořit propojení zdroje dat s ovládacími prvky uživatelského rozhraní.<br /><br />Data v době návrhu se musí vytvořit ručně pro interaktivní prostředí návrhu.|Pro .NET Framework aplikace Vytvářejte ukázková data snadno pro vytváření prototypů a testování. Až budete připraveni, přepněte na živá data.<br /><br />Možnosti generování dat Blend pro Visual Studio jsou nedokončené (můžete rychle přidat názvy, čísla, adresy URL a fotky) a můžete si ušetřit spoustu času.<br /><br />Pro živá data můžete navazovat ovládací prvky uživatelského rozhraní k souboru XML nebo k jakémukoli zdroji dat CLR.|[Zobrazení dat](display-data-in-blend.md)|

Další informace o pokročilém návrhu jazyka XAML naleznete v tématu [Vytvoření uživatelského rozhraní pomocí Blend pro Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Přehled XAML](xaml-overview.md)
- [Přehled Blend pro Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
