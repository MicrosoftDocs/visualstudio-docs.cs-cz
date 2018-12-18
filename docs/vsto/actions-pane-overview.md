---
title: Přehled podokna akcí
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8c7136c1f97f531600799f3aede30170813cf0a
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305673"
---
# <a name="actions-pane-overview"></a>Přehled podokna akcí
  Podokna akcí je přizpůsobitelnou **akcích dokumentu** podokna úloh, které je připojené k určitým dokumentem aplikace Microsoft Office Word nebo sešit aplikace Microsoft Office Excel. V podokně Akce je umístěn uvnitř podokna úloh Office spolu s jiná podokna integrované úlohy, jako **XML použitého jako zdroj** podokna úloh v aplikaci Excel nebo **styly a formátování** podokna úloh v aplikaci Word. Ovládací prvky Windows Forms a ovládacích prvků WPF můžete použít k návrhu uživatelského rozhraní podokna akcí.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

 Podokna akcí můžete vytvořit pouze v přizpůsobení na úrovni dokumentu pro aplikaci Word nebo Excel. Nelze vytvořit podokna akcí v doplňku VSTO. Další informace najdete v tématu [dostupné funkce podle typu aplikace a projekt sady Office](../vsto/features-available-by-office-application-and-project-type.md).  

> [!NOTE]  
>  V podokně Akce se liší od vlastních podoken úloh. Vlastní podokna úloh jsou spojeny s aplikací, ne určitého dokumentu. Můžete vytvořit vlastní podokna úloh v doplňcích VSTO pro některé aplikace Microsoft Office. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).  

 ![odkaz na video](../vsto/media/playvideo.gif "odkaz na video") související video ukázku naleznete v tématu [jak ovládacích prvků WPF použití i do podokna akcí aplikace Excel?](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="display-the-actions-pane"></a>Zobrazení podokna akcí  
 V podokně Akce je reprezentována <xref:Microsoft.Office.Tools.ActionsPane> třídy. Při vytváření projektu úrovni dokumentu, instance této třídy je k dispozici pro váš kód pomocí `ActionsPane` pole `ThisWorkbook` (pro aplikace Excel) nebo `ThisDocument` (pro aplikaci Word) třídy v projektu. Pokud chcete zobrazit podokno akcí, přidejte do ovládacího prvku Windows Forms <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> vlastnost `ActionsPane` pole. Následující příklad kódu přidá ovládací prvek s názvem `actions` do podokna akcí.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  

 V podokně Akce se objevovat grafová za běhu také explicitně přidat do ní ovládací prvek. Po zobrazení podokna akcí můžete dynamicky přidat nebo odebrat ovládací prvky v reakci na akce uživatele. Obvykle přidáte kód k zobrazení v podokně Akce `Startup` obslužná rutina události `ThisDocument` nebo `ThisWorkbook` tak, že v podokně Akce když uživatel poprvé otevře dokument. Můžete však chtít zobrazit podokno akcí pouze v reakci na akce uživatele v dokumentu. Můžete například přidat kód, který `Click` události ovládacího prvku na dokument.  

### <a name="add-multiple-controls-to-the-actions-pane"></a>Přidání více ovládacích prvků do podokna akcí  
 Když přidáte více ovládacích prvků do podokna akcí, by měl seskupení ovládacích prvků do uživatelského ovládacího prvku a poté přidejte uživatelský ovládací prvek <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> vlastnost. Tento proces zahrnuje následující kroky:  

1. Vytvoření uživatelského rozhraní (UI) podokna akcí tak, že přidáte **ovládacího prvku podokna akcí** nebo **uživatelský ovládací prvek** položky do projektu. Obě tyto položky zahrnují vlastních formulářů Windows <xref:System.Windows.Forms.UserControl> třídy. **Ovládacího prvku podokna akcí** a **uživatelský ovládací prvek** položky jsou ekvivalentní; jediným rozdílem je jejich název.  

2. Přidání ovládacích prvků Windows Forms do <xref:System.Windows.Forms.UserControl> pomocí návrháře nebo napsáním kódu.  

   > [!NOTE]  
   >  Můžete také přidat ovládací prvky WPF do podokna akcí tak, že přidáte WPF <xref:System.Windows.Controls.UserControl> do formulářů Windows <xref:System.Windows.Forms.UserControl>. Další informace najdete v tématu [řídí použití WPF v řešeních pro systém Office](../vsto/using-wpf-controls-in-office-solutions.md).  

3. Přidá do ovládacích prvků, které jsou obsaženy v instanci vlastního uživatelského ovládacího prvku `ActionsPane` pole `ThisWorkbook` (pro aplikace Excel) nebo `ThisDocument` (pro aplikaci Word) třídy v projektu.  

   Příklady, které ukazují tento proces v další podrobnosti najdete v tématu [postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  

## <a name="hide-the-actions-pane"></a>Skrýt podokno akcí  
 I když <xref:Microsoft.Office.Tools.ActionsPane> třída nemá <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metoda a <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> vlastnost, nelze odebrat podokna akcí z uživatelského rozhraní pomocí všechny členy skupiny <xref:Microsoft.Office.Tools.ActionsPane> třídu. Volání <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody nebo nastavení <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> vlastnost **false** skryje pouze ovládací prvky v podokně Akce; neskrývá podokna úloh.  

 Chcete-li skrýt podokno úloh ve vašem řešení, máte několik možností:  

-   Slovo, nastavte <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> vlastnost <xref:Microsoft.Office.Interop.Word.TaskPane> objekt, který reprezentuje podokna úloh akcích dokumentu a **false**. Následující příklad kódu je určený ke spuštění z `ThisDocument` třídu ve vašem projektu.  

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]  

-   Pro aplikaci Excel, nastavte <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> objektu **false**. Následující příklad kódu je určený ke spuštění z `ThisWorkbook` třídu ve vašem projektu.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]  

