---
title: 'Návod: Svázání ovládacích prvků obsahu s vlastními částmi XML'
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a80488408f680530ed3c9b4094b2997e97484ce3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544440"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Návod: Svázání ovládacích prvků obsahu s vlastními částmi XML
  Tento návod ukazuje, jak navazovat ovládací prvky obsahu v přizpůsobení na úrovni dokumentu pro Word na data XML, která jsou uložená v dokumentu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word umožňuje ukládat data XML s názvem *Custom XML Parts*v dokumentu. Zobrazení těchto dat můžete řídit vazbou ovládacích prvků obsahu na prvky ve vlastní části XML. Vzorový dokument v tomto návodu zobrazuje informace o zaměstnancích, které jsou uložené ve vlastní části XML. Když otevřete dokument, ovládací prvky obsahu zobrazí hodnoty prvků XML. Všechny změny, které provedete v textu v ovládacích prvcích obsahu, budou uloženy ve vlastní části XML.

 Tento návod znázorňuje následující úlohy:

- Přidávání ovládacích prvků obsahu do dokumentu aplikace Word v projektu na úrovni dokumentu v době návrhu.

- Vytvoření datového souboru XML a schématu XML, které definuje prvky pro svázání s ovládacími prvky obsahu.

- Připojení schématu XML k dokumentu v době návrhu.

- Přidání obsahu souboru XML do vlastní části XML v dokumentu v době běhu.

- Svázat ovládací prvky obsahu s prvky ve vlastní části XML.

- Vytvoří vazbu a <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> na sadu hodnot, které jsou definovány ve schématu XML.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Vytvořit nový projekt wordového dokumentu
 Vytvořte dokument aplikace Word, který budete používat v tomto návodu.

### <a name="to-create-a-new-word-document-project"></a>Vytvoření nového projektu wordového dokumentu

1. Vytvořte projekt wordového dokumentu s názvem **EmployeeControls**. Vytvořte nový dokument pro řešení. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]otevře nový wordový dokument v návrháři a přidá projekt **EmployeeControls** do **Průzkumník řešení**.

## <a name="add-content-controls-to-the-document"></a>Přidat do dokumentu ovládací prvky obsahu
 Vytvoří tabulku, která obsahuje tři různé typy ovládacích prvků obsahu, kde může uživatel zobrazit nebo upravit informace o zaměstnanci.

### <a name="to-add-content-controls-to-the-document"></a>Přidání ovládacích prvků obsahu do dokumentu

1. V dokumentu aplikace Word, který je hostován v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Návrháři, klikněte na pásu karet na kartu **Vložit** .

2. Ve skupině **tabulky** vyberte **tabulka**a vložte tabulku se dvěma sloupci a 3 řádky.

3. Zadejte text do prvního sloupce tak, aby vypadal jako následující sloupec:

   ||
   |-|
   |**Jméno zaměstnance**|
   |**Datum nástupu**|
   |**Nadpis**|

4. Ve druhém sloupci tabulky vyberte první řádek (vedle **pole jméno zaměstnance**).

5. Na pásu karet vyberte kartu **vývojář** .

   > [!NOTE]
   > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. Ve skupině **ovládací prvky** kliknutím na tlačítko **text** ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") přidejte <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> do první buňky.

7. Ve druhém sloupci tabulky vyberte druhý řádek (vedle pole **Datum zařazení**).

8. Ve skupině **ovládací prvky** vyberte tlačítko pro **Výběr data** ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") a přidejte <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> do druhé buňky.

9. Ve druhém sloupci tabulky vyberte třetí řádek (vedle **názvu**).

10. Ve skupině **ovládací prvky** kliknutím na tlačítko **rozevíracího seznamu** ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") přidejte <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> do poslední buňky.

    To je celé uživatelské rozhraní pro tento projekt. Pokud projekt teď spustíte, můžete zadat text do prvního řádku a vybrat datum ve druhém řádku. Dalším krokem je připojení dat, která chcete zobrazit v dokumentu v souboru XML.

## <a name="create-the-xml-data-file"></a>Vytvoření datového souboru XML
 Obvykle budete získávat data XML pro uložení ve vlastní části XML z externího zdroje, jako je například soubor nebo databáze. V tomto návodu vytvoříte soubor XML, který obsahuje údaje o zaměstnancích, označené prvky, které budete navazovat k ovládacím prvkům obsahu v dokumentu. Aby byla data v době běhu k dispozici, vložte soubor XML jako prostředek do sestavení vlastního nastavení.

#### <a name="to-create-the-data-file"></a>Vytvoření datového souboru

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

     Zobrazí se dialogové okno **Přidat novou položku**.

2. V podokně **šablony** vyberte **soubor XML**.

3. Pojmenujte soubor **employees.xml**a pak klikněte na tlačítko **Přidat** .

     **employees.xml** soubor se otevře v editoru kódu.

