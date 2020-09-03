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
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: f8579a4e8088dc0fc6e7403da7f0371e46f2c928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87507960"
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

V zobrazení Návrh je okno obsahující návrhovou plochu aktivním oknem a můžete ho použít jako primární pracovní plochu. Můžete ji použít pro vizuální návrh stránky v aplikaci přidáním, kreslením nebo úpravou prvků. Další informace najdete v tématu [práce s prvky v Návrhář XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Tento obrázek ukazuje návrhovou plochu v zobrazení Návrh.

![zobrazení Návrh Návrhář XAML](media/xaml-artboard.png)

Tyto funkce jsou k dispozici na návrhové ploše:

**Zarovnávacím čárám**

Zarovnávacím čárám jsou *hranice zarovnání* , které se zobrazí jako přerušované čáry, aby se zobrazily, když jsou zarovnány okraje ovládacích prvků nebo jsou zarovnány textové hodnoty. Hranice zarovnání se zobrazí jenom v případě, že je povolený **přichycení k zarovnávacím čárám** .

**Mřížky – kolejnice**

Pro správu řádků a sloupců na panelu [mřížky](xref:Windows.UI.Xaml.Controls.Grid) se používají kolejnice mřížky. Můžete vytvářet a odstraňovat řádky a sloupce a můžete upravit jejich relativní šířky a výšky. Svislá mřížka, která se zobrazuje na levé straně návrhové plochy, se používá pro řádky a vodorovná čára, která se zobrazí v horní části, se používá pro sloupce.

**Doplňky mřížky**

Doplněk mřížky se zobrazuje jako trojúhelník, který má k čáře připojenou svislou nebo vodorovnou čáru v mřížce mřížky. Když přetáhnete doplněk mřížky, šířky a výšky sousedících sloupců nebo řádků se aktualizují při přesunu myši.

Doplňky mřížky slouží k řízení šířky a výšky řádků a sloupců v mřížce. Kliknutím na kolejnice mřížky můžete přidat nový sloupec nebo řádek. Když přidáte nový řádek řádku nebo sloupce pro panel mřížky, který má dva nebo více sloupců nebo řádků, na minipanelu nástrojů se objeví mimo kolejnici, která umožňuje explicitně nastavit šířku a výšku. Minipanel nástrojů umožňuje nastavit možnosti změny velikosti pro řádky a sloupce mřížky.

![Doplňky mřížky v Návrhář XAML](media/grid-adorner.png)

**Úchyty pro změnu velikosti**

Pro vybrané ovládací prvky se zobrazí úchyty pro změnu velikosti a umožňují změnit velikost ovládacího prvku. Při změně velikosti ovládacího prvku se obvykle zobrazují hodnoty šířky a výšky, které vám pomůžou velikost ovládacího prvku. Další informace o manipulaci s ovládacími prvky v **návrhovém** zobrazení najdete v tématu [práce s prvky v Návrhář XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

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

Zobrazí nebo skryje mřížku přichycení, která zobrazuje mřížku. Mřížky se používají, když povolíte **přichycení k mřížce** nebo **přichycení k zarovnávacím čárám**.

**Zapnout nebo vypnout přichycení k mřížce**

Pokud je povoleno **přichycení k mřížce** , je při přetahování na návrhovou plochu element při jejich přetahování na návrhovou plochu zarovnán s nejbližší vodorovnou a svislou mřížkou.

**Přepnout pozadí návrhové plochy**

Přepíná mezi světlým a tmavým pozadím.

**Zapnout nebo vypnout přichycení k zarovnávacím čárám**

Zarovnávacím čárám vám pomůžou Zarovnat ovládací prvky vzhledem k sobě navzájem. Pokud je povoleno **přichycení k zarovnávacím čárám** , když přetáhnete ovládací prvek relativně k jiným ovládacím prvkům, hranice zarovnání se zobrazí, když jsou okraje a text některých ovládacích prvků zarovnány vodorovně nebo svisle. Hranice zarovnání se zobrazí jako červená přerušovaná čára.

**Zakázat kód projektu**

Zakáže [kód projektu](debugging-or-disabling-project-code-in-xaml-designer.md), například vlastní ovládací prvky a převaděče hodnot a znovu načte návrháře.

### <a name="xaml-view"></a>Zobrazení XAML

V zobrazení **XAML** je okno obsahující Editor XAML aktivním oknem a Editor XAML je vaším primárním nástrojem pro tvorbu. Jazyk Extensible Application Markup Language (XAML) (XAML) poskytuje deklarativní slovní slovník založený na jazyce XML pro určení uživatelského rozhraní aplikace. Zobrazení XAML zahrnuje technologii IntelliSense, automatické formátování, zvýrazňování syntaxe a navigaci značek. Následující obrázek znázorňuje zobrazení XAML s otevřenou nabídkou IntelliSense:

![Zobrazení XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Okno Osnova dokumentu

Okno Osnova dokumentu v aplikaci Visual Studio je podobné [objekty a časová osa oknu](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) v Blend pro Visual Studio. Osnova dokumentu vám pomůže provádět tyto úlohy:

- Zobrazení hierarchické struktury všech prvků na návrhové ploše.

- Vyberte prvky, abyste je mohli upravovat. Můžete je například přesunout v hierarchii nebo nastavit jejich vlastnosti v okno Vlastnosti. Další informace najdete v tématu [práce s prvky v Návrhář XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Vytvořte a upravte šablony pro prvky, které jsou ovládacími prvky.

- [Vytváření animací](animate-objects-in-xaml-designer.md) (pouze Blend pro Visual Studio).

Chcete-li zobrazit okno Osnova dokumentu v aplikaci Visual Studio, vyberte v řádku nabídek možnost **Zobrazit**  >  **Další**  >  **osnovu dokumentu**Windows.
Chcete-li zobrazit okno objekty a časová osa v Blend pro Visual Studio, v řádku nabídek vyberte **Zobrazit**  >  **Osnova dokumentu**.

![Okno Osnova dokumentu v aplikaci Visual Studio](media/document-outline-window.png)

Hlavní zobrazení v okně Osnova/Objekty a časová osa v dokumentu zobrazuje hierarchii dokumentu ve stromové struktuře. Hierarchickou povahu osnovy dokumentu můžete použít k prohlédnutí dokumentu na různých úrovních podrobností a k zamčení a skrytí prvků jednotlivě nebo ve skupinách. V okně Osnova/Objekty a časová osa jsou k dispozici následující možnosti:

**Zobrazit/skrýt**

Zobrazí nebo skryje prvky návrhové plochy. Zobrazuje se jako symbol oka, pokud je zobrazený. Můžete také stisknout **kombinaci kláves CTRL** + **h** pro skrytí prvku a **posunutí** + **CTRL** + **h** k zobrazení.

**Zamknout/odemknout**

Zamkne nebo odemkne prvky návrhové plochy. Uzamčené prvky nelze upravovat. Zobrazuje se jako symbol visacího zámku nezobrazuje při uzamčení. Můžete také stisknout **kombinaci kláves CTRL** + **l** pro uzamknutí prvku a jeho stisknutím klávesy **SHIFT** + **CTRL**+ ho + **L** odemknout.

**Vrátit rozsah do pageRoot**

Možnost v horní části okna osnova/Objekty a časová osa, která zobrazuje symbol šipky nahoru, se přesune na předchozí rozsah. Rozsah se dá použít jenom v případě, že jste v oboru stylu nebo šablony.

## <a name="properties-window"></a>Vlastnosti – okno

Okno **vlastnosti** umožňuje nastavit hodnoty vlastností ovládacích prvků. Vypadá takto:

![Vlastnosti – okno](media/xaml-designer-properties-window.png)

V horní části okna **vlastností** jsou k dispozici různé možnosti:

- V poli **název** změňte název aktuálně vybraného prvku.
- V levém horním rohu je ikona, která představuje aktuálně vybraný prvek.
- Pokud chcete vlastnosti uspořádat podle kategorie nebo abecedně, klikněte v seznamu **Uspořádat podle** na **kategorie**, **název**nebo **zdroj** .
- Chcete-li zobrazit seznam událostí ovládacího prvku, klikněte na tlačítko **události** , které se zobrazí jako symbol blesku.
- Chcete-li vyhledat vlastnost, začněte do vyhledávacího pole zadat název vlastnosti. V okně **vlastnosti** se zobrazí vlastnosti, které odpovídají vašemu hledání při psaní.

Některé vlastnosti umožňují nastavit upřesňující vlastnosti tak, že vyberete tlačítko se šipkou dolů.

Napravo od každé hodnoty vlastnosti je *značka vlastnosti* , která se zobrazí jako symbol pole. Vzhled značky vlastnosti označuje, zda existuje datová vazba nebo prostředek aplikovaný na vlastnost. Například symbol bílého pole označuje výchozí hodnotu, symbol černého pole obvykle indikuje, že byl použit místní prostředek, a oranžové pole obvykle indikuje, že byla použita datová vazba. Když kliknete na značku vlastnosti, můžete přejít k definici stylu, otevřít Tvůrce datových vazeb nebo otevřít výběr prostředku.

Další informace o používání vlastností a zpracování událostí naleznete v tématu [Úvod k ovládacím prvkům a vzorům](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Viz také

- [Práce s elementy v Návrháři XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Postup vytvoření a použití prostředku](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Návod: Vazba s daty v Návrháři XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
