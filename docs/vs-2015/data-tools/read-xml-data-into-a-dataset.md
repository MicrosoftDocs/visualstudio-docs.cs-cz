---
title: XML pro čtení dat do datové sady | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6eb85fcef78b4b856c47ccb4436d1314ae440136
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219728"
---
# <a name="read-xml-data-into-a-dataset"></a>Načtení dat XML do datové sady
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
ADO.NET obsahuje jednoduché metody pro práci s daty XML. V tomto návodu vytvoříte aplikaci Windows, který načítá XML data do datové sady. Datová sada se následně zobrazí <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Nakonec schématu XML na základě obsahu souboru XML se zobrazí v textovém poli.  
  
 Tento názorný postup se skládá z pěti hlavních kroků:  
  
1.  Vytvoření nového projektu  
  
2.  Vytvoření souboru XML pro čtení do datové sady  
  
3.  Vytvoření uživatelského rozhraní  
  
4.  Vytvoření datové sady, soubor XML pro čtení a zobrazením v <xref:System.Windows.Forms.DataGridView> ovládacího prvku  
  
5.  Přidání kódu k zobrazení schématu XML založený na souboru XML v <xref:System.Windows.Forms.TextBox> ovládacího prvku  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které se zobrazí, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici, kterou používáte. Chcete-li změnit nastavení na **nástroje** nabídce vyberte možnost**nastavení importu a exportu**. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-new-project"></a>Vytvoření nového projektu  
 V tomto kroku vytvoříte projekt jazyka Visual Basic nebo Visual C#, která obsahuje tento návod.  
  
#### <a name="to-create-the-new-windows-project"></a>Vytvoření nového projektu Windows  
  
1.  Na **souboru** nabídky, vytvořte nový projekt.  
  
2.  Pojmenujte projekt `ReadingXML`.  
  
