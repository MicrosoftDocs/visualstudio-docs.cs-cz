---
title: Schémata XML a data v přizpůsobeních na úrovni dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e62a8a7bef72ce34c46621b63188f9d71512be20
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675998"
---
# <a name="xml-schemas-and-data-in-document-level-customizations"></a>Schémata XML a data v přizpůsobeních na úrovni dokumentu
  **Důležité** informace uvedené v tomto tématu týkající se Microsoft Word je zobrazené výhradně pro výhod a užívání o jednotlivci i organizacemi, kteří se nacházejí mimo Spojené státy a jeho území nebo kteří používají nebo vývoj programy, které běží na produkty Microsoft Word, které byly licencovaných společností Microsoft před 2010 dne, kdy Microsoft odebrána implementace konkrétní funkce související s vlastní XML z aplikace Microsoft Word. Tyto informace týkající se Microsoft Word nemusí být přečteny nebo používány jednotlivcům i organizacím v USA nebo v jeho území, které používáte, nebo vývoji programů, které běží na produkty Microsoft Word, které byly licencovaných společností Microsoft po 10. ledna 2010 ; tyto produkty se chovají stejně jako produkty licenci před tímto datem nebo zakoupených a licencovaná pro použití mimo území Spojených států.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aplikace Microsoft Office Excel a Microsoft Office Word poskytují možnost mapování schémat na dokumenty. Tato funkce může zjednodušit import a export dat XML do a z dokumentu.  
  
 Visual Studio zpřístupňuje namapované elementy schématu v přizpůsobeních na úrovni dokumentu jako ovládací prvky v programovacím modelu. Pro aplikaci Excel Visual Studio přidává podporu pro vytvoření vazby ovládacích prvků na data v databází, webových služeb a objektů. Pro aplikace Word a Excel Visual Studio přidává podporu pro podokna akcí, které je možné použít s dokumentem mapované na schéma k vytvoření koncových uživatelů lepší prostředí pro vaše řešení. Další informace najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  V řešení pro aplikaci Excel nelze použít s více částmi schémat XML.  
  
## <a name="objects-created-when-schemas-are-attached-to-excel-workbooks"></a>Objekty vytvořené při schémata jsou připojena k Excelovým sešitům  
 Když připojit schéma k sešitu sady Visual Studio automaticky vytvoří několik objektů a přidá je do projektu. Tyto objekty nesmí odstranit, pomocí nástrojů sady Visual Studio, protože se spravují v Excelu. Je odstranit, odeberte mapované prvky z listu nebo odpojit schématu s použitím nástroje aplikace Excel.  
  
 Existují dva hlavní objekty:  
  
-   Schématu XML (soubor XSD). Pro každé schéma v sešitu Visual Studio přidá schéma do projektu. Se zobrazuje jako položka projektu s příponou XSD v **Průzkumníka řešení**.  
  
-   Zadaný <xref:System.Data.DataSet> třídy. Tato třída se vytvoří podle schématu. Tato třída dataset je viditelný v **zobrazení tříd**.  
  
## <a name="objects-created-when-schema-elements-are-mapped-to-excel-worksheets"></a>Objekty vytvořené při elementy schématu jsou namapovány na listech aplikace Excel  
 Při mapování element schématu z **XML použitého jako zdroj** podokna úloh do listu, Visual Studio automaticky vytvoří několik objektů a přidá je do projektu:  
  
-   Ovládací prvky. Pro každý mapovaných objektů v sešitu <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládacího prvku (pro elementy schématu bez opakování) nebo <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku (pro opakující se elementy schématu) se vytvoří v programovacím modelu. <xref:Microsoft.Office.Tools.Excel.ListObject> Ovládací prvek lze odstranit pouze tak, že odstraníte mapování a mapovaných objektů ze sešitu. Další informace o ovládacích prvcích najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
-   Objekt BindingSource. Při vytváření <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> mapováním neopakujícími element schématu na listu <xref:System.Windows.Forms.BindingSource> se vytvoří a <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek vázán na <xref:System.Windows.Forms.BindingSource>. Je třeba svázat <xref:System.Windows.Forms.BindingSource> do instance zdroje dat, která odpovídá schématu namapované na dokument, jako je například instance zadaného objektu <xref:System.Data.DataSet> třídu, která byla vytvořena. Vytvoření vazby tak, že nastavíte <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnosti, které jsou přístupné **vlastnosti** okna.  
  
    > [!NOTE]  
    >  <xref:System.Windows.Forms.BindingSource> Není vytvořena pro <xref:Microsoft.Office.Tools.Excel.ListObject> objekty. Musíte ručně vytvořit vazbu <xref:Microsoft.Office.Tools.Excel.ListObject> ke zdroji dat tím, že nastavíte <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnosti v **vlastnosti** okna.  
  
