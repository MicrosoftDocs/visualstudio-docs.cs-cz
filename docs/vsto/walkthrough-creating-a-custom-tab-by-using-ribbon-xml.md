---
title: 'Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 45e35b7cf97a6b9a1f310149817f8e79956a47aa
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808921"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Návod: Vytvoření vlastní karty pomocí kódu XML pásu karet
  Tento návod ukazuje, jak vytvořit vlastní kartu pásu karet pomocí **pásu karet (XML)** položky.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Přidání tlačítek **Add-Ins** kartu. **Add-Ins** karta je výchozí kartu, která je definována v souboru XML pásu karet.  
  
-   Automatizace aplikace Microsoft Office Word s použitím tlačítka na **Add-Ins** kartu.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Aplikace Microsoft Word.  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu doplňku VSTO pro Word. Můžete se později ji přizpůsobíme, **Add-Ins** kartu tohoto dokumentu.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření **doplňku aplikace Word** projektu s názvem **MyRibbonAddIn**.  
  
     Další informace najdete v tématu [postupy: vytvoření Office projekty v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře **ThisAddIn.cs** nebo **ThisAddIn.vb** soubor kódu a přidá **MyRibbonAddIn** projektu **Průzkumníka řešení**.  
  
## <a name="create-the-vsto-add-ins-tab"></a>Vytvoření karty doplňků VSTO  
 Chcete-li vytvořit **Add-Ins** kartu, přidejte **pásu karet (XML)** položky do projektu. Dále v tomto názorném postupu přidáte několik tlačítek na této kartě.  
  
### <a name="to-create-the-add-ins-tab"></a>K vytvoření karty doplňků  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat novou položku**.  
  
2.  V **přidat novou položku** dialogu **pásu karet (XML)**.  
  
3.  Změňte název nového pásu karet na **MyRibbon**a klikněte na tlačítko **přidat**.  
  
     **MyRibbon.cs** nebo **MyRibbon.vb** soubor se otevře v návrháři. Soubor XML, který je pojmenován **MyRibbon.xml** je taky přidaný do projektu.  
  
4.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ThisAddin.cs** nebo **ThisAddin.vb**a potom klikněte na tlačítko **zobrazit kód**.  
  
5.  Přidejte následující kód, který **ThisAddin** třídy. Tento kód přepíše `CreateRibbonExtensibilityObject` třídu metodu a vrátí kódu XML pásu karet aplikace sady Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **MyRibbonAddIn** projektu a pak klikněte na tlačítko **sestavení**. Ověřte, že projekt se sestaví bez chyb.  
  
## <a name="add-buttons-to-the-add-ins-tab"></a>Přidání tlačítek do Add-ins kartu  
 Cílem tohoto doplňku VSTO je uživatelům poskytnout způsob, jak přidat často používaný text a určité tabulky v aktivním dokumentu. K poskytování uživatelského rozhraní, přidejte dvě tlačítka **Add-Ins** kartu úpravou souboru XML pásu karet. Dále v tomto názorném postupu určíte metody zpětného volání pro tlačítka. Další informace o souboru XML pásu karet najdete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
### <a name="to-add-buttons-to-the-add-ins-tab"></a>K přidání tlačítek do Add-ins kartu  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **MyRibbon.xml** a potom klikněte na tlačítko **otevřít**.  
  
2.  Nahraďte obsah **kartu** element s následující kód XML. Tato konfigurace XML se změní popisek skupiny ovládací prvek výchozí **obsahu**, a přidá dvě nová tlačítka s popisky **vložit Text** a **Vložit tabulku**.  
  
    ```xml  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automate-the-document-by-using-the-buttons"></a>Automatizace dokumentu s použitím tlačítka  
 Je nutné přidat `onAction` metody zpětného volání pro **vložit Text** a **Vložit tabulku** tlačítka k provádění akcí po klepnutí na ně. Další informace o metody zpětného volání pro ovládací prvky pásu karet najdete v tématu [kódu XML pásu karet](../vsto/ribbon-xml.md).  
  
### <a name="to-add-callback-methods-for-the-buttons"></a>Chcete-li přidat metody zpětného volání pro tlačítka  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **MyRibbon.cs** nebo **MyRibbon.vb**a potom klikněte na tlačítko **otevřít**.  
  
2.  Přidejte následující kód do horní části **MyRibbon.cs** nebo **MyRibbon.vb** souboru. Tento kód vytvoří alias pro <xref:Microsoft.Office.Interop.Word> oboru názvů.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Přidejte následující metodu do `MyRibbon` třídy. Toto je metoda zpětného volání pro **vložit Text** tlačítko, které přidá řetězec do aktivního dokumentu v aktuálním umístění kurzoru.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Přidejte následující metodu do `MyRibbon` třídy. Toto je metoda zpětného volání pro **Vložit tabulku** tlačítko, které se přidá do aktivního dokumentu v aktuálním umístění kurzoru tabulky.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Testování doplňku VSTO  
 Při spuštění projektu, otevře se aplikace Word a na kartě s názvem **Add-Ins** se zobrazí na pásu karet. Klikněte na tlačítko **vložit Text** a **Vložit tabulku** tlačítka **Add-Ins** kartu pro otestování kódu.  
  
### <a name="to-test-your-vsto-add-in"></a>K otestování vašeho doplňku VSTO  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Ujistěte se, že **Add-Ins** karta je viditelný na pásu karet.  
  
3.  Klikněte na tlačítko **Add-Ins** kartu.  
  
4.  Ujistěte se, že **obsahu** skupina je viditelný na pásu karet.  
  
5.  Klikněte na tlačítko **vložit Text** tlačítko **obsahu** skupiny.  
  
     Řetězec se přidá do dokumentu na aktuální pozici kurzoru.  
  
6.  Klikněte na tlačítko **Vložit tabulku** tlačítko **obsahu** skupiny.  
  
     Tabulka se přidá do dokumentu na aktuální pozici kurzoru.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o tom, jak přizpůsobit uživatelské rozhraní sady Office naleznete v těchto tématech:  
  
-   Přizpůsobení pásu karet z jiné aplikace Office. Další informace o aplikacích, které podporují přizpůsobení pásu karet najdete v tématu [přehled pásu karet](../vsto/ribbon-overview.md).  
  
-   Přizpůsobení pásu karet aplikace sady Office pomocí Návrháře pásu karet. Další informace najdete v tématu [Návrháře pásu karet](../vsto/ribbon-designer.md).  
  
-   Vytvoření vlastní akce podokna. Další informace najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md).  
  
-   Přizpůsobení uživatelského rozhraní aplikace Microsoft Office Outlook s použitím oblastí formulářů aplikace Outlook. Další informace najdete v tématu [návod: Návrh oblasti formuláře Outlooku](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přehled pásu karet](../vsto/ribbon-overview.md)   
 [Pás karet – XML](../vsto/ribbon-xml.md)   
 [Návod: Vytvoření vlastní karty pomocí Návrháře pásu karet](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  