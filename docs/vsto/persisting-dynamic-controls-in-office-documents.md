---
title: Trvalé dynamické ovládací prvky v dokumentech Office
description: Zjistěte, jak můžete do svého řešení přidat kód pro opětovné vytvoření trvalých dynamických ovládacích prvků, když uživatel znovu otevře uzavřený dokument.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9d42aa2d8594ed44e4fd4edbac8a0d64c4dc16da
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826145"
---
# <a name="persist-dynamic-controls-in-office-documents"></a>Trvalé dynamické ovládací prvky v dokumentech Office

Ovládací prvky přidané v době běhu nejsou trvalé, pokud je dokument nebo sešit uložen a zavřen. Přesné chování se liší pro ovládací prvky hostitele a model Windows Forms ovládací prvky. V obou případech můžete do svého řešení přidat kód pro opětovné vytvoření ovládacích prvků, když uživatel znovu otevře dokument.

Ovládací prvky, které přidáte do dokumentů v době běhu, se nazývají *dynamické ovládací prvky*. Další informace o dynamických ovládacích prvcích najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="persist-host-controls-in-the-document"></a>Zachovat ovládací prvky hostitele v dokumentu

Když se dokument uloží a pak zavře, všechny dynamické ovládací prvky hostitele se z dokumentu odeberou. Budou zachovány pouze základní nativní objekty Office. Například <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> hostitelský ovládací prvek se stal <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> . Nativní objekty Office nejsou připojené k událostem hostitelského ovládacího prvku a nemají funkce datové vazby tohoto hostitelského ovládacího prvku.

Následující tabulka uvádí nativní objekt Office, který je ponechán v dokumentu pro každý typ hostitelského ovládacího prvku.

|Typ řízení hostitele|Nativní typ objektu Office|
|-----------------------|-------------------------------|
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|

### <a name="re-create-dynamic-host-controls-when-documents-are-opened"></a>Znovu vytvořit dynamické ovládací prvky hostitele při otevření dokumentů

Můžete znovu vytvořit dynamické ovládací prvky hostitele místo existujících nativních ovládacích prvků pokaždé, když uživatel otevře dokument. Vytváření hostitelských ovládacích prvků tímto způsobem při otevření dokumentu simuluje prostředí, které mohou uživatelé očekávat.

Chcete-li znovu vytvořit hostitelský ovládací prvek pro Word nebo <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> pro ovládací prvek hostitele nebo pro aplikaci Excel, použijte `Add` \<*control class*> metodu <xref:Microsoft.Office.Tools.Excel.ControlCollection?displayProperty=fullName> objektu nebo <xref:Microsoft.Office.Tools.Word.ControlCollection?displayProperty=fullName> . Použijte metodu, která má parametr pro nativní objekt Office.

Například pokud chcete vytvořit <xref:Microsoft.Office.Tools.Excel.ListObject?displayProperty=fullName> hostitelský ovládací prvek z existující nativní <xref:Microsoft.Office.Interop.Excel.ListObject?displayProperty=fullName> , když je dokument otevřen, použijte <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> metodu a předejte existující <xref:Microsoft.Office.Interop.Excel.ListObject> . Následující příklad kódu ukazuje toto v projektu na úrovni dokumentu pro Excel. Kód znovu vytvoří dynamický <xref:Microsoft.Office.Tools.Excel.ListObject> , který je založen na existující <xref:Microsoft.Office.Interop.Excel.ListObject> pojmenované `MyListObject` ve `Sheet1` třídě.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookdynamiccontrols4/Sheet1.cs" id="Snippet6":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookdynamiccontrols4/Sheet1.vb" id="Snippet6":::

### <a name="re-create-chart"></a>Znovu vytvořit graf

Chcete-li znovu vytvořit <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> hostitelský ovládací prvek, je nutné nejprve odstranit nativní <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> a pak znovu vytvořit <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> pomocí <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> metody. Neexistuje žádná `Add` \<*control class*> metoda, která umožňuje vytvořit novou na <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> základě existující <xref:Microsoft.Office.Interop.Excel.Chart?displayProperty=fullName> .

Pokud nativní neodstraníte <xref:Microsoft.Office.Interop.Excel.Chart> , vytvoří se při opětovném vytvoření duplicitního grafu druhý <xref:Microsoft.Office.Tools.Excel.Chart?displayProperty=fullName> .

## <a name="persist-windows-forms-controls-in-documents"></a>Zachovat model Windows Forms ovládací prvky v dokumentech

Když se dokument uloží a pak zavře, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] automaticky odebere všechny dynamicky vytvořené model Windows Forms ovládací prvky z dokumentu. Chování se ale liší pro projekty doplňku na úrovni dokumentu a VSTO.

