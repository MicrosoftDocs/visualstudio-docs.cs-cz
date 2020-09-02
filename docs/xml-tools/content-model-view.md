---
title: Zobrazení modelu obsahu Návrhář schématu XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 830dbdda0027551a25747235e6ad9dffbbc11b23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592910"
---
# <a name="content-model-view"></a>Zobrazení modelu obsahu

Zobrazení modelu obsahu poskytuje grafické reprezentace místních a globálních uzlů schématu a jejich součástí, včetně jednoduchých a složitých typů, prvků, skupin modelů, atributů a skupin atributů. Komentáře XML a pokyny pro zpracování nelze zobrazit v zobrazení modelu obsahu. Zobrazení modelu obsahu obsahuje dva panely: panel **pracovního prostoru** , který obsahuje seznam uzlů v [pracovním prostoru Návrhář schématu XML](../xml-tools/xml-schema-designer-workspace.md)a návrhovou plochu, kde můžete zobrazit model obsahu uzlů schématu, které jsou vybrány na panelu **pracovního prostoru** . Zobrazení modelu obsahu zahrnuje také panel nástrojů Návrhář schématu XML a panel s popisem cesty.

Na následujícím obrázku obsahuje panel **pracovního prostoru** šest uzlů schématu. `purchaseOrder`Uzel je vybrán v panelu **pracovní prostor** a zobrazí se na návrhové ploše.