4. Obsah souboru **employees.xml** nahraďte následujícím textem.

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

5. V **Průzkumník řešení**vyberte soubor **employees.xml** .

6. V okně **vlastnosti** vyberte vlastnost **Akce sestavení** a pak změňte hodnotu na **Integrovaný prostředek**.

     Tento krok vloží soubor XML jako prostředek v sestavení při sestavování projektu. To umožňuje přístup k obsahu souboru XML v době běhu.

## <a name="create-an-xml-schema"></a>Vytvoření schématu XML
 Pokud chcete vytvořit propojení ovládacího prvku obsahu s jediným prvkem ve vlastní části XML, nemusíte používat schéma XML. Chcete-li však vytvořit vázání na <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> sadu hodnot, je nutné vytvořit schéma XML, které ověřuje datový soubor XML, který jste vytvořili dříve. Schéma XML definuje možné hodnoty pro `title` element. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>K tomuto prvku budete přivážet později v tomto návodu.

#### <a name="to-create-an-xml-schema"></a>Vytvoření schématu XML

1. V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.

     Zobrazí se dialogové okno **Přidat novou položku**.

2. V podokně **šablony** vyberte **schéma XML**.

3. Pojmenujte schéma **Employees. xsd** a klikněte na tlačítko **Přidat** .

     Otevře se Návrhář schémat.

4. V **Průzkumník řešení**otevřete místní nabídku pro **Employees. xsd**a pak zvolte **Zobrazit kód**.

5. Obsah souboru **Employees. xsd** nahraďte následujícím schématem.

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

6. V nabídce **soubor** klikněte na **Uložit vše** a uložte změny do **employees.xml** a **Employees. xsd** Files.

## <a name="attach-the-xml-schema-to-the-document"></a>Připojit schéma XML k dokumentu
 Musíte připojit schéma XML k dokumentu, aby bylo možné vytvořit vazby <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> k platným hodnotám `title` elementu.

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>Připojení schématu XML k dokumentu ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. Aktivujte **EmployeeControls.docx** v návrháři.

2. Na pásu karet klikněte na kartu **vývojář** a pak klikněte na tlačítko **Doplňky** .

3. V dialogovém okně **šablony a doplňky** klikněte na kartu **schéma XML** a pak klikněte na tlačítko **Přidat schéma** .

4. Přejděte do schématu **Employees. xsd** , které jste vytvořili dříve, který je umístěn v adresáři projektu, a poté klikněte na tlačítko **otevřít** .

5. V dialogovém okně **Nastavení schématu** klikněte na tlačítko **OK** .

6. Kliknutím na tlačítko **OK** zavřete dialogové okno **šablony a doplňky** .

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>Připojení schématu XML k dokumentu (Word 2010)

1. Aktivujte **EmployeeControls.docx** v návrháři.

2. Na pásu karet vyberte kartu **vývojář** .

3. Ve skupině **XML** klikněte na tlačítko **schéma** .

4. V dialogovém okně **šablony a doplňky** klikněte na kartu **schéma XML** a pak klikněte na tlačítko **Přidat schéma** .

5. Přejděte do schématu **Employees. xsd** , které jste vytvořili dříve, který je umístěn v adresáři projektu, a klikněte na tlačítko **otevřít** .

6. V dialogovém okně **Nastavení schématu** klikněte na tlačítko **OK** .

7. Kliknutím na tlačítko **OK** zavřete dialogové okno **šablony a doplňky** .

     Otevře se podokno úloh **Struktura XML** .

8. Zavřete podokno úloh **Struktura XML** .

## <a name="add-a-custom-xml-part-to-the-document"></a>Přidat vlastní část XML do dokumentu
 Předtím, než můžete navazovat ovládací prvky obsahu na prvky v souboru XML, je nutné přidat obsah souboru XML do nové vlastní části XML v dokumentu.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Přidání vlastní části XML do dokumentu

1. V **Průzkumník řešení**otevřete místní nabídku pro **ThisDocument.cs** nebo **ThisDocument. vb**a pak zvolte **Zobrazit kód**.

2. Do třídy přidejte následující deklarace `ThisDocument` . Tento kód deklaruje několik objektů, které použijete k přidání vlastní části XML do dokumentu.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#1)]

3. Do třídy přidejte následující metodu `ThisDocument` . Tato metoda načte obsah datového souboru XML, který je vložen jako prostředek v sestavení, a vrátí obsah jako řetězec XML.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#3)]

