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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1e43d118a5fcfe00a8eb6eaa7f34a17ff1f6a4be
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389212"
---
# <a name="read-xml-data-into-a-dataset"></a>Načtení dat XML do datové sady

ADO.NET obsahuje jednoduché metody pro práci s daty XML. V tomto návodu vytvoříte aplikaci Windows, který načítá XML data do datové sady. Datová sada se následně zobrazí <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Nakonec schématu XML na základě obsahu souboru XML se zobrazí v textovém poli.

## <a name="create-a-new-project"></a>Vytvoření nového projektu

V tomto kroku vytvoříte projekt jazyka Visual Basic nebo Visual C#.

1. V sadě Visual Studio na **souboru** nabídce vyberte možnost **nový** > **projektu**.

2. Rozbalte buď **Visual C#** nebo **jazyka Visual Basic** v levém podokně vyberte **Windows Desktop**.

3. V prostředním podokně, vyberte **aplikace Windows Forms** typ projektu.

4. Pojmenujte projekt **ReadingXML**a klikněte na tlačítko **OK**.

   **ReadingXML** projekt je vytvořen a přidán do **Průzkumníka řešení**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generovat soubor XML pro čtení do datové sady

Protože tento návod se zaměřuje na čtení dat XML do datové sady, je k dispozici obsah souboru XML.

1. Na **projektu** nabídce vyberte možnost **přidat novou položku**.

2. Vyberte **soubor XML**, pojmenujte soubor **authors.xml**a pak vyberte **přidat**.

   Soubor XML načte do návrháře a je připravený pro úpravy.

3. Vložte následující data XML do editoru níže deklarace XML:

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

4. Na **souboru** nabídce vyberte možnost **uložit authors.xml**.

## <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní

Uživatelské rozhraní pro tuto aplikaci se skládá z následujících akcí:

-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek, který zobrazí obsah souboru XML jako data.

-   A <xref:System.Windows.Forms.TextBox> ovládací prvek, který zobrazí schéma XML pro soubor XML.

-   Dvě <xref:System.Windows.Forms.Button> ovládacích prvků.

    -   Jedno tlačítko přečte soubor XML do datové sady a zobrazí ho v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.

    -   Druhé tlačítko extrahuje schéma z datové sady a prostřednictvím <xref:System.IO.StringWriter> zobrazí ho v <xref:System.Windows.Forms.TextBox> ovládacího prvku.

### <a name="to-add-controls-to-the-form"></a>Chcete-li přidat ovládací prvky do formuláře

1.  Otevřít `Form1` v návrhovém zobrazení.

2.  Z **nástrojů**, přetáhněte následující ovládací prvky na formuláři:

    -   Jeden <xref:System.Windows.Forms.DataGridView> ovládacího prvku

    -   Jeden <xref:System.Windows.Forms.TextBox> ovládacího prvku

    -   Dvě <xref:System.Windows.Forms.Button> ovládacích prvků

3.  Nastavte následující vlastnosti:

    |Ovládací prvek|Vlastnost|Nastavení|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Posuvníky**|**Svisle**|
    |`Button1`|**Jméno**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Jméno**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>Vytvořte datovou sadu, která přijímá XML data

V tomto kroku vytvoříte novou datovou sadu s názvem `authors`. Další informace o datových sadách najdete v tématu [datovou sadu nástrojů v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

1.  V **Průzkumníka řešení**, vyberte zdrojový soubor pro **Form1**a pak vyberte **Návrhář zobrazení** tlačítko **Průzkumníka řešení** panel nástrojů.

2.  Z [panel nástrojů, karta Data](../ide/reference/toolbox-data-tab.md), přetáhněte **datovou sadu** do **Form1**.

3.  V **přidat datovou sadu** dialogu **netypovou datovou sadu**a pak vyberte **OK**.

     **DataSet1** se přidá do panelu komponent.

4.  V **vlastnosti** okno, nastaveno **název** a <xref:System.Data.DataSet.DataSetName%2A> vlastnosti`AuthorsDataSet`.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Vytvořte obslužnou rutinu události ke čtení souboru XML do datové sady

**XML pro čtení** tlačítko přečte soubor XML do datové sady. Potom nastaví vlastnosti pro <xref:System.Windows.Forms.DataGridView> ovládací prvek, který vázat na datovou sadu.

1.  V **Průzkumníka řešení**vyberte **Form1**a pak vyberte **Návrhář zobrazení** tlačítko **Průzkumníka řešení** nástrojů.

2.  Vyberte **XML pro čtení** tlačítko.

     **Editor kódu** se otevře na `ReadXmlButton_Click` obslužné rutiny události.

3.  Zadejte následující kód do `ReadXmlButton_Click` obslužné rutiny události:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4.  V `ReadXMLButton_Click` kód obslužné rutiny událostí, změnit `filepath =` položky na správnou cestu.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Vytvořte obslužnou rutinu události pro zobrazení schématu do textového pole

**Zobrazit schéma** tlačítko vytvoří <xref:System.IO.StringWriter> objekt, který je vyplněna schématu a zobrazí se v <xref:System.Windows.Forms.TextBox>ovládacího prvku.

1.  V **Průzkumníka řešení**vyberte **Form1**a pak vyberte **Návrhář zobrazení** tlačítko.

2.  Vyberte **zobrazit schéma** tlačítko.

     **Editor kódu** se otevře na `ShowSchemaButton_Click` obslužné rutiny události.

3.  Vložte následující kód do `ShowSchemaButton_Click` obslužné rutiny události.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Testovací formulář

Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.

1.  Vyberte **F5** ke spuštění aplikace.

2.  Vyberte **XML pro čtení** tlačítko.

     Ovládací prvek DataGridView zobrazí obsah souboru XML.

3.  Vyberte **zobrazit schéma** tlačítko.

     Do textového pole zobrazuje schéma XML pro soubor XML.

## <a name="next-steps"></a>Další kroky

Tento návod vás naučí základy čtení souboru XML do datové sady, jakož i vytváření schématu na základě obsahu souboru XML. Tady jsou některé úlohy, které vám může dělat:

-   Úprava dat v datové sadě a zápis jej vrátit jako XML. Další informace naleznete v tématu <xref:System.Data.DataSet.WriteXml%2A>.

-   Úprava dat v datové sadě a vypsat do databáze.

## <a name="see-also"></a>Viz také:

- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Nástroje XML v sadě Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)