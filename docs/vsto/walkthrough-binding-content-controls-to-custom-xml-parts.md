---
title: 'Návod: Vazba ovládacích prvků obsahu s vlastní části XML'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1bc8aee0a1294aeda4c57a3416de4a0cc98129f3
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673036"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Návod: Vazba ovládacích prvků obsahu s vlastní části XML
  Tento návod ukazuje, jak svázat ovládací prvky obsahu v přizpůsobení na úrovni dokumentu pro Word XML data, která je uložena v dokumentu.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word umožňuje ukládat data XML s názvem *vlastní části XML*, v dokumentu. Zobrazení těchto dat můžete řídit pomocí vytvoření vazby ovládacích prvků obsahu k elementům ve vlastní část XML. Ukázkový dokument v tomto názorném postupu se zobrazí informace o zaměstnancích, která je uložena v vlastní část XML. Když otevřete dokument, zobrazí ovládací prvky obsahu hodnoty elementů XML. Všechny změny provedené v textu v ovládacích prvcích obsahu jsou ukládány do vlastní část XML.  
  
 Tento návod znázorňuje následující úlohy:  
  
- Přidání ovládacích prvků obsahu do dokumentu aplikace Word v projektu úrovni dokumentu v době návrhu.  
  
- Vytvoření datového souboru XML a schématu XML, který definuje prvky pro vytvoření vazby ovládacích prvků obsahu.  
  
- V době návrhu se připojuje k dokumentu schématu XML.  
  
- Přidání obsahu souboru XML na vlastní část XML v dokumentu za běhu.  
  
- Vytvoření vazby ovládacích prvků obsahu na prvky ve vlastní část XML.  
  
- Vytvoření vazby <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> sadu hodnot, které jsou definovány ve schématu XML.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Aplikace Microsoft Word.  
  
## <a name="create-a-new-word-document-project"></a>Vytvoření nového projektu dokumentu aplikace Word  
 Vytvořte dokument aplikace Word, který budete používat v tomto návodu.  
  
### <a name="to-create-a-new-word-document-project"></a>K vytvoření nového projektu dokumentu aplikace Word  
  
1.  Vytvoření projektu dokumentu aplikace Word s názvem **EmployeeControls**. Vytvoření nového dokumentu pro řešení. Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře se nový dokument aplikace Word v návrháři a přidá **EmployeeControls** projektu **Průzkumníku řešení**.  
  
## <a name="add-content-controls-to-the-document"></a>Přidání ovládacích prvků obsahu do dokumentu  
 Vytvořte tabulku, která obsahuje tři různé typy ovládacích prvků obsahu ve kterém může uživatel zobrazit nebo upravit informace o zaměstnance.  
  
### <a name="to-add-content-controls-to-the-document"></a>Chcete-li přidat ovládací prvky obsahu dokumentu  
  
1. V dokumentu, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer na pásu karet, zvolte **vložit** kartu.  
  
2. V **tabulky** skupině, zvolte **tabulky**a vložit tabulku se sloupci 2 a 3 řádky.  
  
3. Zadejte text v prvním sloupci tak, aby se podobá následující sloupce:  
  
   ||  
   |-|  
   |**Jméno zaměstnance**|  
   |**Datum přijetí**|  
   |**Název**|  
  
4. Ve druhém sloupci tabulky, zvolte na prvním řádku (vedle **jméno zaměstnance**).  
  
