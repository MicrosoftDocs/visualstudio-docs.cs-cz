---
title: 'Návod: Volání kódu z jazyka VBA v projektu jazyka Visual C#'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e2803ef31ec1009215d4490ac527c42cbdc90571
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781686"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Návod: Volání kódu z jazyka VBA v projektu jazyka Visual C#
  Tento návod ukazuje, jak volat metodu v přizpůsobení na úrovni dokumentu pro aplikaci Microsoft Office Excel z jazyka Visual Basic pro kód Applications (VBA) v sešitu. Postup zahrnuje tři základní kroky: Přidejte metodu k `Sheet1` hostování třída položek, zveřejňují metodu pro kód VBA v sešitu a poté zavolejte metodu z jazyka VBA kód v sešitu.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 I když tento návod používá konkrétně aplikace Excel, koncepty jsme vám ukázali podle návodu lze také použít na projekty na úrovni dokumentu aplikace Word.  
  
 Tento návod znázorňuje následující úlohy:  
  
-   Vytvoření sešitu, který obsahuje kód VBA.  
  
-   Důvěřující umístění sešitu s použitím v Centru zabezpečení v aplikaci Excel.  
  
-   Přidání metody do `Sheet1` hostovat třída položek.  
  
-   Extrahování rozhraní pro `Sheet1` hostovat třída položek.  
  
-   Vystavení metodu pro kód VBA.  
  
-   Volání metody z jazyka VBA kód.  
  
> [!NOTE]  
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-a-workbook-that-contains-vba-code"></a>Vytvořte sešit, který obsahuje kód VBA  
 Prvním krokem je vytvoření sešit s podporou maker, který obsahuje jednoduché – makro VBA. Předtím, než můžete zpřístupnit ve vlastní nastavení pro jazyk VBA kód, musí sešit obsahovat již kód VBA. V opačném případě sady Visual Studio nelze změnit projekt VBA umožňující kód VBA, chcete-li volat vlastního nastavení sestavení.  
  
 Pokud už máte sešit, který obsahuje kód VBA, který chcete použít, můžete tento krok přeskočit.  
  
### <a name="to-create-a-workbook-that-contains-vba-code"></a>Chcete-li vytvořit sešit, který obsahuje kód VBA  
  
1.  Spuštění aplikace Excel.  
  
2.  Uložit aktivní dokument jako **Excel Macro-Enabled sešitu (\*.xlsm)** s názvem **WorkbookWithVBA**. Uložte ji do vhodného umístění, například na plochu.  
  
3.  Na pásu karet klikněte na tlačítko **Developer** kartu.  
  
    > [!NOTE]  
    >  Pokud **Developer** karta není zobrazena, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  V **kód** klikněte na možnost **jazyka Visual Basic**.  
  
     Otevře se Editor jazyka Visual Basic.  
  
5.  V **projektu** okna, dvakrát klikněte na panel **ThisWorkbook**.  
  
     V souboru kódu `ThisWorkbook` objektu se otevře.  
  
