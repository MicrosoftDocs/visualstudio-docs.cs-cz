---
title: Rozšiřování dokumentů aplikace Word & excelových sešitů v doplňcích VSTO za běhu
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a80fc10690691e8bd923f9c98270b162e7063ffb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253669"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu
  Doplněk VSTO můžete použít k přizpůsobení dokumentů aplikace Word a sešitů aplikace Excel následujícími způsoby:

- Přidejte spravované ovládací prvky do libovolného otevřeného dokumentu nebo listu.

- Převeďte existující objekt seznamu v excelovém listu na rozšířený <xref:Microsoft.Office.Tools.Excel.ListObject> , který zpřístupňuje události a který je možné svázat s daty pomocí modelu model Windows Forms datové vazby.

- Přístup k událostem na úrovni aplikace, které jsou zpřístupněny v aplikacích Word a Excel pro konkrétní dokumenty, sešity a listy.

  Chcete-li použít tuto funkci, vygenerujete objekt v době běhu, který rozšiřuje dokument nebo sešit.

  **Platí pro:** Informace v tomto článku se vztahují na projekty doplňku VSTO v následujících aplikacích: Aplikace Excel a Word. Další informace najdete v tématu [dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

## <a name="generate-extended-objects-in-vsto-add-ins"></a>Generování rozšířených objektů v doplňcích VSTO
 *Rozšířené objekty* jsou instance typů poskytované modulem runtime Visual Studio Tools for Office, které přidávají funkce do objektů, které existují nativně v aplikacích Word nebo Excel Object Model (tzv. *nativní objekty Office*). Chcete-li vygenerovat rozšířený objekt pro objekt Word nebo Excel, použijte `GetVstoObject` metodu. Při prvním volání `GetVstoObject` metody pro zadaný objekt Word nebo Excel vrátí nový objekt, který rozšiřuje zadaný objekt. Pokaždé, když zavoláte metodu a určíte stejný objekt Word nebo Excel, vrátí se stejný rozšířený objekt.

 Typ rozšířeného objektu má stejný název jako typ nativního objektu Office, ale typ je definován v <xref:Microsoft.Office.Tools.Excel> oboru názvů nebo. <xref:Microsoft.Office.Tools.Word> Například pokud voláte `GetVstoObject` metodu pro <xref:Microsoft.Office.Interop.Word.Document> rozšiřování objektu <xref:Microsoft.Office.Tools.Word.Document> , metoda vrátí objekt.

 `GetVstoObject` Metody jsou určeny pro použití hlavně v projektech doplňku VSTO. Tyto metody můžete použít také v projektech na úrovni dokumentu, ale chovají se odlišně a mají méně použití.

 Chcete-li zjistit, zda rozšířený objekt již byl vygenerován pro určitý nativní objekt Office, použijte `HasVstoObject` metodu. Další informace najdete v tématu [určení, zda byl objekt Office rozšířen](#HasVstoObject).

### <a name="generate-host-items"></a>Generovat položky hostitele
 <xref:Microsoft.Office.Interop.Excel.Workbook> <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Word.Document>Použijete-li prorozšiřováníobjektunaúrovnidokumentu(toznamená,,nebo),vrácenýobjektsenazýváHostitelskápoložka.`GetVstoObject` Položka hostitele je typ, který může obsahovat další objekty, včetně dalších rozšířených objektů a ovládacích prvků. Podobá se odpovídajícímu typu v rámci primárního definičního sestavení (Word nebo Excel), ale má další funkce. Další informace o položkách hostitelů naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

 Jakmile vygenerujete hostitelskou položku, můžete ji použít k přidání spravovaných ovládacích prvků do dokumentu, sešitu nebo listu. Další informace najdete v tématu [Přidání spravovaných ovládacích prvků do dokumentů a listů](#AddControls).

#### <a name="to-generate-a-host-item-for-a-word-document"></a>Vygenerování položky hostitele pro wordový dokument

- Následující příklad kódu ukazuje, jak vygenerovat hostitelskou položku pro aktivní dokument.

     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]

#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Vygenerování položky hostitele pro excelový sešit

- Následující příklad kódu ukazuje, jak vygenerovat hostitelskou položku pro aktivní sešit.

     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]

#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Vygenerování položky hostitele pro excelový list

- Následující příklad kódu ukazuje, jak vygenerovat hostitelskou položku pro aktivní list v projektu.

     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]

### <a name="generate-listobject-host-controls"></a>Generovat ovládací prvky hostitele ListObject
 Použijete `GetVstoObject` -li metodu pro <xref:Microsoft.Office.Interop.Excel.ListObject>rozšiřování <xref:Microsoft.Office.Tools.Excel.ListObject>, metoda vrátí. Obsahuje všechny funkce původního <xref:Microsoft.Office.Interop.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Má také další funkce a může být svázán s daty pomocí modelu model Windows Forms datové vazby. Další informace naleznete v tématu [ListObject Control](../vsto/listobject-control.md).

#### <a name="to-generate-a-host-control-for-a-listobject"></a>Vygenerování hostitelského ovládacího prvku pro ListObject

- Následující příklad kódu ukazuje, jak vygenerovat <xref:Microsoft.Office.Tools.Excel.ListObject> pro první <xref:Microsoft.Office.Interop.Excel.ListObject> v aktivním listu v projektu.

     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]

