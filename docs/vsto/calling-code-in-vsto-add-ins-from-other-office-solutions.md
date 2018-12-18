---
title: Volání kódu v doplňcích VSTO z jiných řešení pro Office
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
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9290fcdd705f6f38b4b7e91e46d5b635f1e309ff
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248095"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Volání kódu v doplňcích VSTO z jiných řešení pro Office
  Objekt můžete zveřejnit v doplňku VSTO pro ostatní řešení, včetně jiných řešení pro Microsoft Office. To je užitečné, pokud váš doplněk VSTO poskytuje službu, kterou chcete povolit použití jiných řešení. Například pokud máte doplňku VSTO pro Microsoft Office Excel, která provádí výpočty finančních dat z webové služby, jiná řešení provádět tyto výpočty pomocí volání do doplňku VSTO pro Excel za běhu.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 V tomto procesu existují dva hlavní kroky:  
  
-   V vašeho doplňku VSTO zveřejněte objektu do jiných řešení.  
  
-   V jiné řešení přístupu k objektu vystavené vašeho doplňku VSTO a volání členy objektu.  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Typy řešení, které můžete volat kódu v doplňku  
 Objekt v doplňku VSTO pro tyto druhy řešení můžete zveřejnit:  
  
-   Kód Visual Basic for Applications (VBA) v dokumentu, který je načten do procesu aplikace jako doplňku VSTO.  
  
-   Přizpůsobení na úrovni dokumentu, které jsou načteny v rámci stejného procesu aplikace jako doplňku VSTO.  
  
-   Další doplňků VSTO vytvořené s použitím šablony projektů pro Office v sadě Visual Studio.  
  
-   Doplňky VSTO modelu COM (to znamená, doplňků VSTO, které implementují <xref:Extensibility.IDTExtensibility2> přímo rozhraní).  
  
-   Jakékoli řešení, které běží v jiného procesu než doplňku VSTO (tyto druhy řešení se také nazývají *klientům mimo proces*). Patří mezi ně aplikace, které automatizují aplikace Office, jako jsou Windows Forms nebo konzolové aplikace a doplňků VSTO, které jsou načteny v jiném procesu.  
  
## <a name="expose-objects-to-other-solutions"></a>Vystavení objektů do jiných řešení  
 K vystavení objektu v doplňku VSTO pro ostatní řešení, proveďte následující kroky v doplňku VSTO:  
  
1.  Definice třídy, kterou chcete zpřístupnit další řešení.  
  
2.  Přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodu `ThisAddIn` třídy. Vrací instanci třídy, kterou chcete zpřístupnit další řešení.  
  
### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Definice třídy, které chcete zpřístupnit pro ostatní řešení  
 Minimálně musí být třídu, kterou chcete vystavit veřejný, musí mít <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut nastaven na **true**, a musí zveřejnit [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) rozhraní.  
  
 Doporučeným způsobem, jak vystavit [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) rozhraní je provést následující kroky:  
  
1. Definujte rozhraní, který deklaruje členy, které chcete zpřístupnit další řešení. Toto rozhraní můžete definovat v projektu doplňku VSTO. Můžete ale chtít definovat toto rozhraní v projektu knihovny samostatné třídy, pokud chcete vystavit třídy, která se bez VBA řešení tak, aby řešení, které volají doplňku VSTO může odkazovat na rozhraní bez odkazování na projekt doplňku VSTO.  
  
2. Použít <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut k tomuto rozhraní a nastavte tento atribut **true**.  
  
3. Upravte třídu pro implementaci tohoto rozhraní.  
  
4. Použít <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut do vaší třídy a nastavte tento atribut **žádný** hodnotu <xref:System.Runtime.InteropServices.ClassInterfaceType> výčtu.  
  
