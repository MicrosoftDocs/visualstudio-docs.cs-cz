---
title: Přehled Návrháře XAML
description: Přečtěte si o uživatelském rozhraní a funkcích Návrhář XAML v Blend pro Visual Studio, které poskytuje vizuální rozhraní, které vám pomůžou navrhovat aplikace založené na jazyce XAML.
ms.date: 03/03/2020
ms.topic: conceptual
ms.custom: contperf-fy21q4, SEO-VS-2020
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.DocumentOutline
- Blend.Start.Dev12
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 8f022d0f27977488fb089f2cffb40aad22365b46
ms.sourcegitcommit: 4a91c63683ba1c1832b1ba96657862a849320d81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2021
ms.locfileid: "110565229"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Vytvoření uživatelského rozhraní pomocí Návrháře XAML

Návrhář XAML v aplikaci Visual Studio a Blend pro Visual Studio poskytuje vizuální rozhraní, které vám umožňuje navrhovat aplikace založené na jazyce XAML, například WPF a UWP. Můžete vytvořit uživatelská rozhraní pro aplikace přetažením ovládacích prvků z okna panelu nástrojů (okno assets v Blend pro Visual Studio) a nastavením vlastností v okno Vlastnosti. Můžete také upravit XAML přímo v zobrazení XAML.

