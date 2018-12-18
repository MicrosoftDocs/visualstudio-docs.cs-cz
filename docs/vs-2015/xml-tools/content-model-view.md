---
title: Zobrazení modelu obsahu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a535a97835491f4a109ed0893d20a4330b218801
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860302"
---
# <a name="content-model-view"></a>Zobrazení modelu obsahu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zobrazení modelu obsahu poskytuje grafické znázornění schématu místní a globální uzlů a jejich komponent, včetně jednoduché a komplexní typy prvků, skupiny modelů, atributy a skupiny atributů. Komentáře XML a pokyny pro zpracování nelze zobrazit v zobrazení modelu obsahu. Zobrazení modelu obsahu obsahuje dva panely: **pracovní prostor** panel, který obsahuje seznam uzlů v [pracovní prostor návrháře schémat XML](../xml-tools/xml-schema-designer-workspace.md)a návrhovou plochu, ve kterém uvidíte modelu obsahu schématu uzly, které jsou vybrány v **pracovní prostor** panelu. Zobrazení modelu obsahu také obsahuje panel nástrojů Návrhář schémat XML a panelu navigace s popisem cesty.  
  
 Na následujícím obrázku obsahuje panelu pracovního prostoru šesti uzlů schémat. `purchaseOrder` Uzlu je vybrán v panelu pracovní prostor a zobrazí se v návrhové ploše.  
  
 ![Zobrazení návrháře modelu obsahu schématu XML](../xml-tools/media/xsddesigner-contentmodelview.gif "XSDDesigner_ContentModelView")  
  
## <a name="workspace-panel"></a>Panelu pracovního prostoru  
 Po přidání uzlů do pracovního prostoru, zobrazí se seznam uzlů v **pracovní prostor** panel ovládacího prvku zobrazení modelu obsahu. Když vyberete uzly v **pracovní prostor** panelu, zobrazí se na povrchu návrhu zobrazení modelu obsahu. K odstranění uzlů ze workpsace, pomocí tohoto panelu nástrojů návrháře XSD **pracovní prostor** panelu Místní nabídky nebo klávesu DELETE.  
  
 Informace o přidání uzlů najdete v tématu v části "Přidání uzlů do pracovní prostor" [pracovní prostor návrháře schémat XML](../xml-tools/xml-schema-designer-workspace.md).  
  
## <a name="design-surface"></a>Návrhová plocha  
 Když je vybrán uzel panelu pracovního prostoru, přidá se do zobrazení modelu obsahu návrhovou plochu, kde najdete podrobnosti o uzlu.  
  
 Model obsahu uzlu je reprezentován rozšíření grafické stromu s prvky a atributy vyskytující se jako uzly stromu. Ve výchozím nastavení je rozšířit jenom jedna úroveň. Další informace, jako je například tvůrce, názvy typů, skupiny a další kontejnery jsou umístěny v svislá čára (při rozbalení) podél elementy a atributy, které jsou uzavřete. Když dvakrát kliknete na svislý pruh, stane se vodorovný a sbalí stromu. Když dvakrát kliknete na vodorovný pruh, stane se svislé a strom roste směrem. Výběr svislá čára vybere všechny uzly v kontejneru. Rozšíření se zobrazí na pravé straně uzlu, pokud element můžete rozbalit nebo sbalit.  
  
 Pokud návrhové ploše je prázdné, jsou uvedeny editoru XML, Průzkumníka schémat XML a vodoznak. *Vodoznak* seznam obsahuje odkazy na všechna zobrazení návrháře XSD. Pokud sadě schémat obsahuje chyby, na konci seznamu se zobrazí následující text: "K zobrazení a opravte chyby v sadě pomocí seznamu chyb."  
  
## <a name="breadcrumb-bar"></a>Navigační panel  
 Na panelu navigace s popisem cesty v dolní části zobrazení modelu obsahu zobrazuje umístění vybraného uzlu v sadě schémat.  
  
## <a name="context-menus"></a>Místní nabídky  
 Když kliknete pravým tlačítkem na položku na návrhovou plochu nebo na panelu pracovního prostoru, zobrazí se kontextová nabídka. Následující tabulka popisuje možnosti, které jsou k dispozici pro zobrazení modelu obsahu návrhovou plochu.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Zobrazit v Průzkumníkovi schémat XML**|Umístí fokus na Průzkumník schémat a zvýrazní schématu sady uzlu.|  
|**Zobrazit v zobrazení grafu**|Přepne do zobrazení grafu.|  
|**Generovat ukázkový soubor XML**|K dispozici pouze pro globální prvky. Generuje ukázkový soubor XML pro prvek globální.|  
|**Zobrazit dokumentaci**|Zobrazí nebo skryje obsah uzlu poznámky a dokumentaci.|  
|**Exportujte Diagram jako obrázek...**|Uloží soubor ve formátu XPS návrhové ploše.|  
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položky vybrané v Průzkumník schémat XML bude také vybrána v editoru XML.|  
|**Okno Vlastnosti**|Otevře **vlastnosti** okna (pokud ještě není otevřený). Toto okno zobrazuje informace o uzlu.|  
  
 Následující tabulka popisuje možnosti, které jsou k dispozici pro panelu pracovního prostoru.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Zobrazit v Průzkumníkovi schémat XML**|Umístí fokus na Průzkumník schémat a zvýrazní schématu sady uzlu.|  
