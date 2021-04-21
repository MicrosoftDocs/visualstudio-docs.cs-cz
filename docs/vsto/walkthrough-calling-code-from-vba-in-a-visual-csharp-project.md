---
title: 'Návod: volání kódu z jazyka VBA v projektu jazyka Visual C#'
description: Naučte se volat metodu v přizpůsobení na úrovni dokumentu pro Microsoft Excel z jazyk Visual Basic for Application (VBA) kódu v sešitu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 260872096f36f91a2618f636e297d3c48b3fe51b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824468"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>Návod: volání kódu z jazyka VBA v projektu jazyka Visual C#
  Tento návod ukazuje, jak volat metodu v přizpůsobení na úrovni dokumentu pro systém Microsoft Office Excel z kódu jazyk Visual Basic for Application (VBA) v sešitu. Postup zahrnuje tři základní kroky: Přidejte metodu do `Sheet1` třídy položky hostitele, vystavte metodu pro kód VBA v sešitu a pak zavolejte metodu z kódu VBA v sešitu.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 I když tento návod používá Excel konkrétně, koncepce znázorněné v tomto návodu se vztahují také na projekty na úrovni dokumentu ve Wordu.

 Tento návod znázorňuje následující úlohy:

- Vytvoření sešitu, který obsahuje kód VBA.

- Důvěřuje umístění sešitu pomocí centra zabezpečení v Excelu.

- Přidání metody do `Sheet1` třídy položky hostitele.

- Extrahování rozhraní pro `Sheet1` třídu položky hostitele.

- Vystavení metody pro kód VBA.

- Volání metody z kódu VBA.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>Vytvoření sešitu, který obsahuje kód VBA
 Prvním krokem je vytvoření sešitu podporujícího makra, který obsahuje jednoduché makro VBA. Předtím, než bude možné vystavit kód v přizpůsobení v jazyce VBA, musí sešit již obsahovat kód VBA. V opačném případě Visual Studio nemůže upravit projekt VBA, aby kód VBA mohl volat do sestavení vlastního nastavení.

 Pokud už máte sešit, který obsahuje kód VBA, který chcete použít, můžete tento krok přeskočit.

### <a name="to-create-a-workbook-that-contains-vba-code"></a>Vytvoření sešitu, který obsahuje kód VBA

1. Spusťte aplikaci Excel.

2. Uložte aktivní dokument jako **excelový Macro-Enabled sešit ( \* . xlsm)** s názvem **WorkbookWithVBA**. Uložte ho do vhodného umístění, jako je například plocha.

3. Na pásu karet klikněte na kartu **vývojář** .

    > [!NOTE]
    > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Ve skupině **kódu** klikněte na **Visual Basic**.

     Otevře se Visual Basic Editor.

5. V okně **projektu** poklikejte na **ThisWorkbook**.

     Otevře se soubor s kódem pro daný `ThisWorkbook` objekt.

6. Do souboru kódu přidejte následující kód VBA. Tento kód definuje jednoduchou funkci, která neprovede žádnou akci. Jediným účelem této funkce je zajistit, aby v sešitu existoval projekt VBA. To je nutné pro pozdější kroky v tomto návodu.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. Uložte dokument a ukončete aplikaci Excel.