V případě pokročilých uživatelů můžete [Návrhář XAML přizpůsobit](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin. Forms nepodporuje návrháře XAML. Pokud chcete zobrazit uživatelská rozhraníy Xamarin. Forms XAML a upravit je, když je aplikace spuštěná, použijte pro Xamarin. Forms XAML Hot reload. Další informace naleznete na stránce [XAML Hot reloading pro Xamarin. Forms (Preview)](/xamarin/xamarin-forms/xaml/hot-reload/) .

## <a name="xaml-designer-workspace"></a>Pracovní prostor Návrhář XAML

Pracovní prostor v Návrhář XAML se skládá z několika prvků vizuálního rozhraní. Mezi ně patří *Kreslicí* plocha (což je vizuální návrhová plocha), Editor XAML, okno Osnova dokumentu (objekty a časová osa okno v Blend pro Visual Studio) a okno Vlastnosti. Chcete-li otevřít Návrhář XAML, klikněte pravým tlačítkem myši na soubor XAML v **Průzkumník řešení** a vyberte možnost **Návrhář zobrazení**.

Návrhář XAML poskytuje zobrazení XAML a synchronizovaný zobrazení Návrh vykresleného kódu XAML vaší aplikace. Se souborem XAML otevřeným v aplikaci Visual Studio nebo Blend pro Visual Studio můžete přepínat mezi zobrazení Návrh a zobrazením XAML pomocí karet **design** a **XAML** . K přepnutí zobrazeného okna v horní části můžete použít tlačítka odkládacích **panelů na** panelu ![ Návrhář XAML ](media/swap-panes.PNG) : buď na návrhovou plochu, nebo na Editor XAML.

### <a name="design-view"></a>zobrazení Návrh

V zobrazení Návrh je okno obsahující návrhovou plochu aktivním oknem a můžete ho použít jako primární pracovní plochu. Můžete ji použít pro vizuální návrh stránky v aplikaci přidáním, kreslením nebo úpravou prvků. Další informace najdete v tématu [práce s prvky v Návrhář XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Tento obrázek znázorňuje kreslicí panel v zobrazení Návrh.

![zobrazení Návrh Návrhář XAML](media/xaml-artboard.png)

V kreslicí kreslicí skříni jsou k dispozici tyto funkce:

**Snaplines**

Zarovnávací čáry *jsou hranice zarovnání,* které se zobrazují jako čáry s červenou přerušovanou čárou, které ukazují, kdy jsou zarovnané hrany ovládacích prvků nebo když jsou zarovnané směrné plány textu. Hranice zarovnání se zobrazí pouze v **případě, že je povolené přichycení k zarovnávacím čarům.**

**Mřížkové kolejnice**

Mřížkové kolejnice se používají ke správě řádků a sloupců na [panelu](xref:Windows.UI.Xaml.Controls.Grid) Mřížka. Můžete vytvářet a odstraňovat řádky a sloupce a upravovat jejich relativní šířky a výšky. Svislá mřížka, která se nachází vlevo od kreslicí desky, se používá pro řádky a vodorovná čára, která se zobrazuje nahoře, se používá pro sloupce.

**Doplňky pro ovládacího prvku Grid**

Doplňková vlastnost mřížky se zobrazí jako trojúhelník, který má na kolejnici mřížky připojenou svislou nebo vodorovnou čáru. Při přetažení ovládacího prvku Grid adorner se při pohybu myší aktualizují šířky nebo výšky sousedících sloupců nebo řádků.

Doplňky mřížky slouží k řízení šířky a výšky řádků a sloupců mřížky. Kliknutím na kolejnice mřížky můžete přidat nový sloupec nebo řádek. Když přidáte nový řádek nebo čáru sloupce pro panel Mřížka, který má dva nebo více sloupců nebo řádků, zobrazí se mimo kolejnici mini toolbar, který umožňuje explicitně nastavit šířku a výšku. Mini toolbar umožňuje nastavit možnosti velikosti pro řádky a sloupce mřížky.

![Adorner mřížky v Návrhář XAML](media/grid-adorner.png)

**Změna velikosti popisovačů**

U vybraných ovládacích prvků se zobrazí úchyty pro změnu velikosti a umožní vám změnit velikost ovládacího prvku. Při změně velikosti ovládacího prvku se obvykle zobrazují hodnoty šířky a výšky, které vám pomůžou velikost ovládacího prvku. Další informace o manipulaci s ovládacími prvky v **návrhovém** zobrazení najdete v tématu [práce s prvky v Návrhář XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Okraje**

Okraje znázorňují velikost pevného prostoru mezi okrajem ovládacího prvku a okrajem jeho kontejneru. Okraje ovládacího prvku lze nastavit pomocí vlastností [okraj](xref:Windows.UI.Xaml.FrameworkElement.Margin) v nabídce **rozložení** v okně **vlastnosti** .

**Doplňky okrajů**

Použijte doplňky okrajů ke změně okrajů prvku relativně vzhledem k jeho kontejneru rozložení. Když je doplněk pro úpravy okrajů otevřený, okraj není nastavený a doplněk pro úpravy okrajů zobrazuje porušený řetězec. V případě, že okraj není nastaven, prvky zůstanou na místě, když je velikost kontejneru rozložení změněna v době běhu. Když je doplněk pro úpravy okrajů uzavřený, doplněk pro úpravy okrajů zobrazuje nepřerušený řetězec a prvky se pohybují s okrajem, protože se velikost kontejneru rozložení mění za běhu (okraj zůstane pevný).

**Obslužné rutiny elementů**

Můžete upravit element pomocí obslužných rutin, které se zobrazí na návrhové ploše, když přesunete ukazatel myši na rohy modrého pole, které obklopuje element. Tyto popisovače umožňují otočit, změnit velikost, překlopit, přesunout nebo přidat poloměr rohu do prvku. Symbol pro popisovač elementu se liší podle funkce a mění se v závislosti na přesném umístění ukazatele. Pokud nevidíte obslužné rutiny elementu, ujistěte se, že je prvek vybrán.

V zobrazení **Návrh** jsou k dispozici další příkazy návrhové plochy v levém dolním rohu okna, jak je znázorněno zde:

![Příkazy zobrazení Návrh](media/xaml-design-view-controls.png)

Tyto příkazy jsou k dispozici na tomto panelu nástrojů:

**Zoom**

Přiblížení umožňuje změnit velikost návrhové plochy. Můžete zvětšit z 12,5% na 800% nebo vybrat možnosti, například **přizpůsobit výběr** a **vše**.

**Zobrazit/skrýt mřížku pro přichycení**

Zobrazí nebo skryje mřížku přichycení, která zobrazuje mřížku. Mřížka se používá,  když povolíte přichycení k mřížce nebo **přichycení k zachytávání**.

**Zapnutí/vypnutí přichycení k mřížce**

Pokud **je zapnuté přichycení** k mřížce, má prvek tendenci při přetažení na kreslicí panel zarovnat s nejbližší vodorovnou a svislou mřížkou.

**Přepnutí pozadí kreslicí plochy**

Přepíná mezi světlým a tmavým pozadím.

**Zapnutí/vypnutí přichycení k zachytávání**

Zarovnané čáry pomáhají vzájemně zarovnat ovládací prvky. Pokud **je přichycení** k zarovnávacím čarám povolené, při přetažení ovládacího prvku vzhledem k jiným ovládacím prvkům se hranice zarovnání zobrazí, když jsou hrany a text některých ovládacích prvků zarovnané vodorovně nebo svisle. Hranice zarovnání se zobrazí jako červená přerušovaná čára.

**Zakázání kódu projektu**

Zakáže kód [projektu,](debugging-or-disabling-project-code-in-xaml-designer.md)například vlastní ovládací prvky a převaděče hodnot, a znovu načte návrháře.

### <a name="xaml-view"></a>Zobrazení XAML

V **zobrazení XAML** je okno obsahující editor XAML aktivním oknem a editor XAML je vaším primárním nástrojem pro vytváření obsahu. Jazyk jazyk Extensible Application Markup Language (XAML) (XAML) poskytuje deklarativní slovník založený na jazyce XML pro určení uživatelského rozhraní aplikace. Zobrazení XAML zahrnuje IntelliSense, automatické formátování, zvýrazňování syntaxe a navigaci ve značce. Následující obrázek ukazuje zobrazení XAML s otevřenou nabídkou IntelliSense:

![Zobrazení XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Okno Osnova dokumentu

Okno Osnova dokumentu v Visual Studio se podobá oknu [Objekty a časová osa v](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) Blend pro Visual Studio. Osnova dokumentu vám pomůže provádět tyto úlohy:

- Zobrazení hierarchické struktury všech prvků na návrhové ploše.

- Vyberte prvky, abyste je mohli upravovat. Můžete je například přesunout v hierarchii nebo nastavit jejich vlastnosti v okno Vlastnosti. Další informace najdete v tématu [práce s prvky v Návrhář XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Vytvořte a upravte šablony pro prvky, které jsou ovládacími prvky.

- [Vytváření animací](animate-objects-in-xaml-designer.md) (pouze Blend pro Visual Studio).

Chcete-li zobrazit okno Osnova dokumentu v aplikaci Visual Studio, vyberte v řádku nabídek možnost **Zobrazit**  >  **Další**  >  **osnovu dokumentu** Windows.
Chcete-li zobrazit okno objekty a časová osa v Blend pro Visual Studio, v řádku nabídek vyberte **Zobrazit**  >  **Osnova dokumentu**.

![Okno Osnova dokumentu v aplikaci Visual Studio](media/document-outline-window.png)

Hlavní zobrazení v okně Osnova/Objekty a časová osa v dokumentu zobrazuje hierarchii dokumentu ve stromové struktuře. Hierarchickou povahu osnovy dokumentu můžete použít k prohlédnutí dokumentu na různých úrovních podrobností a k zamčení a skrytí prvků jednotlivě nebo ve skupinách. V okně Osnova/Objekty a časová osa jsou k dispozici následující možnosti:

**Zobrazit/skrýt**

Zobrazí nebo skryje prvky návrhové plochy. Zobrazuje se jako symbol oka, pokud je zobrazený. Můžete také stisknout **kombinaci kláves CTRL** + **h** pro skrytí prvku a **posunutí** + **CTRL** + **h** k zobrazení.

**Zamknout/odemknout**

Zamkne nebo odemkne prvky návrhové plochy. Uzamčené prvky nelze upravovat. Při uzamčení se zobrazí jako symbol zámku. Můžete také stisknout **Ctrl** L a +  uzamknout prvek a **stisknutím** + **Klávesy Shift** + **L** ho odemknout.

**Vrácení oboru do pageRoot**

Možnost v horní části okna Osnova/Objekty a časová osa dokumentu, které zobrazuje symbol šipky nahoru, se přesune do předchozího oboru. Nastavení rozsahu platí jenom v případě, že se nacházíte v oboru stylu nebo šablony.

## <a name="properties-window"></a>Vlastnosti – okno

Okno **Vlastnosti** umožňuje nastavit hodnoty vlastností u ovládacích prvků. Vypadá takto:

![Vlastnosti – okno](media/xaml-designer-properties-window.png)

V horní části okna **Vlastnosti** jsou různé možnosti:

- Změňte název aktuálně vybraného prvku v **poli Název.**
- V levém horním rohu je ikona, která představuje aktuálně vybraný prvek.
- Pokud chcete vlastnosti uspořádat podle kategorie nebo abecedy, klikněte **v** seznamu **Uspořádat podle** na Kategorie ,  **Název** nebo Zdroj.
- Pokud chcete zobrazit seznam událostí ovládacího prvku, klikněte na tlačítko **Události,** které se zobrazí jako symbol blesku.
- Pokud chcete vyhledat vlastnost, začněte do vyhledávacího pole zadat název vlastnosti. V **okně** Vlastnosti se zobrazí vlastnosti, které odpovídají vašemu hledání při psaní.

Některé vlastnosti umožňují nastavit upřesňující vlastnosti výběrem tlačítka se šipkou dolů.

Napravo od každé hodnoty vlastnosti je značka *vlastnosti, která* se zobrazuje jako symbol pole. Vzhled značky vlastnosti určuje, jestli je na vlastnost použitá datová vazba nebo prostředek. Například symbol bílého rámečku označuje výchozí hodnotu, symbol černé skříňky obvykle označuje, že byl použit místní prostředek, a oranžové pole obvykle indikuje, že byla použita datová vazba. Když kliknete na značku vlastnosti, můžete přejít k definici stylu, otevřít tvůrce datových vazeb nebo otevřít výběr prostředku.

Další informace o používání vlastností a zpracování událostí najdete v tématu [Úvod do ovládacích prvků a vzorů](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Viz také

- [Práce s elementy v Návrháři XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Postup vytvoření a použití prostředku](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Návod: Vazba s daty v Návrháři XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
