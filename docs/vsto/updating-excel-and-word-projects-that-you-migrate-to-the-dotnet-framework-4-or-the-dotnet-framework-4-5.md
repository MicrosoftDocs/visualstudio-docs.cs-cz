---
title: Aktualizace projektu aplikace Excel nebo Word migrovány na .NET Framework 4/4,5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bc211f4d30359c885b22a45910363bbadca236f
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253722"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Aktualizace projektů aplikace Excel a Word, které migrujete do .NET Framework 4 nebo .NET Framework 4,5
  Pokud máte projekt aplikace Excel nebo Word, který používá některou z následujících funkcí, je nutné upravit kód, pokud je cílová architektura změněna na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější:

- [Metody GetVstoObject a HasVstoObject](#GetVstoObject)

- [Generované třídy v projektech na úrovni dokumentu](#generatedclasses)

- [model Windows Forms ovládací prvky v dokumentech](#winforms)

- [Události ovládacích prvků obsahu aplikace Word](#ccevents)

- [Třídy OLEObject a OLEControl](#ole)

- [Controls. Item (Object) – vlastnost](#itemproperty)

- [Kolekce, které jsou odvozeny z CollectionBase](#collections)

  Je také nutné odebrat `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` odkazy a `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` na třídu z projektů aplikace Excel, které jsou přecíleny na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Visual Studio neodstraní tento atribut ani odkaz na třídu za vás.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Odebrání atributu ExcelLocale1033 z projektů Excelu
 Byla odebrána z části sady Visual Studio 2010 Tools for Office runtime, která se používá pro řešení, která cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` Modul CLR (Common Language Runtime) v rozhraní [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a později vždy předává ID národního prostředí 1033 do objektového modelu aplikace Excel a tento atribut již nelze použít k zakázání tohoto chování. Další informace najdete v tématu [globalizace a lokalizace řešení pro Excel](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>Postup odebrání ExcelLocale1033Attribute

1. S projektem otevřeným v aplikaci Visual Studio otevřete **Průzkumník řešení**.

2. V uzlu **vlastnosti** (pro C#) nebo v uzlu **můj projekt** (pro Visual Basic) poklikejte na soubor kódu AssemblyInfo a otevře se v editoru kódu.

    > [!NOTE]
    > V Visual Basic projektů musíte kliknutím na tlačítko **Zobrazit všechny soubory** v **Průzkumník řešení** zobrazit soubor kódu AssemblyInfo.

3. Vyhledejte soubor `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` a buď ho odeberte ze souboru, nebo ho Odkomentujte.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Odebrat odkaz na třídu ExcelLocal1033Proxy
 Projekty, které byly vytvořeny pomocí nástrojů Microsoft Visual Studio 2005 pro systém Microsoft Office systém vytvoří instanci objektu aplikace Excel <xref:Microsoft.Office.Interop.Excel.Application> `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` pomocí třídy. Tato třída byla odebrána z části sady Visual Studio 2010 Tools for Office runtime, která se používá pro řešení, která cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější. Proto je nutné odebrat nebo komentovat řádek kódu, který odkazuje na tuto třídu.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Odebrání odkazu na třídu ExcelLocal1033Proxy

1. Otevřete projekt v aplikaci Visual Studio a pak otevřete **Průzkumník řešení**.

2. V **Průzkumník řešení**otevřete místní nabídku pro *ThisAddIn.cs* (pro C#) nebo *ThisAddIn. vb* (pro Visual Basic) a pak zvolte **Zobrazit kód**.

3. V editoru kódu v `VSTO generated code` oblasti odeberte nebo odkomentujte následující řádek kódu.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="GetVstoObject"></a>Aktualizace kódu, který používá metody GetVstoObject a HasVstoObject
 V projektech, které cílí na .NET Framework 3,5, `GetVstoObject` jsou `HasVstoObject` metody nebo k dispozici jako metody rozšíření v jednom z následujících nativních objektů v projektu <xref:Microsoft.Office.Interop.Word.Document>: <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, nebo <xref:Microsoft.Office.Interop.Excel.ListObject>. Při volání těchto metod není nutné předávat parametr. Následující příklad kódu ukazuje, jak použít metodu GetVstoObject v doplňku aplikace Word VSTO, která cílí na .NET Framework 3,5.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 V projektech, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na nebo novější, je nutné upravit kód pro přístup k těmto metodám jedním z následujících způsobů:

- K těmto metodám můžete přistupovat jako s metodami rozšíření <xref:Microsoft.Office.Interop.Word.Document>pro <xref:Microsoft.Office.Interop.Excel.Workbook>objekty <xref:Microsoft.Office.Interop.Excel.Worksheet>,, <xref:Microsoft.Office.Interop.Excel.ListObject> nebo. Nyní však musíte předat objektu vrácenému `Globals.Factory` vlastností těmto metodám.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Můžete případně přistupovat k těmto metodám objektu, který je vrácen `Globals.Factory` vlastností. Když k těmto metodám přistupujete tímto způsobem, musíte předat nativní objekt, který chcete pro metodu použít.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="generatedclasses"></a>Aktualizace kódu, který používá instance generovaných tříd v projektech na úrovni dokumentu
 V projektech na úrovni dokumentu, které cílí na .NET Framework 3,5, vygenerované třídy v projektech jsou odvozeny z následujících tříd v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>

  V projektech, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na nebo novější, jsou typy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] v uvedeném seznamu rozhraní místo tříd. Generované třídy v projektech, které cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo později, jsou odvozeny z následujících nových tříd [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]v:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

  Pokud kód v projektu odkazuje na instanci jedné z generovaných tříd jako základní třídu, která je odvozena z, je nutné upravit kód.

  Například v projektu excelového sešitu, který cílí na .NET Framework 3,5, může být pomocná metoda, která provádí určitou práci na instancích generovaných `Sheet` *n* tříd v projektu.

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

 Pokud změníte cíl projektu na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo novější, musíte provést jednu z následujících změn kódu:

- Upravte jakýkoli kód, který volá `DoSomethingToSheet` metodu pro <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> předání vlastnosti <xref:Microsoft.Office.Tools.Excel.WorksheetBase> objektu v projektu. Tato vlastnost vrací <xref:Microsoft.Office.Tools.Excel.Worksheet> objekt.

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- <xref:Microsoft.Office.Tools.Excel.WorksheetBase> Upravte parametr `DoSomethingToSheet` metody tak, aby byl místo toho očekáván objekt.

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

## <a name="winforms"></a>Aktualizace kódu, který používá model Windows Forms ovládacích prvků v dokumentech
 Je nutné přidat příkaz **using** (C#) nebo **Import** ( <xref:Microsoft.Office.Tools.Excel> Visual Basic) pro obor názvů nebo <xref:Microsoft.Office.Tools.Word> do horní části jakéhokoli souboru kódu, který používá vlastnost Controls pro přidání model Windows Forms ovládacích prvků do dokumentu nebo listu. různých.

 V projektech, které cílí na .NET Framework 3,5, jsou metody, které přidávají model Windows Forms ovládací prvky `AddButton` (například metoda), definovány <xref:Microsoft.Office.Tools.Excel.ControlCollection> v <xref:Microsoft.Office.Tools.Word.ControlCollection> třídách a.

 V projektech, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na nebo novější, jsou tyto metody rozšiřující metody, které jsou k dispozici ve vlastnosti Controls. Chcete-li použít tyto metody rozšíření, soubor kódu, ve kterém používáte metody, musí mít <xref:Microsoft.Office.Tools.Excel> příkaz **using** nebo **Imports** pro obor <xref:Microsoft.Office.Tools.Word> názvů nebo. Tento příkaz je vygenerován automaticky v nových projektech, které [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] cílí na nebo novější. Tento příkaz však není přidán automaticky v projektech, které cílí na .NET Framework 3,5, takže je nutné jej přidat při změny cílení projektu.

 Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="ccevents"></a>Aktualizace kódu, který zpracovává události ovládacího prvku obsahu aplikace Word
 V projektech, které cílí na .NET Framework 3,5, jsou události ovládacích prvků obsahu aplikace Word zpracovávány <xref:System.EventHandler%601> pomocí obecného delegáta. V projektech, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na nebo novější, jsou tyto události zpracovávány jinými delegáty.

 V následující tabulce jsou uvedeny události ovládacího prvku obsahu aplikace Word a delegáti, kteří jsou k nim přidruženi v [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] projektech, které cílí na nebo novější.

|Událost|Delegát pro použití v [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a novějších projektech|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="ole"></a>Aktualizace kódu, který používá třídy OLEObject a OLEControl
 V projektech, které cílí na .NET Framework 3,5, můžete přidat vlastní ovládací prvky (například model Windows Forms uživatelské ovládací prvky) do dokumentu nebo listu pomocí `Microsoft.Office.Tools.Excel.OLEObject` tříd a. `Microsoft.Office.Tools.Word.OLEControl`

 V projektech, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na nebo novější, byly tyto třídy nahrazeny <xref:Microsoft.Office.Tools.Excel.ControlSite> rozhraními <xref:Microsoft.Office.Tools.Word.ControlSite> a. Je nutné upravit kód, který odkazuje `Microsoft.Office.Tools.Excel.OLEObject` na `Microsoft.Office.Tools.Word.OLEControl` a místo toho, <xref:Microsoft.Office.Tools.Excel.ControlSite> aby <xref:Microsoft.Office.Tools.Word.ControlSite>odkazoval na a. Kromě nových názvů se tyto ovládací prvky chovají stejným způsobem jako v projektech, které cílí na .NET Framework 3,5.

 Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="itemproperty"></a>Aktualizace kódu, který používá vlastnost Controls. Item (Object)
 V projektech, které cílí na .NET Framework 3,5, můžete použít vlastnost Item (Object) třídy Microsoft. Office. Tools. Word. Document. Controls nebo `Microsoft.Office.Tools.Excel.Worksheet.Controls` Collection k určení, zda dokument nebo list má určený ovládací prvek.

 V projektech, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na nebo novější, byla z těchto kolekcí odebrána vlastnost Item (Object). Chcete-li zjistit, zda dokument nebo list obsahuje určený ovládací prvek, použijte místo toho metodu <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> Contains (System. Object) kolekce nebo. <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A>

 Další informace o kolekci dokumentů a listů ovládacích prvků najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="collections"></a>Aktualizace kódu, který používá kolekce odvozené z CollectionBase
 V projektech, které cílí na .NET Framework 3,5, je několik typů kolekcí [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] v odvozených <xref:System.Collections.CollectionBase> od `Microsoft.Office.Tools.Excel.ControlCollection`třídy, například `Microsoft.Office.Tools.SmartTagCollection`, a `Microsoft.Office.Tools.Word.ControlCollection`.

 V projektech, které cílí [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] na nebo novější, jsou nyní tyto typy kolekcí rozhraním, která nejsou <xref:System.Collections.CollectionBase>odvozena z. Někteří členové již nejsou k dispozici u těchto typů kolekcí, například <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>a <xref:System.Collections.CollectionBase.InnerList%2A>.

## <a name="see-also"></a>Viz také:
- [Migrace řešení Office na .NET Framework 4 nebo novější](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Ovládací prvky obsahu](../vsto/content-controls.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