-   Pro aplikaci Word nebo Excel, můžete také nastavit <xref:Microsoft.Office.Core.CommandBar.Visible%2A> vlastnost panelu příkazů, který představuje podokna úloh do **false**. Následující příklad kódu je určený ke spuštění z `ThisDocument` nebo `ThisWorkbook` třídu ve vašem projektu.  

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]  

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Vymazání v podokně Akce při otevření dokumentu  
 Když uživatel uloží dokument, zatímco v podokně Akce je viditelný, podokně Akce je viditelný pokaždé, když tento dokument je otevřen, zda obsahuje všechny ovládací prvky v podokně Akce. Pokud chcete do ovládacího prvku, když se objeví, zavolejte <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> metodu `ActionsPane` pole `Startup` obslužná rutina události `ThisDocument` nebo `ThisWorkbook` zajistit, že v podokně Akce není viditelné při otevření dokumentu.  

### <a name="determine-when-the-actions-pane-is-closed"></a>Určení při uzavření podokna akcí  
 Neexistuje žádná událost, která je vyvolána při zavření podokna akcí. I když <xref:Microsoft.Office.Tools.ActionsPane> třída nemá <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> událost, tato událost se vyvolá, když koncový uživatel zavře podokna akcí. Místo toho se tato událost je aktivována, když jsou voláním skrytý ovládací prvky v podokně Akce <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metoda nebo nastavením <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> vlastnost **false**.  

 Když uživatel zavře podokna akcí, může uživatel zobrazit ho znovu pomocí jedné z následujících postupů v uživatelském rozhraní (UI) aplikace.  

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Pokud chcete zobrazit podokno akcí s použitím uživatelského rozhraní aplikace Word nebo Excel  

1.  Na pásu karet klikněte na tlačítko **zobrazení** kartu.  

2.  V **zobrazit/skrýt** klikněte na položku **akcích dokumentu** přepínacího tlačítka.  

