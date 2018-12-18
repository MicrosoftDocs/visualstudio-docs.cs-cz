---
title: Aktualizace projektů Excel a Word, které při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aeb36f92533992161e2c7fa4f7bbcd3537fd0ebc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919398"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizace projektů Excel a Word, které při migraci na rozhraní .NET Framework 4 nebo .NET Framework 4.5
  Pokud máte projekt aplikace Excel nebo Word, který používá některou z následujících funkcí, je třeba upravit kód, pokud Cílová architektura, která se změní na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější:  
  
- [GetVstoObject a HasVstoObject metody](#GetVstoObject)  
  
- [Generovaných tříd v projektech na úrovni dokumentu](#generatedclasses)  
  
- [Ovládací prvky Windows Forms v dokumentech](#winforms)  
  
- [Události ovládacích prvků obsahu aplikace Word](#ccevents)  
  
- [Objekt OLE a OLEControl třídy](#ole)  
  
- [Vlastnost Controls.Item(Object)](#itemproperty)  
  
- [Kolekce, které jsou odvozeny z CollectionBase](#collections)  
  
  Je potřeba taky odebrat `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` a odkazy na `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` třídy z projekty aplikace Excel, které se změnilo na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Visual Studio neodebere tento atribut nebo odkaz na třídy za vás.  
  
## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Odebrat atribut ExcelLocale1033 z projekty aplikace Excel  
 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` Byla odebrána z část Visual Studio 2010 Tools for Office runtime, který se používá pro řešení, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Common language runtime (CLR) v [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a později vždycky předá národní prostředí ID 1033 k objektovému modelu Excelu kde už tento atribut slouží pro toto chování zakázat. Další informace najdete v tématu [globalizace a lokalizace řešení pro Excel](../vsto/globalization-and-localization-of-excel-solutions.md).  
  
### <a name="to-remove-the-excellocale1033attribute"></a>Chcete-li odebrat ExcelLocale1033Attribute  
  
1.  V sadě Visual Studio po otevření projektu otevřete **Průzkumníka řešení**.  
  
2.  V části **vlastnosti** uzel (pro C#) nebo **Můj projekt** uzel (Visual Basic), poklikejte na soubor AssemblyInfo kódu a otevře se v editoru kódu.  
  
    > [!NOTE]  
    >  V projektech Visual Basic, musíte kliknout na **zobrazit všechny soubory** tlačítko **Průzkumníka řešení** zobrazíte kód souboru AssemblyInfo.  
  
3.  Vyhledejte `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` a odeberte ze souboru nebo ji komentář.  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Odebrat odkaz na třídu ExcelLocal1033Proxy  
 Projekty, které byly vytvořeny pomocí Microsoft Visual Studio 2005 Tools pro Microsoft Office System vytvořit instanci v aplikaci Excel <xref:Microsoft.Office.Interop.Excel.Application> s použitím `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` třídy. Tato třída se odebral z část Visual Studio 2010 Tools for Office runtime, který se má použít pro řešení, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Musíte proto odstranit nebo okomentovat řádek kódu, který odkazuje tato třída.  
  
### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Chcete-li odebrat odkaz na třídu ExcelLocal1033Proxy  
  
1.  Otevřete projekt v sadě Visual Studio a pak otevřete **Průzkumníka řešení**.  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku pro *ThisAddin.cs* (pro C#) nebo *ThisAddin.vb* (pro jazyk Visual Basic) a klikněte na tlačítko **zobrazit kód** .  
  
3.  V editoru kódu v `VSTO generated code` oblasti, odstranit nebo okomentovat následující řádek kódu.  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> Aktualizujte kód, který používá metody GetVstoObject a HasVstoObject  
 V projektech cílených rozhraní .NET Framework 3.5 `GetVstoObject` nebo `HasVstoObject` metody jsou k dispozici jako metody rozšíření v jednom z následujících nativních objektů v projektu: <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, nebo <xref:Microsoft.Office.Interop.Excel.ListObject>. Při volání těchto metod, není potřeba předat parametr. Následující příklad kódu ukazuje, jak použít metodu GetVstoObject VSTO pro Word Add-in, který cílí na rozhraní .NET Framework 3.5.  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, musíte upravit kód pro přístup k tyto metody v jednom z následujících způsobů:  
  
- Budete k němu přístup tyto metody jako metody rozšíření na <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, nebo <xref:Microsoft.Office.Interop.Excel.ListObject> objekty. Však musí nyní předat objekt vrácený rutinou `Globals.Factory` vlastnost těchto metod.  
  
  ```vb  
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
  ```  
  
  ```csharp  
  Microsoft.Office.Tools.Word.Document vstoDocument =   
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
  ```  
  
- Můžete také přístup k tyto metody pro objekt, který je vrácený `Globals.Factory` vlastnost. Při přístupu k tyto metody tímto způsobem, musíte předat nativní objekt, který chcete rozšířit do metody.  
  
  ```vb  
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
  ```  
  
  ```csharp  
  Microsoft.Office.Tools.Word.Document vstoDocument =   
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
  ```  
  
  Další informace najdete v tématu [rozšíření Wordových dokumentů a Excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
##  <a name="generatedclasses"></a> Aktualizujte kód, který používá výskyty vygenerovaných tříd v projektech na úrovni dokumentu  
 Projekty na úrovni dokumentu, které jsou cíleny rozhraní .NET Framework 3.5, odvozovat vygenerovaných tříd v projektech následující třídy v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
  V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, typy v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] uvedené výše budou rozhraním namísto třídy. Generované třídy v projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později jsou odvozeny z následující nové třídy v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
  Pokud kód ve vašem projektu odkazuje na instanci jednoho z vygenerovaných tříd jako základní třída, která je odvozena z, je třeba upravit kód.  
  
  V projektu Excelový sešit, který cílí na rozhraní .NET Framework 3.5, může třeba mít pomocnou metodu, která provede nějakou práci na instancích generované `Sheet` *n* tříd ve vašem projektu.  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)  
    ' Do something to the worksheet object.  
End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)  
{  
    // Do something to the worksheet object.  
}  
```  
  
 Výsledkem změny cílení projekt tak, aby [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, je nutné provést jednu z následujících změn kódu:  
  
-   Upravit veškerý kód, který volá `DoSomethingToSheet` metoda k předání <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.WorksheetBase> ve vašem projektu. Tato vlastnost vrátí <xref:Microsoft.Office.Tools.Excel.Worksheet> objektu.  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   Upravit `DoSomethingToSheet` parametr metody očekávat <xref:Microsoft.Office.Tools.Excel.WorksheetBase> namísto toho objekt.  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)  
        ' Do something to the worksheet object.  
    End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)  
    {  
        // Do something to the worksheet object.  
    }  
    ```  
  
##  <a name="winforms"></a> Aktualizujte kód, který používá ovládací prvky Windows Forms v dokumentech  
 Je nutné přidat **pomocí** (C#) nebo **importy** – příkaz (Visual Basic) pro <xref:Microsoft.Office.Tools.Excel> nebo <xref:Microsoft.Office.Tools.Word> oboru názvů k hornímu okraji jakýkoli soubor s kódem, který používá vlastnost ovládací prvky pro přidání Windows Ovládací prvky k dokumentu nebo listu Forms prostřednictvím kódu programu.  
  
 V projektech cílených rozhraní .NET Framework 3.5, metody, které přidávají ovládací prvky Windows Forms (například `AddButton` metoda) jsou definovány v <xref:Microsoft.Office.Tools.Excel.ControlCollection> a <xref:Microsoft.Office.Tools.Word.ControlCollection> třídy.  
  
 V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později, tyto metody jsou metody rozšíření, které jsou k dispozici na vlastnosti ovládacích prvků. Používat tyto metody rozšíření, musí mít soubor kódu, ve kterém můžete použít metody **pomocí** nebo **importy** příkaz <xref:Microsoft.Office.Tools.Excel> nebo <xref:Microsoft.Office.Tools.Word> oboru názvů. Tento příkaz se vygeneruje automaticky v nových projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Ale tento příkaz není automaticky přidáno v projektech, které se zaměřují rozhraní .NET Framework 3.5, proto je nutné přidat při jejich cíl změnit projekt.  
  
 Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="ccevents"></a> Aktualizujte kód, který zpracovává události ovládacích prvků obsahu aplikace Word  
 V projektech cílených rozhraní .NET Framework 3.5, jsou zpracovávány událostí ovládacích prvků obsahu aplikace Word Obecné <xref:System.EventHandler%601> delegovat. V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později, tyto události jsou zpracovávány jiných delegátů.  
  
 Následující tabulka uvádí události ovládacího prvku obsahu aplikace Word a delegáty, které jsou spojeny s nimi v projektech cílených [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější.  
  
|Událost|Delegát pro použití v [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a novější projekty|  
|-----------| - |  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> Aktualizujte kód, který používá objekt OLE a OLEControl třídy  
 V projektech cílených rozhraní .NET Framework 3.5, můžete přidat vlastní ovládací prvky (například uživatelské ovládací prvky Windows Forms) k dokumentu nebo sešitu pomocí `Microsoft.Office.Tools.Excel.OLEObject` a `Microsoft.Office.Tools.Word.OLEControl` třídy.  
  
 V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později, tyto třídy byly nahrazeny <xref:Microsoft.Office.Tools.Excel.ControlSite> a <xref:Microsoft.Office.Tools.Word.ControlSite> rozhraní. Je třeba upravit kód, který odkazuje na `Microsoft.Office.Tools.Excel.OLEObject` a `Microsoft.Office.Tools.Word.OLEControl` místo o <xref:Microsoft.Office.Tools.Excel.ControlSite> a <xref:Microsoft.Office.Tools.Word.ControlSite>. Tyto ovládací prvky než nové názvy se chovají stejně, jako v projektech cílených rozhraní .NET Framework 3.5.  
  
 Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="itemproperty"></a> Aktualizujte kód, který používá vlastnost Controls.Item(Object)  
 V projektech cílených rozhraní .NET Framework 3.5, můžete použít vlastnost Item(Object) Microsoft.Office.Tools.Word.Document.Controls nebo `Microsoft.Office.Tools.Excel.Worksheet.Controls` kolekce slouží k určení, zda zadaný ovládací prvek má dokumentu nebo sešitu.  
  
 V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později, byla odebrána vlastnost Item(Object) z těchto kolekcí. Pokud chcete zjistit, zda dokumentu nebo sešitu obsahuje zadaný ovládací prvek, použijte metodu Contains(System.Object) <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> kolekce místo.  
  
 Další informace o kolekci ovládacích prvků dokumentů a listy, naleznete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="collections"></a> Aktualizujte kód, který používá kolekce, které jsou odvozeny z CollectionBase  
 V projektech cílených rozhraní .NET Framework 3.5, napíše několik kolekcí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] odvozovat <xref:System.Collections.CollectionBase> třídy, jako například `Microsoft.Office.Tools.SmartTagCollection`, `Microsoft.Office.Tools.Excel.ControlCollection`, a `Microsoft.Office.Tools.Word.ControlCollection`.  
  
 V projektech, které se zaměřují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, jsou tyto typy kolekcí nyní rozhraní, která není odvozena od <xref:System.Collections.CollectionBase>. Některé členy už nejsou k dispozici na tyto typy kolekcí, jako například <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>, a <xref:System.Collections.CollectionBase.InnerList%2A>.  
  
## <a name="see-also"></a>Viz také:  
 [Migrace řešení Office na rozhraní .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Ovládací prvky obsahu](../vsto/content-controls.md)   
 [Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  