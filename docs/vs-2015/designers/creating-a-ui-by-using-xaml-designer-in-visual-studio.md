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
ms.openlocfilehash: 879d8457a0f5fd4bf63a2d69a4f3f026ce4c6fe1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294666"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Vytvoření uživatelského rozhraní pomocí Návrháře XAML v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrhář XAML v sadě Visual Studio poskytuje vizuální rozhraní při návrhu aplikací založených na XAML Windows Store, Windows Phone, WPF a Silverlight. Můžete vytvářet uživatelská rozhraní pro aplikace přetažením ovládacích prvků z **panelu nástrojů** a vlastností nastavení v okně **vlastnosti** . XAML můžete také upravit přímo v XAML zobrazení.

 V případě pokročilých úloh návrhu jazyka XAML, jako jsou například animace a chování, najdete informace v tématu [Vytvoření uživatelského rozhraní pomocí Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>Pracovní prostor návrháře XAML
 Pracovní prostor v Návrháři XAML se skládá z několika prvků vizuální rozhraní. Patří mezi ně návrhové ploše editoru XAML, okno zařízení, Osnova dokumentu – okno a okno Vlastnosti. Chcete-li otevřít Návrhář XAML, klikněte pravým tlačítkem myši na soubor XAML v **Průzkumník řešení** a vyberte možnost **Návrhář zobrazení**.

## <a name="authoring-views"></a>Zobrazení pro vytváření
 Návrhář XAML zobrazuje XAML a synchronizované zobrazení návrhu vaší aplikace vykreslované značky XAML. Se souborem XAML otevřeným v aplikaci Visual Studio můžete přepínat mezi zobrazení Návrh a zobrazením XAML pomocí karet **design** a **XAML** . K přepnutí zobrazeného okna v horní části můžete použít tlačítko **podokna záměny** : buď návrhová plocha, nebo Editor XAML.

 V zobrazení Návrh je okno obsahující návrhovou *plochu* aktivním oknem a můžete ho použít jako primární pracovní plochu. Můžete ho použít přidáním nebo výkresu prvky a jejich úpravou vizuálně navrhnout stránku ve vaší aplikaci. Další informace naleznete v tématu [práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md). Tento obrázek ukazuje návrhové ploše v zobrazení Návrh.

 ![zobrazení Návrh Návrhář XAML](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Tyto funkce jsou dostupné v návrhové plochy:

 **Zarovnávacím čárám** Zarovnávacím čárám jsou *hranice zarovnání* , které se zobrazí jako přerušované čáry, aby se zobrazily, když jsou zarovnány okraje ovládacích prvků, nebo když jsou zarovnány textové hodnoty. Hranice zarovnání se zobrazí jenom v případě, že je povolený **přichycení k zarovnávacím čárám** .

 Pro správu řádků a sloupců na panelu [mřížky](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) se **používají kolejnice `Grid`** kolejnice. Můžete vytvářet a odstraňovat řádky a sloupce a můžeme upravit jejich relativní šířky a výšky. Svislé lišty mřížky, které se zobrazí na levé straně návrhové plochy, se používá pro řádky a vodorovná čára, která se zobrazí v horní části, se používá pro sloupce.

 **Doplňky mřížky** `Grid` doplněk se zobrazí jako trojúhelník, který má k němu připojenou svislou nebo vodorovnou čáru na `Grid` kolejnici. Když přetáhnete `Grid` doplňku, šířky a výšky sousedících sloupců nebo řádků se aktualizují při přesunu myši.

 `Grid` doplňky jsou používány k řízení šířky a výšky řádků `Grid`a sloupců. Kliknutím na `Grid` kolejnice můžete přidat nový sloupec nebo řádek. Když přidáte nový řádek řádku nebo sloupce pro `Grid` panel, který má dva nebo více sloupců nebo řádků, na minipanelu nástrojů se objeví mimo kolejnici, která umožňuje explicitně nastavit šířku a výšku. Minipanel nástrojů umožňuje nastavit možnosti změny velikosti pro `Grid` řádky a sloupce.

 **Úchyty pro změnu velikosti** Pro vybrané ovládací prvky se zobrazí úchyty pro změnu velikosti a umožňují změnit velikost ovládacího prvku. Při změně velikosti ovládacího prvku se zobrazí hodnoty šířky a výšky obvykle umožňují upravit velikost ovládacího prvku. Další informace o manipulaci s ovládacími prvky v zobrazení Návrh najdete v tématu [práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md).

 **Okraje** Okraje znázorňují velikost pevného prostoru mezi okrajem ovládacího prvku a okrajem jeho kontejneru. Okraje ovládacího prvku lze nastavit pomocí vlastností [okraj](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) v oblasti **rozložení** v okno Vlastnosti.

 **Doplňky okrajů** Chcete-li změnit okraje elementu relativně vzhledem k jeho kontejneru rozložení, můžete použít doplňky pro úpravy okrajů. Při otevření okrajů není nastavená okraj a doplněk pro úpravy rozpětí zobrazí porušený řetězec. Když není nastavená na okraji, zůstane prvky při změně velikosti kontejneru rozložení v době běhu na místě. Při zavření okrajů okrajů zobrazí Nepřerušený řetěz a prvky budou přesunuty spolu s okrajem při změně velikosti kontejneru rozložení v době běhu (na okraj zůstanou pevné).

 **Obslužné rutiny elementů** Můžete upravit element pomocí obslužných rutin, které se zobrazí na návrhové ploše, když přesunete ukazatel myši na rohy modrého pole, které obklopuje element. Tyto manipulační body umožňují otočení, změna velikosti, překlopit, přesunout nebo přidat poloměr na prvek. Značka pro element popisovač se liší podle funkcí a mění v závislosti na přesné umístění ukazatele. Pokud nevidíte element popisovače, ujistěte se, že je vybraný prvek.

 V návrhovém zobrazení jsou k dispozici v levé dolní části obrazovky, příkazy další návrhovou plochu, jak je znázorněno zde:

 ![Příkazy zobrazení Návrh](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Tyto příkazy jsou k dispozici na tomto panelu nástrojů:

 **Zvětšení** Přiblížení umožňuje změnit velikost návrhové plochy. Můžete zvětšit z 12,5% na 800% nebo vybrat možnosti, například **přizpůsobit výběru** a **přizpůsobit vše**.

 **Zobrazit/skrýt mřížku pro přichycení** Zobrazí nebo skryje mřížku přichycení, která zobrazuje mřížku. Mřížka se používá, pokud je povolená možnost **přichycení k mřížce** nebo **přichycení k zarovnávacím čárám** .

 **Zapnout nebo vypnout přichycení k mřížce** Pokud je povoleno **přichycení k mřížce** , když přetáhnete prvek na návrhovou plochu, element zamýšlí zarovnat s nejbližší vodorovnou a svislou mřížkou.

 **Zapnout nebo vypnout přichycení k zarovnávacím čárám** Zarovnávacím čárám vám pomůžou Zarovnat ovládací prvky vzhledem k sobě navzájem. Pokud je povoleno **přichycení k zarovnávacím čárám** , když přetáhnete ovládací prvek relativně k jiným ovládacím prvkům, hranice zarovnání se zobrazí, když jsou okraje a text některých ovládacích prvků zarovnány vodorovně nebo svisle. Hranici zarovnání se zobrazí jako červená přerušovaná čára.

 V XAML zobrazení okna obsahujícího editoru XAML je aktivní okno a editoru XAML je primární nástroj pro vytváření. Rozšiřitelné aplikace Markup Language (XAML) obsahuje slovník deklarativní, založený na formátu XML pro zadání uživatelského rozhraní aplikace. Zobrazení XAML obsahuje technologie IntelliSense, automatického formátování, zvýrazňování syntaxe a navigace značek. Tento obrázek ukazuje XAML zobrazení:

 ![Zobrazení XAML](../designers/media/xaml-editor.png "xaml_editor")

 **Rozdělit pruh zobrazení** Rozdělený pruh zobrazení se zobrazí v horní části zobrazení XAML, když je Editor XAML v dolním okně. Zobrazení příčku umožňuje řídit relativní velikosti zobrazení návrhové a XAML zobrazení. Můžete také vyměnit umístění zobrazení (pomocí tlačítka **odkládací podokna** ), určit, zda jsou zobrazení uspořádána vodorovně nebo svisle, a sbalit buď zobrazení.

 **Zvětšení kódu** Zvětšení kódu umožňuje zobrazit velikost zobrazení XAML. Můžete zvětšit z 20 % na 400 %.

## <a name="device-window"></a>Okno zařízení
 V okně zařízení v Návrháři XAML umožňuje simulovat v době návrhu různá zobrazení, zobrazení a zobrazení možností pro projekt Windows Store nebo Windows Phone. Okno zařízení je k dispozici v nabídce **Návrh** při práci na Návrhář XAML. Zde je, jak to funguje:

 ![Okno zařízení](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Jedná se o možnostech dostupných v okně zařízení:

 **Zobrazit** Určuje různé velikosti zobrazení a jejich rozlišení pro aplikaci.

 **Orientace** Určuje různé orientace aplikace: **na šířku** nebo **na výšku**.

 **Hraniční** Určuje různá zarovnání okrajů **aplikace:,** **vlevo**, **vpravo**nebo **žádné**.

 **Vysoký kontrast** Zobrazte náhled aplikace na základě vybraného nastavení kontrastu. Toto nastavení, pokud je nastaveno na jinou hodnotu než **výchozí**, přepíše vlastnost `RequestedTheme` nastavenou v souboru App. XAML.

 **Přepsat škálování** Zapne a vypne emulaci měřítka dokumentu v návrhové ploše. To umožňuje škálování procento zvýšit jediný faktor. Zaškrtněte políčko Zapnout emulace. Například pokud vaše škálování procentuální hodnota je 100 %, dokumentu na návrhové ploše se bude škálovat 140 %. Tato možnost je zakázaná, pokud je aktuální procento škálování 180.

 **Minimální šířka** Určuje nastavení minimální šířky. Minimální šířka lze změnit v souboru App.xaml.

 **Motiv** Určuje motiv aplikace. Například může přepínat mezi tmavý a světlý motiv.

 **Zobrazit Chrome** Zapne a vypne simulovaný tabletový rámeček kolem vaší aplikace v zobrazení Návrh. Zaškrtněte políčko Zobrazit rámce.

 **Vystřihnout k zobrazení** Určuje režim zobrazení. Zaškrtněte políčko do Galerie velikost dokumentu na velikost zobrazení.

## <a name="document-outline-window"></a>Osnova dokumentu – okno
 Okno osnovy dokumentu v Návrháři XAML umožňuje provádět tyto úkoly:

- Zobrazte hierarchickou strukturu všech prvků na návrhové ploše.

- Vyberte elementy tak, aby možno upravovat (přesunout je kolem v hierarchii, je upravovat návrhovou plochu, nastavit jejich vlastnosti v okně Vlastnosti a tak dále). Další informace naleznete v tématu [práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md)

- Vytvářet a upravovat šablony pro prvky, které jsou ovládací prvky.

- Pomocí místní nabídky pro vybrané elementy. Stejnou nabídku je také k dispozici pro vybrané elementy na návrhovou plochu.

  Chcete-li zobrazit okno Osnova dokumentu, na panelu nabídek vyberte možnost **zobrazení**, **ostatní okna**, **Osnova dokumentu**.

  ![Okno Osnova dokumentu](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Jedná se o možnostech dostupných v okně Osnova dokumentu:

  **Osnova dokumentu** Hlavní zobrazení v okně Osnova dokumentu zobrazuje hierarchii dokumentu ve stromové struktuře. Hierarchickou povahu Osnova dokumentu můžete použít k prozkoumání dokumentu na různých úrovních podrobností a k uzamčení nebo skrytí prvků jednotlivě nebo ve skupinách.

  **Zobrazit/skrýt** Zobrazí nebo skryje prvky návrhové plochy, které odpovídají položkám v osnově dokumentu. Pomocí tlačítek **Zobrazit/skrýt** zobrazíte symbol oka, pokud je zobrazený, nebo stisknutím kombinace kláves CTRL + h můžete elementy zobrazit a SHIFT + CTRL + h je zobrazit.

  **Zamknout/odemknout** Zamkne nebo odemkne prvky návrhové plochy, které odpovídají položkám v osnově dokumentu. Uzamčené elementy se nedá upravit. Použijte tlačítka **zamknout/odemknout** , které zobrazí symbol visacího zámku nezobrazuje při uzamčení, nebo stiskněte klávesy CTRL + L pro zamčení prvků a jejich odemčení stisknutím kláves CTRL + Ctrl + l.

  **Vrátit rozsah do pageRoot** Možnost v horní části okna Osnova dokumentu, která zobrazuje symbol šipky nahoru, vrátí osnovu dokumentu k předchozímu rozsahu. Přesouvání rozsahu směrem nahoru platí pouze v případě, že jste v rámci stylu nebo šablony.

## <a name="properties-window"></a>Vlastnosti – okno
 V okně Vlastnosti vám umožní nastavit hodnoty vlastností v ovládacích prvcích. Zde je, jak to funguje:

 ![okno Vlastnosti](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Existují různé možnosti v horní části okna Vlastnosti. Název aktuálně vybraného prvku můžete změnit pomocí pole **název** . V levém horním rohu je ikona, která reprezentuje aktuálně vybraný element. Pokud chcete vlastnosti uspořádat podle kategorie nebo abecedně, klikněte v seznamu **Uspořádat podle** na **kategorie**, **název**nebo **zdroj** . Chcete-li zobrazit seznam událostí ovládacího prvku, klikněte na tlačítko **události** , které zobrazuje symbol blesku. Chcete-li vyhledat vlastnost, začněte do pole **Vlastnosti hledání** zadat název vlastnosti. V okně vlastností zobrazuje vlastnosti, které odpovídají zadanému hledání během psaní. Některé vlastnosti umožňují nastavit upřesňující vlastnosti tak, že vyberete šipku dolů. Další informace o používání vlastností a zpracování událostí najdete v tématu [rychlý Start: Přidání ovládacích prvků a zpracování událostí.](https://go.microsoft.com/fwlink/?LinkID=247983)

 Napravo od každé hodnoty vlastnosti je *značka vlastnosti* , která se zobrazí jako symbol pole. Vzhled značky vlastnost označuje, zda je datové vazby nebo prostředek použitý pro vlastnost. Například symbol bílé pole určuje výchozí hodnotu, symbol černé skříňky obvykle označuje, že použití místního prostředku a oranžová pole se obvykle označuje, že byl použit datové vazby. Po kliknutí na značku vlastnosti, můžete přejít na definici stylu, otevřete Tvůrce vazeb dat nebo otevřít výběr prostředku.

## <a name="see-also"></a>Viz také
 [Práce s prvky v Návrhář XAML](../designers/working-with-elements-in-xaml-designer.md) [Vytvoření a použití](../designers/how-to-create-and-apply-a-resource.md) [návodu k prostředku: vazba na data v Návrhář XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
