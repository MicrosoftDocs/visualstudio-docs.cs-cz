---
title: 'Postupy: skrytí ovládacích prvků na listech při tisku'
description: Naučte se, že ovládací prvky můžete skrýt při tisku systém Microsoft Office excelového listu, který obsahuje ovládací prvky model Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d87da5c22969fc355fe473e9505c61429b8023f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934803"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Postupy: skrytí ovládacích prvků na listech při tisku
  Když tisknete systém Microsoft Office excelový dokument, který obsahuje ovládací prvky model Windows Forms, ovládací prvky se zobrazí na vytištěném listu. Ovládací prvky lze skrýt při tisku listu.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Pokud skryjete ovládací prvky, které zobrazují data, jako například <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> , data v ovládacím prvku nebudou viditelná na vytištěném listu.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Skrytí ovládacích prvků při tisku listu

1. Vytvořte nebo otevřete excelový projekt v aplikaci Visual Studio a ověřte, zda je v Návrháři zobrazená **List1** . Informace o vytváření projektů naleznete v tématu [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na kartě **běžné ovládací prvky** **panelu nástrojů** přetáhněte <xref:Microsoft.Office.Tools.Excel.Controls.Button> ovládací prvek na buňku v `Sheet1` .

3. V okně **vlastnosti** nastavte <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> vlastnost na **hodnotu NEPRAVDA**.

## <a name="see-also"></a>Viz také
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přehled model Windows Formsch ovládacích prvků v dokumentech Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Postupy: Přidání ovládacích prvků model Windows Forms do dokumentů Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Postupy: Změna velikosti ovládacích prvků v buňkách listu](../vsto/how-to-resize-controls-within-worksheet-cells.md)