## <a name="create-the-project"></a>Vytvoření projektu
 Nyní můžete vytvořit projekt na úrovni dokumentu pro aplikaci Excel, který používá sešit s podporou maker, který jste vytvořili dříve.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Spustit [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. V nabídce **soubor** přejděte na příkaz **Nový** a klikněte na **projekt**.

3. V podokně šablony rozbalte položku **Visual C#** a poté rozbalte položku **Office/SharePoint**.

4. Vyberte uzel **Doplňky pro Office** .

5. V seznamu šablon projektu vyberte **sešit excel 2010** nebo projekt **Excelu 2013** .

6. Do pole **název** zadejte **CallingCodeFromVBA**.

7. Klikněte na **OK**.

     Otevře se **Průvodce projektem Visual Studio Tools for Office** .

8. Vyberte možnost **zkopírovat existující dokument** a v poli **Úplná cesta k existujícímu dokumentu** zadejte umístění sešitu **WorkbookWithVBA** , který jste vytvořili dříve. Pokud používáte vlastní sešit s podporou maker, místo toho určete umístění tohoto sešitu.

9. Klikněte na **Finish** (Dokončit).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře sešit **WorkbookWithVBA** v návrháři a přidá projekt **CallingCodeFromVBA** do **Průzkumník řešení**.

## <a name="trust-the-location-of-the-workbook"></a>Důvěřovat umístění sešitu
 Předtím, než můžete v sešitu vystavit kód v rámci vašeho řešení, je třeba důvěřovat modulu VBA v sešitu, aby bylo možné jej spustit. Existuje několik způsobů, jak to udělat. V tomto návodu tuto úlohu vyplníte tak, že důvěřujete umístění sešitu v **Centru zabezpečení** v Excelu.

### <a name="to-trust-the-location-of-the-workbook"></a>Chcete-li důvěřovat umístění sešitu

1. Spusťte aplikaci Excel.

2. Klikněte na kartu **soubor** .

3. Klikněte na tlačítko **Možnosti aplikace Excel** .

4. V podokně kategorie klikněte na **Centrum zabezpečení**.

5. V podokně podrobností klikněte na **Nastavení centra zabezpečení**.

6. V podokně kategorie klikněte na možnost **důvěryhodná umístění**.

7. V podokně podrobností klikněte na **Přidat nové umístění**.

8. V dialogovém okně **systém Microsoft Office důvěryhodné umístění** přejděte do složky, která obsahuje projekt **CallingCodeFromVBA** .

9. Vybrat **podsložky tohoto umístění jsou také důvěryhodné**.

10. V dialogovém okně **systém Microsoft Office důvěryhodné umístění** klikněte na tlačítko **OK**.

11. V dialogovém okně **Centrum zabezpečení** klikněte na tlačítko **OK**.

12. V dialogovém okně **Možnosti aplikace Excel** klikněte na tlačítko **OK**.

13. Ukončete **aplikaci Excel**.

## <a name="add-a-method-to-the-sheet1-class"></a>Přidání metody do třídy List1
 Teď, když je projekt VBA nastavený, přidejte veřejnou metodu do `Sheet1` třídy hostitelské položky, kterou můžete volat z kódu VBA.

### <a name="to-add-a-method-to-the-sheet1-class"></a>Přidání metody do třídy List1

1. V **Průzkumník řešení** klikněte pravým tlačítkem na **List1. cs** a pak klikněte na **Zobrazit kód**.

     V editoru kódu se otevře soubor **List1. cs** .

2. Do třídy `Sheet1` přidejte následující kód. `CreateVstoNamedRange`Metoda vytvoří nový <xref:Microsoft.Office.Tools.Excel.NamedRange> objekt v zadaném rozsahu. Tato metoda také vytvoří obslužnou rutinu události pro <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> událost <xref:Microsoft.Office.Tools.Excel.NamedRange> . Později v tomto návodu budete volat `CreateVstoNamedRange` metodu z kódu VBA v dokumentu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet2":::

3. Do třídy přidejte následující metodu `Sheet1` . Tato metoda přepíše <xref:Microsoft.Office.Tools.Excel.WorksheetBase.GetAutomationObject%2A> metodu, která vrátí aktuální instanci `Sheet1` třídy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet3":::

4. Použijte následující atributy před první řádek `Sheet1` deklarace třídy. Tyto atributy nastaví třídu jako viditelnou pro model COM, ale bez generování rozhraní třídy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs" id="Snippet1":::

## <a name="extract-an-interface-for-the-sheet1-class"></a>Extrakce rozhraní pro třídu List1
 Předtím, než můžete vystavit `CreateVstoNamedRange` metodu pro kód VBA, je nutné vytvořit veřejné rozhraní, které definuje tuto metodu, a je nutné vystavit toto rozhraní modelu COM.

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Extrakce rozhraní pro třídu List1

1. V souboru kódu **List1. cs** Klikněte kamkoli do `Sheet1` třídy.

2. V nabídce **Refaktorovat** klikněte na **Extrahovat rozhraní**.

3. V dialogovém okně **Extrahovat rozhraní** v poli **Vybrat veřejné členy do formuláře rozhraní** klikněte na položku pro `CreateVstoNamedRange` metodu.

4. Klikněte na **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vygeneruje nové rozhraní s názvem `ISheet1` a upraví definici `Sheet1` třídy tak, aby implementovala `ISheet1` rozhraní. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] také otevře soubor **ISheet1. cs** v editoru kódu.