![Zobrazení modelu obsahu Návrhář schématu XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panel pracovního prostoru

Po přidání uzlů do pracovního prostoru se seznam uzlů zobrazí na panelu **pracovního prostoru** v zobrazení modelu obsahu. Když vyberete uzly na panelu **pracovní prostor** , objeví se na návrhové ploše zobrazení modelu obsahu. Chcete-li odstranit uzly z pracovního prostoru, použijte panel nástrojů Návrhář XSD, panel **pracovního prostoru** , klepněte pravým tlačítkem myši na nabídku nebo na **Odstranit** klíč.

Informace o přidávání uzlů naleznete v části Přidání uzlů do pracovního prostoru v [pracovním prostoru Návrhář schématu XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Návrhová plocha

Když je na panelu **pracovního prostoru** vybraný uzel, přidá se do návrhové plochy zobrazení modelu obsahu, kde můžete zobrazit podrobnosti uzlu.

Model obsahu uzlu je reprezentován rozbalením grafického stromu s elementy a atributy, které se zobrazují jako uzly stromu. Ve výchozím nastavení je rozbalena pouze jedna úroveň. Další informace, jako jsou sestavování, názvy typů, skupiny a další kontejnery, jsou umístěny ve svislém pruhu (Pokud je rozbaleno) podél prvků a atributů, které jsou k nim uzavřeny. Když dvakrát kliknete na svislý pruh, dojde k jeho horizontálnímu a sbalení stromové struktury. Když dvakrát kliknete na vodorovný pruh, dojde k jeho svislému a strom se rozbalí. Výběrem svislého panelu se vybere všechny uzly v kontejneru. Pokud je prvek možné rozbalit nebo sbalit, zobrazí se na pravé straně uzlu.

Pokud je návrhová plocha prázdná, zobrazí se editor XML, **Průzkumník schémat XML**a vodoznak. *Vodoznak* je seznam odkazů na všechna zobrazení návrháře XSD. Pokud má sada schémat chyby, na konci seznamu se zobrazí následující text: "pomocí Seznam chyb můžete zobrazit a opravit chyby v sadě."

## <a name="breadcrumb-bar"></a>Panel s popisem cesty

Panel s popisem cesty v dolní části zobrazení modelu obsahu ukazuje, kde se vybraný uzel nachází v sadě schémat.

## <a name="context-menus"></a>Místní nabídky

Když kliknete pravým tlačítkem myši na položku na panelu návrh nebo **pracovní prostor** , zobrazí se místní nabídka. Následující tabulka popisuje možnosti, které jsou k dispozici pro návrhovou plochu zobrazení modelu obsahu.

|Možnost|Popis|
|-|-----------------|
|**Zobrazit v Průzkumníkovi schémat XML**|Umístí fokus do Průzkumníka schémat a zvýrazní uzel sada schémat.|
|**Zobrazit v zobrazení grafu**|Přepne do zobrazení grafu.|
|**Generovat vzorový kód XML**|K dispozici pouze pro globální prvky. Vygeneruje vzorový soubor XML pro globální prvek.|
|**Zobrazit dokumentaci**|Zobrazí nebo skryje obsah uzlu poznámky nebo dokumentace.|
|**Exportovat diagram jako obrázek**|Uloží návrhovou plochu do souboru XPS.|
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položka, která je vybrána v **Průzkumníku schémat XML** , je vybrána také v editoru XML.|
|**Okno vlastností**|Otevře okno **vlastnosti** (Pokud ještě není otevřené). V tomto okně se zobrazují informace o uzlu.|

Následující tabulka popisuje možnosti, které jsou k dispozici pro panel **pracovního prostoru** .

|Možnost|Popis|
|-|-----------------|
|**Zobrazit v Průzkumníkovi schémat XML**|Umístí fokus do Průzkumníka schémat a zvýrazní uzel sada schémat.|
|**Zobrazit v zobrazení grafu**|Přepne do zobrazení grafu.|
|**Vymazat pracovní prostor**|Vymaže pracovní prostor a návrhovou plochu.|
|**Odebrat z pracovního prostoru**|Odebere vybrané uzly z pracovního prostoru a na návrhovou plochu.|
|**Odebrat všechny kromě výběry z pracovního prostoru**|Odebere uzly, které nejsou vybrané z pracovního prostoru a na návrhové ploše.|
|**Generovat vzorový kód XML**|K dispozici pouze pro globální prvky. Vygeneruje vzorový soubor XML pro globální prvek.|
|**Vybrat vše**|Vybere všechny uzly na panelu **pracovního prostoru** .|
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položka, která je vybrána v **Průzkumníku schémat XML** , je vybrána také v editoru XML.|
|**Okno vlastností**|Otevře okno **vlastnosti** (Pokud ještě není otevřené). V tomto okně se zobrazují informace o uzlu.|

## <a name="properties-window"></a>Vlastnosti – okno

Otevřete okno **vlastnosti** kliknutím pravým tlačítkem (kontextová nabídka). Ve výchozím nastavení se okno **vlastnosti** zobrazí v pravém dolním rohu sady Visual Studio. Když kliknete na uzel, který je vykreslený v zobrazení modelu obsahu, zobrazí se vlastnosti tohoto uzlu v okně **vlastnosti** .

## <a name="xsd-designer-toolbar"></a>Panel nástrojů Návrhář XSD

Následující tlačítka panelu nástrojů návrháře XSD jsou povolena, když je aktivní zobrazení modelu obsahu.

![Panel nástrojů Návrhář schématu XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Možnost|Popis|
|-|-----------------|
|**Zobrazit úvodní zobrazení**|Přepne do [zobrazení začátek](../xml-tools/start-view.md). K tomuto zobrazení je možné přistupovat pomocí klávesových zkratek: **CTRL** + **1**.|
|**Zobrazit zobrazení modelu obsahu**|Přepne do [zobrazení modelu obsahu](../xml-tools/content-model-view.md). K tomuto zobrazení je možné přistupovat pomocí klávesových zkratek: **CTRL** + **2**.|
|**Zobrazit zobrazení grafu**|Přepne do [zobrazení grafu](../xml-tools/graph-view.md). K tomuto zobrazení je možné přistupovat pomocí klávesových zkratek: **CTRL** + **3**.|
|**Vymazat pracovní prostor**|Vymaže pracovní prostor a návrhovou plochu.|
|**Odebrat z pracovního prostoru**|Odebere vybrané uzly z pracovního prostoru a na návrhovou plochu.|
|**Odebrat všechny kromě výběry z pracovního prostoru**|Odebere uzly, které nejsou vybrané z pracovního prostoru a na návrhové ploše.|
|**Zobrazit dokumentaci**|Zobrazí nebo skryje obsah uzlu poznámky nebo dokumentace.|

## <a name="panscroll"></a>Posun/posun

Návrhovou plochu můžete posunout pomocí posuvníků nebo podržením klávesy **CTRL** při kliknutí myší a přetažením. Když posuňte návrhovou plochu pomocí kliknutí a přetažením, ukazatel se změní na čtyři šipky ukazující na čtyři směry.

## <a name="undoredo"></a>Vrátit zpět/znovu

Možnost vrátit zpět/znovu je v zobrazení modelu obsahu povolena pro následující akce:

- Přidání jednoho uzlu přetažením.

- Přidání více uzlů z okna výsledků hledání v Průzkumníku schémat.

- Přidávání uzlů ze zobrazení Start.

- Odstranění jednoho nebo více uzlů.

## <a name="zoom"></a>Zoom

Přiblížení je k dispozici v pravém dolním rohu zobrazení modelu obsahu.

Přiblížení lze ovládat následujícími způsoby:

- Podržením klávesy **CTRL** a otočením kolečka myši při přesunutí ukazatele myši na plochu zobrazení modelu obsahu.

- Pomocí ovládacího prvku posuvník. Posuvník zobrazuje aktuální úroveň přiblížení.

Posuvník přiblížení je neprůhledný, když ho vyberete, najeďte myší na něj, nebo můžete použít **klávesovou zkratku CTRL** s kolečkem myši pro přiblížení. ve všech ostatních případech je transparentní.

## <a name="xml-editor-integration"></a>Integrace editoru XML

Můžete přepínat mezi **návrhářem XSD** a editorem XML pomocí nabídky po kliknutí pravým tlačítkem (kontext).

Pokud provedete změny v sadě schémat v editoru XML, změny se synchronizují v zobrazení modelu obsahu. Další informace najdete v tématu [integrace s editorem XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Viz také

- [Pracovní prostor návrháře schématu XML](../xml-tools/xml-schema-designer-workspace.md)
