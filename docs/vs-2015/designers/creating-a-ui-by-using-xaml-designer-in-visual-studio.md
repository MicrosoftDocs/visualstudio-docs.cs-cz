---
title: Vytvoření uživatelského rozhraní pomocí Návrháře XAML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d230d9a4719e1757820de87b60bcc7566a785f99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844021"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Vytvoření uživatelského rozhraní pomocí Návrháře XAML v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrhář XAML v aplikaci Visual Studio poskytuje vizuální rozhraní, které vám umožní navrhovat aplikace pro Windows Store, Windows Phone, WPF a Silverlight založené na jazyce XAML. Můžete vytvářet uživatelská rozhraní pro aplikace přetažením ovládacích prvků z **panelu nástrojů** a vlastností nastavení v okně **vlastnosti** . Můžete také upravit XAML přímo v zobrazení XAML.

 V případě pokročilých úloh návrhu jazyka XAML, jako jsou například animace a chování, najdete informace v tématu [Vytvoření uživatelského rozhraní pomocí Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>Pracovní prostor Návrhář XAML
 Pracovní prostor v Návrhář XAML se skládá z několika prvků vizuálního rozhraní. Mezi ně patří návrhová plocha, Editor XAML, okno zařízení, okno Osnova dokumentu a okno Vlastnosti. Chcete-li otevřít Návrhář XAML, klikněte pravým tlačítkem myši na soubor XAML v **Průzkumník řešení** a vyberte možnost **Návrhář zobrazení**.

## <a name="authoring-views"></a>Zobrazení vytváření obsahu
 Návrhář XAML poskytuje zobrazení XAML a synchronizovaný zobrazení Návrh vykresleného kódu XAML vaší aplikace. Se souborem XAML otevřeným v aplikaci Visual Studio můžete přepínat mezi zobrazení Návrh a zobrazením XAML pomocí karet **design** a **XAML** . K přepnutí zobrazeného okna v horní části můžete použít tlačítko **podokna záměny** : buď návrhová plocha, nebo Editor XAML.

 V zobrazení Návrh je okno obsahující návrhovou *plochu* aktivním oknem a můžete ho použít jako primární pracovní plochu. Můžete ji použít pro vizuální návrh stránky v aplikaci přidáním nebo kreslením prvků a pak úpravou. Další informace naleznete v tématu [práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md). Tento obrázek ukazuje návrhovou plochu v zobrazení Návrh.

 ![zobrazení Návrh Návrhář XAML](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Tyto funkce jsou k dispozici na návrhové ploše:

 **Zarovnávacím čárám** Zarovnávacím čárám jsou *hranice zarovnání* , které se zobrazí jako přerušované čáry, aby se zobrazily, když jsou zarovnány okraje ovládacích prvků, nebo když jsou zarovnány textové hodnoty. Hranice zarovnání se zobrazí jenom v případě, že je povolený **přichycení k zarovnávacím čárám** .

 **Mřížky – kolejnice** `Grid` kolejnice se používají ke správě řádků a sloupců na panelu [mřížky](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) . Můžete vytvářet a odstraňovat řádky a sloupce a můžete upravit jejich relativní šířky a výšky. Svislá mřížka, která se zobrazuje na levé straně návrhové plochy, se používá pro řádky a vodorovná čára, která se zobrazí v horní části, se používá pro sloupce.

 **Doplňky mřížky** `Grid` Doplněk se zobrazí jako trojúhelník, který má k němu připojenou svislou nebo vodorovnou čáru na `Grid` kolejnici. Když přetáhnete doplňkovou stránku `Grid` , šířky a výšky sousedících sloupců nebo řádků se aktualizují při přesunu myši.

 `Grid` Doplňky se používají k řízení šířky a výšky `Grid` řádků a sloupců. Kliknutím na kolejnice můžete přidat nový sloupec nebo řádek `Grid` . Když přidáte nový řádek řádku nebo sloupce pro `Grid` panel, který má dva nebo více sloupců nebo řádků, zobrazí se malý panel nástrojů mimo kolejnici, která umožňuje explicitně nastavit šířku a výšku. Minipanel nástrojů umožňuje nastavit možnosti změny velikosti pro `Grid` řádky a sloupce.

 **Úchyty pro změnu velikosti** Pro vybrané ovládací prvky se zobrazí úchyty pro změnu velikosti a umožňují změnit velikost ovládacího prvku. Při změně velikosti ovládacího prvku se obvykle zobrazují hodnoty šířky a výšky, které vám pomůžou velikost ovládacího prvku. Další informace o manipulaci s ovládacími prvky v zobrazení Návrh najdete v tématu [práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md).

 **Okraje** Okraje znázorňují velikost pevného prostoru mezi okrajem ovládacího prvku a okrajem jeho kontejneru. Okraje ovládacího prvku lze nastavit pomocí vlastností [okraj](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) v oblasti **rozložení** v okno Vlastnosti.

 **Doplňky okrajů** Chcete-li změnit okraje elementu relativně vzhledem k jeho kontejneru rozložení, můžete použít doplňky pro úpravy okrajů. Když je doplněk pro úpravy okrajů otevřený, okraj není nastavený a doplněk pro úpravy okrajů zobrazuje porušený řetězec. Pokud okraj není nastaven, prvky zůstanou zachovány při změně velikosti kontejneru rozložení v době běhu. Když je doplněk pro úpravy okrajů uzavřený, doplněk pro úpravy okrajů zobrazuje nepřerušený řetězec a prvky se přesunou s okrajem, protože velikost kontejneru rozložení se za běhu (okraj zůstane pevně nastavená).

 **Obslužné rutiny elementů** Můžete upravit element pomocí obslužných rutin, které se zobrazí na návrhové ploše, když přesunete ukazatel myši na rohy modrého pole, které obklopuje element. Tyto popisovače umožňují otočit, změnit velikost, překlopit, přesunout nebo přidat poloměr rohu do prvku. Symbol pro popisovač elementu se liší podle funkce a mění se v závislosti na přesném umístění ukazatele. Pokud nevidíte obslužné rutiny elementu, ujistěte se, že je prvek vybrán.

 V zobrazení Návrh jsou k dispozici další příkazy pro návrhovou plochu v levém dolním rohu obrazovky, jak je znázorněno zde:

 ![Příkazy zobrazení Návrh](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Tyto příkazy jsou k dispozici na tomto panelu nástrojů:

 **Zvětšení** Přiblížení umožňuje změnit velikost návrhové plochy. Můžete zvětšit z 12,5% na 800% nebo vybrat možnosti, například **přizpůsobit výběru** a **přizpůsobit vše**.

 **Zobrazit/skrýt mřížku pro přichycení** Zobrazí nebo skryje mřížku přichycení, která zobrazuje mřížku. Mřížka se používá, pokud je povolená možnost **přichycení k mřížce** nebo **přichycení k zarovnávacím čárám** .

 **Zapnout nebo vypnout přichycení k mřížce** Pokud je povoleno **přichycení k mřížce** , když přetáhnete prvek na návrhovou plochu, element zamýšlí zarovnat s nejbližší vodorovnou a svislou mřížkou.

 **Zapnout nebo vypnout přichycení k zarovnávacím čárám** Zarovnávacím čárám vám pomůžou Zarovnat ovládací prvky vzhledem k sobě navzájem. Pokud je povoleno **přichycení k zarovnávacím čárám** , když přetáhnete ovládací prvek relativně k jiným ovládacím prvkům, hranice zarovnání se zobrazí, když jsou okraje a text některých ovládacích prvků zarovnány vodorovně nebo svisle. Hranice zarovnání se zobrazí jako červená přerušovaná čára.

 V zobrazení XAML je okno obsahující Editor XAML aktivním oknem a Editor XAML je vaším primárním nástrojem pro tvorbu. Jazyk Extensible Application Markup Language (XAML) (XAML) poskytuje deklarativní slovní slovník založený na jazyce XML pro určení uživatelského rozhraní aplikace. Zobrazení XAML zahrnuje technologii IntelliSense, automatické formátování, zvýrazňování syntaxe a navigaci značek. Tento obrázek znázorňuje zobrazení XAML:

 ![Zobrazení XAML](../designers/media/xaml-editor.png "xaml_editor")

 **Rozdělit pruh zobrazení** Rozdělený pruh zobrazení se zobrazí v horní části zobrazení XAML, když je Editor XAML v dolním okně. Rozdělený panel zobrazení umožňuje řídit relativní velikosti zobrazení Návrh a zobrazení XAML. Můžete také vyměnit umístění zobrazení (pomocí tlačítka **odkládací podokna** ), určit, zda jsou zobrazení uspořádána vodorovně nebo svisle, a sbalit buď zobrazení.

 **Zvětšení kódu** Zvětšení kódu umožňuje zobrazit velikost zobrazení XAML. Můžete zvětšit z 20% na 400%.

## <a name="device-window"></a>Okno zařízení
 Okno zařízení v Návrhář XAML umožňuje simulovat v době návrhu různá zobrazení, zobrazení a možnosti zobrazení pro Windows Store nebo projekt Windows Phone. Okno zařízení je k dispozici v nabídce **Návrh** při práci na Návrhář XAML. Vypadá takto:

 ![Okno zařízení](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Tyto možnosti jsou k dispozici v okně zařízení:

 **Zobrazit** Určuje různé velikosti zobrazení a jejich rozlišení pro aplikaci.

 **Orientace** Určuje různé orientace aplikace: **na šířku** nebo **na výšku**.

 **Hraniční** Určuje různá zarovnání okrajů **aplikace:,** **vlevo**, **vpravo**nebo **žádné**.

 **Vysoký kontrast** Zobrazte náhled aplikace na základě vybraného nastavení kontrastu. Toto nastavení, pokud je nastaveno na jinou hodnotu než **výchozí**, přepíše `RequestedTheme` vlastnost nastavenou v souboru App. XAML.

 **Přepsat škálování** Zapne a vypne emulaci měřítka dokumentu v návrhové ploše. To umožňuje zvýšit procento škálování podle jednoho faktoru. Zaškrtněte políčko pro zapnutí emulace. Pokud je například procento škálování 100%, dokument v návrhové ploše bude škálovat až na 140%. Tato možnost je zakázaná, pokud je aktuální procento škálování 180.

 **Minimální šířka** Určuje nastavení minimální šířky. Minimální šířka se dá změnit v souboru App. XAML.

 **Motiv** Určuje motiv aplikace. Můžete například přepínat mezi tmavým a světlým motivem.

 **Zobrazit Chrome** Zapne a vypne simulovaný tabletový rámeček kolem vaší aplikace v zobrazení Návrh. Zaškrtněte políčko pro zobrazení rámce.

 **Vystřihnout k zobrazení** Určuje režim zobrazení. Zaškrtněte políčko pro oříznutí velikosti dokumentu na velikost zobrazení.

## <a name="document-outline-window"></a>Okno Osnova dokumentu
 Okno Osnova dokumentu v Návrhář XAML pomáhá provádět tyto úlohy:

- Zobrazení hierarchické struktury všech prvků na návrhové ploše.

- Vyberte prvky, abyste je mohli upravit (pohybovat v hierarchii, upravovat je na návrhové ploše, nastavit jejich vlastnosti v okno Vlastnosti atd.). Další informace naleznete v tématu [práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md)

- Vytvořte a upravte šablony pro prvky, které jsou ovládacími prvky.

- Použijte kontextovou nabídku pro vybrané prvky. Stejná nabídka je k dispozici také pro vybrané prvky na návrhové ploše.

  Chcete-li zobrazit okno Osnova dokumentu, na panelu nabídek vyberte možnost **zobrazení**, **ostatní okna**, **Osnova dokumentu**.

  ![Okno Osnova dokumentu](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Tyto možnosti jsou k dispozici v okně Osnova dokumentu:

  **Osnova dokumentu** Hlavní zobrazení v okně Osnova dokumentu zobrazuje hierarchii dokumentu ve stromové struktuře. Hierarchickou povahu osnovy dokumentu můžete použít k prohlížení dokumentu na různých úrovních podrobností a k zamčení a skrytí prvků jednotlivě nebo ve skupinách.

  **Zobrazit/skrýt** Zobrazí nebo skryje prvky návrhové plochy, které odpovídají položkám v osnově dokumentu. Pomocí tlačítek **Zobrazit/skrýt** zobrazíte symbol oka, pokud je zobrazený, nebo stisknutím kombinace kláves CTRL + h můžete elementy zobrazit a SHIFT + CTRL + h je zobrazit.

  **Zamknout/odemknout** Zamkne nebo odemkne prvky návrhové plochy, které odpovídají položkám v osnově dokumentu. Uzamčené prvky nelze upravovat. Použijte tlačítka **zamknout/odemknout** , které zobrazí symbol visacího zámku nezobrazuje při uzamčení, nebo stiskněte klávesy CTRL + L pro zamčení prvků a jejich odemčení stisknutím kláves CTRL + Ctrl + l.

  **Vrátit rozsah do pageRoot** Možnost v horní části okna Osnova dokumentu, která zobrazuje symbol šipky nahoru, vrátí osnovu dokumentu k předchozímu rozsahu. Rozsah se dá použít jenom v případě, že jste v oboru stylu nebo šablony.

## <a name="properties-window"></a>Vlastnosti – okno
 Okno Vlastnosti umožňuje nastavit hodnoty vlastností ovládacích prvků. Vypadá takto:

 ![Vlastnosti – okno](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 V horní části okno Vlastnosti jsou k dispozici různé možnosti. Název aktuálně vybraného prvku můžete změnit pomocí pole **název** . V levém horním rohu je ikona, která představuje aktuálně vybraný prvek. Pokud chcete vlastnosti uspořádat podle kategorie nebo abecedně, klikněte v seznamu **Uspořádat podle** na **kategorie**, **název**nebo **zdroj** . Chcete-li zobrazit seznam událostí ovládacího prvku, klikněte na tlačítko **události** , které zobrazuje symbol blesku. Chcete-li vyhledat vlastnost, začněte do pole **Vlastnosti hledání** zadat název vlastnosti. Okno Vlastnosti zobrazuje vlastnosti, které odpovídají vašemu hledání při psaní. Některé vlastnosti umožňují nastavit upřesňující vlastnosti tak, že vyberete tlačítko se šipkou dolů. Další informace o používání vlastností a zpracování událostí najdete v tématu [rychlý Start: Přidání ovládacích prvků a zpracování událostí.](https://msdn.microsoft.com/library/windows/apps/xaml/hh465336.aspx)

 Napravo od každé hodnoty vlastnosti je *značka vlastnosti* , která se zobrazí jako symbol pole. Vzhled značky vlastnosti označuje, zda existuje datová vazba nebo prostředek aplikovaný na vlastnost. Například symbol bílého pole označuje výchozí hodnotu, symbol černého pole obvykle indikuje, že byl použit místní prostředek, a oranžové pole obvykle indikuje, že byla použita datová vazba. Když kliknete na značku vlastnosti, můžete přejít k definici stylu, otevřít Tvůrce datových vazeb nebo otevřít výběr prostředku.

## <a name="see-also"></a>Viz také
 [Práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md) [Vytvoření a použití](../designers/how-to-create-and-apply-a-resource.md) [návodu k prostředku: vazba na data v Návrhář XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
