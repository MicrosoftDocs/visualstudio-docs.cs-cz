---
title: Zobrazení grafu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba58777700ba34de3dc3b7a842f26462daf08c89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656352"
---
# <a name="graph-view"></a>Zobrazení grafu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení grafu poskytuje grafické znázornění globálních uzlů schématu a vztahů mezi uzly. Všimněte si, že zobrazení grafu neumožňuje měnit rozložení sady schémat na návrhové ploše. Zobrazení grafu také obsahuje panel nástrojů návrháře schématu XML a panel s popisem cesty.

 Následující obrázek znázorňuje zobrazení grafu se šesti globálními uzly na své návrhové ploše.

 ![Zobrazení grafu návrháře schématu XML](../xml-tools/media/xsddesigner-graphview.gif "XSDDesigner_GraphView")

## <a name="design-surface"></a>Návrhová plocha
 Návrhová plocha zobrazení grafu zobrazuje obsah [pracovního prostoru Návrhář schématu XML](../xml-tools/xml-schema-designer-workspace.md). Pokud pracovní prostor obsahuje všechny globální uzly ze sady schémat, uzly se zobrazí na návrhové ploše zobrazení grafu a mezi uzly, které mají relace, se vykreslí šipky.

 Dvojím kliknutím na uzel v zobrazení grafu se zobrazí editor XML.

 Chcete-li odstranit vybrané uzly z pracovního prostoru, použijte panel nástrojů Návrhář XSD nebo odstranit klíč.

 Pokud je návrhová plocha prázdná, zobrazí se editor XML, Průzkumník schémat XML a vodoznak. *Vodoznak* je seznam odkazů na všechna zobrazení návrháře XSD.

 ![Návrhář XSD; Zobrazení grafu](../xml-tools/media/xsdgraphviewwatermark.gif "XSDGraphViewWatermark")

 Pokud má sada schémat chyby, na konci seznamu se zobrazí následující text: "pomocí Seznam chyb můžete zobrazit a opravit chyby v sadě."

## <a name="breadcrumb-bar"></a>Panel s popisem cesty
 Panel s popisem cesty v dolní části zobrazení grafu ukazuje, kde se vybraný uzel nachází v sadě schémat. Pokud je vybráno více položek, panel s popisem cesty bude prázdný.

## <a name="context-menu"></a>Místní nabídka
 Následující tabulka popisuje možnosti, které jsou k dispozici pro všechny uzly na návrhové ploše zobrazení grafu.

|Možnost|Popis|
|------------|-----------------|
|**Zobrazit v Průzkumníkovi schémat XML**|Umístí fokus do Průzkumníka schémat a zvýrazní uzel sada schémat.|
|**Zobrazit v zobrazení grafu**|Přepne zobrazení grafu (zobrazené šedě).|
|**Generovat vzorový kód XML**|K dispozici pouze pro globální prvky. Vygeneruje vzorový soubor XML pro globální prvek.|
|**Vymazat pracovní prostor**|Vymaže pracovní prostor a návrhovou plochu.|
|**Odebrat z pracovního prostoru**|Odebere vybrané uzly z pracovního prostoru a na návrhovou plochu.|
|**Odebrat všechny kromě výběry z pracovního prostoru**|Odebere uzly, které nejsou vybrané z pracovního prostoru a na návrhové ploše.|
|**Exportovat diagram jako obrázek...**|Uloží návrhovou plochu do souboru XPS.|
|**Vybrat vše**|Vybere všechny uzly na návrhové ploše.|
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položka, která je vybrána v Průzkumníku schémat XML, bude také vybrána v editoru XML.|
|**Okno vlastností**|Otevře okno **vlastnosti** (Pokud ještě není otevřené). V tomto okně se zobrazují informace o uzlu.|

 Kromě běžných možností popsaných výše má kontextová nabídka pro globální prvky také následující možnosti:

|Možnost|Popis|
|------------|-----------------|
|**Přidat definici typu**|Přidá do diagramu základní typ.|
|**Přidat všechny odkazy**|Přidá všechny uzly, které odkazují na element a nakreslí šipky k označení vztahů mezi nimi.|
|**Přidat členy skupiny nahrazení**|Přidá všechny členy substituční skupiny. Tato možnost se zobrazí v zobrazení, pokud je element vedoucím nebo členem substituční skupiny.|
|**Generovat vzorový kód XML**|Vygeneruje vzorový soubor XML pro globální prvek.|

 Kromě běžných možností popsaných výše má kontextová nabídka globálních jednoduchých a globálních komplexních typů následující možnosti:

|Možnost|Popis|
|------------|-----------------|
|**Přidat základní typ**|Pokud je vybraný typ odvozen z globálního typu, přidá základní typ vybraného typu.|
|**Přidat všechny odkazy**|Přidá všechny odkazy vybraného typu. To zahrnuje elementy a atributy vybraného typu a typy odvozené z vybraného typu.|
|**Přidat všechny odvozené typy**|Přidá všechny typy, které jsou přímo a nepřímo odvozené z vybraného typu.|
|**Přidat všechny nadřazené prvky**|Přidá všechny nadřazené (základní) typy.|

 Kromě výše popsaných obecných možností má kontextová nabídka pro globální skupiny a skupiny atributů také následující možnosti:

