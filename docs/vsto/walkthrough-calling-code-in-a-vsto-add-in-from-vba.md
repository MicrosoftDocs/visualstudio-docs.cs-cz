---
title: 'Návod: Volání kódu v doplňku VSTO z jazyka VBA'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e46cf9032cae7d6400822be7d72394a7845314f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843818"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Návod: Volání kódu v doplňku VSTO z jazyka VBA
  Tento návod ukazuje, jak vystavit objektu v doplňku VSTO do jiných řešení pro Microsoft Office, včetně jazyka Visual Basic for Applications (VBA) a doplňky modelu COM VSTO.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 I když tento návod používá konkrétně aplikace Excel, koncepty jsme vám ukázali podle návodu platí pro všechny doplňku VSTO šablona projektu poskytovaný sadou Visual Studio.  
  
 Tento návod znázorňuje následující úlohy:  
  
- Definuje třídu, která by bylo možné vystavit do jiných řešení pro Office.  
  
- Vystavení třídy do jiných řešení pro Office.  
  
- Volání metody třídy z jazyka VBA kód.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-the-vsto-add-in-project"></a>Vytvoření projektu doplňku VSTO  
 Prvním krokem je vytvoření projektu doplňku VSTO pro Excel.  
  
### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1.  Vytvoření projektu doplňku VSTO pro Excel s názvem **ExcelImportData**, pomocí šablony projektu doplňku VSTO v Excelu. Další informace najdete v tématu [postupy: vytváření projektů pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otevře **ThisAddIn.cs** nebo **ThisAddIn.vb** soubor kódu a přidá **ExcelImportData** projektu **Průzkumníka řešení**.  
  
## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Definujte třídu, která můžete zpřístupnit pro ostatní řešení pro Office  
 Účelem tohoto návodu je volat `ImportData` metoda třídy s názvem `AddInUtilities` v doplňku VSTO z jazyka VBA kód. Tato metoda zapíše řetězec do buňky A1 aktivního listu.  
  
 Zveřejnit `AddInUtilities` třídy do jiných řešení pro Office, je třeba třídu veřejné a zobrazit v modelu COM. Také musí vystavit [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) rozhraní ve třídě. Kód v následujícím postupu ukazuje jeden způsob, jak tyto požadavky splňují. Další informace najdete v tématu [volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Chcete-li definovat třídu, která mohou vystavit do jiných řešení pro Office  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat třídu**.  
  
2.  V **přidat novou položku** dialogové okno pole, změňte název nové třídy, která se **AddInUtilities**a klikněte na tlačítko **přidat**.  
  
     **AddInUtilities.cs** nebo **AddInUtilities.vb** soubor se otevře v editoru kódu.  
  
3.  Na začátek souboru přidejte následující příkazy.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]  
  
4.  Nahraďte `AddInUtilities` třídy následujícím kódem.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
     Tento kód provede `AddInUtilities` třídy viditelné modelu COM, a přidá `ImportData` metodu do třídy. Zveřejnit [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) rozhraní, `AddInUtilities` třída má také <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut který implementuje rozhraní, která je viditelná modelu COM.  
  
## <a name="expose-the-class-to-other-office-solutions"></a>Vystavení třídy do jiných řešení pro Office  
 Vystavit `AddInUtilities` třídy do jiných řešení pro Office, přepište <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodu `ThisAddIn` třídy. V přepsání, vracet instanci `AddInUtilities` třídy.  
  
### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>K vystavení AddInUtilities třídy do jiných řešení pro Office  
  
1.  V **Průzkumníka řešení**, rozbalte **Excel**.  
  
2.  Klikněte pravým tlačítkem na **ThisAddIn.cs** nebo **ThisAddIn.vb**a potom klikněte na tlačítko **zobrazit kód**.  
  
3.  Přidejte následující kód, který `ThisAddIn` třídy.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
4.  Na **sestavení** nabídky, klikněte na tlačítko **sestavit řešení**.  
  
     Ověřte, že řešení sestaví bez chyb.  
  
## <a name="test-the-vsto-add-in"></a>Testování doplňku VSTO  
 Můžete volat `AddInUtilities` třídy z několika různých typů řešení pro systém Office. V tomto názorném postupu použijete kód VBA v sešitu aplikace Excel. Další informace o ostatních typech řešení pro Office můžete také použít, najdete v části [volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-test-your-vsto-add-in"></a>K otestování vašeho doplňku VSTO  
  
1.  Stisknutím klávesy **F5** ke spuštění projektu.  
  
2.  V aplikaci Excel aktivní sešit uložte jako sešit Excel Macro-Enabled (*.xlsm). Uložte ho na místě, například na plochu.  
  
3.  Na pásu karet klikněte na tlačítko **Developer** kartu.  
  
    > [!NOTE]  
    >  Pokud **Developer** karta není zobrazena, musíte ji nejdříve zobrazit. Další informace najdete v tématu [postupy: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  V **kód** klikněte na možnost **jazyka Visual Basic**.  
  
     Otevře se Editor jazyka Visual Basic.  
  
5.  V **projektu** okna, dvakrát klikněte na panel **ThisWorkbook**.  
  
     V souboru kódu `ThisWorkbook` objektu se otevře.  
  
6.  Přidejte následující kód VBA do souboru kódu. Tento kód nejprve načte COMAddIn objekt, který představuje **ExcelImportData** doplňku VSTO. Potom tento kód použije objekt vlastnosti objektu COMAddIn volat `ImportData` metody.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim addIn As COMAddIn  
        Dim automationObject As Object  
        Set addIn = Application.COMAddIns("ExcelImportData")  
        Set automationObject = addIn.Object  
        automationObject.ImportData  
    End Sub  
    ```  
  
7.  Stisknutím klávesy **F5**.  
  
8.  Ověřte, že nový **importovat Data** list je přidaný do sešitu. Dál ověřte tuto buňku A1 obsahuje řetězec **jedná se o Moje data**.  
  
9. Ukončete aplikaci Excel.  
  
## <a name="next-steps"></a>Další kroky  
 Další informace o programování doplňků VSTO z těchto témat:  
  
-   Použití `ThisAddIn` třídy k automatizaci hostitelská aplikace a provádění dalších úloh v projekty doplňku VSTO. Další informace najdete v tématu [doplňků Program VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Vytvoření vlastního podokna úloh v doplňku VSTO. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md) a [postupy: Přidání vlastního podokna úloh do aplikace](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Přizpůsobení pásu karet v doplňku VSTO. Další informace najdete v tématu [přehled pásu karet](../vsto/ribbon-overview.md) a [postupy: Začínáme s přizpůsobením pásu karet](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## <a name="see-also"></a>Viz také:  
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Volání kódu v doplňcích VSTO z jiných řešení pro Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Přizpůsobení funkcí uživatelského rozhraní pomocí rozšiřujících rozhraní](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  