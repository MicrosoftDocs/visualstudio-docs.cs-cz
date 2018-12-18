---
title: Zobrazení grafu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d1c0bbe55f2e63c1d86d71556392d57d1330c6b4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813619"
---
# <a name="graph-view"></a>Zobrazení grafu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zobrazení grafu poskytuje grafické znázornění schématu globální uzlů a relací mezi uzly. Všimněte si, že zobrazení grafu neumožňuje změnit rozložení schéma, nastavte na návrhové ploše. Zobrazení grafu také obsahuje panel nástrojů Návrhář schémat XML a panelu navigace s popisem cesty.  
  
 Následující obrázek ukazuje zobrazení grafu se šesti globální uzly na jeho návrhové ploše.  
  
 ![Schéma XML-zobrazení návrháře grafu](../xml-tools/media/xsddesigner-graphview.gif "XSDDesigner_GraphView")  
  
## <a name="design-surface"></a>Návrhová plocha  
 Na návrhovou plochu zobrazení grafu zobrazí obsah [pracovní prostor návrháře schémat XML](../xml-tools/xml-schema-designer-workspace.md). Pokud pracovní prostor obsahuje všechny globální uzly v sadě schémat, uzly se zobrazují na návrhové ploše zobrazení grafu a šipky se vykreslují mezi uzly, které mají relace.  
  
 Dvojitým kliknutím na uzel v zobrazení grafu otevřete tak Editor XML.  
  
 Pokud chcete odstranit vybrané uzly z pracovního prostoru, použijte klávesu DELETE nebo panelu nástrojů návrháře XSD.  
  
 Pokud návrhové ploše je prázdné, jsou uvedeny editoru XML, Průzkumníka schémat XML a vodoznak. *Vodoznak* seznam obsahuje odkazy na všechna zobrazení návrháře XSD.  
  
 ![XSD návrháře; Zobrazení grafu](../xml-tools/media/xsdgraphviewwatermark.gif "XSDGraphViewWatermark")  
  
 Pokud sadě schémat obsahuje chyby, na konci seznamu se zobrazí následující text: "K zobrazení a opravte chyby v sadě pomocí seznamu chyb."  
  
## <a name="breadcrumb-bar"></a>Navigační panel  
 Na panelu navigace s popisem cesty v dolní části zobrazení grafu zobrazuje umístění vybraného uzlu v sadě schémat. Pokud je vybráno více položek, panelu navigace s popisem cesty bude prázdné.  
  
## <a name="context-menu"></a>Místní nabídka  
 Následující tabulka popisuje možnosti, které jsou k dispozici pro všechny uzly na návrhové ploše zobrazení grafu.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Zobrazit v Průzkumníkovi schémat XML**|Umístí fokus na Průzkumník schémat a zvýrazní schématu sady uzlu.|  
|**Zobrazit v zobrazení grafu**|Přepne do zobrazení grafu (šedě).|  
|**Generovat ukázkový soubor XML**|K dispozici pouze pro globální prvky. Generuje ukázkový soubor XML pro prvek globální.|  
|**Vymazat pracovní prostor**|Vymaže pracovní prostor a návrhovou plochu.|  
|**Odebrat z pracovního prostoru**|Odebere vybrané uzly z pracovního prostoru a návrhovou plochu.|  
|**Odeberte všechny kromě výběru z pracovního prostoru**|Odebere uzly, které nejsou vybrané z pracovního prostoru a návrhovou plochu.|  
|**Exportujte Diagram jako obrázek...**|Uloží soubor ve formátu XPS návrhové ploše.|  
|**Vybrat vše**|Vybere všechny uzly na návrhové ploše.|  
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položky vybrané v Průzkumník schémat XML bude také vybrána v editoru XML.|  
|**Okno Vlastnosti**|Otevře **vlastnosti** okna (pokud ještě není otevřený). Toto okno zobrazuje informace o uzlu.|  
  
 Kromě běžných nastavení je popsáno výše kontextovou nabídku pro globální prvky také obsahuje následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přidat definici typu**|Přidá základní typ do diagramu.|  
|**Přidat všechny odkazy**|Přidá všechny uzly, které odkazovat na prvek a vykreslí šipky znázorňující vztahy mezi nimi.|  
|**Přidat členy skupiny nahrazení**|Přidá všechny členy skupiny nahrazení. Tato možnost se objeví v zobrazení, pokud je element head nebo členem substituční skupiny.|  
|**Generovat ukázkový soubor XML**|Generuje ukázkový soubor XML pro prvek globální.|  
  
 Kromě běžných nastavení je popsáno výše kontextovou nabídku pro globální jednoduché a globální komplexní typy také obsahuje následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přidat základní typ**|Pokud vybraný typ je odvozen od typu globální, přidá základní typ vybraného typu.|  
|**Přidat všechny odkazy**|Přidá všechny odkazy vybraného typu. To zahrnuje elementy a atributy vybraného typu a typy odvozené od vybraného typu.|  
|**Přidat všechny odvozené typy**|Přidá všechny typy, které jsou přímo i nepřímo odvozeny z vybraného typu.|  
|**Přidat všechny nadřazené prvky**|Přidá všechny nadřazené (základní) typy.|  
  
 Kromě běžných nastavení je popsáno výše kontextovou nabídku pro globální skupiny a skupiny atributů obsahuje také následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přidat všechny odkazy**|Přidá všechny uzly, které odkazují do skupiny a vykreslí šipky znázorňující vztahy mezi nimi.|  