V přizpůsobení na úrovni dokumentu jsou ovládací prvky a jejich podkladové obálky ActiveX (které se používají k hostování ovládacích prvků v dokumentu) při příštím otevření dokumentu odebrány. Neexistuje žádné náznaky, že tam ovládací prvky byly někdy.

V doplňcích VSTO se ovládací prvky odeberou, ale v dokumentu zůstanou i obálky ActiveX. Když uživatel příště otevře dokument, zobrazí se obálky ActiveX. V aplikaci Excel jsou v obálkách ActiveX zobrazeny obrázky ovládacích prvků, jak se zobrazily při posledním uložení dokumentu. V aplikaci Word jsou obálky ActiveX neviditelné, pokud na ně uživatel neklikne, v takovém případě se zobrazí tečkovaná čára, která představuje ohraničení ovládacích prvků. Obálky ActiveX můžete odebrat několika způsoby. Další informace najdete v tématu [Odebrání obálek ActiveX v doplňku](#removingActiveX).

### <a name="re-create-windows-forms-controls-when-documents-are-opened"></a>Po otevření dokumentů znovu vytvořit model Windows Forms ovládací prvky

Odstraněné model Windows Forms ovládací prvky můžete znovu vytvořit, když uživatel znovu otevře dokument. K tomu vaše řešení musí provádět následující úlohy:

1. Uložení informací o velikosti, umístění a stavu ovládacích prvků při uložení nebo zavření dokumentu. V přizpůsobení na úrovni dokumentu můžete ukládat data do mezipaměti dat v dokumentu. V doplňku VSTO můžete data uložit do vlastní části XML v dokumentu.

2. Znovu vytvořte ovládací prvky v události, která je vyvolána při otevření dokumentu. V projektech na úrovni dokumentu můžete to provést v `Sheet`  `_Startup` `ThisDocument_Startup` rutinách n nebo. V projektech doplňku VSTO to můžete udělat v obslužných rutinách událostí pro <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> události nebo.

### <a name="remove-activex-wrappers-in-an-add-in"></a><a name="removingActiveX"></a> Odebrat obálky ActiveX v doplňku

Když do dokumentů přidáte dynamické ovládací prvky model Windows Forms pomocí doplňku VSTO, můžete zabránit tomu, aby se obálky ActiveX pro ovládací prvky v dokumentu při příštím otevření zobrazovaly následujícími způsoby.

#### <a name="remove-activex-wrappers-when-the-document-is-opened"></a>Při otevření dokumentu odebrat obálky ActiveX

Chcete-li odebrat všechny obálky ActiveX, zavolejte `GetVstoObject` metodu pro vygenerování položky hostitele pro <xref:Microsoft.Office.Interop.Word.Document> nebo <xref:Microsoft.Office.Interop.Excel.Workbook> , která představuje nově otevřený dokument. Chcete-li například odebrat všechny obálky ActiveX z wordového dokumentu, můžete zavolat `GetVstoObject` metodu pro vygenerování položky hostitele pro <xref:Microsoft.Office.Interop.Word.Document> objekt, který je předán obslužné rutině události pro <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> událost.

Tento postup je užitečný, když víte, že dokument bude otevřen pouze v počítačích s nainstalovaným doplňkem VSTO. Pokud je možné dokument předat jiným uživatelům, kteří nemají nainstalovaný doplněk VSTO, zvažte odebrání ovládacích prvků před zavřením dokumentu.

Následující příklad kódu ukazuje, jak zavolat `GetVstoObject` metodu při otevření dokumentu.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet11":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet11":::

Přestože se `GetVstoObject` Metoda používá primárně k vygenerování nové položky hostitele za běhu, tato metoda také vymaže všechny obálky ActiveX z dokumentu při prvním volání pro konkrétní dokument. Další informace o tom, jak používat tuto `GetVstoObject` metodu, najdete v tématu [rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

Pokud doplněk VSTO vytvoří dynamické ovládací prvky při otevření dokumentu, váš doplněk VSTO už tuto metodu zavolá `GetVstoObject` jako součást procesu vytváření ovládacích prvků. Nemusíte přidávat samostatné volání `GetVstoObject` metody pro odebrání obálek ActiveX v tomto scénáři.

#### <a name="remove-the-dynamic-controls-before-the-document-is-closed"></a>Odebrat dynamické ovládací prvky před zavřením dokumentu

Doplněk VSTO umožňuje explicitně odebrat každý dynamický ovládací prvek z dokumentu před zavřením dokumentu. Tento postup je vhodný pro dokumenty, které mohou být předány jiným uživatelům, kteří nemají nainstalovaný doplněk VSTO.

Následující příklad kódu ukazuje, jak odebrat všechny model Windows Forms ovládací prvky z dokumentu aplikace Word při zavření dokumentu.

:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet10":::
:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet10":::

## <a name="see-also"></a>Viz také

- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