|**Zobrazit v zobrazení grafu**|Přepne do zobrazení grafu.|  
|**Vymazat pracovní prostor**|Vymaže pracovní prostor a návrhovou plochu.|  
|**Odebrat z pracovního prostoru**|Odebere vybrané uzly z pracovního prostoru a návrhovou plochu.|  
|**Odeberte všechny kromě výběru z pracovního prostoru**|Odebere uzly, které nejsou vybrané z pracovního prostoru a návrhovou plochu.|  
|**Generovat ukázkový soubor XML**|K dispozici pouze pro globální prvky. Generuje ukázkový soubor XML pro prvek globální.|  
|**Vybrat vše**|Vybere všechny uzly v panelu pracovního prostoru.|  
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položky vybrané v Průzkumník schémat XML bude také vybrána v editoru XML.|  
|**Okno Vlastnosti**|Otevře **vlastnosti** okna (pokud ještě není otevřený). Toto okno zobrazuje informace o uzlu.|  
  
## <a name="properties-window"></a>Okno vlastností  
 Pomocí místní nabídky k prvním spuštění **vlastnosti** okna. Ve výchozím nastavení **vlastnosti** okno se zobrazí v pravém dolním rohu sady Visual Studio. Po kliknutí na uzel, který se vykreslí v zobrazení modelu obsahu, vlastnosti uzlu se zobrazí v **vlastnosti** okna.  
  
## <a name="xsd-designer-toolbar"></a>Panel nástrojů návrháře XSD  
 Při aktivním zobrazení modelu obsahu jsou povoleny následující tlačítka panelu nástrojů návrháře XSD.  
  
 ![Panel nástrojů návrháře schémat XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Ukázat počáteční zobrazení**|Přepne [počáteční zobrazení](../xml-tools/start-view.md). Toto zobrazení je přístupný pomocí klávesové zkratky: **CTRL + 1**.|  
|**Ukázat zobrazení modelu obsahu**|Přepne [zobrazení modelu obsahu](../xml-tools/content-model-view.md). Toto zobrazení je přístupný pomocí klávesové zkratky: **CTRL + 2**.|  
|**Ukázat zobrazení grafu**|Přepne [grafu zobrazení](../xml-tools/graph-view.md). Toto zobrazení je přístupný pomocí klávesové zkratky: **CTRL + 3**.|  
|**Vymazat pracovní prostor**|Vymaže pracovní prostor a návrhovou plochu.|  
|**Odebrat z pracovního prostoru**|Odebere vybrané uzly z pracovního prostoru a serface návrhu.|  
|**Odeberte všechny kromě výběru z pracovního prostoru**|Odebere uzly, které nejsou vybrané z pracovního prostoru a serface návrhu.|  
|**Zobrazit dokumentaci**|Zobrazí nebo skryje obsah uzlu poznámky a dokumentaci.|  
  
## <a name="panscroll"></a>Posun/posuvníku  
 Návrhovou plochu se můžete pohybovat pomocí posuvníky nebo tím, že podržíte klávesu CTRL při klikněte a přetáhněte myší. Při posouvání návrhové plochy, klikněte na tlačítko a přetáhněte kurzoru se změní na čtyři překřížené šipky směřující do čtyř směrů.  
  
## <a name="undoredo"></a>Zpět/znovu  
 Funkce Zpět/znovu je povolená v zobrazení modelu obsahu pro následující akce:  
  
-   Přidání jednoho uzlu pomocí přetahování.  
  
-   Přidání více uzlů z výsledků hledání v Průzkumníkovi schémat.  
  
-   Přidávání uzlů ze zobrazení spuštění.  
  
-   Odstraňuje se jeden nebo více uzlů.  
  
## <a name="zoom"></a>Lupa  
 Přiblížení je k dispozici v v pravém dolním rohu zobrazení modelu obsahu.  
  
 Zvětšení lze řídit následujícími způsoby:  
  
- Podržením klávesy CTRL a otáčení kolečka myši, když myš je přesunutá na plochu zobrazení modelu obsahu.  
  
- Pomocí posuvníku. Posuvník zobrazuje aktuální úroveň přiblížení.  
  
  Posuvník přiblížení je neprůhledný, když vyberte ho, podržte ukazatel myši nad, nebo pomocí kombinace kláves CTRL kolečko myši pro přiblížení; v jinou dobu je transparentní.  
  
## <a name="xml-editor-integration"></a>Integrace editoru XML  
 Můžete přepínat vpřed a zpět mezi XSD Návrhář a Editor souborů XML pomocí místní nabídky.  
  
 Pokud provedete změny schématu, nastavte v editoru XML změny budou synchronizovány v zobrazení modelu obsahu. Další informace najdete v tématu [integrace s editorem XML](../xml-tools/integration-with-xml-editor.md).  
  
## <a name="see-also"></a>Viz také  
 [Pracovní prostor Návrháře schémat XML](../xml-tools/xml-schema-designer-workspace.md)