5. V souboru **ISheet1. cs** nahraďte `ISheet1` deklaraci rozhraní následujícím kódem. Tento kód nastaví `ISheet1` rozhraní jako veřejné a použije <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut, aby bylo rozhraní viditelné pro model COM.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs" id="Snippet4":::

6. Sestavte projekt.

## <a name="expose-the-method-to-vba-code"></a>Vystavení metody pro kód VBA
 K vystavení `CreateVstoNamedRange` metody pro kód VBA v sešitu nastavte vlastnost **ReferenceAssemblyFromVbaProject** pro `Sheet1` položku hostitele na **hodnotu true**.

### <a name="to-expose-the-method-to-vba-code"></a>Vystavení metody pro kód VBA

1. V **Průzkumník řešení** poklikejte na **List1. cs**.

     Soubor **WorkbookWithVBA** se otevře v návrháři a zobrazí se List1.

2. V okně **vlastnosti** vyberte vlastnost **ReferenceAssemblyFromVbaProject** a změňte hodnotu na **true**.

3. Ve zprávě, která se zobrazí, klikněte na **OK** .

4. Sestavte projekt.

## <a name="call-the-method-from-vba-code"></a>Volání metody z kódu VBA
 Nyní můžete volat `CreateVstoNamedRange` metodu z kódu VBA v sešitu.

> [!NOTE]
> V tomto návodu přidáte do sešitu kód VBA během ladění projektu. Kód VBA, který přidáte do tohoto dokumentu, bude při příštím sestavení projektu přepsán, protože Visual Studio nahradí dokument ve výstupní složce sestavení kopií dokumentu z hlavní složky projektu. Pokud chcete kód VBA uložit, můžete ho zkopírovat do dokumentu ve složce projektu. Další informace najdete v tématu [Kombinování přizpůsobení na úrovni VBA a dokumentu](../vsto/combining-vba-and-document-level-customizations.md).

### <a name="to-call-the-method-from-vba-code"></a>Volání metody z kódu jazyka VBA

1. Stisknutím klávesy **F5** spusťte projekt.

2. Na kartě **vývojář** ve skupině **kód** klikněte na **Visual Basic**.

     Otevře se Visual Basic Editor.

3. V nabídce **Vložit** klikněte na **modul**.

4. Do nového modulu přidejte následující kód.

     Tento kód volá `CreateTable` metodu v sestavení přizpůsobení. Makro přistupuje k této metodě pomocí globální `GetManagedClass` metody pro přístup k `Sheet1` třídě položky hostitele, kterou jste vystavili v kódu VBA. `GetManagedClass`Metoda se automaticky vygenerovala při nastavení vlastnosti **ReferenceAssemblyFromVbaProject** dříve v tomto návodu.

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. Stiskněte klávesu **F5**.

6. V otevřeném sešitu klikněte na buňku **a1** na **List1**. Ověřte, že se zobrazí okno se zprávou.

7. Ukončete aplikaci Excel bez uložení změn.

## <a name="next-steps"></a>Další kroky
 Další informace o volání kódu v řešeních pro systém Office z jazyka VBA najdete v těchto tématech:

- Volání kódu v položce hostitele v Visual Basic přizpůsobení z jazyka VBA. Tento proces se liší od procesu Visual C#. Další informace naleznete v tématu [Návod: volání kódu z jazyka VBA v projektu Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).

- Volání kódu v doplňku VSTO z jazyka VBA. Další informace naleznete v tématu [Návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

## <a name="see-also"></a>Viz také
- [Kombinování přizpůsobení na úrovni VBA a dokumentů](../vsto/combining-vba-and-document-level-customizations.md)
- [Přizpůsobení na úrovni dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Postupy: vystavení kódu v projektu Visual Basic v jazyce VBA](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Postupy: vystavení kódu pro jazyk VBA ve Visual C&#35; projektu](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Návod: volání kódu z jazyka VBA v projektu Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
