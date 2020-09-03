---
title: Načtení dat XML do datové sady
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 6cceca336403bdd8907cf0e28e36387eb25a2402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281783"
---
# <a name="read-xml-data-into-a-dataset"></a>Načtení dat XML do datové sady

ADO.NET poskytuje jednoduché metody pro práci s daty XML. V tomto návodu vytvoříte aplikaci pro Windows, která načte data XML do datové sady. Datová sada se pak zobrazí v <xref:System.Windows.Forms.DataGridView> ovládacím prvku. Nakonec se schéma XML na základě obsahu souboru XML zobrazí v textovém poli.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

Vytvořte nový projekt **aplikace model Windows Forms** pro C# nebo Visual Basic. Pojmenujte projekt **ReadingXML**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Vygenerovat soubor XML, který se má číst do datové sady

Vzhledem k tomu, že se tento návod zaměřuje na čtení dat XML do datové sady, je k dispozici obsah souboru XML.

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

2. Vyberte **soubor XML**, název souboru **authors.xml**a pak vyberte **Přidat**.

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

4. V nabídce **soubor** vyberte **Uložit authors.xml**.

## <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní

Uživatelské rozhraní pro tuto aplikaci se skládá z těchto možností:

- <xref:System.Windows.Forms.DataGridView>Ovládací prvek, který zobrazí obsah souboru XML jako data.

- <xref:System.Windows.Forms.TextBox>Ovládací prvek, který zobrazuje schéma XML pro soubor XML.

- Dva <xref:System.Windows.Forms.Button> ovládací prvky.

  - Jedno tlačítko přečte soubor XML do datové sady a zobrazí ho v <xref:System.Windows.Forms.DataGridView> ovládacím prvku.

  - Druhé tlačítko extrahuje schéma z datové sady a prostřednictvím <xref:System.IO.StringWriter> <xref:System.Windows.Forms.TextBox> ovládacího prvku ho zobrazí.

### <a name="to-add-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

1. Otevřete `Form1` v návrhovém zobrazení.

2. Z **panelu nástrojů**přetáhněte následující ovládací prvky do formuláře:

    - Jeden <xref:System.Windows.Forms.DataGridView> ovládací prvek

    - Jeden <xref:System.Windows.Forms.TextBox> ovládací prvek

    - Dva <xref:System.Windows.Forms.Button> ovládací prvky

3. Nastavte následující vlastnosti:

    |Řízení|Vlastnost|Nastavení|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Posuvníky**|**Svisle**|
    |`Button1`|**Name**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Name**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Vytvoření datové sady, která přijímá data XML

V tomto kroku vytvoříte novou datovou sadu s názvem `authors` . Další informace o datových sadách naleznete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1. V **Průzkumník řešení**vyberte zdrojový soubor pro **Form1**a pak na panelu nástrojů **Průzkumník řešení** vyberte tlačítko **Návrhář zobrazení** .

2. Na [kartě sada nástrojů data](../ide/reference/toolbox-data-tab.md)přetáhněte **datovou sadu** na **Form1**.

3. V dialogovém okně **Přidat datovou sadu** vyberte **netypové datové sady**a pak vyberte **OK**.

     **DataSet1.** se přidá do zásobníku komponent.

4. V okně **vlastnosti** nastavte **název** a <xref:System.Data.DataSet.DataSetName%2A> vlastnosti pro `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Vytvoření obslužné rutiny události pro čtení souboru XML do datové sady

Tlačítko **číst XML** přečte soubor XML do datové sady. Poté nastaví vlastnosti <xref:System.Windows.Forms.DataGridView> ovládacího prvku, který jej sváže s datovou sadou.

1. V **Průzkumník řešení**vyberte **Form1**a pak na panelu nástrojů **Průzkumník řešení** vyberte tlačítko **Návrhář zobrazení** .

2. Vyberte tlačítko **číst XML** .

     **Editor kódu** se otevře v `ReadXmlButton_Click` obslužné rutině události.

3. Do `ReadXmlButton_Click` obslužné rutiny události zadejte následující kód:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. V `ReadXMLButton_Click` kódu obslužné rutiny události změňte `filepath =` položku na správnou cestu.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Vytvoření obslužné rutiny události pro zobrazení schématu v textovém poli

Tlačítko **Zobrazit schéma** vytvoří <xref:System.IO.StringWriter> objekt, který je vyplněn schématem a je zobrazen v <xref:System.Windows.Forms.TextBox> ovládacím prvku.

1. V **Průzkumník řešení**vyberte **Form1**a pak klikněte na tlačítko **Návrhář zobrazení** .

2. Vyberte tlačítko **Zobrazit schéma** .

     **Editor kódu** se otevře v `ShowSchemaButton_Click` obslužné rutině události.

3. Vložte následující kód do `ShowSchemaButton_Click` obslužné rutiny události.

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

- Upravte data v datové sadě a zapište je zpět jako XML. Další informace naleznete v tématu <xref:System.Data.DataSet.WriteXml%2A>.

- Upravte data v datové sadě a zapište je do databáze.

## <a name="see-also"></a>Viz také

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Nástroje XML v sadě Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
