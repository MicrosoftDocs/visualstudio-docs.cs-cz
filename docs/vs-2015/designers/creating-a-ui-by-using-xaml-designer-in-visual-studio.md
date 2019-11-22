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

Návrhář XAML v sadě Visual Studio poskytuje vizuální rozhraní při návrhu aplikací založených na XAML Windows Store, Windows Phone, WPF a Silverlight. Uživatelská rozhraní pro vaše aplikace můžete vytvořit přetažením ovládacích prvků **nástrojů** a nastavení vlastností ve **vlastnosti** okno. XAML můžete také upravit přímo v XAML zobrazení.

 Pokročilé úlohy návrhu XAML například animace a chování, naleznete v tématu [vytvoření uživatelského rozhraní pomocí nástroje Blend pro Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>Pracovní prostor návrháře XAML
 Pracovní prostor v Návrháři XAML se skládá z několika prvků vizuální rozhraní. Patří mezi ně návrhové ploše editoru XAML, okno zařízení, Osnova dokumentu – okno a okno Vlastnosti. Chcete-li otevřít Návrhář XAML, klikněte pravým tlačítkem na soubor XAML v **Průzkumníka řešení** a zvolte **Návrhář zobrazení**.

## <a name="authoring-views"></a>Zobrazení pro vytváření
 Návrhář XAML zobrazuje XAML a synchronizované zobrazení návrhu vaší aplikace vykreslované značky XAML. S XAML soubor otevřít v sadě Visual Studio, můžete přepínat mezi návrhové a XAML zobrazení pomocí **návrhu** a **XAML** karty. Můžete použít **zaměnit podokna** tlačítkem přepnete okna se zobrazí v horní části: návrhové ploše nebo v editoru XAML.

 V návrhovém zobrazení okna obsahující *návrhové plochy* aktivní okno a slouží jako primární pracovní plocha. Můžete ho použít přidáním nebo výkresu prvky a jejich úpravou vizuálně navrhnout stránku ve vaší aplikaci. Další informace najdete v tématu [práce s elementy v Návrháři XAML](../designers/working-with-elements-in-xaml-designer.md). Tento obrázek ukazuje návrhové ploše v zobrazení Návrh.

 ![zobrazení Návrh Návrhář XAML](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Tyto funkce jsou dostupné v návrhové plochy:

 **Zarovnávacích čar** jsou zarovnávacích čar *hranicích zarovnání* , která se zobrazují jako přerušovaná red řádky k zobrazení při okraji ovládací prvky odpovídají nebo když jsou zarovnané text směrné plány. Hranice pro zarovnání se zobrazí pouze tehdy, když **přichycování k zarovnávacím čárám** je povolená.

 **Mřížka rails** `Grid` rails se používají ke správě řádků a sloupců v [mřížky](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) panelu. Můžete vytvářet a odstraňovat řádky a sloupce a můžeme upravit jejich relativní šířky a výšky. Svislé lišty mřížky, které se zobrazí na levé straně návrhové plochy, se používá pro řádky a vodorovná čára, která se zobrazí v horní části, se používá pro sloupce.

 **Doplňky pro úpravy mřížky** A `Grid` doplněk pro úpravy se zobrazí jako trojúhelník, který má k němu připojená na svislý nebo vodorovný řádku `Grid` lišty. Při přetažení `Grid` doplněk pro úpravy, šířky nebo výšky sousedící sloupce nebo řádky aktualizovat, protože najeďte myší.

 `Grid` doplňky pro úpravy se používají k řízení šířku a výšku `Grid`na řádky a sloupce. Kliknutím můžete přidat nový sloupec nebo řádek `Grid` rails. Když přidáte nový řádek řádku nebo sloupce pro `Grid` mimo lišty, která umožňuje explicitně nastavit šířku a výšku. Otevře se panel, který má dvě nebo více sloupců nebo řádků, zkrácené nástrojů. Zkrácené nástrojů vám umožní nastavit možnosti nastavení velikosti pro `Grid` řádků a sloupců.

 **Úchyty pro změnu velikosti** úchyty pro změnu velikosti, zobrazí se na vybraných ovládacích prvků a vám umožní změnit velikost ovládacího prvku. Při změně velikosti ovládacího prvku se zobrazí hodnoty šířky a výšky obvykle umožňují upravit velikost ovládacího prvku. Další informace o manipulaci s ovládacích prvků v návrhovém zobrazení najdete v tématu [práce s elementy v Návrháři XAML](../designers/working-with-elements-in-xaml-designer.md).

 **Okraje** okraje představují velikost pevné mezery mezi okrajem ovládacího prvku a hraničními zařízeními svého kontejneru. Můžete nastavit okraje ovládacího prvku pomocí [okraj](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) pod **rozložení** v okně Vlastnosti.

 **Doplňky pro úpravy okrajů** Změna okrajů elementu vzhledem k jeho kontejner rozložení můžete použít doplňků pro úpravy rozpětí. Při otevření okrajů není nastavená okraj a doplněk pro úpravy rozpětí zobrazí porušený řetězec. Když není nastavená na okraji, zůstane prvky při změně velikosti kontejneru rozložení v době běhu na místě. Při zavření okrajů okrajů zobrazí Nepřerušený řetěz a prvky budou přesunuty spolu s okrajem při změně velikosti kontejneru rozložení v době běhu (na okraj zůstanou pevné).

 **Element popisovače** upravíte elementu pomocí elementu popisovače, které se zobrazí na návrhové ploše při přesunutí ukazatele myši do rohů modrý obdélník, který kolem prvku. Tyto manipulační body umožňují otočení, změna velikosti, překlopit, přesunout nebo přidat poloměr na prvek. Značka pro element popisovač se liší podle funkcí a mění v závislosti na přesné umístění ukazatele. Pokud nevidíte element popisovače, ujistěte se, že je vybraný prvek.

 V návrhovém zobrazení jsou k dispozici v levé dolní části obrazovky, příkazy další návrhovou plochu, jak je znázorněno zde:

 ![Příkazy zobrazení Návrh](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Tyto příkazy jsou k dispozici na tomto panelu nástrojů:

 **Přiblížení** přiblížení umožňuje změnit velikost na návrhovou plochu. Můžete zvětšit z % 12,5 800 % nebo vyberte možnosti, jako je například **přizpůsobit výběru** a **přizpůsobit všechny**.

 **Zobrazit/skrýt přichytávací mřížku** zobrazí nebo skryje přichytávací mřížku, která zobrazuje mřížky. Mřížka se používají při buď **přichycování k čarám mřížky** nebo **přichycování k zarovnávacím čárám** je povolená.

 **Zapnutí a vypnutí přichycování k čarám mřížky** Pokud **přichycování k čarám mřížky** je povolená, když při přetahování prvku na návrhové ploše, element obvykle bylo v souladu s nejbližší vodorovné a svislé mřížky.

 **Zapnout či vypnout přichycování k zarovnávacím čárám** usnadňují zarovnávacích čar zarovnání určuje relativní vzhledem k sobě navzájem. Pokud **přichycování k zarovnávacím čárám** je povolena, když přetahujete ovládacího prvku vzhledem k další ovládací prvky, zarovnání hranice zobrazí, když okrajů a text některé ovládací prvky jsou zarovnaná vodorovně nebo svisle. Hranici zarovnání se zobrazí jako červená přerušovaná čára.

 V XAML zobrazení okna obsahujícího editoru XAML je aktivní okno a editoru XAML je primární nástroj pro vytváření. Rozšiřitelné aplikace Markup Language (XAML) obsahuje slovník deklarativní, založený na formátu XML pro zadání uživatelského rozhraní aplikace. Zobrazení XAML obsahuje technologie IntelliSense, automatického formátování, zvýrazňování syntaxe a navigace značek. Tento obrázek ukazuje XAML zobrazení:

 ![Zobrazení XAML](../designers/media/xaml-editor.png "xaml_editor")

 **Zobrazení příčku** příčku zobrazení se zobrazí v horní části zobrazení XAML, když je editoru XAML v dolním okně. Zobrazení příčku umožňuje řídit relativní velikosti zobrazení návrhové a XAML zobrazení. Můžete také exchange umístění zobrazení (pomocí **zaměnit podokna** tlačítko), určete, zda jsou vodorovně nebo svisle uspořádané zobrazení a následně sbalí buď zobrazení.

 **Přiblížení značek** přiblížení značky vám umožní na velikost zobrazení XAML. Můžete zvětšit z 20 % na 400 %.

## <a name="device-window"></a>Okno zařízení
 V okně zařízení v Návrháři XAML umožňuje simulovat v době návrhu různá zobrazení, zobrazení a zobrazení možností pro projekt Windows Store nebo Windows Phone. V okně zařízení je k dispozici na **návrhu** nabídky při práci v Návrháři XAML. Zde je, jak to funguje:

 ![Okno zařízení](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Jedná se o možnostech dostupných v okně zařízení:

 **Zobrazit** určuje různé velikosti zobrazení a řešení pro aplikaci.

 **Orientace** Určuje jinou orientace aplikace: **na šířku** nebo **na výšku**.

 **Edge** Určuje zarovnání různých edge pro vaši aplikaci: **obě**, **vlevo**, **vpravo**, nebo **žádný**.

 **Vysoký kontrast –** zobrazte si náhled aplikace podle vybraného nastavení kontrastu. Toto nastavení, při nastavení na hodnotu jiné než **výchozí**, přepíše `RequestedTheme` nastavenou v souboru App.xaml.

 **Přepsat škálování** Zapne nebo vypne emulace škálování na návrhovou plochu dokumentu. To umožňuje škálování procento zvýšit jediný faktor. Zaškrtněte políčko Zapnout emulace. Například pokud vaše škálování procentuální hodnota je 100 %, dokumentu na návrhové ploše se bude škálovat 140 %. Tato možnost je zakázaná, pokud je aktuální procento škálování 180.

 **Minimální šířka** určuje nastavení minimální šířky. Minimální šířka lze změnit v souboru App.xaml.

 **Motiv** určuje motivu aplikace. Například může přepínat mezi tmavý a světlý motiv.

 **Zobrazit chrome** Zapne nebo vypne simulované tablet rámeček okolo vaší aplikace v návrhovém zobrazení. Zaškrtněte políčko Zobrazit rámce.

 **Oříznout přesahy displeje** Určuje režim zobrazení. Zaškrtněte políčko do Galerie velikost dokumentu na velikost zobrazení.

## <a name="document-outline-window"></a>Osnova dokumentu – okno
 Okno osnovy dokumentu v Návrháři XAML umožňuje provádět tyto úkoly:

- Zobrazte hierarchickou strukturu všech prvků na návrhové ploše.

- Vyberte elementy tak, aby možno upravovat (přesunout je kolem v hierarchii, je upravovat návrhovou plochu, nastavit jejich vlastnosti v okně Vlastnosti a tak dále). Další informace najdete v tématu [práce s elementy v Návrháři XAML](../designers/working-with-elements-in-xaml-designer.md)

- Vytvářet a upravovat šablony pro prvky, které jsou ovládací prvky.

- Pomocí místní nabídky pro vybrané elementy. Stejnou nabídku je také k dispozici pro vybrané elementy na návrhovou plochu.

  Chcete-li zobrazit okno osnovy dokumentu, na panelu nabídek zvolte **zobrazení**, **ostatní Windows**, **Osnova dokumentu**.

  ![Okno Osnova dokumentu](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Jedná se o možnostech dostupných v okně Osnova dokumentu:

  **Osnova dokumentu** hlavního zobrazení v okně Osnova dokumentu ukazuje hierarchii dokumentu ve stromové struktuře. Hierarchickou povahu Osnova dokumentu můžete použít k prozkoumání dokumentu na různých úrovních podrobností a k uzamčení nebo skrytí prvků jednotlivě nebo ve skupinách.

  **Zobrazit/skrýt** zobrazí nebo skryje prvky návrhové plochy, které odpovídají položkám v Osnova dokumentu. Použití **zobrazit/skrýt** tlačítka, který zobrazí symbol oka, když se zobrazí, nebo stiskněte kombinaci kláves CTRL + H skrýt elementy a SHIFT + CTRL + H k jejich zobrazení.

  **Zamknout/odemknout** zamkne a odemkne prvky návrhové plochy, které odpovídají položkám v Osnova dokumentu. Uzamčené elementy se nedá upravit. Použití **Zamknout/odemknout** tlačítka, které budou zobrazovat ikona zámku symbol v případě, že nebo stiskněte kombinaci kláves CTRL + L prvkům zámek a CTRL + SHIFT + L odemčení.

  **Obnovit obor na pageRoot** možnosti v horní části okna Osnova dokumentu, který zobrazuje symbol šipku nahoru, vrátí do předchozího oboru Osnova dokumentu. Přesouvání rozsahu směrem nahoru platí pouze v případě, že jste v rámci stylu nebo šablony.

## <a name="properties-window"></a>Vlastnosti – okno
 V okně Vlastnosti vám umožní nastavit hodnoty vlastností v ovládacích prvcích. Zde je, jak to funguje:

 ![okno Vlastnosti](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Existují různé možnosti v horní části okna Vlastnosti. Můžete změnit název aktuálně vybraného prvku s použitím **název** pole. V levém horním rohu je ikona, která reprezentuje aktuálně vybraný element. Chcete-li seřadit vlastnosti podle kategorie nebo abecedy, klikněte na tlačítko **kategorie**, **název**, nebo **zdroje** v **uspořádat podle** seznamu. Pokud chcete zobrazit seznam událostí pro ovládací prvek, klikněte na tlačítko **události** tlačítko, které zobrazí symbol boltu blesku. Vyhledejte vlastnost, začněte zadáním názvu vlastnosti v **vlastnosti hledání** pole. V okně vlastností zobrazuje vlastnosti, které odpovídají zadanému hledání během psaní. Některé vlastnosti umožňují nastavit upřesňující vlastnosti tak, že vyberete šipku dolů. Další informace o používání vlastností a zpracování událostí naleznete v tématu [rychlý start: Přidání ovládacích prvků a zpracování událostí](https://go.microsoft.com/fwlink/?LinkID=247983)

 Vpravo od každé vlastnosti je hodnota *značka vlastnosti* , který se zobrazí jako pole symbolu. Vzhled značky vlastnost označuje, zda je datové vazby nebo prostředek použitý pro vlastnost. Například symbol bílé pole určuje výchozí hodnotu, symbol černé skříňky obvykle označuje, že použití místního prostředku a oranžová pole se obvykle označuje, že byl použit datové vazby. Po kliknutí na značku vlastnosti, můžete přejít na definici stylu, otevřete Tvůrce vazeb dat nebo otevřít výběr prostředku.

## <a name="see-also"></a>Viz také
 [Práce s elementy v Návrháři XAML](../designers/working-with-elements-in-xaml-designer.md) [vytvoření a použití prostředku](../designers/how-to-create-and-apply-a-resource.md) [návod: vazba s daty v Návrháři XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