5. Na pásu karet, zvolte **Developer** kartu.  
  
   > [!NOTE]  
   >  Pokud **Developer** karta není zobrazena, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6. V **ovládací prvky** skupině, zvolte **Text** tlačítko ![plaintextcontentcontrol –](../vsto/media/plaintextcontrol.gif "plaintextcontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>do první buňky.  
  
7. V druhém sloupci v tabulce, vyberte druhý řádek (vedle **datum přijetí**).  
  
8. V **ovládací prvky** skupině, zvolte **výběr data** tlačítko ![datepickercontentcontrol –](../vsto/media/datepicker.gif "datepickercontentcontrol –") přidáte <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do druhé buňce.  
  
9. Ve druhém sloupci tabulky, zvolte třetí řádek (vedle **Title**).  
  
10. V **ovládací prvky** skupině, zvolte **rozevíracího seznamu** tlačítko ![dropdownlistcontentcontrol –](../vsto/media/dropdownlist.gif "dropdownlistcontentcontrol –") přidat <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do poslední buňky.  
  
    To je celé uživatelské rozhraní pro tento projekt. Pokud spustíte projekt teď můžete do prvního řádku zadejte text a vyberte datum ve druhém řádku. Dalším krokem je připojení dat, který chcete zobrazit v dokumentu v souboru XML.  
  
## <a name="create-the-xml-data-file"></a>Vytvoření datového souboru XML  
 Obvykle se získat data XML pro ukládání ve vlastní část XML z externího zdroje, jako je například soubor nebo databáze. V tomto návodu vytvoříte soubor XML, který obsahuje data zaměstnanců, označen prvky, které vytvoří vazbu na ovládací prvky obsahu v dokumentu. Zpřístupnit data za běhu, vložen jako prostředek v sestavení přizpůsobení souboru XML.  
  
#### <a name="to-create-the-data-file"></a>Vytvoření datového souboru  
  
1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
     **Přidat novou položku** zobrazí se dialogové okno.  
  
2.  V **šablony** vyberte **soubor XML**.  
  
3.  Název souboru **employees.xml**a klikněte na tlačítko **přidat** tlačítko.  
  
     **Employees.xml** soubor se otevře v editoru kódu.  
  
4.  Nahraďte obsah **employees.xml** soubor s následujícím textem.  
  
    ```xml 
    <?xml version="1.0" encoding="utf-8" ?>  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  V **Průzkumníka řešení**, zvolte **employees.xml** souboru.  
  
6.  V **vlastnosti** okna, vyberte **akce sestavení** vlastnost a potom změňte hodnotu na **integrovaný prostředek**.  
  
     Tento krok vloží soubor XML jako prostředek v sestavení při vytváření projektu. Umožňuje získat přístup k obsahu souboru XML v době běhu.  
  
## <a name="create-an-xml-schema"></a>Vytvoření schématu XML  
 Pokud chcete vytvořit vazbu ovládacího prvku obsahu na jednom elementu vlastní část XML, není nutné používat schématu XML. Však vazba <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do sady hodnot, je nutné vytvořit schéma XML, která ověřuje datový soubor XML, který jste vytvořili dříve. Možné hodnoty pro definuje schéma XML `title` elementu. Vytvoří vazbu <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> na tento element později v tomto názorném postupu.  
  
#### <a name="to-create-an-xml-schema"></a>Vytvoření schématu XML  
  
1.  Na **projektu** nabídce zvolte **přidat novou položku**.  
  
     **Přidat novou položku** zobrazí se dialogové okno.  
  
2.  V **šablony** vyberte **schématu XML**.  
  
3.  Název schématu **employees.xsd** a zvolte **přidat** tlačítko.  
  
     Otevře se Návrhář schémat.  
  
4.  V **Průzkumníka řešení**, otevřete místní nabídku pro **employees.xsd**a klikněte na tlačítko **zobrazit kód**.  
  
5.  Nahraďte obsah **employees.xsd** soubor s následujícím schématu.  
  
    ```xml
    <?xml version="1.0" encoding="utf-8" ?>  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  Na **souboru** nabídky, klikněte na tlačítko **Uložit vše** uložte provedené změny do **employees.xml** a **employees.xsd** soubory.  
  
## <a name="attach-the-xml-schema-to-the-document"></a>Připojit schéma XML v dokumentu  
 Schéma XML musí připojit k dokumentu, vytvoření vazby <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> na platné hodnoty `title` elementu.  
  
### <a name="to-attach-the-xml-schema-to-the-document--includeword15shortvstoincludesword-15-short-mdmd"></a>Připojit k tomuto dokumentu schématu XML ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)])  
  
1.  Aktivovat **EmployeeControls.docx** v návrháři.  
  
2.  Na pásu karet, zvolte **Developer** kartu a klikněte na tlačítko **Add-Ins** tlačítko.  
  
3.  V **šablon a doplňků** dialogového okna zvolte **schématu XML** kartu a klikněte na tlačítko **přidat schéma** tlačítko.  
  
4.  Přejděte **employees.xsd** schématu jste vytvořili dříve, který je umístěn v adresáři projektu a klikněte na tlačítko **otevřít** tlačítko.  
  
5.  Zvolte **OK** tlačítko **schéma – nastavení** dialogové okno.  
  
6.  Zvolte **OK** tlačítko pro uzavření **šablon a doplňků** dialogové okno.  
  
### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Připojit schéma XML v dokumentu (Wordu 2010)  
  
1.  Aktivovat **EmployeeControls.docx** v návrháři.  
  
2.  Na pásu karet, zvolte **Developer** kartu.  
  
3.  V **XML** skupině, zvolte **schématu** tlačítko.  
  
4.  V **šablon a doplňků** dialogového okna zvolte **schématu XML** kartu a klikněte na tlačítko **přidat schéma** tlačítko.  
  
5.  Přejděte **employees.xsd** schématu, který jste vytvořili dříve, který je umístěn v adresáři projektu a zvolte **otevřít** tlačítko.  
  
6.  Zvolte **OK** tlačítko **schéma – nastavení** dialogové okno.  
  
7.  Zvolte **OK** tlačítko pro uzavření **šablon a doplňků** dialogové okno.  
  
     **Struktura XML** otevře se podokno úloh.  
  
8.  Zavřít **struktura XML** podokna úloh.  
  
## <a name="add-a-custom-xml-part-to-the-document"></a>Přidat vlastní část XML v dokumentu  
 Než ovládacích prvků obsahu můžete vázat na prvky v souboru XML, musíte přidat obsah souboru XML do nové vlastní část XML v dokumentu.  
  
### <a name="to-add-a-custom-xml-part-to-the-document"></a>Chcete-li přidat vlastní část XML v dokumentu  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro **ThisDocument.cs** nebo **ThisDocument.vb**a klikněte na tlačítko **zobrazit kód**.  
  
2.  Přidejte následující deklarace do `ThisDocument` třídy. Tento kód deklaruje několik objektů, které použijete k přidání vlastních částí XML v dokumentu.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]  
  
