---
title: Čtení dat XML do datové sady | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652894"
---
# <a name="read-xml-data-into-a-dataset"></a>Načtení dat XML do datové sady
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET poskytuje jednoduché metody pro práci s daty XML. V tomto návodu vytvoříte aplikaci pro Windows, která načte data XML do datové sady. Datová sada se pak zobrazí v <xref:System.Windows.Forms.DataGridView> ovládacím prvku. Nakonec se schéma XML na základě obsahu souboru XML zobrazí v textovém poli.

 Tento názorný postup se skládá z pěti hlavních kroků:

1. Vytvoření nového projektu

2. Vytvoření souboru XML pro čtení do datové sady

3. Vytvoření uživatelského rozhraní

4. Vytvoření datové sady, čtení souboru XML a jeho zobrazení v <xref:System.Windows.Forms.DataGridView> ovládacím prvku

5. Přidání kódu pro zobrazení schématu XML na základě souboru XML v <xref:System.Windows.Forms.TextBox> ovládacím prvku

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici, kterou používáte. Chcete-li změnit nastavení, v nabídce  **nástroje** vyberte**Nastavení importu a exportu**. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Vytvoření nového projektu
 V tomto kroku vytvoříte projekt Visual Basic nebo Visual C#, který obsahuje tento návod.

#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows

1. V nabídce **soubor** vytvořte nový projekt.

2. Pojmenujte projekt `ReadingXML` .

3. Vyberte **aplikace systému Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **ReadingXML** je vytvořen a přidán do **Průzkumník řešení**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Vygenerovat soubor XML, který se má číst do datové sady
 Vzhledem k tomu, že se tento návod zaměřuje na čtení dat XML do datové sady, je k dispozici obsah souboru XML.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Chcete-li vytvořit soubor XML, který bude načten do datové sady

1. V nabídce **projekt** vyberte možnost**Přidat novou položku**.

2. Vyberte **soubor XML**, zadejte název souboru `authors.xml` a pak vyberte **Přidat**.

     Soubor XML se načte do návrháře a je připravený k úpravám.

3. Do editoru pod deklarací XML vložte následující kód:

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

4. V nabídce **soubor** vyberte**Uložit authors.xml**.

## <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní
 Uživatelské rozhraní pro tuto aplikaci se skládá z těchto možností:

- <xref:System.Windows.Forms.DataGridView>Ovládací prvek, který zobrazí obsah souboru XML jako data.

- <xref:System.Windows.Forms.TextBox>Ovládací prvek, který zobrazuje schéma XML pro soubor XML.

- Dva <xref:System.Windows.Forms.Button> ovládací prvky.

  - Jedno tlačítko přečte soubor XML do datové sady a zobrazí ho v <xref:System.Windows.Forms.DataGridView> ovládacím prvku.

  - Druhé tlačítko extrahuje schéma z datové sady a prostřednictvím <xref:System.IO.StringWriter> <xref:System.Windows.Forms.TextBox> ovládacího prvku ho zobrazí.

#### <a name="to-add-controls-to-the-form"></a>Přidání ovládacích prvků do formuláře

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

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Vytvoření datové sady thatreceives daty XML
 V tomto kroku vytvoříte novou datovou sadu s názvem `authors` . Další informace o datových sadách naleznete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Vytvoření nové datové sady, která přijímá data XML

1. V **Průzkumník řešení**vyberte zdrojový soubor pro **Form1**a pak na panelu nástrojů **Průzkumník řešení** vyberte tlačítko **Návrhář zobrazení** .

2. Na [kartě sada nástrojů data](../ide/reference/toolbox-data-tab.md)přetáhněte **datovou sadu** na **Form1**.

3. V dialogovém okně **Přidat datovou sadu** vyberte **netypové datové sady**a pak vyberte **OK**.

     **DataSet1.** se přidá do zásobníku komponent.

4. V okně **vlastnosti** nastavte **název** a <xref:System.Data.DataSet.DataSetName%2A> vlastnosti pro `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Vytvoření obslužné rutiny události pro čtení souboru XML do datové sady
 Tlačítko **číst XML** přečte soubor XML do datové sady. Poté nastaví vlastnosti <xref:System.Windows.Forms.DataGridView> ovládacího prvku, který jej sváže s datovou sadou.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>Přidání kódu do obslužné rutiny události ReadXmlButton_Click

1. V **Průzkumník řešení**vyberte **Form1**a pak na panelu nástrojů **Průzkumník řešení** vyberte tlačítko **Návrhář zobrazení** .

2. Vyberte tlačítko **číst XML** .

     **Editor kódu** se otevře v `ReadXmlButton_Click` obslužné rutině události.

3. Do `ReadXmlButton_Click` obslužné rutiny události zadejte následující kód:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. V `ReadXMLButton_Click` kódu obslužné rutiny události změňte `filepath =` položku na správnou cestu.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Vytvoření obslužné rutiny události pro zobrazení schématu v textovém poli
 Tlačítko **Zobrazit schéma** vytvoří <xref:System.IO.StringWriter> objekt, který je vyplněn schématem a je zobrazen v <xref:System.Windows.Forms.TextBox> ovládacím prvku.

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>Přidání kódu do obslužné rutiny události ShowSchemaButton_Click

1. V **Průzkumník řešení**vyberte **Form1**a pak klikněte na tlačítko **Návrhář zobrazení** .

2. Vyberte tlačítko **Zobrazit schéma** .

     **Editor kódu** se otevře v `ShowSchemaButton_Click` obslužné rutině události.

3. Do `ShowSchemaButton_Click` obslužné rutiny události zadejte následující kód.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

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
 [Návody](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) k datům [, které přistupují k datům v aplikaci Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [Příprava aplikace pro příjem](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [nástrojů XML data v aplikaci Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
