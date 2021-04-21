---
title: Volání kódu v doplňcích VSTO z jiných řešení pro systém Office
description: Přečtěte si, jak můžete vystavit objekt v doplňku VSTO do dalších řešení, včetně dalších systém Microsoft Office řešení.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2519c9d1a22eb6f5577a258fb9b465cfd7caafc2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826977"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>Volání kódu v doplňcích VSTO z jiných řešení pro systém Office
  Objekt v doplňku VSTO můžete vystavit jiným řešením, včetně dalších systém Microsoft Office řešení. To je užitečné v případě, že doplněk VSTO poskytuje službu, kterou chcete povolit pro používání jiných řešení. Pokud máte například doplněk VSTO pro systém Microsoft Office Excel, který provádí výpočty s finančními daty z webové služby, další řešení mohou provádět tyto výpočty voláním do doplňku Excel VSTO v době běhu.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 V tomto procesu jsou dva hlavní kroky:

- V doplňku VSTO vystavte objekt jiným řešením.

- V jiném řešení přejděte k objektu vystavenému doplňkem VSTO a zavolejte členy objektu.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>Typy řešení, které mohou volat kód v doplňku
 Objekt v doplňku VSTO můžete vystavit pro následující typy řešení:

- Kód jazyk Visual Basic for Application (VBA) v dokumentu, který je načten do stejného procesu aplikace jako doplněk VSTO.

- Přizpůsobení na úrovni dokumentu, která jsou načtena do stejného procesu aplikace jako doplněk VSTO.

- Další doplňky VSTO vytvořené pomocí šablon projektů Office v sadě Visual Studio.

- Doplňky VSTO COM (tj. doplňky VSTO, které rozhraní implementují <xref:Extensibility.IDTExtensibility2> přímo).

- Jakékoli řešení, které běží v jiném procesu než doplněk VSTO (tyto typy řešení se také nazývají *Klienti mimo proces*). Mezi ně patří aplikace, které automatizují aplikaci Office, například model Windows Forms nebo konzolovou aplikaci, a doplňky VSTO, které se načítají v jiném procesu.

## <a name="expose-objects-to-other-solutions"></a>Vystavení objektů jiným řešením
 K vystavení objektu v doplňku VSTO do dalších řešení proveďte v doplňku VSTO následující kroky:

1. Definujte třídu, kterou chcete zpřístupnit ostatním řešením.

2. Přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodu ve `ThisAddIn` třídě. Vrátí instanci třídy, kterou chcete zpřístupnit ostatním řešením.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>Definujte třídu, kterou chcete zpřístupnit ostatním řešením.
 Přinejmenším třída, kterou chcete zveřejnit, musí být veřejná, musí mít <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut nastaven na **hodnotu true** a musí vystavit rozhraní [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) .

 Doporučeným způsobem, jak vystavit rozhraní [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) , je provést následující kroky:

1. Definujte rozhraní, které deklaruje členy, které chcete zveřejnit pro jiná řešení. Toto rozhraní můžete definovat v projektu doplňku VSTO. Toto rozhraní však můžete definovat v samostatném projektu knihovny tříd, pokud chcete vystavit třídu pro řešení mimo jazyk VBA, aby řešení, která volají doplněk VSTO, mohla odkazovat na rozhraní bez odkazování na projekt doplňku VSTO.

2. Použijte <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut na toto rozhraní a nastavte tento atribut na **hodnotu true**.

3. Upravte třídu pro implementaci tohoto rozhraní.

4. Použijte <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atribut pro třídu a nastavte tento atribut na hodnotu **none** <xref:System.Runtime.InteropServices.ClassInterfaceType> výčtu.

