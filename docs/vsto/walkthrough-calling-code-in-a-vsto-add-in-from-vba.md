---
title: 'Návod: volání kódu v doplňku VSTO z jazyka VBA'
description: Naučte se, jak vystavit objekt v doplňku VSTO pro další systém Microsoft Office řešení, včetně jazyk Visual Basic for Application (VBA) a COM VSTO doplňků.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 21e0928396327911ea794c6270340c6efd27a43e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824598"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Návod: volání kódu v doplňku VSTO z jazyka VBA
  Tento názorný postup ukazuje, jak vystavit objekt v doplňku VSTO pro jiná systém Microsoft Office řešení, včetně jazyk Visual Basic for Application (VBA) a COM VSTO doplňky.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 I když tento návod používá aplikaci Excel konkrétně, koncepce znázorněné v tomto návodu se vztahují na všechny šablony projektů doplňku VSTO poskytované aplikací Visual Studio.

 Tento návod znázorňuje následující úlohy:

- Definování třídy, která může být vystavena jiným řešením pro systém Office.

- Vystavení třídy jiným řešením pro systém Office.

- Volání metody třídy z kódu jazyka VBA.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat následující komponenty:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-the-vsto-add-in-project"></a>Vytvoření projektu doplňku VSTO
 Prvním krokem je vytvoření projektu doplňku VSTO pro Excel.

### <a name="to-create-a-new-project"></a>Vytvoření nového projektu

1. Pomocí šablony projektu doplňku VSTO pro Excel vytvořte projekt doplňku VSTO pro Excel s názvem **ExcelImportData**. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otevře soubor kódu **ThisAddIn. cs** nebo **ThisAddIn. vb** a přidá projekt **ExcelImportData** do **Průzkumník řešení**.

## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definovat třídu, kterou můžete vystavit jiným řešením pro systém Office
 Účelem tohoto návodu je zavolat do `ImportData` metody třídy s názvem `AddInUtilities` v doplňku VSTO z kódu VBA. Tato metoda zapíše řetězec do buňky a1 aktivního listu.

 Pokud chcete třídu vystavit `AddInUtilities` jiným řešením pro systém Office, je nutné, aby byla třída veřejná a viditelná pro model COM. Je také nutné vystavit rozhraní [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) ve třídě. Kód v následujícím postupu ukazuje jeden ze způsobů, jak tyto požadavky splnit. Další informace najdete v tématu [volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definování třídy, kterou můžete vystavit jiným řešením pro systém Office

1. V nabídce **projekt** klikněte na možnost **Přidat třídu**.

2. V dialogovém okně **Přidat novou položku** změňte název nové třídy na **AddInUtilities** a klikněte na **Přidat**.

     V editoru kódu se otevře soubor **AddInUtilities. cs** nebo **AddInUtilities. vb** .

3. Na začátek souboru přidejte následující direktivy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet2":::

4. Třídu nahraďte `AddInUtilities` následujícím kódem.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

     Tento kód zpřístupňuje `AddInUtilities` třídu modelu COM a přidá `ImportData` metodu do třídy. Aby bylo možné vystavit rozhraní [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) , `AddInUtilities` má třída také <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut a implementuje rozhraní, které je viditelné pro model COM.

## <a name="expose-the-class-to-other-office-solutions"></a>Vystavení třídy jiným řešením pro systém Office
 Pokud chcete třídu vystavit `AddInUtilities` jiným řešením pro systém Office, přepište <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodu ve `ThisAddIn` třídě. V přepsání vrátí instanci `AddInUtilities` třídy.

### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Vystavení třídy AddInUtilities jiným řešením pro systém Office

1. V **Průzkumník řešení** rozbalte položku **Excel**.

2. Klikněte pravým tlačítkem na **ThisAddIn. cs** nebo **ThisAddIn. vb** a pak klikněte na **Zobrazit kód**.

3. Do třídy `ThisAddIn` přidejte následující kód.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

4. V nabídce **Sestavení** klikněte na **Sestavit řešení**.

     Ověřte, že řešení je sestavení bez chyb.

## <a name="test-the-vsto-add-in"></a>Testování doplňku VSTO
 Do třídy můžete zavolat `AddInUtilities` z několika různých typů řešení pro systém Office. V tomto návodu použijete kód VBA v excelovém sešitu. Další informace o dalších typech řešení pro systém Office, které můžete použít také, najdete v tématu [kód volání v doplňcích VSTO z jiných řešení pro systém Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

### <a name="to-test-your-vsto-add-in"></a>Testování doplňku VSTO

1. Stisknutím klávesy **F5** spusťte projekt.

2. V Excelu uložte aktivní sešit jako excelový Macro-Enabled sešit (*. xlsm). Uložte ho do vhodného umístění, jako je například plocha.

3. Na pásu karet klikněte na kartu **vývojář** .

    > [!NOTE]
    > Pokud karta **vývojář** není zobrazená, musíte ji nejdřív zobrazit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. Ve skupině **kódu** klikněte na **Visual Basic**.

     Otevře se Visual Basic Editor.

5. V okně **projektu** poklikejte na **ThisWorkbook**.

     Otevře se soubor s kódem pro daný `ThisWorkbook` objekt.

6. Do souboru kódu přidejte následující kód VBA. Tento kód nejprve získá objekt COMAddIn, který představuje doplněk VSTO **ExcelImportData** . Potom kód použije vlastnost Object objektu COMAddIn k volání `ImportData` metody.

    ```vb
    Sub CallVSTOMethod()
        Dim addIn As COMAddIn
        Dim automationObject As Object
        Set addIn = Application.COMAddIns("ExcelImportData")
        Set automationObject = addIn.Object
        automationObject.ImportData
    End Sub
    ```

7. Stiskněte klávesu **F5**.

8. Ověřte, že do sešitu byl přidán nový **importovaný datový** list. Ověřte také, zda buňka a1 obsahuje řetězec **moje data**.

9. Ukončete aplikaci Excel.

## <a name="next-steps"></a>Další kroky
 Další informace o programování doplňků VSTO najdete v těchto tématech:

- Použijte `ThisAddIn` třídu k automatizaci hostitelské aplikace a provádění dalších úloh v projektech doplňku VSTO. Další informace najdete v tématu [programové doplňky VSTO](../vsto/programming-vsto-add-ins.md).

- Vytvoření vlastního podokna úloh v doplňku VSTO. Další informace najdete v tématech [vlastní podokna úloh](../vsto/custom-task-panes.md) a [Postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

- Přizpůsobení pásu karet v doplňku VSTO. Další informace najdete v tématech [Přehled pásu karet](../vsto/ribbon-overview.md) a [Postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).

## <a name="see-also"></a>Viz také
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Volání kódu v doplňcích VSTO z jiných řešení pro systém Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