### <a name="AddControls"></a>Přidání spravovaných ovládacích prvků do dokumentů a listů
 Po vygenerování <xref:Microsoft.Office.Tools.Word.Document> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet>můžete do dokumentu nebo listu přidat ovládací prvky, které tyto rozšířené objekty reprezentují. Chcete-li přidat ovládací prvky `Controls` , použijte vlastnost <xref:Microsoft.Office.Tools.Word.Document> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet>. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Můžete přidat ovládací prvky model Windows Forms nebo *hostitelské ovládací prvky*. Hostitelský ovládací prvek je ovládací prvek [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , který poskytuje odpovídající ovládací prvek v rámci primárního definičního sestavení Word nebo Excelu. Hostitelský ovládací prvek zpřístupňuje všechna chování základního nativního objektu Office. Také vyvolává události a mohou být vázány na data pomocí modelu model Windows Forms datové vazby. Další informace naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

> [!NOTE]
> Pomocí doplňku VSTO <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> nelze do dokumentu přidat ovládací prvek <xref:Microsoft.Office.Tools.Word.XMLNode> ani ovládací <xref:Microsoft.Office.Tools.Word.XMLNodes> prvek nebo. Tyto hostitelské ovládací prvky nelze přidat prostřednictvím kódu programu. Další informace najdete v tématu [programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

### <a name="persist-and-remove-controls"></a>Zachovat a odebrat ovládací prvky
 Když do dokumentu nebo listu přidáte spravované ovládací prvky, ovládací prvky se při uložení a zavření dokumentu neuloží. Všechny hostitelské ovládací prvky se odeberou, aby zůstaly jenom základní nativní objekty Office. Například, se může <xref:Microsoft.Office.Tools.Excel.ListObject> jednat o <xref:Microsoft.Office.Interop.Excel.ListObject>a. Odeberou se také všechny model Windows Forms ovládací prvky, ale obálky ActiveX pro ovládací prvky zůstanou v dokumentu. Chcete-li vyčistit ovládací prvky nebo znovu vytvořit ovládací prvky při příštím otevření dokumentu, je nutné do doplňku VSTO použít kód. Další informace najdete v tématu [trvalé dynamické ovládací prvky v dokumentech Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

## <a name="access-application-level-events-on-documents-and-workbooks"></a>Přístup k událostem na úrovni aplikace na dokumentech a v sešitech
 Některé události dokumentu, sešitu a listu v nativních objektech aplikace Word a Excel jsou vyvolány pouze na úrovni aplikace. Například <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událost je vyvolána, když je dokument otevřen v aplikaci Word, ale tato událost je definována <xref:Microsoft.Office.Interop.Word.Application> ve <xref:Microsoft.Office.Interop.Word.Document> třídě namísto třídy.

 Když v doplňku VSTO použijete jenom nativní objekty Office, musíte tyto události na úrovni aplikace zpracovat a pak napsat další kód, abyste zjistili, jestli dokument, který vyvolal událost, je ten, který jste přizpůsobili. Hostitelské položky poskytují tyto události na úrovni dokumentu, aby bylo snazší zpracovávat události pro konkrétní dokument. Můžete vygenerovat hostitelskou položku a pak zpracovat událost pro tuto položku hostitele.

### <a name="example-that-uses-native-word-objects"></a>Příklad, který používá nativní objekty aplikace Word
 Následující příklad kódu ukazuje, jak zpracovat událost na úrovni aplikace pro dokumenty aplikace Word. Metoda vytvoří nový dokument a pak <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> definuje obslužnou rutinu události, která brání uložení tohoto dokumentu. `CreateDocument` Událost je událost na úrovni aplikace, která je vyvolána <xref:Microsoft.Office.Interop.Word.Application> pro objekt, a obslužná rutina události musí `Doc` porovnat parametr s `document1` objektem, aby bylo možné určit `document1` , zda představuje uložený dokument.

 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]

### <a name="examples-that-use-a-host-item"></a>Příklady, které používají hostitelskou položku
 Následující příklady kódu zjednodušují tento proces zpracováním <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> události <xref:Microsoft.Office.Tools.Word.Document> hostitelské položky. Metoda v těchto příkladech <xref:Microsoft.Office.Tools.Word.Document> generuje `document2` objekt, který rozšiřuje objekt, a poté definuje <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> obslužnou rutinu události, která brání uložení dokumentu. `CreateDocument2` Obslužná rutina události je volána pouze `document2` v případě, že je uložena a může akci uložení zrušit bez provedení jakékoli další práce k ověření, který dokument byl uložen.

 Následující příklad kódu ukazuje tuto úlohu.

 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]

## <a name="HasVstoObject"></a>Určení, zda byl objekt Office rozšířen
 Chcete-li zjistit, zda rozšířený objekt již byl vygenerován pro určitý nativní objekt Office, použijte `HasVstoObject` metodu. Tato metoda vrátí **hodnotu true** , pokud rozšířený objekt již byl vygenerován.

 `Globals.Factory.HasVstoMethod` Použijte metodu. Předejte nativní objekt Word nebo Excel, jako je <xref:Microsoft.Office.Interop.Word.Document> například nebo <xref:Microsoft.Office.Interop.Excel.Worksheet>, který chcete otestovat pro rozšířený objekt.

 Metoda `HasVstoObject` je užitečná v případě, že chcete spustit kód pouze v případě, že zadaný objekt Office má rozšířený objekt. Například pokud máte doplněk aplikace Word VSTO, který zpracovává <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událost pro odebrání spravovaných ovládacích prvků z dokumentu před jeho uložením, `HasVstoObject` použijte metodu k určení, zda byl dokument rozšířen. Pokud dokument nebyl rozšířen, nemůže mít spravované ovládací prvky a obslužná rutina události může vracet bez pokusu o vyčištění ovládacích prvků v dokumentu.

## <a name="see-also"></a>Viz také:
- [Programové doplňky VSTO](../vsto/programming-vsto-add-ins.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