5. Pokud chcete tuto třídu vystavit klientům mimo proces, může být nutné provést následující akce:

   - Odvodit třídu z <xref:System.Runtime.InteropServices.StandardOleMarshalObject> . Další informace najdete v tématu [vystavení tříd pro klienty mimo proces](#outofproc).

   - V projektu, kde definujete rozhraní, nastavte vlastnost **Register pro zprostředkovatele komunikace s objekty COM** . Tato vlastnost je nutná pouze v případě, že chcete klientům povolit použití předčasné vazby pro volání doplňku VSTO.

   Následující příklad kódu ukazuje `AddInUtilities` třídu s `ImportData` metodou, která může být volána jinými řešeními. Chcete-li zobrazit tento kód v kontextu většího návodu, viz [Návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs" id="Snippet3":::
   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb" id="Snippet3":::

### <a name="expose-classes-to-vba"></a>Vystavení tříd do VBA
 Když provedete výše uvedené kroky, kód VBA může volat pouze metody, které deklarujete v rozhraní. Kód VBA nemůže volat žádné jiné metody ve vaší třídě, včetně metod, které vaše třída získává ze základních tříd, jako je <xref:System.Object> .

 Rozhraní [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) můžete případně zveřejnit nastavením <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atributu na hodnotu Dispatch nebo AutoDual Value <xref:System.Runtime.InteropServices.ClassInterfaceType> výčtu. Pokud vystavíte rozhraní, nemusíte deklarovat metody v samostatném rozhraní. Kód VBA však může volat libovolné veřejné a nestatické metody ve vaší třídě, včetně metod získaných ze základních tříd, jako je <xref:System.Object> . Kromě toho mimoprocesové klienti, kteří používají předčasné vázání, nemohou volat vaši třídu.

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Vystavení tříd klientům mimo proces
 Pokud chcete vystavit třídu v doplňku VSTO pro mimoprocesové klienty, měli byste odvodit třídu z, <xref:System.Runtime.InteropServices.StandardOleMarshalObject> abyste zajistili, že klienti mimo proces můžou volat vystavený objekt doplňku VSTO. V opačném případě se pokusí získat instanci vystaveného objektu v klientském klientovi, který neočekávaně selže.

 Tato chyba je způsobena tím, že všechna volání do objektového modelu aplikace sady Office musí být provedena v hlavním vlákně uživatelského rozhraní, ale volání z klienta mimo proces do vašeho objektu se dostanou do libovolného vlákna RPC (vzdálené volání procedury). Mechanismus zařazování modelu COM v .NET Framework nebude přepínat vlákna a namísto hlavního vlákna uživatelského rozhraní se místo toho pokusí zařadit volání do objektu ve příchozím vlákně RPC. Je-li objekt instancí třídy, která je odvozena z <xref:System.Runtime.InteropServices.StandardOleMarshalObject> , jsou příchozí volání na objekt automaticky zařazena do vlákna, kde byl vystavený objekt vytvořen, což bude hlavní vlákno uživatelského rozhraní hostitelské aplikace.

 Další informace o použití vláken v řešeních pro systém Office najdete v tématu [Podpora vláken v systému Office](../vsto/threading-support-in-office.md).

### <a name="override-the-requestcomaddinautomationservice-method"></a>Přepsat metodu RequestComAddInAutomationService
 Následující příklad kódu ukazuje, jak přepsat <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> `ThisAddIn` třídu v doplňku VSTO. V příkladu se předpokládá, že jste definovali třídu s názvem `AddInUtilities` , kterou chcete zpřístupnit ostatním řešením. Chcete-li zobrazit tento kód v kontextu většího návodu, viz [Návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb" id="Snippet1":::

 Když je doplněk VSTO načtený, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] volá <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodu. Modul runtime přiřadí vrácený objekt k vlastnosti COMAddIn. Object <xref:Microsoft.Office.Core.COMAddIn> objektu, který představuje doplněk VSTO. Tento <xref:Microsoft.Office.Core.COMAddIn> objekt je k dispozici pro jiná řešení Office a pro řešení, která automatizují Office.

## <a name="access-objects-from-other-solutions"></a>Přístup k objektům z jiných řešení
 Pokud chcete volat vystavený objekt v doplňku VSTO, proveďte v řešení klienta následující kroky:

1. Získejte <xref:Microsoft.Office.Core.COMAddIn> objekt, který představuje vystavený doplněk VSTO. Klienti mají přístup ke všem dostupným doplňkům VSTO pomocí `Application.COMAddIns` vlastnosti v objektovém modelu hostitelské aplikace Office.

2. Přístup k vlastnosti COMAddIn. Object <xref:Microsoft.Office.Core.COMAddIn> objektu. Tato vlastnost vrátí vystavený objekt z doplňku VSTO.

3. Zavolejte členy vystaveného objektu.

   Způsob, jakým použijete návratovou hodnotu vlastnosti COMAddIn. Object, se liší pro klienty VBA a klienty mimo jazyk VBA. Pro klienty mimo procesy je potřeba další kód, aby se předešlo možnému konfliktu časování.

### <a name="access-objects-from-vba-solutions"></a>Přístup k objektům z řešení VBA
 Následující příklad kódu ukazuje, jak použít jazyk VBA k volání metody, která je vystavena doplňku VSTO. Toto makro VBA volá metodu s názvem `ImportData` , která je definována v doplňku VSTO s názvem **ExcelImportData**. Chcete-li zobrazit tento kód v kontextu většího návodu, viz [Návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).

```vb
Sub CallVSTOMethod()
    Dim addIn As COMAddIn
    Dim automationObject As Object
    Set addIn = Application.COMAddIns("ExcelImportData")
    Set automationObject = addIn.Object
    automationObject.ImportData
End Sub
```

### <a name="access-objects-from-non-vba-solutions"></a>Přístup k objektům z jiných řešení než VBA
 V řešení, které není v jazyce VBA, je nutné přetypovat hodnotu vlastnosti COMAddIn. Object na rozhraní, které implementuje, a poté můžete volat vystavené metody objektu rozhraní. Následující příklad kódu ukazuje, jak zavolat `ImportData` metodu z jiného doplňku VSTO, který byl vytvořen pomocí nástrojů pro vývojáře sady Office v sadě Visual Studio.

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

 V tomto příkladu, pokud se pokusíte přetypovat hodnotu vlastnosti COMAddIn. Object na `AddInUtilities` třídu, nikoli na `IAddInUtilities` rozhraní, kód vyvolá výjimku <xref:System.InvalidCastException> .

## <a name="see-also"></a>Viz také
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Návod: volání kódu v doplňku VSTO z jazyka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Postupy: vytváření projektů Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Přizpůsobení funkcí uživatelského rozhraní pomocí rozhraní rozšiřitelnosti](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