6.  Přidejte následující kód VBA do souboru kódu. Tento kód definuje jednoduchou funkci, která nemá žádný účinek. Jediným účelem této funkce je zajistit, že existuje projekt VBA v sešitu. Toto je nezbytné pro pozdější kroky v tomto názorném postupu.  
  
    ```vb  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Dokument uložte a ukončete aplikaci Excel.  
  
## <a name="create-the-project"></a>Vytvoření projektu  
 Nyní můžete vytvořit projekt úrovni dokumentu pro Excel, která se používá s podporou maker sešit, který jste vytvořili dříve.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a potom klikněte na tlačítko **projektu**.  
  
3.  V podokně šablony rozbalte **Visual C#** a potom rozbalte **Office/SharePoint**.  
  
4.  Vyberte **Office Add-ins** uzlu.  
  
5.  V seznamu šablon projektu vyberte **sešit aplikace Excel 2010** nebo **sešit aplikace Excel 2013** projektu.  
  
6.  V **název** zadejte **CallingCodeFromVBA**.  
  
7.  Klikněte na tlačítko **OK**.  
  
     **Visual Studio Tools for Office Project Wizard** otevře.  
  
8.  Vyberte **zkopírovat existující dokument**a v **úplnou cestu k existujícímu dokumentu** zadejte umístění **WorkbookWithVBA** sešit, který jste vytvořili dříve . Pokud používáte s podporou maker sešit, zadejte umístění tohoto sešitu.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře **WorkbookWithVBA** sešit v návrháři a přidá **CallingCodeFromVBA** projektu **Průzkumníka řešení**.  
  
## <a name="trust-the-location-of-the-workbook"></a>Důvěřujete umístění sešitu  
 Před vystavení kódu v řešení pro kód VBA v sešitu, musí důvěřovat VBA v sešit, který chcete spustit. Chcete-li to provést několika způsoby. V tomto názorném postupu se provést tuto úlohu důvěryhodnou umístění v sešitu **centrum** v aplikaci Excel.  
  
### <a name="to-trust-the-location-of-the-workbook"></a>Důvěřovat umístění sešitu  
  
1.  Spuštění aplikace Excel.  
  
2.  Klikněte na tlačítko **souboru** kartu.  
  
3.  Klikněte na tlačítko **možnosti aplikace Excel** tlačítko.  
  
4.  V podokně kategorie, klikněte na tlačítko **centrum**.  
  
5.  V podokně podrobností klikněte na tlačítko **nastavení Centra zabezpečení**.  
  
6.  V podokně kategorie, klikněte na tlačítko **důvěryhodná umístění**.  
  
7.  V podokně podrobností klikněte na tlačítko **přidat nové umístění**.  
  
8.  V **Microsoft Office důvěryhodné umístění** dialogové okno, přejděte do složky, která obsahuje **CallingCodeFromVBA** projektu.  
  
9. Vyberte **podsložky tohoto umístění jsou také důvěryhodné**.  
  
10. V **Microsoft Office důvěryhodné umístění** dialogové okno, klikněte na tlačítko **OK**.  
  
11. V **centrum** dialogové okno, klikněte na tlačítko **OK**.  
  
12. V **možnosti aplikace Excel** dialogové okno, klikněte na tlačítko **OK**.  
  
13. Ukončení **Excel**.  
  
## <a name="add-a-method-to-the-sheet1-class"></a>Přidejte metodu Sheet1 – třída  
 Teď, když je nastavení projektu VBA, přidejte veřejnou metodu pro `Sheet1` hostovat třída položek, které můžete volat z jazyka VBA kód.  
  
### <a name="to-add-a-method-to-the-sheet1-class"></a>Přidání metody Sheet1 – třída  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Sheet1.cs**a potom klikněte na tlačítko **zobrazit kód**.  
  
     **Sheet1.cs** soubor se otevře v editoru kódu.  
  
2.  Přidejte následující kód, který `Sheet1` třídy. `CreateVstoNamedRange` Metoda vytvoří nový <xref:Microsoft.Office.Tools.Excel.NamedRange> objekt v zadaném rozsahu. Tato metoda také vytvoří obslužnou rutinu události pro <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> událost <xref:Microsoft.Office.Tools.Excel.NamedRange>. Později v tomto návodu budete volat `CreateVstoNamedRange` metodu z kód VBA v dokumentu.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]  
  
3.  Přidejte následující metodu do `Sheet1` třídy. Přepíše tuto metodu <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> metoda vrátí aktuální instancí třídy `Sheet1` třídy.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]  
  
4.  Použijte následující atributy před první řádek `Sheet1` deklarace třídy. Tyto atributy zviditelnit třídy modelu COM, ale bez generování třídy rozhraní.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]  
  
## <a name="extract-an-interface-for-the-sheet1-class"></a>Extrahovat rozhraní pro Sheet1 – třída  
 Předtím, než můžete zveřejnit `CreateVstoNamedRange` metodu pro kód VBA, musíte vytvořit veřejného rozhraní, která definuje tuto metodu, a musí zveřejnit toto rozhraní modelu COM.  
  
### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Extrahovat rozhraní pro Sheet1 – třída  
  
1.  V **Sheet1.cs** soubor kódu, klikněte kamkoli do `Sheet1` třídy.  
  
2.  Na **Refaktorovat** nabídky, klikněte na tlačítko **extrahování rozhraní**.  
  
3.  V **extrahování rozhraní** v dialogu **vyberte veřejné členy rozhraní** pole, klikněte na položku `CreateVstoNamedRange` metoda.  
  
4.  Klikněte na tlačítko **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] generuje nové rozhraní s názvem `ISheet1`, a mění definici `Sheet1` třídy tak, aby se implementuje `ISheet1` rozhraní. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] také se otevře **ISheet1.cs** souboru v editoru kódu.  
  
5.  V **ISheet1.cs** souboru, nahradí `ISheet1` rozhraní deklarace s následujícím kódem. Tento kód provede `ISheet1` veřejné rozhraní a se vztahuje <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut využívajícího rozhraní modelu COM.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]  
  
6.  Sestavte projekt.  
  
## <a name="expose-the-method-to-vba-code"></a>Vystavit metodu pro kód VBA  
 Vystavit `CreateVstoNamedRange` metodu pro kód VBA v sešitu, nastavte **ReferenceAssemblyFromVbaProject** vlastnost `Sheet1` položka hostitele na **True**.  
  
### <a name="to-expose-the-method-to-vba-code"></a>Vystavit metodu pro kód VBA  
  
1.  V **Průzkumníka řešení**, dvakrát klikněte na panel **Sheet1.cs**.  
  
     **WorkbookWithVBA** soubor se otevře v návrháři se List1 viditelné.  
  
2.  V **vlastnosti** okna, vyberte **ReferenceAssemblyFromVbaProject** vlastnost a změňte hodnotu na **True**.  
  
3.  Klikněte na tlačítko **OK** ve zprávě, která se zobrazí.  
  
4.  Sestavte projekt.  
  
## <a name="call-the-method-from-vba-code"></a>Volání metody z jazyka VBA kód  
 Nyní můžete volat `CreateVstoNamedRange` metodu z jazyka VBA kód v sešitu.  
  
> [!NOTE]  
>  V tomto názorném postupu přidáte kód VBA v sešitu při ladění projektu. Kód VBA, který přidáte do tohoto dokumentu se přepíše při příštím sestavení projektu, protože Visual Studio nahradí kopii dokumentu ze složky projektu hlavní dokument ve výstupní složce sestavení. Pokud chcete uložit kód VBA, zkopírujte jej do dokumentu ve složce projektu. Další informace najdete v tématu [kombinovat VBA a přizpůsobení na úrovni dokumentu](../vsto/combining-vba-and-document-level-customizations.md).  
  
### <a name="to-call-the-method-from-vba-code"></a>Volat metodu z jazyka VBA kód  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  Na **Developer** kartě **kód** klikněte na možnost **jazyka Visual Basic**.  
  
     Otevře se Editor jazyka Visual Basic.  
  
3.  Na **vložit** nabídky, klikněte na tlačítko **modulu**.  
  
4.  Přidejte následující kód do nového modulu.  
  
     Tento kód volá `CreateTable` metoda v vlastního nastavení sestavení. Makro má přístup k této metody pomocí globální `GetManagedClass` metody přístup `Sheet1` hostovat položky třídu, která je vystavená pro kód VBA. `GetManagedClass` Metoda automaticky vygenerované při nastavení **ReferenceAssemblyFromVbaProject** vlastnost dříve v tomto návodu.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1  
        Set VSTOSheet1 = GetManagedClass(Sheet1)  
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")  
    End Sub  
    ```  
  
5.  Stisknutím klávesy **F5**.  
  
6.  Do otevřeného sešitu, klikněte na buňku **A1** na **List1**. Ověřte, že se objeví okno zpráv.  
  
7.  Ukončete aplikaci Excel bez uložení změn.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o volání kódu v řešeních pro systém Office z jazyka VBA v těchto tématech:  
  
-   Volání kódu v položce hostitel ve vlastním nastavení jazyka Visual Basic z jazyka VBA. Tento proces se liší od procesu Visual C#. Další informace najdete v tématu [návod: volání kódu z jazyka VBA v projektu jazyka Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   Volání kódu v doplňku VSTO z jazyka VBA. Další informace najdete v tématu [návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>Viz také:  
 [Kombinování přizpůsobení na úrovni dokumentu a VBA](../vsto/combining-vba-and-document-level-customizations.md)   
 [Programování přizpůsobení na úrovni dokumentu](../vsto/programming-document-level-customizations.md)   
 [Postupy: vystavení kódu do VBA v projektu jazyka Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Postupy: vystavení kódu v aplikaci Visual C pro jazyk VBA&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Návod: Volání kódu z jazyka VBA v projektu jazyka Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  