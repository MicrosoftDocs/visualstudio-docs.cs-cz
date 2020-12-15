---
title: Omezení model Windows Formsch ovládacích prvků v dokumentech Office
description: Přečtěte si o omezeních metod a vlastností ovládacích prvků model Windows Forms v dokumentu systém Microsoft Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63459f4daf1f9fe717946491a997ba47510fbab8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524456"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Omezení model Windows Formsch ovládacích prvků v dokumentech Office

Mezi ovládacími prvky model Windows Forms, které jsou přidány do systém Microsoft Office dokumentů aplikace Word nebo systém Microsoft Office listů aplikace Excel, existují rozdíly a model Windows Forms ovládací prvky, které jsou přidány do model Windows Forms. Například když přidáte <xref:Microsoft.Office.Tools.Word.Controls.Button> ovládací prvek do dokumentu, vlastnosti, například,, a nebudete se <xref:System.Windows.Forms.Control.Dock> chovat, <xref:System.Windows.Forms.Control.Anchor> <xref:System.Windows.Forms.Control.TabIndex> jak očekáváte.

Mnohé z těchto rozdílů způsobují způsob, jakým jsou model Windows Forms ovládací prvky hostovány v dokumentech. Při přidání ovládacího prvku model Windows Forms do dokumentu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vloží ovládací prvek ActiveX, který potom hostuje ovládací prvek model Windows Forms v dokumentu. Ovládací prvek model Windows Forms není vložen přímo do dokumentu.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Omezení metod a vlastností model Windows Formsch ovládacích prvků

Existuje několik metod a vlastností model Windows Formsch ovládacích prvků, které nefungují stejným způsobem na dokumentu, protože by byly ve formuláři Windows a proto se nedoporučuje používat. Například nastavení vlastností, například <xref:System.Windows.Forms.Control.Dock> a <xref:System.Windows.Forms.Control.Anchor> ovlivňuje pouze pozici ovládacího prvku s ohledem na ovládací prvek ActiveX kontejneru místo dokumentu. Následuje seznam nepodporovaných metod a vlastností model Windows Forms ovládacích prvků pro Word a Excel:

- Nepodporované vlastnosti ovládacích prvků Excelu:

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Nepodporované metody a vlastnosti ovládacích prvků aplikace Word:

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Nemůžete také nastavit <xref:System.Windows.Forms.Control.Left> <xref:System.Windows.Forms.Control.Top> vlastnost nebo model Windows Formsch ovládacích prvků, které jsou v dokumentu aplikace Word v souladu s textem. Ovládací prvky model Windows Forms jsou přidány v řádku s textem v následujících případech:

- Programově přidáte ovládací prvek do dokumentu aplikace Word a použijete metodu, která určuje rozsah umístění.

- Ovládací prvek model Windows Forms přidáte do dokumentu aplikace Word v době návrhu. Můžete to změnit úpravou ovládacího prvku v návrháři.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Rozdíly mezi ovládacími prvky model Windows Forms v dokumentech Office

Ovládací prvky model Windows Forms obvykle mají stejné chování jako v dokumentu Office ve formuláři Windows, ale některé rozdíly existují. Následující tabulka popisuje rozdíly, které existují pro model Windows Forms ovládací prvky v dokumentech Office.