### <a name="office-mapped-schemas-and-the-visual-studio-data-sources-window"></a>Office mapovány schémata a v okně zdroje dat aplikace Visual Studio  
 Funkce schématu pro mapovanou systému Office a sady Visual Studio **zdroje dat** okno vám umožňují prezentovat data na listu aplikace Excel pro vytváření sestav, nebo úpravy. V obou případech můžete přetáhnout datové prvky do Excelového listu. Obě metody vytvořit ovládací prvky, které jsou data svázána prostřednictvím <xref:System.Windows.Forms.BindingSource> ke zdroji dat, jako <xref:System.Data.DataSet> nebo webové službě.  
  
> [!NOTE]  
>  Při namapování opakující se element schématu na listu, vytvoří Visual Studio <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Není automaticky vázán na data prostřednictvím <xref:System.Windows.Forms.BindingSource>. Musíte ručně vytvořit vazbu <xref:Microsoft.Office.Tools.Excel.ListObject> ke zdroji dat tím, že nastavíte <xref:System.Windows.Forms.BindingSource.DataSource%2A> a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnosti v **vlastnosti** okna.  
  
 V následující tabulce jsou uvedeny některé rozdíly mezi dvěma způsoby.  
  
|Schématu XML|okno Zdroje dat|  
|----------------|-------------------------|  
|Používá rozhraní systému Office.|Používá **zdroje dat** okna v sadě Visual Studio.|  
|Umožňuje použít integrované funkce Office pro import a export dat ze souborů XML.|Musí poskytovat import a export funkcí prostřednictvím kódu programu.|  
|Musíte napsat kód tak, aby vyplnil vygenerovaný ovládací prvky s daty.|Ovládací prvky přidané od **zdroje dat** okno mít kód se vygeneroval automaticky tak, aby vyplnil, spolu s nezbytné připojovací řetězce při použití databázových serverů.|  
  
## <a name="behavior-when-schemas-are-attached-to-word-documents"></a>Chování při schémata jsou připojené do dokumentů aplikace Word  
 Datové objekty nejsou vytvořeny při připojit schéma k dokumentu aplikace Word, který se používá v projektu úrovni dokumentu Office. Ale při mapování element schématu dokumentu, vytvoření ovládacích prvků. Typ ovládacího prvku, závisí na jaký typ prvku je namapovat; opakující se generovat prvky <xref:Microsoft.Office.Tools.Word.XMLNodes> a ovládacích prvků s neopakujícími generovat <xref:Microsoft.Office.Tools.Word.XMLNode> ovládacích prvků. Další informace najdete v tématu [XmlNodes – ovládací prvek](../vsto/xmlnodes-control.md) a [XmlNode – ovládací prvek](../vsto/xmlnode-control.md).  
  
## <a name="deployment-of-solutions-that-include-xml-schemas"></a>Nasazení řešení, která zahrnují schémat XML  
 Měli byste vytvořit instalační službu pro nasazení řešení, které používá schématu XML, který je namapovaný na dokument. Instalační program měli zaregistrovat schéma do knihovny schémat na počítači uživatele. Pokud nezaregistrujete schéma, řešení budou i nadále fungovat, protože aplikace Word generuje dočasné schéma založené na prvky, které jsou v dokumentu, když ho uživatel neotevře. Uživatel ale nebude možné provést ověření proti nebo uložení souboru schématu, která byla použita k vytvoření projektu. Další informace o instalačních programů najdete v tématu [nasazení aplikací, služeb a součástí](/visualstudio/deployment/deploying-applications-services-and-components).  
  
 Můžete také přidat kód do vašeho projektu, zkontrolujte, zda je v knihovně schématu a zaregistrován. Pokud není, můžete uživatele upozornit.  
  
 [!code-vb[Trin_VstcoreDataWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataWordVB/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstcoreDataWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataWordCS/ThisDocument.cs#1)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: mapování schémat na dokumenty aplikace Word v sadě Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Postupy: mapování schémat na listy v prostředí Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  
