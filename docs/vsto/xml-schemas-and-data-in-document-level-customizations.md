---
title: Schémata XML a data v přizpůsobeních na úrovni dokumentu
description: Microsoft Excel a Word poskytují možnost mapovat schémata na dokumenty a můžou zjednodušit import a export dat XML v dokumentu a z něj.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio]
- schemas [Office development in Visual Studio]
- XML [Office development in Visual Studio], XML schemas
- XML schemas [Office development in Visual Studio], about XML schemas and data
- Office development in Visual Studio, XML
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57fad7982f762c4837399e12552cd109c9a9086c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527859"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Schémata XML a data v přizpůsobeních na úrovni dokumentu
  **Důležité** informace Informace uvedené v tomto tématu týkající se Microsoft Wordu se poskytují výhradně pro zvýhodnění a použití jednotlivců a organizací, kteří se nacházejí mimo USA a její oblasti nebo kteří používají nebo vyvíjí programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od společnosti Microsoft před lednem 2010, když společnost Microsoft odebrala implementaci konkrétních funkcí souvisejících s vlastním kódem XML z aplikace Microsoft Word. Tyto informace týkající se Microsoft Wordu nemusí číst ani používat jednotlivci nebo organizace v USA nebo na jejích oblastech, kteří používají, nebo vyvíjet programy, na kterých běží, od společnosti Microsoft Word, které byly licencované od Microsoftu po 10. ledna 2010. Tyto produkty se nebudou chovat stejně jako produkty licencované před tímto datem nebo zakoupené a licencované pro použití mimo USA.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Systém Microsoft Office Excel a systém Microsoft Office Word poskytují možnost mapovat schémata do vašich dokumentů. Tato funkce může zjednodušit import a export dat XML v dokumentu a z něj.

 Visual Studio zveřejňuje prvky mapovaného schématu v přizpůsobení na úrovni dokumentu jako ovládací prvky v programovacím modelu. V aplikaci Excel aplikace Visual Studio přidává podporu pro vazbu ovládacích prvků k datům v databázích, webových službách a objektech. Pro aplikace Word a Excel přidává Visual Studio podporu pro podokna akcí, které lze použít s dokumentem mapovaným schématu k vytvoření rozšířeného prostředí koncových uživatelů pro vaše řešení. Další informace najdete v tématu [Přehled podokna akcí](../vsto/actions-pane-overview.md).

> [!NOTE]
> V řešeních aplikace Excel nelze použít schémata XML s více částmi.

## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objekty, které se vytvořily, když jsou schémata připojená k sešitům Excelu
 Když připojíte schéma k sešitu, Visual Studio automaticky vytvoří několik objektů a přidá je do projektu. Tyto objekty by neměly být odstraněny pomocí nástrojů sady Visual Studio, protože jsou spravovány v aplikaci Excel. Pokud je chcete odstranit, odeberte namapované prvky z listu nebo odpojte schéma pomocí nástrojů aplikace Excel.

 Existují dva hlavní objekty:

- Schéma XML (soubor XSD). Pro každé schéma v sešitu Visual Studio přidá schéma do projektu. Zobrazuje se jako položka projektu s rozšířením XSD v **Průzkumník řešení**.

- Typová <xref:System.Data.DataSet> Třída. Tato třída je vytvořena na základě schématu. Tato datová třída je viditelná v **zobrazení tříd**.

## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objekty vytvořené při mapování prvků schématu na listy aplikace Excel
 Pokud namapujete prvek schématu z podokna úloh **zdroj XML** na list, Visual Studio automaticky vytvoří několik objektů a přidá je do projektu:

- Ovládací prvky. Pro každý mapovaný objekt v sešitu <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> je v programovacím modelu vytvořen ovládací prvek (pro opakující se prvky schématu) nebo <xref:Microsoft.Office.Tools.Excel.ListObject> ovládací prvek (pro opakující se prvky schématu). <xref:Microsoft.Office.Tools.Excel.ListObject>Ovládací prvek lze odstranit pouze odstraněním mapování a mapovaných objektů ze sešitu. Další informace o ovládacích prvcích naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

