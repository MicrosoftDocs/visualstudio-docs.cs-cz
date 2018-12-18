---
title: Omezení ovládacích prvků Windows Forms v dokumentech Office
ms.date: 02/02/2017
ms.technology: office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 104b8b3449b2ffb689caf66d5c180817b633f83e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572956"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Omezení ovládacích prvků Windows Forms v dokumentech Office

Existují určité rozdíly mezi ovládacími prvky Windows Forms, které jsou přidány do dokumentů aplikace Microsoft Office Word nebo sešitů aplikace Microsoft Office Excel a ovládací prvky Windows Forms, které jsou přidány do Windows Forms. Například když přidáte <xref:Microsoft.Office.Tools.Word.Controls.Button> řídit k dokumentu, vlastnosti, jako <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, a <xref:System.Windows.Forms.Control.TabIndex> nefungují tak, jak by se dalo očekávat.

Řadu tyto rozdíly jsou způsobena tím, že Windows Forms – ovládací prvky jsou hostované na dokumentech. Při přidání ovládacího prvku Windows Forms k dokumentu, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vložení ovládacího prvku ActiveX, který je hostitelem pak ovládacího prvku Windows Forms v dokumentu. Ovládací prvek Windows Forms není vložených přímo v dokumentu.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Omezení metod a vlastností ovládacích prvků Windows Forms

Existuje několik metod a vlastností ovládacích prvků Windows Forms, které nefungují stejným způsobem jako v dokumentu, jako kdyby je sdíleli ve formuláři Windows, a proto se doporučuje, aby se nepoužívaly. Například nastavení vlastností <xref:System.Windows.Forms.Control.Dock> a <xref:System.Windows.Forms.Control.Anchor> má vliv pouze na pozici řízení s ohledem na ovládací prvek ActiveX kontejneru, nikoli dokumentu. Následuje seznam nepodporovaných metod a vlastností ovládacích prvků Windows Forms pro Word a Excel:

- Nepodporované vlastnosti ovládací prvky aplikace Excel:

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- Nepodporované metody a vlastnosti ovládací prvky aplikace Word:

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

Také nelze nastavit <xref:System.Windows.Forms.Control.Left> nebo <xref:System.Windows.Forms.Control.Top> vlastnosti ovládacích prvků Windows Forms, které odpovídají text na dokument aplikace Word. Ovládací prvky Windows Forms přidají v textu v následujících případech:

- Přidání ovládacího prvku na dokument aplikace Word prostřednictvím kódu programu a použít metodu, která určuje rozsah pro umístění.

- Dokument aplikace Word přidáte ovládacího prvku Windows Forms v době návrhu. Toto můžete změnit úpravou ovládacího prvku v návrháři.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Rozdíly v ovládacích prvcích Windows Forms v dokumentech Office

Ovládací prvky Windows Forms obecně mít stejné chování na dokument Office, jako se ve formuláři Windows, ale existují určité rozdíly. Následující tabulka popisuje rozdíly, které jsou pro ovládací prvky Windows Forms v dokumentech Office.

