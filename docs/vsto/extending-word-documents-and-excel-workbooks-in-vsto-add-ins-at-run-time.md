---
title: Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 424b2cf8a6461ed0d60a1c16555c49c0ed8a0136
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895779"
---
# <a name="extend-word-documents-and-excel-workbooks-in-vsto-add-ins-at-runtime"></a>Rozšíření dokumentů aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu
  Doplněk VSTO slouží k přizpůsobení dokumentů aplikace Word a sešitů aplikace Excel následujícími způsoby:  
  
- Přidáte spravované ovládací prvky na libovolnou otevřeného dokumentu nebo listu.  
  
- Převést existující objekt seznamu v listu aplikace Excel na rozšířená <xref:Microsoft.Office.Tools.Excel.ListObject> , který zpřístupňuje události a může být vázaný na data pomocí vazby datového modelu Windows Forms.  
  
- Přístup k událostem na úrovni aplikace, které jsou vystaveny ve Wordu a Excelu pro konkrétní dokumenty, sešity a listy nástroje.  
  
  Tuto funkci použít, generovat objektu za běhu, který rozšiřuje dokumentu nebo sešitu.  
  
  **Platí pro:** informace v tomto článku se vztahují na projekty doplňku VSTO v následujících aplikacích: Excel a Word. Další informace najdete v tématu [dostupné funkce podle typu aplikace a projekt sady Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="generate-extended-objects-in-vsto-add-ins"></a>Generovat rozšířených objektů v doplňcích VSTO  
 *Rozšířených objektů* jsou instance typů, poskytuje Visual Studio Tools pro systém Office runtime, které přidávají funkce do objektů, které nativně existovat v aplikaci Word nebo Excel objektové modely (volá *nativních objektů Office*). Chcete-li generovat rozšířeného objektu pro objekt aplikace Word nebo Excel, použijte `GetVstoObject` metody. Při prvním volání `GetVstoObject` objekt metodu pro zadané aplikace Word nebo Excel, vrátí nový objekt, který rozšiřuje zadaného objektu. Pokaždé, když volat metodu a zadejte stejné aplikace Word nebo Excel objekt vrací stejný objekt rozšířené.  
  
 Typ objektu rozšířené má stejný název jako typ objektu nativní Office, ale typ je definován v <xref:Microsoft.Office.Tools.Excel> nebo <xref:Microsoft.Office.Tools.Word> oboru názvů. Například, pokud zavoláte `GetVstoObject` – metoda rozšíření <xref:Microsoft.Office.Interop.Word.Document> objektů, metoda vrátí <xref:Microsoft.Office.Tools.Word.Document> objektu.  
  
 `GetVstoObject` Metody jsou určeny pro použití především projekty doplňku VSTO. Tyto metody lze také použít v projektech na úrovni dokumentu, ale chovají odlišně a máte méně používá.  
  
 Chcete-li zjistit, zda rozšířený objekt již byl vygenerován pro konkrétní nativní objekt Office, použijte `HasVstoObject` metody. Další informace najdete v tématu [určit, zda bylo rozšířeno Office objekt](#HasVstoObject).  
  
### <a name="generate-host-items"></a>Generovat hostitelské položky  
 Při použití `GetVstoObject` rozšířit objekt na úrovni dokumentu (to znamená, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, nebo <xref:Microsoft.Office.Interop.Word.Document>), vráceného objektu je volána *hostitelský objekt*. Hostitelská položka je typ, který může obsahovat další objekty, včetně jiných rozšířených objektů a ovládacích prvků. Vypadá podobně jako odpovídající typ v aplikaci Word nebo Excel primární sestavení vzájemné spolupráce, ale má další funkce. Další informace o hostitelských položkách naleznete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
 Jakmile vygenerujete položku hostitele, můžete přidat ovládací prvky spravovaného dokumentu, sešitu nebo listu. Další informace najdete v tématu [přidat spravovaných ovládacích prvků na dokumenty a sešity](#AddControls).  
  
#### <a name="to-generate-a-host-item-for-a-word-document"></a>Generovat položku hostitele pro dokument aplikace Word  
  
-   Následující příklad kódu ukazuje, jak generovat položku hostitele pro aktivní dokument.  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]
     [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>Ke generování hostitelská položka sešitu aplikace Excel  
  
-   Následující příklad kódu ukazuje, jak generovat hostitelská položka sešitu aktivní.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
#### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>Generovat položku hostitele pro listu aplikace Excel  
  
-   Následující příklad kódu ukazuje, jak generovat hostitelská položka pro aktivního listu v projektu.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generate-listobject-host-controls"></a>Generovat hostitelských ovládacích prvků ListObject  
 Při použití `GetVstoObject` – metoda rozšíření <xref:Microsoft.Office.Interop.Excel.ListObject>, metoda vrátí <xref:Microsoft.Office.Tools.Excel.ListObject>. <xref:Microsoft.Office.Tools.Excel.ListObject> Má všechny funkce původní <xref:Microsoft.Office.Interop.Excel.ListObject>. Také obsahuje další funkce a může být vázaný na data pomocí vazby datového modelu Windows Forms. Další informace najdete v tématu [ListObject – ovládací prvek](../vsto/listobject-control.md).  
  
#### <a name="to-generate-a-host-control-for-a-listobject"></a>Ke generování hostitelského ovládacího prvku pro ListObject  
  
-   Následující příklad kódu ukazuje, jak vygenerovat <xref:Microsoft.Office.Tools.Excel.ListObject> poprvé <xref:Microsoft.Office.Interop.Excel.ListObject> v aktivním listu v projektu.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]
     [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
###  <a name="AddControls"></a> Přidání spravovaných ovládacích prvků do dokumentů a listů  
 Jakmile vygenerujete <xref:Microsoft.Office.Tools.Word.Document> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet>, můžete přidat ovládací prvky v dokumentu nebo listu, že tyto rozšířené objekty představují. Chcete-li přidat ovládací prvky, použijte `Controls` vlastnost <xref:Microsoft.Office.Tools.Word.Document> nebo <xref:Microsoft.Office.Tools.Excel.Worksheet>. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Můžete přidat ovládací prvky Windows Forms nebo *hostování ovládacích prvků*. Hostitelský ovládací prvek je ovládací prvek poskytované [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , která zabalí odpovídající ovládací prvek v aplikaci Word nebo Excel primárního spolupracujícího sestavení. Hostitelský ovládací prvek zpřístupní všechna chování základní nativní objekt Office. Také vyvolává události a může být vázaný na data pomocí vazby datového modelu Windows Forms. Další informace najdete v tématu [hostovat položky a hostujte Přehled ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  Nelze přidat <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládacího prvku do listu, nebo <xref:Microsoft.Office.Tools.Word.XMLNode> nebo <xref:Microsoft.Office.Tools.Word.XMLNodes> ovládacího prvku na dokument, pomocí doplňku VSTO. Tyto hostitelské ovládací prvky nelze programově přidat. Další informace najdete v tématu [programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="persist-and-remove-controls"></a>Zachovat a odebrání ovládacích prvků  
 Při přidání spravované ovládacích prvků do dokumentu nebo sešitu, ovládací prvky nejsou trvalé při uložení a pak zavření dokumentu. Všechny hostitelské ovládací prvky jsou odebrány, aby se zachovají jenom základní nativních objektů sady Office. Například <xref:Microsoft.Office.Tools.Excel.ListObject> stane <xref:Microsoft.Office.Interop.Excel.ListObject>. Budou odebrány také všechny ovládací prvky Windows Forms, ale ActiveX obálky pro ovládací prvky se zachovají v dokumentu. Je nutné zahrnout kód v vašeho doplňku VSTO pro vyčištění ovládací prvky nebo znovu vytvořte ovládací prvky při příštím otevření dokumentu. Další informace najdete v tématu [uchování dynamických ovládacích prvků v dokumentech systému Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## <a name="access-application-level-events-on-documents-and-workbooks"></a>Událostí na úrovni aplikace přístup na dokumenty a sešity  
 Některé události dokumentu, sešitu a listu v nativní modely objektů aplikace Word a Excel jsou vyvolány pouze na úrovni aplikace. Například <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> událost se vyvolá při otevření dokumentu ve Wordu, ale tato událost je definována v <xref:Microsoft.Office.Interop.Word.Application> třídy, spíše než <xref:Microsoft.Office.Interop.Word.Document> třídy.  
  
 Pokud používáte pouze nativní objektů systému Office v doplňku VSTO, musí zpracování těchto událostí na úrovni aplikace a potom psát další kód. Chcete-li zjistit, jestli dokument, který vyvolal událost je ten, který jste upravili. Hostitelské položky poskytují tyto události na úrovni dokumentu, tak, aby bylo jednodušší zpracování událostí pro určitého dokumentu. Můžete generovat položku hostitele a následně zpracovat událost pro danou položku hostitele.  
  
### <a name="example-that-uses-native-word-objects"></a>Příklad použití nativních objektů aplikace Word  
 Následující příklad kódu ukazuje, jak zpracovat událost úrovni aplikace pro Wordové dokumenty. `CreateDocument` Metoda vytvoří nový dokument a pak definuje <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> obslužná rutina události, které zabrání ukládání tohoto dokumentu. Události se událost úrovni aplikace, která se vyvolá pro <xref:Microsoft.Office.Interop.Word.Application> objektu a obslužné rutiny události musí porovnat `Doc` parametr `document1` objektu k určení, zda `document1` představuje uložené dokumenty.  
  
 [!code-vb[Trin_WordAddInDynamicControls #12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)]
 [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>Příklady, které používají hostitelská položka  
 Následující příklady kódu zjednodušení tohoto procesu pomocí manipulace <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> události <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt. `CreateDocument2` Generuje metodu v těchto příkladech <xref:Microsoft.Office.Tools.Word.Document> , který rozšiřuje `document2` definuje objekt a pak <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> obslužná rutina události, které zabrání ukládání dokumentu. Obslužná rutina události je volána pouze tehdy, když `document2` se uloží a uložení můžete zrušit akci bez provádění jakékoli další práce k ověření, který dokument se uložila.  
  
 Následující příklad kódu ukazuje tuto úlohu.  
  
 [!code-vb[Trin_WordAddInDynamicControls #13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)]
 [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> Určení, zda objekt Office se prodloužila  
 Chcete-li zjistit, zda rozšířený objekt již byl vygenerován pro konkrétní nativní objekt Office, použijte `HasVstoObject` metody. Tato metoda vrátí **true** Pokud rozšířené objekt již byl vytvořen.  
  
 Použití `Globals.Factory.HasVstoMethod` metody. Předat do nativní aplikace Word nebo Excel objektu, například <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Interop.Excel.Worksheet>, který chcete testovat rozšířeného objektu.  
  
 `HasVstoObject` Metoda je užitečná, pokud chcete spustit kód, jenom když má zadaný objekt Office rozšířeného objektu. Například, pokud máte VSTO pro Word doplňku, který zpracovává <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> události a odeberte spravované ovládací prvky z dokumentu před uložením `HasVstoObject` metodou ke zjištění, zda bylo rozšířeno dokumentu. Pokud dokument nebylo rozšířené, nemůže mít spravovaných ovládacích prvků a obslužná rutina události může vrátit bez pokusu o vyčištění u daného dokumentu řízení.  
  
## <a name="see-also"></a>Viz také:  
 [Programování doplňků VSTO](../vsto/programming-vsto-add-ins.md)   
 [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Ukázky vývoje pro Office a názorné postupy](../vsto/office-development-samples-and-walkthroughs.md)  
  
  