- BindingSource. Když vytvoříte <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> mapováním neopakujícího se elementu schématu na list, vytvoří <xref:System.Windows.Forms.BindingSource> se a <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek je svázán s <xref:System.Windows.Forms.BindingSource> . Musíte vytvořit vazby <xref:System.Windows.Forms.BindingSource> na instanci zdroje dat, která odpovídá schématu namapovanému na dokument, jako je například instance typované <xref:System.Data.DataSet> třídy, která byla vytvořena. Vytvořte vazbu nastavením <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastností a, které jsou zpřístupněny v okně **vlastnosti** .

    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource>Pro objekty není vytvořen <xref:Microsoft.Office.Tools.Excel.ListObject> . Je nutné ručně vytvořit vazby na <xref:Microsoft.Office.Tools.Excel.ListObject> zdroj dat nastavením <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastností a v okně **vlastnosti** .

### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Mapová schémata Office a okno zdroje dat v sadě Visual Studio
 Funkce mapovaného schématu v Office i v okně **zdroje dat** sady Visual Studio vám může pomáhat při sestavování dat v excelovém sešitu pro vytváření sestav nebo úpravy. V obou případech můžete prvky dat přetáhnout do excelového listu. Obě metody vytvářejí ovládací prvky, které jsou data vázaná prostřednictvím <xref:System.Windows.Forms.BindingSource> na zdroj dat, jako je například <xref:System.Data.DataSet> nebo webová služba.

> [!NOTE]
> Při mapování opakujícího se elementu schématu na list vytvoří Visual Studio <xref:Microsoft.Office.Tools.Excel.ListObject> . <xref:Microsoft.Office.Tools.Excel.ListObject>Není automaticky svázán s daty prostřednictvím <xref:System.Windows.Forms.BindingSource> . Je nutné ručně vytvořit vazby na <xref:Microsoft.Office.Tools.Excel.ListObject> zdroj dat nastavením <xref:System.Windows.Forms.BindingSource.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastností a v okně **vlastnosti** .

 V následující tabulce jsou uvedeny některé rozdíly mezi těmito dvěma způsoby.

|Schéma XML|okno Zdroje dat|
|----------------|-------------------------|
|Používá rozhraní Office.|Používá okno **zdroje dat** v aplikaci Visual Studio.|
|Povolí integrované funkce Office pro import a export dat ze souborů XML.|Funkce importu a exportu musíte poskytnout programově.|
|Je nutné napsat kód, který vyplní vygenerované ovládací prvky daty.|Ovládací prvky přidané z okna **zdrojů dat** mají automaticky generovaný kód, který je vyplní spolu s potřebnými připojovacími řetězci při použití databázových serverů.|

## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Chování při připojení schémat k dokumentům aplikace Word
 Datové objekty se nevytvoří při připojení schématu k dokumentu aplikace Word, který se používá v projektu Office na úrovni dokumentu. Nicméně při mapování elementu schématu na dokument jsou vytvořeny ovládací prvky. Typ ovládacího prvku závisí na typu prvku, který namapujete; opakující se prvky generují <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládací prvky a prvky, které nejsou opakující se, generují <xref:Microsoft.Office.Tools.Word.XMLNode> ovládací prvky. Další informace naleznete v tématu [ovládací prvek XmlNode](../vsto/xmlnodes-control.md) a [ovládací prvek XmlNode](../vsto/xmlnode-control.md).

## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Nasazení řešení, která zahrnují schémata XML
 Měli byste vytvořit instalační program pro nasazení řešení, které používá schéma XML, které je namapováno na dokument. Instalační program by měl zaregistrovat schéma v knihovně schémat v počítači uživatele. Pokud schéma nezaregistrujete, řešení bude i nadále fungovat, protože aplikace Word vygeneruje dočasné schéma na základě prvků, které jsou v dokumentu, když ho uživatel otevře. Uživatel však nebude moci provádět ověřování proti nebo uložit schéma, které bylo použito k vytvoření projektu. Další informace o instalačních programů najdete v tématu [nasazení aplikací, služeb a součástí](../deployment/deploying-applications-services-and-components.md).

 Do projektu můžete také přidat kód, chcete-li ověřit, zda je schéma v knihovně a zaregistrováno. Pokud tomu tak není, můžete uživatele varovat.

 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]

## <a name="see-also"></a>Viz také

- [Postupy: mapování schémat na dokumenty aplikace Word v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Postupy: mapování schémat na listy v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