|**Přidat všechny členy**|Přidá všechny členy skupiny a vykreslí šipky znázorňující vztahy mezi nimi.|  
  
 Kromě běžných nastavení je popsáno výše kontextovou nabídku pro globální atributy také obsahuje následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přidat všechny odkazy**|Přidá všechny uzly, které odkazují do skupiny a vykreslí šipky znázorňující vztahy mezi nimi.|  
  
## <a name="properties-window"></a>Okno vlastností  
 Pomocí místní nabídky k prvním spuštění **vlastnosti** okna. Ve výchozím nastavení **vlastnosti** okno se zobrazí v pravém dolním rohu sady Visual Studio. Po kliknutí na uzel, který se vykreslí v zobrazení modelu obsahu, vlastnosti uzlu se zobrazí v **vlastnosti** okna.  
  
## <a name="xsd-toolbar"></a>Panel nástrojů XSD  
 Při aktivním zobrazení grafu jsou povoleny následující tlačítka panelu nástrojů XSD.  
  
 ![Panel nástrojů návrháře schémat XML](../xml-tools/media/xsdgraphviewtoolbar.gif "XSDGraphViewToolbar")  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Ukázat počáteční zobrazení**|Přepne [počáteční zobrazení](../xml-tools/start-view.md). Toto zobrazení je přístupný pomocí klávesové zkratky: **CTRL + 1**.|  
|**Ukázat zobrazení modelu obsahu**|Přepne [zobrazení modelu obsahu](../xml-tools/content-model-view.md). Toto zobrazení je přístupný pomocí klávesové zkratky: **CTRL + 2**.|  
|**Ukázat zobrazení grafu**|Přepne [grafu zobrazení](../xml-tools/graph-view.md). Toto zobrazení je přístupný pomocí klávesové zkratky: **CTRL + 3**.|  
|**Vymazat pracovní prostor**|Vymaže pracovní prostor a návrhovou plochu.|  
|**Odebrat z pracovního prostoru**|Odebere vybrané uzly z pracovního prostoru a serface návrhu.|  
|**Odeberte všechny kromě výběru z pracovního prostoru**|Odebere uzly, které nejsou vybrané z pracovního prostoru a serface návrhu. Tato možnost je povolená v zobrazení modelu obsahu a zobrazení grafu.|  
|**Zleva doprava**|Rozložení v zobrazení grafu se změní na uzly Hierarchická reprezentace zleva doprava. Tuto možnost lze přistupovat pomocí klávesové zkratky: **Alt + šipka vpravo**.|  
|**Zprava doleva**|Rozložení v zobrazení grafu se změní na uzly Hierarchická reprezentace zprava doleva. Tuto možnost lze přistupovat pomocí klávesové zkratky: **Alt + šipka vlevo**.|  
|**Shora dolů**|Rozložení v zobrazení grafu se změní na uzly Hierarchická reprezentace shora dolů. Tuto možnost lze přistupovat pomocí klávesové zkratky: **Alt + Šipka dolů**.|  
|**Zdola nahoru**|Změní rozložení v zobrazení grafu do dolní části horní Hierarchická reprezentace uzly. Tuto možnost lze přistupovat pomocí klávesové zkratky: **Alt + šipka nahoru**.|  
  
## <a name="panscroll"></a>Posun/posuvníku  
 Návrhovou plochu se můžete pohybovat pomocí posuvníky nebo tím, že podržíte klávesu CTRL při klikněte a přetáhněte myší. Při posouvání návrhové plochy, klikněte na tlačítko a přetáhněte kurzoru se změní na čtyři překřížené šipky směřující do čtyř směrů.  
  
## <a name="undoredo"></a>Zpět/znovu  
 Funkce Zpět/znovu je povolená v zobrazení grafu pro následující akce:  
  
-   Přidání jednoho uzlu pomocí přetahování.  
  
-   Přidání více uzlů z výsledků hledání v dotazech Průzkumník schémat nebo zobrazení Start.  
  
-   Odstraňuje se jeden nebo více uzlů.  
  
## <a name="zoom"></a>Lupa  
 Přiblížení je k dispozici v pravém dolním rohu zobrazení grafu.  
  
 Zvětšení lze řídit následujícími způsoby:  
  
- Podržením klávesy CTRL a otáčení kolečka myši, když myš je přesunutá na plochu grafu.  
  
- Pomocí posuvníku. Posuvník zobrazuje aktuální úroveň přiblížení.  
  
  Posuvník přiblížení je neprůhledný, když vyberte ho, podržte ukazatel myši nad, nebo pomocí kombinace kláves CTRL kolečko myši pro přiblížení; v jinou dobu je transparentní.  
  
## <a name="xml-editor-integration"></a>Integrace editoru XML  
 Můžete přepínat vpřed a zpět mezi zobrazení grafu a Editor souborů XML tak, že kliknete na uzel a pomocí kontextové nabídky zobrazení kódu.  
  
 Pokud provedete změny schématu, nastavte v editoru XML, změny budou synchronizovány v zobrazení grafu. Další informace najdete v tématu [integrace s editorem XML](../xml-tools/integration-with-xml-editor.md).  
  
## <a name="see-also"></a>Viz také  
 [Návrhová plocha](../xml-tools/xml-schema-designer-workspace.md)



