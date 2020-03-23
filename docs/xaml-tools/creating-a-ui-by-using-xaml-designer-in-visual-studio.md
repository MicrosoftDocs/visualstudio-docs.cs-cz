---
title: Přehled Návrháře XAML
ms.date: 03/03/2020
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
- Blend.Start.Dev12
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a2a0e25779df1e0b91a69518dc2257119e33cca4
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79190340"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Vytvoření uživatelského rozhraní pomocí Návrháře XAML

Návrhář XAML v sadě Visual Studio a Blend for Visual Studio poskytuje vizuální rozhraní, které vám pomůže navrhnout aplikace založené na XAML, jako jsou aplikace WPF, UpWP a Xamarin.Forms. Uživatelská rozhraní pro aplikace můžete vytvořit přetažením ovládacích prvků z okna Panelu nástrojů (okno Datové zdroje v prolnutí pro sadu Visual Studio) a nastavením vlastností v okně Vlastnosti. XAML můžete také upravit přímo v zobrazení XAML.

Pro pokročilé uživatele můžete dokonce [přizpůsobit XAML Designer](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin.Forms nepodporuje návrháře XAML. Chcete-li zobrazit xamarin.forms XAML umělá nastavení a upravit je, když je aplikace spuštěná, použijte XAML Hot Reload pro Xamarin.Forms. Další informace naleznete na stránce [XAML Hot Reload for Xamarin.Forms (Preview).](/xamarin/xamarin-forms/xaml/hot-reload/)

## <a name="xaml-designer-workspace"></a>Pracovní prostor Návrháře XAML

Pracovní prostor v Návrháři XAML se skládá z několika prvků vizuálního rozhraní. Patří mezi ně *kreslicí plochy* (což je vizuální návrhová plocha), editor XAML, okno Osnova dokumentu (objekty a okno časové osy v prolnutí pro visual studio) a okno Vlastnosti. Chcete-li otevřít Návrhář XAML, klepněte pravým tlačítkem myši na soubor XAML v **Průzkumníkovi řešení** a zvolte **Návrhář zobrazení**.

XAML Designer poskytuje zobrazení XAML a synchronizované návrhové zobrazení vykreslených značek XAML vaší aplikace. Se souborem XAML otevřeným v sadě Visual Studio nebo Blend for Visual Studio můžete přepínat mezi návrhovým zobrazením a zobrazením XAML pomocí karet **Návrh** a **XAML.** Pomocí tlačítka **Zaměnit podokna** ![v Návrháři](media/swap-panes.PNG) XAML můžete použít tlačítko Zaměnit podokna a přepnout okno, které se zobrazí nahoře: buď kreslicí plochy, nebo editor XAML.

### <a name="design-view"></a>Návrhové zobrazení

V návrhovém zobrazení je aktivním oknem okno obsahující kreslicí plochy a můžete ho použít jako primární pracovní plochu. Můžete ji použít k vizuálnímu návrhu stránky v aplikaci přidáním, kreslením nebo úpravou prvků. Další informace naleznete [v tématu Práce s prvky v Návrháři XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Tento obrázek znázorňuje kreslicí plochy v návrhovém zobrazení.

![Návrh aplikace XAML Designer](media/xaml-artboard.png)

Tyto funkce jsou k dispozici v kreslicí desce:

**Snaplines**

Snaplines jsou *hranice trasy,* které se zobrazují jako červeně přerušované čáry, které se zobrazují, když jsou okraje ovládacích prvků zarovnány nebo když jsou zarovnány účaří textu. Hranice trasy se zobrazí pouze v případě, že je povoleno **přitahování na snaplines.**

**Kolejnice sítě**

Kolejnice mřížky se používají ke správě řádků a sloupců v panelu [Mřížka.](xref:Windows.UI.Xaml.Controls.Grid) Můžete vytvářet a odstraňovat řádky a sloupce a můžete upravit jejich relativní šířky a výšky. Svislá kolejnice mřížky, která se zobrazí vlevo od kreslicí plochy, se používá pro řádky a vodorovná čára, která se zobrazí nahoře, se používá pro sloupce.

**Mřížka adorners**

Vylepšení mřížky se zobrazí jako trojúhelník, ke kterému je připojena svislá nebo vodorovná čára na kolejnici Mřížka. Při přetahování grid adorner, šířky nebo výšky sousedních sloupců nebo řádků aktualizovat při pohybu myší.

Vylepšení mřížky se používají k řízení šířky a výšky řádků a sloupců mřížky. Nový sloupec nebo řádek můžete přidat kliknutím na lišty Mřížka. Když přidáte nový řádek nebo řádek sloupce pro panel Mřížka, který má dva nebo více sloupců nebo řádků, zobrazí se mimo lištu minipanel nástrojů, který umožňuje explicitně nastavit šířku a výšku. Minipanel nástrojů umožňuje nastavit volby velikosti pro řádky a sloupce mřížky.

![Ozdoba mřížky v Návrháři XAML](media/grid-adorner.png)

**Změna velikosti úchytů**

U vybraných ovládacích prvků se zobrazí úchyty pro měnit velikost a umožňují změnit velikost ovládacího prvku. Při změně velikosti ovládacího prvku, šířka a výška hodnoty obvykle zobrazí, které vám pomohou velikost ovládacího prvku. Další informace o manipulaci s ovládacími prvky v **návrhovém** zobrazení naleznete [v tématu Práce s prvky v Návrháři XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Okraje**

Okraje představují velikost pevné mezery mezi okrajem ovládacího prvku a okrajem jeho kontejneru. Okraje ovládacího prvku můžete nastavit pomocí vlastností [okraje](xref:Windows.UI.Xaml.FrameworkElement.Margin) v části **Rozložení** v okně **Vlastnosti.**

**Ozdoby okrajů**

Pomocí ozdoby okrajů můžete změnit okraje prvku vzhledem k jeho kontejneru rozložení. Když je otevřena ozdoba okraje, okraj není nastaven a ozdoba okraje zobrazí přerušený řetězec. Pokud okraj není nastaven, prvky zůstávají na místě, když je velikost kontejneru rozložení za běhu. Když je ozdoba okraje uzavřena, ozdobovač okrajů zobrazí nepřerušený řetězec a prvky se přesunou s okrajem, protože kontejner rozložení se změní za běhu (okraj zůstane pevný).

**Úchyty elementů**

Prvek můžete upravit pomocí úchytů elementu, které se zobrazí na kreslicí desce, když přesunete ukazatel nad rohy modrého rámečku, který obklopuje prvek. Tyto úchyty umožňují otáčet, měnit velikost, překlápět, přesouvat nebo přidávat poloměr rohu k prvku. Symbol pro popisovač prvku se liší podle funkce a mění se v závislosti na přesném umístění ukazatele. Pokud nevidíte úchyty prvku, ujistěte se, že je vybraný prvek.

V **návrhovém** zobrazení jsou v levém dolním rohu okna k dispozici další příkazy kreslicí plochy, jak je znázorněno zde:

![Příkazy návrhového zobrazení](media/xaml-design-view-controls.png)

Tyto příkazy jsou k dispozici na tomto panelu nástrojů:

**Zoom**

Zoom umožňuje velikost návrhové plochy. Můžete zvětšit z 12,5 % na 800 % nebo vybrat možnosti, jako je **volba přizpůsobit** a **přizpůsobit vše**.

**Zobrazit/skrýt mřížku přichycení**

Zobrazí nebo skryje mřížku přichycení, která zobrazuje mřížku. Mřížky se používají, když povolíte **přitahování k mřížky** nebo **přitahování na snaplines**.

**Zapnutí/vypnutí přitahování k mřížky**

Pokud je povoleno **přitahování k mřížky,** prvek má tendenci zarovnat s nejbližší vodorovnou a svislou mřížkou, když ji přetáhnete na kreslicí plochy.

**Přepnout pozadí kreslicího pozadí**

Přepíná mezi světlým a tmavým pozadím.

**Zapnutí/vypnutí přitahování na snaplines**

Snaplines pomáhají zarovnat ovládací prvky vzhledem k sobě navzájem. Pokud je povoleno **přitahování na snaplines,** když přetáhnete ovládací prvek vzhledem k jiným ovládacím prvkům, hranice trasy se zobrazí, když jsou okraje a text některých ovládacích prvků zarovnány vodorovně nebo svisle. Hranice trasy se zobrazí jako čára červeně.

**Zakázat kód projektu**

Zakáže [kód projektu](debugging-or-disabling-project-code-in-xaml-designer.md), například vlastní ovládací prvky a převaděče hodnot a znovu načte návrháře.

### <a name="xaml-view"></a>Zobrazení XAML

V zobrazení **XAML** je aktivním oknem okno obsahující editor XAML a editor XAML je primárním nástrojem pro vytváření. Extensible Application Markup Language (XAML) poskytuje deklarativní slovník založený na XML pro určení uživatelského rozhraní aplikace. Zobrazení XAML zahrnuje technologie IntelliSense, automatické formátování, zvýraznění syntaxe a navigaci na značkách. Následující obrázek znázorňuje zobrazení XAML s otevřenou nabídkou IntelliSense:

![Zobrazení XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Okno Osnova dokumentu

Okno Osnova dokumentu v sadě Visual Studio je podobné [oknu Objekty a Časová osa](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) v prolnutí pro Visual Studio. Osnova dokumentu pomáhá provádět tyto úkoly:

- Zobrazení hierarchické struktury všech prvků na kreslicí desce.

- Vyberte prvky, abyste je mohli upravit. Můžete je například přesunout v hierarchii nebo nastavit jejich vlastnosti v okně Vlastnosti. Další informace naleznete [v tématu Práce s prvky v Návrháři XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Vytvořte a upravte šablony pro prvky, které jsou ovládacími prvky.

- [Vytvořte animace](animate-objects-in-xaml-designer.md) (Blend pouze pro Visual Studio).

Chcete-li zobrazit okno Osnova dokumentu v sadě Visual Studio, vyberte na řádku nabídek **možnost Zobrazit** > další**osnovu dokumentu systému****Windows** > .
Chcete-li zobrazit okno Objekty a časová osa v prolnutí pro Visual Studio, vyberte na řádku nabídek **možnost Zobrazit** > **obrys dokumentu**.

![Okno Osnova dokumentu v Sadě Visual Studio](media/document-outline-window.png)

Hlavní zobrazení v okně Osnova dokumentu/Objekty a Časová osa zobrazuje hierarchii dokumentu ve stromové struktuře. Hierarchickou povahu osnovy dokumentu můžete použít ke kontrole dokumentu na různých úrovních podrobností a k uzamčení a skrytí prvků, které jsou jednotlivé nebo ve skupinách. V okně Osnova dokumentu/Objekty a Časová osa jsou k dispozici následující volby:

**Zobrazit/skrýt**

Zobrazí nebo skryje prvky kreslicí plochy. Zobrazí se jako symbol oka, když je zobrazen. Můžete také stisknout **kombinaci kláves Ctrl**+**H,** chcete-li prvek skrýt, a **stisknutím klávesCtrl**+**Ctrl**+**H** jej zobrazit.

**Zamknout/odemknout**

Zamkne nebo odemkne prvky kreslicí plochy. Uzamčené prvky nelze změnit. Zobrazí se jako symbol visacího zámku, když je zamknutý. Můžete také stisknout **kombinaci kláves Ctrl**+**L** zamknout prvek a **Shift**+**Ctrl**+**L** odemknout.

**Vrátit obor do kořenové stránky**

Volba v horní části okna Osnova/Objekty a Časová osa dokumentu, která zobrazuje symbol šipky nahoru, se přesune do předchozího oboru. Vymezení rozsahu je použitelné pouze v případě, že jste v rozsahu stylu nebo šablony.

## <a name="properties-window"></a>Vlastnosti – okno

Okno **Vlastnosti** umožňuje nastavit hodnoty vlastností ovládacích prvků. Jak to vypadá:

![Vlastnosti – okno](media/xaml-designer-properties-window.png)

V horní části okna **Vlastnosti** jsou různé možnosti:

- Změňte název aktuálně vybraného prvku v poli **Název.**
- V levém horním rohu je ikona, která představuje aktuálně vybraný prvek.
- Chcete-li uspořádat vlastnosti podle kategorie nebo abecedně, klepněte v seznamu **Uspořádat položku** **Kategorie**, **Název**nebo **Zdroj.**
- Chcete-li zobrazit seznam událostí ovládacího prvku, klepněte na tlačítko **Události,** které se zobrazí jako symbol blesku.
- Chcete-li vyhledat vlastnost, začněte do vyhledávacího pole zadávat název vlastnosti. V okně **Vlastnosti** se při psaní zobrazí vlastnosti, které odpovídají vašemu hledání.

Některé vlastnosti umožňují nastavit upřesňující vlastnosti výběrem tlačítka se šipkou dolů.

Vpravo od každé hodnoty vlastnosti je *značka vlastnosti,* která se zobrazí jako symbol pole. Vzhled značky vlastnosti označuje, zda je na vlastnost použita datová vazba nebo prostředek. Například symbol bílého rámečku označuje výchozí hodnotu, symbol černého rámečku obvykle označuje, že byl použit místní prostředek, a oranžové pole obvykle označuje, že byla použita datová vazba. Po klepnutí na značku vlastnosti můžete přejít na definici stylu, otevřít tvůrce datových vazeb nebo otevřít výběr prostředků.

Další informace o používání vlastností a zpracování událostí naleznete [v tématu Intro to controls and patterns](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Viz také

- [Práce s elementy v Návrháři XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Postup vytvoření a použití prostředku](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Návod: Vazba s daty v Návrháři XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
