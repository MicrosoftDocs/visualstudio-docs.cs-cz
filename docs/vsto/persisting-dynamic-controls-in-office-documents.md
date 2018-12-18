---
title: Uchování dynamických ovládacích prvků v dokumentech Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Office documents [Office development in Visual Studio, host controls
- controls [Office development in Visual Studio], persisting in the document
- Windows Forms controls [Office development in Visual Studio], persisting in the document
- documents [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], host controls
- host controls [Office development in Visual Studio], persisting in the document
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b77310f797db3eb031bc311f4fc68bc7fd6b4c56
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37059331"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Uchování dynamických ovládacích prvků v dokumentech Office

Ovládací prvky, které jsou přidány za běhu nejsou trvalé, když je uložit a zavřít tento dokument nebo sešitu. Přesné chování se liší pro hostitele a ovládacích prvků Windows Forms. V obou případech můžete přidat kód pro vaše řešení se znovu vytvořit ovládacích prvků, když uživatel znovu otevře dokument.

Ovládací prvky, které přidáte do dokumentů za běhu, se nazývají *dynamických ovládacích prvků*. Další informace o dynamických ovládacích prvků najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Zachovat hostitelské ovládací prvky v dokumentu

Pokud dokument je uložit a potom uzavřen, všechny dynamické hostitelské ovládací prvky jsou vyřazeny z dokumentu. Zůstanou pouze základní nativních objektů Office za. Například <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> stane hostitelského ovládacího prvku <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName>. Nativní objektů Office nejsou připojené k události ovládacího prvku hostitele a nemají funkce vazby dat z hostitelského ovládacího prvku.

Následující tabulka uvádí nativní Office objekt, který je ponecháno v dokumentu pro každý typ hostitelského ovládacího prvku.

|Hostitel – typ ovládacího prvku|Typ objektu nativní Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Když jsou otevřené dokumenty znovu vytvořit dynamické hostitelské ovládací prvky

Dynamické hostitelské ovládací prvky místo existující nativní ovládací prvky můžete znovu vytvořit pokaždé, když uživatel otevře dokument. Vytváření ovládacích prvků hostitele tímto způsobem, při otevření dokumentu simuluje prostředí, které uživatelé můžou očekávat.

Opětovné vytvoření hostitelského ovládacího prvku pro Word, nebo <xref:Microsoft.Office.Tools.Excel.NamedRange> nebo <xref:Microsoft.Office.Tools.Excel.ListObject> hostování ovládacího prvku pro aplikaci Excel, použijte `Add` \< *třídu ovládacího prvku*> metodu <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> nebo <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> objektu. Použijte metodu, která má parametr pro objekt nativní Office.

Například, pokud chcete vytvořit <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> hostování ovládacího prvku z existující nativní <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> při otevření dokumentu, použijte <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> metoda a předejte jí existující <xref:Microsoft.Office.Interop.Excel.ListObject>. Následující příklad kódu ukazuje to v projektech na úrovni dokumentu pro Excel. Kód znovu vytvoří dynamický <xref:Microsoft.Office.Tools.Excel.ListObject> založený na existujícím <xref:Microsoft.Office.Interop.Excel.ListObject> s názvem `MyListObject` v `Sheet1` třídy.

[!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs#6)]
[!code-vb[Trin_ExcelWorkbookDynamicControls#6](../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb#6)]

### <a name="re-create-chart"></a>Znovu vytvořte graf

Znovu vytvořit <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> hostování ovládacího prvku, musíte nejprve odstranit nativního <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>a potom je znovu vytvořit <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> pomocí <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> metoda. Neexistuje žádné `Add` \< *třídu ovládacího prvku*> metoda, která umožňuje vytvořit nový <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> na základě existujícího <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName>.

Pokud nejdříve neodstraníte nativního <xref:Microsoft.Office.Interop.Excel.Chart>, pak vytvoříte druhý, duplicitní grafu, když znovu vytvoříte <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName>.

## <a name="persist-windows-forms-controls-in-documents"></a>Zachovat ovládací prvky Windows Forms v dokumentech

Když je dokument uložit a potom uzavřen, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automaticky odstraní všechny ovládací prvky Windows Forms dynamicky vytvořený z dokumentu. Chování se ale liší na úrovni dokumentu a projekty doplňku VSTO.

V přizpůsobeních na úrovni dokumentu budou odebrány při příštím otevření dokumentu ovládací prvky a jejich základní obálky ActiveX (které budou použity k hostování ovládacích prvků na dokument). Neexistuje žádná informace, které ovládací prvky byly někdy existuje.

V doplňcích VSTO ovládací prvky jsou odebrány, ale obálky ActiveX zůstanou v dokumentu. Při příštím otevření dokumentu obálky ActiveX jsou viditelné. V aplikaci Excel obálky ActiveX zobrazit obrázky ovládací prvky, jako jsou uvedeny posledním uložení dokumentu. V aplikaci Word obálky ActiveX jsou neviditelná, pokud uživatel klikne na nich, v takovém případě se zobrazí tečkovaná čára, který představuje ohraničení ovládacích prvků. Obálky ActiveX můžete odebrat několika způsoby. Další informace najdete v tématu [odebrat obálky ActiveX v doplňku](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Když jsou otevřené dokumenty znovu vytvořit ovládací prvky Windows Forms

Můžete znovu vytvořit odstraněné ovládací prvky Windows Forms, když uživatel znovu otevře dokument. Chcete-li to provést, musí vaše řešení provádět následující úlohy:

1.  Uložení informací o velikosti, umístění a stavu ovládacích prvků, když je dokument uložit nebo uzavřený. V přizpůsobení na úrovni dokumentu můžete uložit data do mezipaměti data v dokumentu. VSTO Add-in můžete data uložit na vlastní část XML v dokumentu.

2.  Ovládací prvky v událost, která se vyvolá, když je dokument otevřít znovu vytvořte. V projektech na úrovni dokumentu, můžete k tomu `Sheet` *n* `_Startup` nebo `ThisDocument_Startup` obslužné rutiny událostí. Na projekty doplňku VSTO lze provádět v tomto událostí obslužné rutiny <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> nebo <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> události.

###  <a name="removingActiveX"></a> Odebrat obálky ActiveX v doplňku

Když přidáte dynamických ovládacích prvků Windows Forms do dokumentů pomocí doplňku VSTO, můžete obálky ActiveX ovládacích prvků zabránit zobrazování v dokumentu, při příštím otevření následujícími způsoby.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Při otevření dokumentu odebrat ActiveX obálky

Chcete-li odebrat všechny ActiveX obálky, volejte `GetVstoObject` metoda ke generování položku hostitele pro <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Interop.Excel.Workbook> představující nově otevřené dokumentu. Například, všechny obálky ActiveX odebrat z dokumentu aplikace Word, může zavolat `GetVstoObject` metoda ke generování položku hostitele pro <xref:Microsoft.Office.Interop.Word.Document> objekt, který je předán do obslužné rutiny události pro <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> událostí.

Tento postup je užitečný, když víte, že, otevřou se jenom na počítače, které mají VSTO doplněk nainstalován. Pokud dokument mohla být předána do jiných uživatelů, kteří nemají VSTO doplněk nainstalován, zvažte odebrání ovládacích prvků před jeho zavřením dokumentu místo toho.

Následující příklad kódu ukazuje způsob volání `GetVstoObject` metoda při otevření dokumentu.

[!code-vb[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#11)]
[!code-csharp[Trin_WordAddInDynamicControls#11](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#11)]

I když `GetVstoObject` metoda slouží především ke generování novou položku hostitele za běhu, tato metoda také odstraní všechny obálky ActiveX z dokumentu při prvním volání pro konkrétní dokument. Další informace o tom, jak používat `GetVstoObject` metodu, najdete v části [dokumentů rozšířit aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

Pokud vaše doplňku VSTO vytvoří dynamických ovládacích prvků při otevření dokumentu, vaše doplňku VSTO již zavolá `GetVstoObject` metoda jako součást procesu vytváření ovládacích prvků. Není potřeba přidat samostatné volání `GetVstoObject` metoda odebrat obálky ActiveX v tomto scénáři.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Před zavření dokumentu odebrat dynamických ovládacích prvků

Vaše doplňku VSTO můžete explicitně odebrat každý dynamické řízení z dokumentu před zavření dokumentu. Tento postup je užitečný pro dokumenty, které mohla být předána do jiných uživatelů, kteří nemají VSTO doplněk nainstalován.

Následující příklad kódu ukazuje, jak odebrat všechny ovládací prvky Windows Forms z dokumentu aplikace Word při zavření v dokumentu.

[!code-vb[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#10)]
[!code-csharp[Trin_WordAddInDynamicControls#10](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#10)]

## <a name="see-also"></a>Viz také:

- [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