|Funkce|Rozdíl|
|-------------------|----------------|
|Pořadí karet ovládacích prvků|Ovládací prvky, které jsou umístěny na excelový sešit nebo wordový dokument, nemůžete tabulátorem.|
|Seskupení ovládacích prvků|Ovládací prvek nelze použít <xref:System.Windows.Forms.GroupBox> k zahrnutí dalších ovládacích prvků v dokumentu Office. Když přidáte více přepínačů přímo do dokumentu, přepínače se vzájemně nevylučují. Můžete napsat kód, aby se přepínače vzájemně vylučují; upřednostňovaným přístupem však je přidat přepínače do uživatelského ovládacího prvku a následně přidat uživatelský ovládací prvek do dokumentu. Další informace naleznete v ukázce ukázka nebo ukázka v aplikaci Excel v [ukázkách vývoje pro systém Office a v návodech](../vsto/office-development-samples-and-walkthroughs.md).|
|Typ ovládacího prvku|Model Windows Forms ovládací prvky používané v dokumentech jsou zabaleny do třídy poskytované rozhraním [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , které poskytuje ovládací prvky pro další funkce specifické pro excelový sešit nebo wordový dokument. Například pokud máte ovládací prvek **tlačítko** na listu aplikace Excel, nezapomeňte zadat typ jako <xref:Microsoft.Office.Tools.Excel.Controls.Button> místo <xref:System.Windows.Forms.Button> při odkazování nebo přetypování objektu.|
|Pozice a velikost ovládacího prvku|Velikost a poloha ovládacího prvku jsou určeny vlastnostmi, které jsou součástí kontejneru ovládacího prvku ActiveX. Vlastnosti ovládacího prvku ActiveX mají jiné hodnoty než ekvivalentní vlastnosti ovládacího prvku model Windows Forms. Když nastavíte `Top` vlastnosti, `Left` , `Height` nebo `Width` ovládacího prvku, je měřeno v bodech, nikoli v pixelech.|
|Pozice ovládacího prvku u dokumentů aplikace Word|Pokud přidáte ovládací prvky do rozložení založeného na toku, pamatujte na to, že ovládací prvky budou s obsahem předávány jako změny obsahu. Ovládací prvek nelze ukotvit k odstavci, když jej přetáhnete ze **sady nástrojů** , protože ovládací prvek je přidán do dokumentu aplikace Word na řádku s textem. Použijete-li k přidání ovládacího prvku jinou metodu, například Poklikáním na ovládací prvek, ovládací prvek bude vložen podle možnosti Wordu, kterou jste nastavili pro vložení obrázků.<br /><br /> Nelze nastavit `Left` `Top` vlastnost nebo ovládacího prvku, který je vložen s textem.<br /><br /> Ovládací prvky nelze umístit v záhlaví nebo zápatí nebo v rámci vnořeného dokumentu.|
|Události ovládacích prvků|Když je vybrán ovládací prvek, vyvolá události v následujícím pořadí:<br /><br /> první.  `Enter`<br />odst.  `GotFocus`<br /><br /> Když je ovládací prvek nevybraný, vyvolá události v následujícím pořadí:<br /><br /> první.  `Leave`<br />odst.  `Validating`<br />1.  `Validated`<br />4.  `LostFocus`|
|Škálování ovládacího prvku|Když změníte nastavení přiblížení dokumentu na jinou hodnotu než 100%, ovládací prvky jsou zakázané, ale zdá se, že se škálují s dokumentem. Pokud například kliknete na tlačítko v případě, že je dokument v 130% přiblížení, zobrazí se zpráva, že byl ovládací prvek zakázán, dokud není přiblížení nastaveno na 100%. Pokud změníte přiblížení na 100%, ovládací prvky budou fungovat správně.|
|Hodnoty vlastností ovládacího prvku|I když vlastnosti ovládacích prvků ve formuláři Windows jsou nastaveny na celočíselnou hodnotu, jsou nastaveny na jeden pro ovládací prvky v dokumentu aplikace Word. V aplikaci Excel jsou hodnoty vlastností ovládacích prvků nastaveny na hodnotu Double. Pokud `Height` vlastnost a `Width` ovládacího prvku na listu překročí velikost listu nebo obrazovky, hodnota se zkrátí.|
|Změna velikosti ovládacího prvku|Pokud změníte velikost ovládacího prvku v dokumentu pomocí jednoho z osmi úchytů pro změnu velikosti, nové rozměry ovládacího prvku se neprojeví v okně **vlastnosti** , dokud nebude ovládací prvek znovu vybrán.|
|Chování ovládacího prvku|Ovládací prvky v excelovém listu se můžou při rozdělení okna listu chovat nepředvídatelné. Například přístup k portálu <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> na list může být k dispozici pouze v jednom z oken.|
|Řízení názvů|K ovládacím prvkům pojmenování nelze použít vyhrazená slova. Například pokud přidáte <xref:Microsoft.Office.Tools.Excel.Controls.Button> do listu a změníte název na **systém**, dojde k chybám při sestavování projektu.|
|Přidávání ovládacích prvků prostřednictvím kódu programu|Nepoužívejte konstruktor ovládacího prvku pro přidání ovládacího prvku do dokumentu v době běhu. Místo toho použijte pomocné metody, které poskytuje [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Například použijte <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> metodu pro přidání tlačítka do listu. Chcete-li přidat ovládací prvek, který není podporován těmito podpůrnými metodami, můžete použít `AddControl` metodu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Kopírování ovládacích prvků|Pokud zkopírujete ovládací prvek model Windows Forms a vložíte ho do dokumentu za běhu, vloží se do dokumentu prázdný ovládací prvek ActiveX kontejneru. Ovládací prvek model Windows Forms se nezobrazuje v novém umístění a kód na pozadí původního ovládacího prvku není zkopírován do ovládacího prvku ActiveX kontejneru.|

## <a name="limitations-in-document-level-projects"></a>Omezení v projektech na úrovni dokumentu

Některá omezení používání model Windows Formsch ovládacích prvků v dokumentech jsou jedinečná pro projekty na úrovni dokumentu.

### <a name="control-support-at-design-time"></a>Podpora řízení v době návrhu

Některé ovládací prvky model Windows Forms jsou odebrány ze **sady nástrojů** , když je sešit aplikace Excel nebo dokument aplikace Word otevřen v návrháři aplikace Visual Studio. Důvodem je technické omezení nebo skutečnost, že funkce jsou již k dispozici v aplikaci Word nebo Excel. Projekty aplikace Excel a Word podporují všechny model Windows Forms ovládací prvky a další komponenty, které se zobrazí v sadě **nástrojů** , když se dokument zaměřuje na fokus, a můžete také přidat ovládací prvky třetích stran do listu nebo dokumentu.

> [!NOTE]
> Všechny ovládací prvky jsou odstraněny ze **sady nástrojů** , když je dokument chráněn. Informace o ochraně dokumentu najdete v tématu [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Aby bylo možné použít v řešení Office, musí mít ovládací prvky třetích stran <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut nastaven na **hodnotu true** .

Následující ovládací prvky a komponenty nejsou k dispozici v sadě **nástrojů**:

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

### <a name="support-for-legacy-activex-controls"></a>Podpora pro starší ovládací prvky ActiveX

Pokud vytvoříte projekt na úrovni dokumentu Office, který používá existující dokument aplikace Word nebo excelový sešit, který obsahuje ovládací prvky ActiveX, funkce ovládacích prvků ActiveX se neztratí. není však k dispozici podpora pro přidání nových ovládacích prvků ActiveX do dokumentů z aplikace Visual Studio. Například pokud má vaše aplikace Word tlačítko z panelu nástrojů **ovládacího prvku** , který spouští makro jazyk Visual Basic for Application (VBA), bude pokračovat v spuštění makra po použití dokumentu v projektu sady Office. Doporučuje se ale odebrat ovládací prvky ActiveX a makra VBA a nahradit je model Windows Formsmi ovládacími prvky a spravovaným kódem.

## <a name="see-also"></a>Viz také

- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