## <a name="program-actions-pane-events"></a>Program události podokna akce  
 Můžete přidat více uživatelských ovládacích prvků do podokna akce a potom napsat kód, který reagovat na události v dokumentu pomocí zobrazení a skrytí uživatelské ovládací prvky. Pokud namapujete prvků schématu XML k dokumentu, můžete zobrazit některé uživatelské ovládací prvky v podokně Akce pokaždé, když se kurzor nachází uvnitř jeden z elementů XML. Další informace najdete v tématu [postupy: mapování schémat na dokumenty aplikace Word v sadě Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) a [postupy: mapování schémat na listy v prostředí Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  

 Můžete také napsat kód pro reakci na události z libovolného objektu, včetně hostitelský ovládací prvek, aplikace nebo dokumentu události. Další informace najdete v tématu [názorný postup: Program ošetření událostí ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Vytvoření vazby dat s ovládacími prvky v podokně Akce  
 Ovládací prvky v podokně akce mají stejné možnosti vázání dat jako ovládacích prvků ve Windows Forms. Můžete svázat ovládací prvky zdroje dat, jako jsou datové sady, typové datové sady a XML. Další informace najdete v tématu [a datové vazby Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  

 Do stejného objektu dataset lze svázat ovládací prvky v podokně Akce a ovládací prvky v dokumentu. Můžete například vytvořit hlavní a podrobný vztah mezi ovládacími prvky v podokně akcí a ovládacích prvků na list. Další informace najdete v tématu [návod: vytvoření vazby dat k ovládacím prvkům v podokně akcí aplikace Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  

## <a name="validate-data-in-actions-pane-controls"></a>Ověřování dat v podokně Akce ovládacích prvků  
 Pokud se zobrazí okno se zprávou ve <xref:System.Windows.Forms.Control.Validating> mohla být vyvolána obslužná rutina události ovládacího prvku v podokně akce události podruhé když fokus přesunete z ovládacího prvku okna se zprávou. Chcete-li předejít tomuto problému, použijte <xref:System.Windows.Forms.ErrorProvider> ovládací prvek pro zobrazení všech chybových zpráv ověření.  

## <a name="user-control-stacking-order"></a>Uživatelský ovládací prvek pořadí překrývání  
 Pokud používáte více uživatelských ovládacích prvků, můžete napsat kód pro uživatelské ovládací prvky v podokně Akce správně zásobníku, zda je ukotven vodorovně nebo svisle. Pořadí uživatelské ovládací prvky v podokně akcí můžete nastavit pomocí <xref:Microsoft.Office.Tools.StackStyle> výčet <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> vlastnost. Další informace najdete v tématu [postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)  

 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> Vlastnost může mít následující <xref:Microsoft.Office.Tools.StackStyle> hodnot výčtu.  

|Překrývání styl|Definice|  
|--------------------|----------------|  
|FromBottom|Zásobníku v dolní části podokna akcí.|  
|FromLeft|Stack – od levé části podokna akcí.|  
|FromRight|Stack – z pravé strany podokna akcí.|  
|FromTop|Stack – od horní části podokna akcí.|  
|Žádné|Žádné pořadí definovaný pořadí je řízen vývojářem.|  

 Následující kód nastaví <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> vlastnost zásobníku uživatelské ovládací prvky z horní části podokna akcí.  

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]  

## <a name="anchor-controls"></a>Ukotvení ovládacích prvků  
 Pokud uživatel změní velikost podokna akcí za běhu, změnit velikost ovládacích prvků s podoknem akcí. Můžete použít <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost ovládacího prvku Windows Forms do ovládacích prvků ukotvení pro podokna akcí. Stejným způsobem můžete také ukotvit ovládacích prvků Windows Forms do uživatelského ovládacího prvku. Další informace najdete v tématu [postupy: Ukotvování ovládacích prvků ve Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).  

## <a name="resize-the-actions-pane"></a>Změnit velikost podokna akcí  
 Nelze přímo změnit velikost <xref:Microsoft.Office.Tools.ActionsPane> protože <xref:Microsoft.Office.Tools.ActionsPane> se vloží do podokna úloh. Však můžete programově změnit šířku v podokně úloh tak, že nastavíte <xref:Microsoft.Office.Core.CommandBar.Width%2A> vlastnost <xref:Microsoft.Office.Core.CommandBar> , která představuje podokna úloh. Pokud je ukotven vodorovně nebo plovoucí můžete změnit výšku v podokně úloh.  

 Programová změna velikosti v podokně úloh se nedoporučuje, protože uživatel měli být schopni vybrat velikost podokna, který nejlépe vyhovuje jejich potřebám. Nicméně pokud musíte změnit velikost Šířka podokna úloh, můžete použít následující kód k provedení této úlohy.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]  

## <a name="reposition-the-actions-pane"></a>Změna umístění v podokně Akce  
 Nelze změnit umístění přímo <xref:Microsoft.Office.Tools.ActionsPane> vzhledem k tomu, že je video vložené v podokně úloh. Však můžete programově přesunout podokna úloh tak, že nastavíte <xref:Microsoft.Office.Core.CommandBar.Position%2A> vlastnost <xref:Microsoft.Office.Core.CommandBar> , která představuje podokna úloh.  

 Programově přemístění podokna úloh se nedoporučuje, protože uživatel měli být schopni vybrat pozici podokno úloh na obrazovce, která nejlépe vyhovuje potřebám své. Nicméně pokud je nutné přesunout v podokně úloh na konkrétní pozici, můžete použít následující kód k provedení této úlohy.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]  

> [!NOTE]  
>  Koncovým uživatelům můžete přemístit ručně v podokně úloh v každém okamžiku. Neexistuje žádný způsob, jak zajistit, že v podokně úloh zůstane ukotvený na pozici, která jste prostřednictvím kódu programu. Můžete však zjišťovat změny orientace a ujistěte se, že ovládací prvky v podokně Akce jsou navršeny správným směrem. Další informace najdete v tématu [postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md).  

 Nastavení <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> a <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> vlastnosti <xref:Microsoft.Office.Tools.ActionsPane> nedojde ke změně jeho pozice vzhledem k tomu, <xref:Microsoft.Office.Tools.ActionsPane> objekt je vložen do podokna úloh.  

 Pokud není ukotven podokna úloh, můžete nastavit <xref:Microsoft.Office.Core.CommandBar.Top%2A> a <xref:Microsoft.Office.Core.CommandBar.Left%2A> vlastnosti <xref:Microsoft.Office.Core.CommandBar> , která představuje podokna úloh. Následující kód neukotvené panely podokna přesune do levého horního rohu dokumentu.  

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]  

## <a name="see-also"></a>Viz také:  
 [Použití ovládacích prvků WPF v řešeních pro systém Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)   
 [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Návod: Vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Návod: Vytvoření vazby dat s ovládacími prvky v podokně akcí aplikace Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Návod: Vytvoření vazby dat k ovládacím prvkům v podokně akcí aplikace Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Návod: Vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