|Funkce|Rozdíl|
|-------------------|----------------|
|Pořadí karet ovládacího prvku|Nelze kartě prostřednictvím ovládací prvky na sešitu aplikace Excel nebo dokument aplikace Word.|
|Seskupení ovládací prvek|Nelze použít <xref:System.Windows.Forms.GroupBox> ovládacího prvku tak, aby obsahovala další ovládací prvky v dokumentu systému Office. Když přidáte více přepínačů přímo k dokumentu, přepínací tlačítka se vzájemně nevylučují. Můžete napsat kód, aby přepínací tlačítka se vzájemně vylučují. je však žádoucí přidat uživatelský ovládací prvek přepínačů a potom přidat uživatelský ovládací prvek v dokumentu. Další informace najdete v tématu Ukázka ovládací prvky aplikace Word nebo ukázku ovládací prvky aplikace Excel najdete na adrese [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).|
|– Typ ovládacího prvku|Ovládacích prvků Windows Forms v dokumentech jsou uzavřen do třídy poskytované [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] udávající další funkce, které jsou specifické pro ovládací prvky pro sešit aplikace Excel nebo dokument aplikace Word. Pokud máte například **tlačítko** řízení na listu aplikace Excel, je nutné zadat typ jako <xref:Microsoft.Office.Tools.Excel.Controls.Button> místo <xref:System.Windows.Forms.Button> při odkazování na nebo přetypování objektu.|
|Ovládací prvek pozice a velikosti|Velikost a umístění ovládacího prvku je určen podle vlastnosti, které jsou součástí kontejneru ovládacího prvku ActiveX. Vlastnosti ovládacích prvků ActiveX trvat jiné hodnoty než ekvivalentní vlastností ovládacího prvku Windows Forms. Když nastavíte `Top`, `Left`, `Height`, nebo `Width` vlastností ovládacího prvku se měří v bodů namísto pixelů.|
|Umístění v ovládacím prvku na dokumenty aplikace Word|Pokud přidáte na základě toku rozložení ovládacích prvků, mějte na paměti, že budou ovládací prvky toku s obsahem jako změny obsahu. Ovládací prvek pro odstavec nelze ukotvení, při přetažení z **sada nástrojů** vzhledem k tomu, že je ovládací prvek přidán na dokument aplikace Word v textu. Pokud použijete jinou metodu přidání ovládacího prvku, jako je například poklepáním na ovládací prvek, je podle možnost slovo, které jste nastavili pro vložení obrázků vložit ovládací prvek.<br /><br /> Nelze nastavit `Left` nebo `Top` vlastností ovládacího prvku, který je vložený s textem.<br /><br /> Ovládací prvky nelze umístit v záhlaví nebo zápatí stránky, nebo v rámci vnořeného dokumentu.|
|Události ovládacího prvku|Pokud je vybraný ovládací prvek, vyvolá události v následujícím pořadí:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Když ovládací prvek není vybraná, vyvolá události v následujícím pořadí:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Změna velikosti ovládacího prvku|Když změníte nastavení přiblížení či oddálení dokumentu na jakoukoli jinou hodnotu než 100 %, ovládací prvky jsou zakázány, i když se objeví na škálování se dokumentu. Například pokud klepnete na tlačítko, když váš dokument 130 % zvětšení, se zobrazí zpráva, ovládacího prvku byla zakázána, dokud se nenastaví zvětšení na 100 %. Ovládací prvky bude fungovat správně při změně přiblížení na 100 %.|
|Hodnoty vlastností ovládacího prvku|I když jsou vlastnosti ovládacích prvků ve formuláři Windows nastavené na celočíselnou hodnotu, jsou nastaveny na jednu pro ovládací prvky na dokument aplikace Word. V aplikaci Excel jsou nastavené hodnoty vlastností ovládacích prvků na dvojitou hodnotu. Pokud `Height` a `Width` vlastností ovládacího prvku na listu je větší než velikost listu nebo obrazovky, hodnota je oříznuta.|
|Změna velikosti ovládacího prvku|Pokud změníte velikost ovládacího prvku na dokumentu pomocí jedné z osmi úchyty, nový ovládací prvek dimenze se neprojeví v **vlastnosti** okno, dokud je znovu vybrány ovládacího prvku.|
|Chování ovládacího prvku|Ovládací prvky v listu aplikace Excel může nepředvídatelné chování, když okno listu je rozděleno. Například přístup k <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> na listu může být k dispozici pouze v jednom ze systému windows.|
|Názvy ovládacího prvku|Vyhrazená slova k ovládacím prvkům název nelze použít. Například, pokud přidáte <xref:Microsoft.Office.Tools.Excel.Controls.Button> do listu a změňte název **systému**, při sestavování projektu dojít k chybám.|
|Přidání ovládacích prvků prostřednictvím kódu programu|Přidání ovládacího prvku do dokumentu za běhu nepoužívejte konstruktoru ovládacího prvku. Místo toho použijte pomocné metody poskytované [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Například použít <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> metodu za účelem přidání tlačítka do listu. Pokud chcete přidat ovládací prvek, který nepodporuje tyto metody helper, můžete použít `AddControl` metoda. Další informace najdete v tématu [přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Kopírování ovládacích prvků|Pokud zkopírujete ovládacího prvku Windows Forms a vložte jej do dokumentu za běhu, prázdný kontejner ovládacího prvku ActiveX je vložen do dokumentu. Ovládací prvek Windows Forms nezobrazí v novém umístění a kódu na pozadí ovládacího prvku původní není zkopírovat do kontejneru ovládacího prvku ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Omezení v projekty na úrovni dokumentu

Některá omezení používání ovládacích prvků Windows Forms v dokumentech jsou jedinečné pro projekty na úrovni dokumentu.

### <a name="control-support-at-design-time"></a>Podpora ovládacího prvku v době návrhu

Některé ovládací prvky Windows Forms se odeberou z **sada nástrojů** když je otevřen v návrháři Visual Studio sešitu aplikace Excel nebo dokument aplikace Word. Toto je z důvodu technická omezení nebo proto, že funkce je již k dispozici v rámci Word či Excel. Projekty aplikace Excel a Word podporovat všechny ovládací prvky Windows Forms a další součásti, které se zobrazují v **sada nástrojů** když dokument má právě fokus a jiných ovládacích prvků můžete také přidat do listu nebo dokumentu.

> [!NOTE]
> Všechny ovládací prvky jsou odebrány z **sada nástrojů** když je dokument chráněný. Informace o ochraně dokumentů najdete v tématu [dokumentu ochrany v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Ovládací prvky třetích stran, musí mít <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut nastaven na **true** aby bylo možné použít v řešení Office.

Následující ovládací prvky a součásti nejsou k dispozici v **sada nástrojů**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Podpora pro starší verze ovládací prvky ActiveX

Pokud vytvoříte projekt úrovni dokumentů Office, která používá stávající dokument aplikace Word nebo sešitu aplikace Excel, která obsahuje ovládací prvky ActiveX, není ztraceny; funkci ovládacích prvků ActiveX neexistuje však žádná podpora pro přidání nových ovládacích prvků ActiveX do dokumentů z Visual Studia. Například, pokud má tlačítko z dokumentu aplikace Word **řízení** sada nástrojů, který spouští Visual Basic for Applications (VBA) – makro, se bude nadále spouštět makro po dokumentu používá v projektech Office. Doporučujeme však odebrat ovládací prvky ActiveX a makra VBA a nahraďte ovládací prvky Windows Forms a spravovaného kódu.

## <a name="see-also"></a>Viz také:

- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Ovládací prvky Windows Forms na přehled dokumenty sady Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Přidání ovládacích prvků do dokumentů Office za běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Postupy: Přidání ovládacích prvků Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)