3.  Přidejte následující metodu do `ThisDocument` třídy. Tato metoda načte obsah datového souboru XML, který je vložený jako prostředek v sestavení a vrátí obsah jako řetězec XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]  
  
4.  Přidejte následující metodu do `ThisDocument` třídy. `AddCustomXmlPart` Metoda vytvoří novou vlastní část XML, který obsahuje řetězec XML, který je předán metodě.  
  
     Ujistěte se, že vlastní část XML je vytvořen pouze jednou, kterou metoda vytvoří vlastní XML část jenom v případě, že vlastní část XML s odpovídajícím identifikátorem GUID již neexistuje v dokumentu. Tato metoda je volána, poprvé ji uloží hodnotu <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> vlastnost `employeeXMLPartID` řetězec. Hodnota `employeeXMLPartID` řetězce je trvalá v dokumentu, protože byla deklarovaná příkazem using <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atribut.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]  
  
## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Vytvoření vazby ovládacích prvků obsahu k elementům ve vlastní část XML  
 Vytvoření vazby každý ovládací prvek na prvek v vlastní část XML pomocí **XMLMapping** vlastností každého ovládacího prvku obsahu.  
  
### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>K vytvoření vazby ovládacích prvků obsahu k elementům ve vlastní část XML  
  
1.  Přidejte následující metodu do `ThisDocument` třídy. Tato metoda váže každý ovládací prvek k prvku v vlastní část XML a nastaví formát zobrazení data <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]  
  
