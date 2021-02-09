---
title: Přehled podokna akcí
description: Seznamte se s tím, jak je podokno akcí přizpůsobitelné akce dokumentu podokno úloh, které je připojené k určitému systém Microsoft Office dokumentu aplikace Word nebo excelovém sešitu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9579de6712b742dde1f9b399ca8a1e4598783679
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896764"
---
# <a name="actions-pane-overview"></a>Přehled podokna akcí
  Podokno akcí je podokno úloh přizpůsobitelné **Akce dokumentu** , které je připojené k určitému systém Microsoft Office dokumentu aplikace Word nebo systém Microsoft Office excelovém sešitu. Podokno akce je hostováno v podokně úloh Office společně s dalšími vestavěnými podokny úloh, jako je podokno úloh **zdroj XML** v aplikaci Excel nebo podokno úloh **styly a formátování** ve Wordu. Můžete použít ovládací prvky model Windows Forms nebo ovládací prvky WPF pro návrh uživatelského rozhraní podokna akce.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Podokno akce můžete vytvořit pouze v přizpůsobení na úrovni dokumentu aplikace Word nebo Excel. V doplňku VSTO nemůžete vytvořit podokno akcí. Další informace najdete v tématu [dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> Podokno akce se liší od vlastních podoken úloh. Vlastní podokna úloh jsou přidružená k aplikaci, ne ke konkrétnímu dokumentu. V Doplňkech VSTO můžete vytvořit vlastní podokna úloh pro některé aplikace systém Microsoft Office. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

## <a name="display-the-actions-pane"></a>Zobrazení podokna akce
 Podokno akce je reprezentované <xref:Microsoft.Office.Tools.ActionsPane> třídou. Při vytváření projektu na úrovni dokumentu je instance této třídy k dispozici pro váš kód pomocí `ActionsPane` pole `ThisWorkbook` (pro Excel) nebo `ThisDocument` (pro Word) třídy v projektu. Chcete-li zobrazit podokno akce, přidejte ovládací prvek model Windows Forms do <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> vlastnosti `ActionsPane` pole. Následující příklad kódu přidá ovládací prvek s názvem `actions` do podokna akce.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 Podokno akce se zobrazí v době běhu hned po přidání ovládacího prvku do něj. Po zobrazení podokna akce můžete dynamicky přidávat nebo odebírat ovládací prvky v reakci na akce uživatele. Obvykle přidáte kód pro zobrazení podokna akce v `Startup` obslužné rutině události `ThisDocument` nebo tak, aby se `ThisWorkbook` podokno akce zobrazilo, když uživatel poprvé otevře dokument. Je však možné, že budete chtít zobrazit podokno akce pouze v reakci na akci uživatele v dokumentu. Můžete například přidat kód do `Click` události ovládacího prvku v dokumentu.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Přidání více ovládacích prvků do podokna akce
 Přidáte-li do podokna akce více ovládacích prvků, měli byste seskupit ovládací prvky do uživatelského ovládacího prvku a následně do vlastnosti přidat uživatelský ovládací prvek <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> . Tento proces zahrnuje následující kroky:

1. Vytvořte uživatelské rozhraní (UI) podokna akce přidáním **ovládacího prvku podokno akcí** nebo položky **uživatelského ovládacího prvku** do projektu. Obě tyto položky zahrnují vlastní <xref:System.Windows.Forms.UserControl> třídu model Windows Forms. **Ovládací prvky podokna akce** a položky **uživatelského ovládacího prvku** jsou ekvivalentní; Jediným rozdílem je jejich jméno.

2. Přidejte model Windows Forms ovládací prvky pomocí <xref:System.Windows.Forms.UserControl> návrháře nebo psaním kódu.

   > [!NOTE]
   > Můžete také přidat ovládací prvky WPF do podokna akcí přidáním WPF <xref:System.Windows.Controls.UserControl> do model Windows Forms <xref:System.Windows.Forms.UserControl> . Další informace najdete v tématu [použití ovládacích prvků WPF v řešeních pro systém Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Přidejte instanci vlastního uživatelského ovládacího prvku do ovládacích prvků, které jsou obsaženy v `ActionsPane` poli `ThisWorkbook` třídy (pro Excel) nebo `ThisDocument` (pro Word) ve vašem projektu.

   Příklady, které ukazují tento postup podrobněji, naleznete v tématu [How to: Add a Actions Pane to a Word Documents or Excel sešits](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

## <a name="hide-the-actions-pane"></a>Skrýt podokno akcí
 I když <xref:Microsoft.Office.Tools.ActionsPane> Třída obsahuje <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metodu a <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> vlastnost, nelze odebrat podokno akce z uživatelského rozhraní pomocí jakýchkoli členů <xref:Microsoft.Office.Tools.ActionsPane> samotné třídy. Volání <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody nebo nastavení <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> vlastnosti na **hodnotu false** skryje pouze ovládací prvky v podokně akce. neskryje podokno úloh.

 Chcete-li skrýt podokno úloh ve vašem řešení, máte několik možností:

- V případě aplikace Word nastavte <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> vlastnost <xref:Microsoft.Office.Interop.Word.TaskPane> objektu, která představuje podokno úloh Akce dokumentu na **hodnotu NEPRAVDA**. Následující příklad kódu je určen ke spuštění z `ThisDocument` třídy v projektu.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- V aplikaci Excel nastavte <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> vlastnost <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> objektu na **hodnotu NEPRAVDA**. Následující příklad kódu je určen ke spuštění z `ThisWorkbook` třídy v projektu.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- V aplikaci Word nebo Excel můžete případně nastavit <xref:Microsoft.Office.Core.CommandBar.Visible%2A> vlastnost panelu příkazů, která představuje podokno úloh na **hodnotu NEPRAVDA**. Následující příklad kódu je určen ke spuštění z `ThisDocument` `ThisWorkbook` třídy nebo v projektu.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Při otevření dokumentu vymazat podokno akcí
 Když uživatel dokument uloží, když je podokno akce viditelné, podokno akce se zobrazí při každém otevření dokumentu bez ohledu na to, jestli podokno akce obsahuje nějaké ovládací prvky. Pokud chcete určit, kdy se zobrazí, zavolejte <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> metodu `ActionsPane` pole v `Startup` obslužné rutině události `ThisDocument` nebo, `ThisWorkbook` abyste zajistili, že podokno akce není při otevření dokumentu viditelné.

### <a name="determine-when-the-actions-pane-is-closed"></a>Určení, kdy se zavře podokno akcí
 Při zavření podokna akce není vyvolána žádná událost. I když <xref:Microsoft.Office.Tools.ActionsPane> Třída obsahuje <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged> událost, tato událost není vyvolána, když koncový uživatel zavře podokno akce. Namísto toho je tato událost vyvolána, když jsou ovládací prvky v podokně akce skryty voláním <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> metody nebo nastavením <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> vlastnosti na **hodnotu false**.

 Když uživatel zavře podokno akce, uživatel ho může znovu zobrazit provedením jednoho z následujících postupů v uživatelském rozhraní (UI) aplikace.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Zobrazení podokna akce pomocí uživatelského rozhraní Wordu nebo Excelu

1. Na pásu karet klikněte na kartu **zobrazení** .

2. Ve skupině **Zobrazit/skrýt** klikněte na přepínací tlačítko **Akce dokumentu** .

## <a name="program-actions-pane-events"></a>Události v podokně akce programu
 Můžete přidat více uživatelských ovládacích prvků do podokna akce a potom napsat kód, který reaguje na události v dokumentu zobrazením a skrytím uživatelských ovládacích prvků. Pokud namapujete prvky schématu XML na dokument, můžete zobrazit určité uživatelské ovládací prvky v podokně akce vždy, když je kurzor uvnitř jednoho elementu XML. Další informace najdete v tématu [Postup: mapování schémat na dokumenty aplikace Word v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) a [Postupy: mapování schémat na listy v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).

 Můžete také napsat kód, který reaguje na události libovolného objektu, včetně událostí řízení hostitele, aplikace nebo dokumentu. Další informace naleznete v tématu [Návod: program v událostech ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Svázání dat s ovládacími prvky v podokně akce
 Ovládací prvky v podokně akce mají stejné možnosti datové vazby jako ovládací prvky na model Windows Forms. Ovládací prvky lze navazovat na zdroje dat, jako jsou datové sady, typové datové sady a XML. Další informace najdete v tématu [datové vazby a model Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Ovládací prvky lze navazovat v podokně akce a ovládacích prvcích v dokumentu na stejnou datovou sadu. Můžete například vytvořit relaci hlavní/podrobnosti mezi ovládacími prvky v podokně akce a ovládacími prvky na listu. Další informace najdete v tématu [Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

## <a name="validate-data-in-actions-pane-controls"></a>Ovládací prvky pro ověření dat v podokně akcí
 Pokud zobrazíte okno se zprávou v <xref:System.Windows.Forms.Control.Validating> obslužné rutině události ovládacího prvku v podokně akce, může být událost vyvolána podruhé, když se fokus přesune z ovládacího prvku do pole zpráva. Chcete-li předejít tomuto problému, použijte <xref:System.Windows.Forms.ErrorProvider> ovládací prvek k zobrazení všech chybových zpráv ověřování.

## <a name="user-control-stacking-order"></a>Pořadí vrstvení uživatelského ovládacího prvku
 Pokud používáte více uživatelských ovládacích prvků, můžete napsat kód pro správné vytvoření zásobníku uživatelských ovládacích prvků v podokně akce bez ohledu na to, jestli je ukotvený svisle nebo vodorovně. Pořadí vrstvení uživatelských ovládacích prvků lze nastavit v podokně akce pomocí <xref:Microsoft.Office.Tools.StackStyle> výčtu <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> Vlastnosti. Další informace najdete v tématu [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>Vlastnost může mít následující <xref:Microsoft.Office.Tools.StackStyle> hodnoty výčtu.

|Styl skládání|Definice|
|--------------------|----------------|
|FromBottom|Zásobník v dolní části podokna akce.|
|FromLeft|Zásobník vlevo od podokna akce.|
|FromRight|Stack z napravo od podokna akce.|
|FromTop|Zásobník v horní části podokna akcí.|
|Žádné|Není definováno žádné pořadí skládání; pořadí řídí vývojář.|

 Následující kód nastaví <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> vlastnost tak, aby nahrála uživatelské ovládací prvky z horní části podokna akcí.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Ovládací prvky ukotvení
 Pokud uživatel změní velikost podokna akce v době běhu, ovládací prvky mohou změnit velikost pomocí podokna akce. Můžete použít <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost ovládacího prvku model Windows Forms k ukotvení ovládacích prvků do podokna akce. Můžete také ukotvit ovládací prvky model Windows Forms do uživatelského ovládacího prvku stejným způsobem. Další informace naleznete v tématu [How to: Anchor Controls on model Windows Forms](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms).

## <a name="resize-the-actions-pane"></a>Změna velikosti podokna akcí
 Nemůžete přímo změnit velikost objektu <xref:Microsoft.Office.Tools.ActionsPane> , protože <xref:Microsoft.Office.Tools.ActionsPane> je vložený v podokně úloh. Šířku podokna úloh ale můžete programově změnit nastavením <xref:Microsoft.Office.Core.CommandBar.Width%2A> vlastnosti <xref:Microsoft.Office.Core.CommandBar> , která představuje podokno úloh. Můžete změnit výšku podokna úloh, pokud je ukotven vodorovně nebo je plovoucí.

 Programové změny velikosti podokna úloh se nedoporučují, protože uživatel by měl být schopný vybrat velikost podokna úloh, která nejlépe vyhovuje jejich potřebám. Pokud však musíte změnit velikost šířky podokna úloh, můžete k dosažení této úlohy použít následující kód.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Změna umístění podokna akcí
 Přímo nelze změnit umístění, <xref:Microsoft.Office.Tools.ActionsPane> protože je vloženo v podokně úloh. Podokno úloh však můžete programově přesunout nastavením <xref:Microsoft.Office.Core.CommandBar.Position%2A> vlastnosti <xref:Microsoft.Office.Core.CommandBar> , která představuje podokno úloh.

 Programové přemístění podokna úloh se nedoporučuje, protože uživatel by měl mít možnost zvolit umístění podokna úloh na obrazovce, která nejlépe vyhovuje vašim potřebám. Pokud však musíte přesunout podokno úloh na konkrétní pozici, můžete k dosažení této úlohy použít následující kód.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Koncoví uživatelé můžou podokno úloh kdykoli přemístit ručně. Neexistuje žádný způsob, jak zajistit, aby podokno úloh zůstalo ukotveno na pozici, kterou označíte programově. Můžete ale zkontrolovat změny orientace a zajistit, aby se ovládací prvky v podokně akcí navrstveny správným směrem. Další informace najdete v tématu [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md).

 Nastavení <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> vlastností a se <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> <xref:Microsoft.Office.Tools.ActionsPane> nezmění jeho umístění, protože <xref:Microsoft.Office.Tools.ActionsPane> objekt je vložený v podokně úloh.

 Pokud není podokno úloh ukotveno, můžete nastavit <xref:Microsoft.Office.Core.CommandBar.Top%2A> <xref:Microsoft.Office.Core.CommandBar.Left%2A> vlastnosti a <xref:Microsoft.Office.Core.CommandBar> , které představují podokno úloh. Následující kód přesune neukotvené podokno úloh do levého horního rohu dokumentu.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>Viz také
- [Použití ovládacích prvků WPF v řešeních pro systém Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Postupy: Přidání podokna akcí do dokumentů aplikace Word nebo sešitů aplikace Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Návod: vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Návod: svázání dat s ovládacími prvky v podokně akcí aplikace Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Postupy: Správa rozložení ovládacích prvků v podoknech akcí](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Návod: vložení textu do dokumentu z podokna akcí](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
