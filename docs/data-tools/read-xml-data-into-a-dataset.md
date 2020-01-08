---
title: Načtení dat XML do datové sady
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5f89645b9d5ec8ab0f69fad4fea5a399d8e6764d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586325"
---
# <a name="read-xml-data-into-a-dataset"></a>Načtení dat XML do datové sady

ADO.NET poskytuje jednoduché metody pro práci s daty XML. V tomto návodu vytvoříte aplikaci pro Windows, která načte data XML do datové sady. Datová sada se pak zobrazí v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Nakonec se schéma XML na základě obsahu souboru XML zobrazí v textovém poli.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Vytvořte nový projekt **aplikace model Windows Forms** pro buď C# nebo Visual Basic. Pojmenujte projekt **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Vygenerovat soubor XML, který se má číst do datové sady

Vzhledem k tomu, že se tento návod zaměřuje na čtení dat XML do datové sady, je k dispozici obsah souboru XML.

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

2. Vyberte **soubor XML**, pojmenujte soubor **Authors. XML**a potom vyberte **Přidat**.

   Soubor XML se načte do návrháře a je připravený k úpravám.

3. Do editoru pod deklarací XML vložte následující data XML:

   ```xml
   <Authors_Table>
     <authors>
       <au_id>172-32-1176</au_id>
       <au_lname>White</au_lname>
       <au_fname>Johnson</au_fname>
       <phone>408 496-7223</phone>
       <address>10932 Bigge Rd.</address>
       <city>Menlo Park</city>
       <state>CA</state>
       <zip>94025</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>213-46-8915</au_id>
       <au_lname>Green</au_lname>
       <au_fname>Margie</au_fname>
       <phone>415 986-7020</phone>
       <address>309 63rd St. #411</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94618</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>238-95-7766</au_id>
       <au_lname>Carson</au_lname>
       <au_fname>Cheryl</au_fname>
       <phone>415 548-7723</phone>
       <address>589 Darwin Ln.</address>
       <city>Berkeley</city>
       <state>CA</state>
       <zip>94705</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>267-41-2394</au_id>
       <au_lname>Hunter</au_lname>
       <au_fname>Anne</au_fname>
       <phone>408 286-2428</phone>
       <address>22 Cleveland Av. #14</address>
       <city>San Jose</city>
       <state>CA</state>
       <zip>95128</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>274-80-9391</au_id>
       <au_lname>Straight</au_lname>
       <au_fname>Dean</au_fname>
       <phone>415 834-2919</phone>
       <address>5420 College Av.</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94609</zip>
       <contract>true</contract>
     </authors>
   </Authors_Table>
   ```

4. V nabídce **soubor** vyberte **Uložit Authors. XML**.

## <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní

Uživatelské rozhraní pro tuto aplikaci se skládá z těchto možností:

- <xref:System.Windows.Forms.DataGridView> ovládací prvek, který zobrazí obsah souboru XML jako data.

- <xref:System.Windows.Forms.TextBox> ovládací prvek, který zobrazuje schéma XML pro soubor XML.

- Dva <xref:System.Windows.Forms.Button> ovládací prvky.

  - Jedno tlačítko přečte soubor XML do datové sady a zobrazí ho v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.

  - Druhé tlačítko extrahuje schéma z datové sady a prostřednictvím <xref:System.IO.StringWriter> jej zobrazí v ovládacím prvku <xref:System.Windows.Forms.TextBox>.

### <a name="to-add-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

1. Otevřete `Form1` v návrhovém zobrazení.

2. Z **panelu nástrojů**přetáhněte následující ovládací prvky do formuláře:

    - Jeden ovládací prvek <xref:System.Windows.Forms.DataGridView>

    - Jeden ovládací prvek <xref:System.Windows.Forms.TextBox>

    - Dva <xref:System.Windows.Forms.Button> ovládací prvky

3. Nastavte následující vlastnosti:

    |Control|Vlastnost|Nastavení|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Posuvníky**|**Svislé**|
    |`Button1`|**Jméno**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Jméno**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Vytvoření datové sady, která přijímá data XML

V tomto kroku vytvoříte novou datovou sadu s názvem `authors`. Další informace o datových sadách naleznete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. V **Průzkumník řešení**vyberte zdrojový soubor pro **Form1**a pak na panelu nástrojů **Průzkumník řešení** vyberte tlačítko **Návrhář zobrazení** .

2. Na [kartě sada nástrojů data](../ide/reference/toolbox-data-tab.md)přetáhněte **datovou sadu** na **Form1**.

3. V dialogovém okně **Přidat datovou sadu** vyberte **netypové datové sady**a pak vyberte **OK**.

     **DataSet1.** se přidá do zásobníku komponent.

4. V okně **vlastnosti** nastavte vlastnosti **název** a <xref:System.Data.DataSet.DataSetName%2A> pro`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Vytvoření obslužné rutiny události pro čtení souboru XML do datové sady

Tlačítko **číst XML** přečte soubor XML do datové sady. Poté nastaví vlastnosti ovládacího prvku <xref:System.Windows.Forms.DataGridView>, který jej sváže s datovou sadou.

1. V **Průzkumník řešení**vyberte **Form1**a pak na panelu nástrojů **Průzkumník řešení** vyberte tlačítko **Návrhář zobrazení** .

2. Vyberte tlačítko **číst XML** .

     **Editor kódu** se otevře v obslužné rutině události `ReadXmlButton_Click`.

3. Do obslužné rutiny události `ReadXmlButton_Click` zadejte následující kód:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. V kódu obslužné rutiny události `ReadXMLButton_Click` změňte položku `filepath =` na správnou cestu.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Vytvoření obslužné rutiny události pro zobrazení schématu v textovém poli

Tlačítko **Zobrazit schéma** vytvoří objekt <xref:System.IO.StringWriter>, který je vyplněn schématem a je zobrazen v ovládacím prvku <xref:System.Windows.Forms.TextBox>.

1. V **Průzkumník řešení**vyberte **Form1**a pak klikněte na tlačítko **Návrhář zobrazení** .

2. Vyberte tlačítko **Zobrazit schéma** .

     **Editor kódu** se otevře v obslužné rutině události `ShowSchemaButton_Click`.

3. Vložte následující kód do obslužné rutiny události `ShowSchemaButton_Click`.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Testování formuláře

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.

1. Pro spuštění aplikace vyberte **F5** .

2. Vyberte tlačítko **číst XML** .

     Ovládací prvek DataGridView zobrazuje obsah souboru XML.

3. Vyberte tlačítko **Zobrazit schéma** .

     Textové pole zobrazuje schéma XML pro soubor XML.

## <a name="next-steps"></a>Další kroky

Tento návod vás seznámí se základy čtení souboru XML do datové sady a vytváření schématu založeného na obsahu souboru XML. Tady je několik úloh, které můžete udělat dál:

- Upravte data v datové sadě a zapište je zpět jako XML. Další informace najdete v tématu <xref:System.Data.DataSet.WriteXml%2A>.

- Upravte data v datové sadě a zapište je do databáze.

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Nástroje XML v aplikaci Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