5. Pokud chcete zpřístupnit tuto třídu klientům mimo proces, budete pravděpodobně potřebovat provést následující kroky:  
  
   -   Odvodit třídu z <xref:System.Runtime.InteropServices.StandardOleMarshalObject>. Další informace najdete v tématu [vystavit třídy klientům mimo proces](#outofproc).  
  
   -   Nastavte **zaregistrovat pro interoperabilitu COM** vlastnost v projektu, ve kterém definujete rozhraní. Tato vlastnost je nutné pouze v případě, že chcete povolit klientům používat časná vazba provést volání do doplňku VSTO.  
  
   Následující příklad kódu ukazuje `AddInUtilities` třídy s `ImportData` metodu, která je možné vyvolat v jiných řešení. Tento kód v rámci větší názorného postupu najdete v tématu [názorný postup: Volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="expose-classes-to-vba"></a>Vystavení třídy pro jazyk VBA  
 Při provádění kroků, které jste zadali výše pro kód VBA může volat pouze metody, které deklarujete v rozhraní. VBA kód nelze volat všechny ostatní metody ve třídě, včetně metod, které vaše třída získává ze základní třídy, jako <xref:System.Object>.  
  
 Případně můžete zveřejnit [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) rozhraní tak, že nastavíte <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut vazby AutoDispatch nebo AutoDual hodnotu <xref:System.Runtime.InteropServices.ClassInterfaceType> výčtu. Pokud je zveřejnit rozhraní, nemají deklarovat metody v samostatných rozhraní. Však můžete volat všechny veřejné a nestatické metody ve třídě, včetně metod získaných ze základních tříd, jako kód VBA <xref:System.Object>. Kromě toho mimo proces klienty, kteří používají časná vazba nejde volat metodu vaší třídy.  
  
###  <a name="outofproc"></a> Vystavení třídy klientům mimo proces  
 Pokud chcete vystavit třídu v doplňku VSTO klientům mimo proces, by měl být odvozen ze třídy <xref:System.Runtime.InteropServices.StandardOleMarshalObject> zajistit, že klienti mimo proces mohou volat vystavené objektu doplňku VSTO. V opačném případě může neočekávaně selhat pokusy o získání instance objektu zveřejněné v klientovi mimo proces.  
  
 Tato chyba je vzhledem k tomu, že všechna volání do objektového modelu aplikace Office se musí provádět v hlavním vlákně uživatelského rozhraní, ale volání z klienta na více instancí procesu do objektu dorazí na libovolné vlákno RPC (vzdálené volání procedur). Mechanismu zařazování modelu COM v rozhraní .NET Framework nebude přepnout vlákna a místo toho se pokusí k zařazování volání objektu na příchozí vlákno RPC místo hlavního vlákna uživatelského rozhraní. Pokud vaše je objekt instancí třídy, která je odvozena z <xref:System.Runtime.InteropServices.StandardOleMarshalObject>, příchozí volání do objektu, jsou automaticky zařazeny do vlákna kde byl vytvořen vystavené objektu, který může mít hlavní vlákno uživatelského rozhraní hostitelské aplikace.  
  
 Další informace o používání vláken v řešeních pro systém Office naleznete v tématu [podpora v systému Office práce s vlákny](../vsto/threading-support-in-office.md).  
  
### <a name="override-the-requestcomaddinautomationservice-method"></a>Potlačí metodu RequestComAddInAutomationService  
 Následující příklad kódu ukazuje, jak přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> v `ThisAddIn` třídy v doplňku VSTO. Příklad předpokládá, že jste definovali třídu s názvem `AddInUtilities` , kterou chcete zpřístupnit další řešení. Tento kód v rámci větší názorného postupu najdete v tématu [názorný postup: Volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 Doplněk VSTO je načtena, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] volání <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. Modul runtime přiřadí vlastnost COMAddIn.Object vráceného objektu <xref:Microsoft.Office.Core.COMAddIn> objekt, který reprezentuje doplňku VSTO. To <xref:Microsoft.Office.Core.COMAddIn> objekt je k dispozici pro ostatní řešení pro Office a na řešení, které automatizují Office.  
  
## <a name="access-objects-from-other-solutions"></a>Přístup k objektům z jiných řešení  
 Volání vystavené objektu v doplňku VSTO, proveďte následující kroky v řešení pro klienta:  
  
1. Získejte <xref:Microsoft.Office.Core.COMAddIn> objekt, který reprezentuje zveřejněné doplňku VSTO. Klienti mohou přistupovat ke všem Add in k dispozici VSTO pomocí `Application.COMAddIns` vlastnost v modelu objektu hostitele aplikace Office.  
  
2. Přístup k vlastnosti COMAddIn.Object <xref:Microsoft.Office.Core.COMAddIn> objektu. Tato vlastnost vrátí objekt vystavené z doplňku VSTO.  
  
3. Volejte členy zveřejněné objektu.  
  
   Způsob, jak použít návratová hodnota vlastnosti COMAddIn.Object se liší pro klienty VBA a jiných VBA. Klientům mimo proces dodatečný kód je nezbytný, aby se zabránilo možné časování.  
  
### <a name="access-objects-from-vba-solutions"></a>Přístup k objektům z jazyka VBA řešení  
 Následující příklad kódu ukazuje, jak používat VBA pro volání metody, který je zveřejněný prostřednictvím doplňku VSTO. Toto makro VBA volá metodu s názvem `ImportData` , který je definován v VSTO doplňku, který je pojmenován **ExcelImportData**. Tento kód v rámci větší názorného postupu najdete v tématu [názorný postup: Volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
```vb
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="access-objects-from-non-vba-solutions"></a>Přístup k objektům z řešení bez VBA  
 V jiných VBA řešení musíte přetypovat COMAddIn.Object hodnoty vlastnosti, které implementuje rozhraní a pak můžete volat metody vystavené pro objekt rozhraní. Následující příklad kódu ukazuje, jak volat `ImportData` metodu z jiné VSTO doplňku, který byl vytvořen pomocí nástroje Office developer tools v sadě Visual Studio.  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 V tomto příkladu, pokud se pokusíte převést hodnotu vlastnosti COMAddIn.Object, která má `AddInUtilities` třídy místo `IAddInUtilities` rozhraní, vyvolají kód <xref:System.InvalidCastException>.  
  
## <a name="see-also"></a>Viz také:  
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Návod: Volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Postupy: Vytvářet projekty pro Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Přizpůsobení funkcí uživatelského rozhraní pomocí rozšiřujících rozhraní](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  