3.  Vyberte **aplikace Windows**a pak vyberte **OK**. Další informace najdete v tématu [klientské aplikace](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **ReadingXML** projekt je vytvořen a přidán do **Průzkumníka řešení**.  
  
## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Generovat soubor XML pro čtení do datové sady  
 Protože tento návod se zaměřuje na čtení dat XML do datové sady, je k dispozici obsah souboru XML.  
  
#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>K vytvoření souboru XML, který se načtou do datové sady  
  
1.  Na **projektu** nabídce vyberte možnost**přidat novou položku**.  
  
2.  Vyberte **soubor XML**, pojmenujte soubor `authors.xml`a pak vyberte **přidat**.  
  
     Soubor XML načte do návrháře a je připravený pro úpravy.  
  
3.  Vložte následující kód do editoru níže deklarace XML:  
  
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
  
4.  Na **souboru** nabídce vyberte možnost**uložit authors.xml**.  
  
## <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
 Uživatelské rozhraní pro tuto aplikaci se skládá z následujících akcí:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek, který zobrazí obsah souboru XML jako data.  
  
-   A <xref:System.Windows.Forms.TextBox> ovládací prvek, který zobrazí schéma XML pro soubor XML.  
  
-   Dvě <xref:System.Windows.Forms.Button> ovládacích prvků.  
  
    -   Jedno tlačítko přečte soubor XML do datové sady a zobrazí ho v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
    -   Druhé tlačítko extrahuje schéma z datové sady a prostřednictvím <xref:System.IO.StringWriter> zobrazí ho v <xref:System.Windows.Forms.TextBox> ovládacího prvku.  
  
#### <a name="to-add-controls-to-the-form"></a>Chcete-li přidat ovládací prvky do formuláře  
  
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
  
## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Vytvořit datovou sadu thatreceives XML data  
 V tomto kroku vytvoříte novou datovou sadu s názvem `authors`. Další informace o datových sadách najdete v tématu [datovou sadu nástrojů v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Chcete-li vytvořit novou datovou sadu, která přijímá XML data  
  
1.  V **Průzkumníka řešení**, vyberte zdrojový soubor pro **Form1**a pak vyberte **Návrhář zobrazení** tlačítko **Průzkumníka řešení** panel nástrojů.  
  
2.  Z [sady nástrojů, karta Data](../ide/reference/toolbox-data-tab.md), přetáhněte **datovou sadu** do **Form1**.  
  
3.  V **přidat datovou sadu** dialogu **netypovou datovou sadu**a pak vyberte **OK**.  
  
     **DataSet1** se přidá do panelu komponent.  
  
4.  V **vlastnosti** okno, nastaveno **název** a <xref:System.Data.DataSet.DataSetName%2A> vlastnosti`AuthorsDataSet`.  
  
## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Vytvořte obslužnou rutinu události ke čtení souboru XML do datové sady  
 **XML pro čtení** tlačítko přečte soubor XML do datové sady. Potom nastaví vlastnosti pro <xref:System.Windows.Forms.DataGridView> ovládací prvek, který vázat na datovou sadu.  
  
#### <a name="to-add-code-to-the-readxmlbuttonclick-event-handler"></a>Chcete-li přidat kód do obslužné rutiny události ReadXmlButton_Click  
  
1.  V **Průzkumníka řešení**vyberte **Form1**a pak vyberte **Návrhář zobrazení** tlačítko **Průzkumníka řešení** nástrojů.  
  
2.  Vyberte **XML pro čtení** tlačítko.  
  
     **Editor kódu** se otevře na `ReadXmlButton_Click` obslužné rutiny události.  
  
3.  Zadejte následující kód do `ReadXmlButton_Click` obslužné rutiny události:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]  
  
4.  V `ReadXMLButton_Click` kód obslužné rutiny událostí, změnit `filepath =` položky na správnou cestu.  
  
## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Vytvořte obslužnou rutinu události pro zobrazení schématu do textového pole  
 **Zobrazit schéma** tlačítko vytvoří <xref:System.IO.StringWriter> objekt, který je vyplněna schématu a zobrazí se v <xref:System.Windows.Forms.TextBox>ovládacího prvku.  
  
#### <a name="to-add-code-to-the-showschemabuttonclick-event-handler"></a>Chcete-li přidat kód do obslužné rutiny události ShowSchemaButton_Click  
  
1.  V **Průzkumníka řešení**vyberte **Form1**a pak vyberte **Návrhář zobrazení** tlačítko.  
  
2.  Vyberte **zobrazit schéma** tlačítko.  
  
     **Editor kódu** se otevře na `ShowSchemaButton_Click` obslužné rutiny události.  
  
3.  Zadejte následující kód do `ShowSchemaButton_Click` obslužné rutiny události.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]  
  
## <a name="test-the-form"></a>Testovací formulář  
 Teď můžete otestovat formulář, abyste měli jistotu, že se chová podle očekávání.  
  
#### <a name="to-test-the-form"></a>K otestování formuláře  
  
1.  Vyberte **F5** ke spuštění aplikace.  
  
2.  Vyberte **XML pro čtení** tlačítko.  
  
     Ovládací prvek DataGridView zobrazí obsah souboru XML.  
  
3.  Vyberte **zobrazit schéma** tlačítko.  
  
     Do textového pole zobrazuje schéma XML pro soubor XML.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod vás naučí základy čtení souboru XML do datové sady, jakož i vytváření schématu na základě obsahu souboru XML. Tady jsou některé úlohy, které vám může dělat:  
  
-   Úprava dat v datové sadě a zápis jej vrátit jako XML. Další informace naleznete v tématu <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Úprava dat v datové sadě a vypsat do databáze. Další informace najdete v tématu [ukládání dat](../data-tools/saving-data.md).  
  
## <a name="see-also"></a>Viz také  
 [Návody k datům](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Příprava aplikace pro příjem dat](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Nástroje XML v sadě Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)

