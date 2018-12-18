---
title: Usnadnění v projektech pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c39a68d13e2fd3d4932e169e713ed8534e0d266
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305127"
---
# <a name="accessibility-in-office-projects"></a>Usnadnění v projektech pro systém Office
  Microsoft Visual Studio a Microsoft Office zahrnout mnoho funkcí usnadnění, které vám umožní sestavovat vlastní řešení, které splňují požadavky na standardní usnadnění přístupu. Microsoft zveřejňuje pokyny pro přístupnost na webu. Podrobnosti najdete v tématu [webu usnadnění](http://go.microsoft.com/fwlink/?LinkID=37113).  

 Ve většině případů splňovat projektech pro systém Office v sadě Visual Studio usnadnění standardy nebo zveřejňuje vlastnosti, které lze nastavit na zpřístupnit vaše řešení. Existují však některé funkce, které mají omezenou dostupnost.  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>Usnadnění přístupu v době návrhu  

### <a name="use-shortcut-keys-in-document-level-projects"></a>Použití klávesových zkratek v projektech na úrovni dokumentu  
 V otevřeném dokumentu aplikace Microsoft Office Word nebo sešitu aplikace Microsoft Office Excel v sadě Visual Studio, obdrží jenom jednu aplikaci v čase klíče příkazy místní. Ve výchozím nastavení, Visual Studio přijímá všechny místní klíče příkazy, ale může být Word nebo Excel přijímat, když je dokument fokus tak, že vyberete **chéma dynamické klávesnice** na **nastavení klávesnice** stránky nástroje **možnosti** dialogové okno. Další informace najdete v tématu [klávesnice Microsoft Office Word, nastavení klávesnice Microsoft Office, dialogové okno Možnosti](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) a [klávesnice Microsoft Office Excel, nastavení klávesnice Microsoft Office, dialogové okno Možnosti](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Zobrazí klávesové zkratky pro pás karet v projektech na úrovni dokumentu  
 Při otevření v sadě Visual Studio Wordového dokumentu nebo Excelového sešitu nejde stisknout klávesa **Alt** klíče zobrazíte klávesové zkratky pro ovládací prvky na pásu karet a karty. Chcete-li zobrazit klávesové zkratky, zatímco je otevřen v Návrháři dokumentem nebo sešitem, proveďte následující kroky.  

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Chcete-li zobrazit klávesové zkratky pro pás karet a ovládacích prvků v Návrháři  

1.  V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  

2.  Rozbalte **nástroje Office** uzel a vyberte možnost **klávesnice Microsoft Office Excel** nebo **klávesnice Microsoft Office Word**podle potřeby.  

3.  Vyberte **chéma dynamické klávesnice**.  

     Zobrazí se zpráva s oznámením, že je třeba restartovat Visual Studio tato změna projevila.  

4.  Klikněte na tlačítko **OK**.  

5.  Restartujte Visual Studio a znovu otevřete projekt.  

6.  Otevření dokumentu nebo sešitu Návrháře projektu.  

7.  Stisknutím klávesy **F6** zobrazíte klávesové zkratky pro pás karet.  

## <a name="accessibility-at-runtime"></a>Usnadnění přístupu za běhu  

### <a name="windows-forms-controls-on-office-documents"></a>Ovládací prvky Windows Forms v dokumentech Office  
 Ovládací prvky Windows Forms vystavit vlastnosti usnadnění poskytnout informace o ovládacím prvku pro usnadnění, například čtečky obrazovky. Můžete využít výhod tyto vlastnosti usnadnění přístupu, když jsou ovládací prvky v dokumentu systému Office v přizpůsobení na úrovni dokumentu. Další informace najdete v tématu [poskytují informace o usnadnění pro ovládací prvky ve formuláři Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  

 Existují však některá omezení usnadnění přístupu za běhu při ovládacích prvků Windows Forms jsou hostované na Excelový sešit nebo dokument aplikace Word:  

- Nelze kartu z jednoho ovládacího prvku do jiného.  

- Ovládací prvky v dokumentu zakázány, když se změní nastavení přiblížení dokumentu na jinou hodnotu než 100 %.  

  Informace o omezeních ovládacích prvků Windows Forms v dokumentech, najdete v části [omezení Windows Forms ovládací prvky v dokumentech Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  

### <a name="actions-panes-and-custom-task-panes"></a>Podokna akcí a vlastních podoken úloh  
 Když je podokna akcí nebo vlastního podokna úloh fokus, můžete ovládací prvky přístupu stejným způsobem, jakým přistupujete by ovládací prvky v aplikaci Windows Forms. Přesunutím kurzoru mezi podoknem akcí a dokumentu, můžete stisknutím **F6**.  

 Další informace o podoknech akcí a vlastních podoken úloh najdete v tématu [přehled podokna akcí](../vsto/actions-pane-overview.md) a [vlastní podokna úloh](../vsto/custom-task-panes.md).  

### <a name="display-modes"></a>Režimy zobrazení  
 Visual Studio má následující omezení související s režimy zobrazení:  

- Ovládací prvky ve Wordovém dokumentu nebo Excelového listu jsou zakázané, když se změní nastavení přiblížení dokumentu na jinou hodnotu než 100 %.  

- **Nový projekt** dialogové okno zobrazit ovládací prvky správně, jestliže uživatel změní možnosti usnadnění přístupu počítače a **vysoký kontrast – použití**.  

  Lupa můžete použít k překonání těchto omezení. Lupa je nástroj, který zobrazení ve Windows, který vytvoří samostatné okno zobrazující zvětšená část obrazovky.  

## <a name="see-also"></a>Viz také:  
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)   
 [Usnadnění pro postižené osoby](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Funkce pro usnadnění přístupu sady Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