|Možnost|Popis|
|------------|-----------------|
|**Přidat všechny odkazy**|Přidá všechny uzly, které odkazují na skupinu, a nakreslí šipky k označení vztahů mezi nimi.|
|**Přidat všechny členy**|Přidá všechny členy skupiny a nakreslí šipky k označení vztahů mezi nimi.|

 V kromě na společné možnosti popsané výše má kontextová nabídka pro globální atributy také následující možnosti:

|Možnost|Popis|
|------------|-----------------|
|**Přidat všechny odkazy**|Přidá všechny uzly, které odkazují na skupinu, a nakreslí šipky k označení vztahů mezi nimi.|

## <a name="properties-window"></a>Okno vlastností
 K počátečnímu otevření okna **vlastností** použijte kontextovou nabídku. Ve výchozím nastavení se okno **vlastnosti** zobrazí v pravém dolním rohu sady Visual Studio. Když kliknete na uzel, který je vykreslený v zobrazení modelu obsahu, zobrazí se vlastnosti tohoto uzlu v okně **vlastnosti** .

## <a name="xsd-toolbar"></a>Panel nástrojů XSD
 Následující tlačítka panelu nástrojů XSD jsou povolena, když je aktivní zobrazení grafu.

 ![Panel nástrojů Návrhář schématu XML](../xml-tools/media/xsdgraphviewtoolbar.gif "XSDGraphViewToolbar")

|Možnost|Popis|
|------------|-----------------|
|**Zobrazit úvodní zobrazení**|Přepne do [zobrazení začátek](../xml-tools/start-view.md). K tomuto zobrazení je možné přistupovat pomocí klávesových zkratek: **CTRL + 1**.|
|**Zobrazit zobrazení modelu obsahu**|Přepne do [zobrazení modelu obsahu](../xml-tools/content-model-view.md). K tomuto zobrazení je možné přistupovat pomocí klávesových zkratek: **CTRL + 2**.|
|**Zobrazit zobrazení grafu**|Přepne do [zobrazení grafu](../xml-tools/graph-view.md). K tomuto zobrazení je možné přistupovat pomocí klávesových zkratek: **CTRL + 3**.|
|**Vymazat pracovní prostor**|Vymaže pracovní prostor a návrhovou plochu.|
|**Odebrat z pracovního prostoru**|Odebere vybrané uzly z pracovního prostoru a serface návrhu.|
|**Odebrat všechny kromě výběry z pracovního prostoru**|Odebere uzly, které nejsou vybrané z pracovního prostoru a serface návrhu. Tato možnost je povolená v zobrazení modelu obsahu a v zobrazení grafu.|
|**Zleva doprava**|Změní rozložení v zobrazení grafu na hierarchické znázornění uzlů na základě zleva doprava. K této možnosti lze přistupovat pomocí klávesových zkratek: **ALT + šipka vpravo**.|
|**Zprava doleva**|Změní rozložení v zobrazení grafu na hierarchické reprezentace uzlů v rámci pravého na levé. K této možnosti lze přistupovat pomocí klávesových zkratek **ALT + šipka vlevo**.|
|**Shora dolů**|Změní rozložení v zobrazení grafu na hierarchické znázornění uzlů v horní části. K této možnosti lze přistupovat pomocí klávesových zkratek: **ALT + Šipka dolů**.|
|**Zdola nahoru**|Změní rozložení v zobrazení grafu na hierarchické znázornění uzlů na úrovni zdola. K této možnosti lze přistupovat pomocí klávesové zkratky **ALT + šipka nahoru**.|

## <a name="panscroll"></a>Posun/posun
 Návrhovou plochu můžete posunout pomocí posuvníků nebo podržením klávesy CTRL při kliknutí myší a přetažením. Když posuňte návrhovou plochu pomocí kliknutí a přetažením, ukazatel se změní na čtyři šipky ukazující na čtyři směry.

## <a name="undoredo"></a>Vrátit zpět/znovu
 V zobrazení grafu jsou povoleny funkce zpět a znovu pro následující akce:

- Přidání jednoho uzlu přetažením.

- Přidání více uzlů z okna výsledků hledání v Průzkumníku schémat nebo zobrazení dotazů.

- Odstranění jednoho nebo více uzlů.

## <a name="zoom"></a>Zoom
 Přiblížení je k dispozici v pravém dolním rohu zobrazení grafu.

 Přiblížení lze ovládat následujícími způsoby:

- Podržením klávesy CTRL a otočením kolečka myši při přesunutí ukazatele myši na plochu zobrazení grafu.

- Pomocí ovládacího prvku posuvník. Posuvník zobrazuje aktuální úroveň přiblížení.

  Posuvník přiblížení je neprůhledný, když ho vyberete, najeďte myší na něj, nebo můžete použít klávesovou zkratku CTRL s kolečkem myši pro přiblížení. ve všech ostatních případech je transparentní.

## <a name="xml-editor-integration"></a>Integrace editoru XML
 Můžete přepínat mezi zobrazením grafu a editorem XML kliknutím na uzel a pomocí místní nabídky Zobrazit kód.

 Pokud provedete změny v sadě schémat v editoru XML, změny se synchronizují v zobrazení grafu. Další informace najdete v tématu [integrace s editorem XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Viz také
 [Návrhová plocha](../xml-tools/xml-schema-designer-workspace.md)
