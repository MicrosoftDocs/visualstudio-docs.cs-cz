---
title: Usnadnění v projektech pro systém Office
description: Přečtěte si, jak systém Microsoft Office projekty obsahují mnoho funkcí usnadnění, které vám umožní vytvářet vlastní řešení, která splňují standardní požadavky na přístupnost.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4021517aa296f3c1e6355b82260b00590181f4cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955148"
---
# <a name="accessibility-in-office-projects"></a>Usnadnění v projektech pro systém Office

Microsoft Visual Studio a systém Microsoft Office obsahují mnoho funkcí pro usnadnění přístupu, které umožňují vytvářet vlastní řešení, která splňují standardní požadavky na přístupnost. Microsoft zveřejňuje pokyny pro přístupnost na webu. Podrobnosti najdete na [webu usnadnění](https://www.microsoft.com/accessibility/).

Ve většině případů projekty Office v sadě Visual Studio splňují standardy přístupnosti nebo zpřístupňují vlastnosti, které můžete nastavit tak, aby vaše řešení byla přístupná. Existují však některé funkce, které mají omezené usnadnění přístupu.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Přístupnost v době návrhu

### <a name="use-shortcut-keys-in-document-level-projects"></a>Použití klávesových zkratek v projektech na úrovni dokumentu
 Systém Microsoft Office když je v aplikaci Visual Studio otevřený dokument aplikace Word nebo excelový sešit aplikace systém Microsoft Office, obdrží příkazy klávesových zkratek jenom jedna aplikace v jednom okamžiku. Ve výchozím nastavení Visual Studio obdrží všechny příkazy klávesových zkratek, ale Word nebo Excel je přijme, když na stránce **nastavení klávesnice** v dialogovém okně **Možnosti** vyberete možnost **Dynamická klávesnice** . Další informace najdete v tématu [systém Microsoft Office klávesnice Word, nastavení systém Microsoft Office klávesnice, dialogové okno Možnosti](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) a [systém Microsoft Office klávesnicí aplikace Excel, systém Microsoft Office nastavení klávesnice, dialogové okno Možnosti](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Zobrazení klávesových zkratek pro pás karet v projektech na úrovni dokumentu
 Když je v aplikaci Visual Studio otevřen dokument aplikace Word nebo excelový sešit, nelze stisknutím klávesy **ALT** zobrazit klávesové zkratky karet a ovládacích prvků na pásu karet. Chcete-li zobrazit klávesové zkratky v době, kdy je dokument nebo sešit otevřen v návrháři, proveďte následující kroky.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Zobrazení klávesových zkratek pro karty pásu karet a ovládací prvky v Návrháři

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **Možnosti**.

2. Rozbalte uzel **nástroje Office** a v případě potřeby vyberte **systém Microsoft Office klávesnice aplikace Excel** nebo **systém Microsoft Office Word**.

3. Vyberte **dynamické schéma klávesnice**.

     Zobrazí se zpráva, že je nutné restartovat aplikaci Visual Studio, aby se změna projevila.

4. Klikněte na **OK**.

5. Restartujte Visual Studio a znovu otevřete projekt.

6. Otevřete návrháře dokumentu nebo sešitu pro váš projekt.

7. Stisknutím klávesy **F6** Zobrazte klávesové zkratky pro pás karet.

## <a name="accessibility-at-run-time"></a>Přístupnost v době běhu

### <a name="windows-forms-controls-on-office-documents"></a>model Windows Forms ovládací prvky v dokumentech Office
 Model Windows Forms ovládací prvky zpřístupňují vlastnosti přístupnosti a poskytují informace o ovládacím prvku k pomůckám pro usnadnění přístupu, jako jsou třeba čtečky obrazovky. Tyto vlastnosti přístupnosti můžete využít, když jsou ovládací prvky v dokumentu Office v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [poskytnutí informací o usnadnění pro ovládací prvky ve formuláři Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Při spuštění model Windows Formsch ovládacích prvků v excelovém sešitu nebo v dokumentu aplikace Word je však k dispozici několik omezení přístupnosti.

- Nemůžete z jednoho ovládacího prvku tabulátor na jiný.

- Ovládací prvky v dokumentu jsou zakázané, když změníte nastavení přiblížení dokumentu na jinou hodnotu než 100%.

  Informace o omezeních ovládacích prvků model Windows Forms v dokumentech najdete v tématu [omezení model Windows Forms ovládacích prvků v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Podokna akcí a vlastní podokna úloh
 Pokud má podokno akce nebo vlastní podokno úloh fokus, získáte přístup k řízení stejným způsobem jako při přístupu k ovládacím prvkům aplikace model Windows Forms. Pokud chcete přesunout kurzor mezi podoknem Akce a dokumentem, můžete stisknout klávesu **F6**.

 Další informace o podoknech akcí a vlastních podoknech úloh najdete v části [Přehled podokna akce](../vsto/actions-pane-overview.md) a [vlastní podokna úloh](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Režimy zobrazení

Visual Studio má následující omezení související se režimy zobrazení:

- Ovládací prvky dokumentu aplikace Word nebo excelového listu jsou při změně nastavení přiblížení dokumentu na jinou hodnotu než 100% zakázané.

- V dialogovém okně **Nový projekt** se nezobrazí ovládací prvky správně, pokud uživatel změní možnosti přístupnosti počítače na **použití vysoký kontrast**.

Tato omezení můžete překonat pomocí lupy. Lupa je zobrazovací nástroj ve Windows, který vytvoří samostatné okno, ve kterém se zobrazí zvětšená část obrazovky.

## <a name="see-also"></a>Viz také

- [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Usnadnění pro osoby s postižením](../ide/reference/accessibility-features-of-visual-studio.md)
- [Funkce usnadnění v aplikaci Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)