4. Do třídy přidejte následující metodu `ThisDocument` . `AddCustomXmlPart`Metoda vytvoří novou vlastní část XML, která obsahuje řetězec XML, který je předán metodě.

     Aby bylo zajištěno, že je vlastní část XML vytvořena pouze jednou, metoda vytvoří vlastní část XML pouze v případě, že v dokumentu již neexistuje vlastní část XML se shodným identifikátorem GUID. Při prvním volání této metody uloží hodnotu <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> vlastnosti do `employeeXMLPartID` řetězce. Hodnota `employeeXMLPartID` řetězce je uchována v dokumentu, protože byla deklarována pomocí <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributu.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#4)]

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Svázání ovládacích prvků obsahu s prvky ve vlastní části XML
 Navažte každý ovládací prvek obsahu na prvek ve vlastní části XML pomocí vlastnosti **XmlMapping** každého ovládacího prvku obsahu.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>Svázání ovládacích prvků obsahu s prvky ve vlastní části XML

1. Do třídy přidejte následující metodu `ThisDocument` . Tato metoda váže každý ovládací prvek obsahu k elementu ve vlastní části XML a nastaví formát zobrazení data <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> .

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#5)]

## <a name="run-your-code-when-the-document-is-opened"></a>Spustit kód při otevření dokumentu
 Vytvořte vlastní část XML a navažte vlastní ovládací prvky na data při otevření dokumentu.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Spuštění kódu při otevření dokumentu

1. Do metody třídy přidejte následující kód `ThisDocument_Startup` `ThisDocument` . Tento kód Získá řetězec XML ze souboru **employees.xml** , přidá řetězec XML do nové vlastní části XML v dokumentu a váže ovládací prvky obsahu k prvkům ve vlastní části XML.

     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb#2)]

## <a name="test-the-project"></a>Testování projektu
 Když otevřete dokument, ovládací prvky obsahu zobrazí data z prvků ve vlastní části XML. Kliknutím na můžete <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> vybrat jednu ze tří platných hodnot `title` prvku, které jsou definovány v souboru **Employees. xsd** . Pokud data upravíte v některém z ovládacích prvků obsahu, budou nové hodnoty uloženy do vlastní části XML v dokumentu.

### <a name="to-test-the-content-controls"></a>Testování ovládacích prvků obsahu

1. Stisknutím klávesy **F5** spusťte projekt.

2. Ověřte, že tabulka v dokumentu se podobá následující tabulce. Každý z řetězců ve druhém sloupci je získán z prvku v části vlastní XML v dokumentu.

    |Sloupec|Hodnota|
    |-|-|
    |**Jméno zaměstnance**|**Karina Leal**|
    |**Datum nástupu**|**1. dubna 1999**|
    |**Nadpis**|**Manager**|

3. Vyberte buňku napravo od buňky **název zaměstnance** a zadejte jiný název.

4. Zvolte buňku napravo od buňky **kalendářního data přijetí** a vyberte jiné datum v ovládacím prvku pro výběr data.

5. Zvolte buňku napravo od buňky **nadpisu** a v rozevíracím seznamu vyberte novou položku.

6. Uložte a zavřete dokument.

7. V Průzkumníku souborů otevřete složku *\bin\debug* v umístění projektu.

8. Otevřete místní nabídku pro **EmployeeControls.docx** a pak zvolte možnost **Přejmenovat**.

9. Pojmenujte soubor **EmployeeControls.docx.zip**.

     Dokument **EmployeeControls.docx** je uložen ve formátu Open XML. Přejmenováním tohoto dokumentu s příponou názvu souboru *. zip* můžete prošetřit obsah dokumentu. Další informace o Open XML najdete v technickém článku [představení formátů souborů XML sady Office (2007)](/previous-versions/office/developer/office-2007/aa338205(v=office.12)).

10. Otevřete soubor **EmployeeControls.docx.zip** .

11. Otevřete složku **customXml** .

12. Otevřete místní nabídku pro **item2.xml** a pak zvolte **otevřít**.

     Tento soubor obsahuje vlastní část XML, kterou jste přidali do dokumentu.

13. Ověřte, zda `name` `hireDate` prvky, a `title` obsahují nové hodnoty, které jste zadali do ovládacích prvků obsahu v dokumentu.

14. Zavřete soubor **item2.xml** .

## <a name="next-steps"></a>Další kroky
 Další informace o tom, jak používat ovládací prvky obsahu, najdete v těchto tématech:

- K vytvoření šablony použijte všechny dostupné ovládací prvky obsahu. Další informace najdete v tématu [Návod: Vytvoření šablony s použitím ovládacích prvků obsahu](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

- Upravte data ve vlastních částech XML při zavření dokumentu. Při příštím otevření dokumentu uživatel zobrazí ovládací prvky obsahu, které jsou vázány na prvky XML, a zobrazí nová data.

- Pomocí ovládacích prvků obsahu můžete chránit části dokumentu. Další informace najdete v tématu [Postupy: Ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="see-also"></a>Viz také
- [Automatizace Wordu pomocí rozšířených objektů](../vsto/automating-word-by-using-extended-objects.md)
- [Ovládací prvky obsahu](../vsto/content-controls.md)
- [Postupy: Přidání ovládacích prvků obsahu do dokumentů aplikace Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Postupy: Ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