## <a name="run-your-code-when-the-document-is-opened"></a>Svůj kód spustit, když je dokument otevřít  
 Vytvořit vlastní část XML a vytvořit vazbu na vlastní ovládací prvky na data při otevření dokumentu.  
  
### <a name="to-run-your-code-when-the-document-is-opened"></a>Ke spuštění kódu při otevření dokumentu  
  
1.  Přidejte následující kód, který `ThisDocument_Startup` metodu `ThisDocument` třídy. Tento kód získá řetězec XML z **employees.xml** soubor, přidá řetězec XML do nové vlastní část XML v dokumentu a naváže ovládací prvky obsahu na prvky ve vlastní část XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]  
  
## <a name="test-the-project"></a>Testování projektu  
 Když otevřete dokument, ovládací prvky obsahu zobrazení dat z prvků v vlastní část XML. Můžete kliknout <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> vyberte jednu ze tří platné hodnoty pro `title` element, který jsou definovány v **employees.xsd** souboru. Při úpravě dat v některém z ovládacích prvků obsahu, nové hodnoty jsou ukládány do vlastní část XML v dokumentu.  
  
### <a name="to-test-the-content-controls"></a>Pro testování ovládacích prvků obsahu  
  
1.  Stisknutím klávesy **F5** spusťte projekt.  
  
2.  Ověřte, že v tabulce v dokumentu, vypadá podobně jako v následující tabulce. Každý z řetězců v druhém sloupci je získat z prvku v vlastní část XML v dokumentu.  
  
    |||  
    |-|-|  
    |**Jméno zaměstnance**|**Karina Leal**|  
    |**Datum přijetí**|**1. dubna 1999**|  
    |**Název**|**Správce**|  
  
3.  Vyberte buňku napravo od **jméno zaměstnance** buňky a zadejte jiný název.  
  
4.  Vyberte buňku napravo od **datum přijetí** buňku a vyberte jiné datum v prvku Výběr data.  
  
5.  Vyberte buňku napravo od **název** buňku a vyberte novou položku z rozevíracího seznamu.  
  
6.  Uložte a zavřete dokument.  
  
7.  V Průzkumníku souborů otevřete *\bin\Debug* složku v umístění projektu.  
  
8.  Otevřete místní nabídku pro **EmployeeControls.docx** a klikněte na tlačítko **přejmenovat**.  
  
9. Název souboru **EmployeeControls.docx.zip**.  
  
     **EmployeeControls.docx** je dokument uložen ve formátu Open XML. Přejmenováním tohoto dokumentu se *ZIP* příponu názvu souboru můžete prozkoumat obsah dokumentu. Další informace o Open XML naleznete v tématu technického článku [Představujeme Open XML Office (2007) formáty souborů](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).  
  
10. Otevřít **EmployeeControls.docx.zip** souboru.  
  
11. Otevřít **customXml** složky.  
  
12. Otevřete místní nabídku pro **item2.xml** a klikněte na tlačítko **otevřít**.  
  
     Tento soubor obsahuje vlastní část XML, který jste přidali do dokumentu.  
  
13. Ověřte, že `name`, `hireDate`, a `title` elementy obsahovat nové hodnoty, které jste zadali do ovládacích prvků obsahu v dokumentu.  
  
14. Zavřít **item2.xml** souboru.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak používat ovládací prvky obsahu naleznete v těchto tématech:  
  
-   Použijte všechny dostupné ovládací prvky obsahu k vytvoření šablony. Další informace najdete v tématu [návod: vytvoření šablony s použitím ovládacích prvků obsahu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Upravte data ve vlastních částí XML při zavření dokumentu. Při příštím otevření dokumentu a ovládací prvky obsahu, které jsou vázány na prvky XML se zobrazí nová data.  
  
-   Použití ovládacích prvků obsahu s ochrana částí dokumentů. Další informace najdete v tématu [postupy: ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="see-also"></a>Viz také:  
 [Automatizace aplikace Word s použitím rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)   
 [Ovládací prvky obsahu](../vsto/content-controls.md)   
 [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Postupy: ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  