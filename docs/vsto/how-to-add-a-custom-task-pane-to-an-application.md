---
title: 'Postupy: Přidání vlastního podokna úloh do aplikace'
description: Přečtěte si, jak můžete do aplikací přidat vlastní podokno úloh pomocí doplňku Visual Studio Tools for Office (VSTO).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b0bac1f14994dea73526aa3684851412ad2cf1b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910200"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Postupy: Přidání vlastního podokna úloh do aplikace
  Pomocí doplňku VSTO můžete přidat vlastní podokno úloh k aplikacím uvedeným výše. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="add-a-custom-task-pane-to-an-application"></a>Přidání vlastního podokna úloh do aplikace

### <a name="to-add-a-custom-task-pane-to-an-application"></a>Přidání vlastního podokna úloh do aplikace

1. Otevřete nebo vytvořte projekt doplňku VSTO pro jednu z výše uvedených aplikací. Další informace najdete v tématu [Postupy: vytváření projektů pro systém Office v sadě Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. V nabídce **projekt** klikněte na příkaz **Přidat uživatelský ovládací prvek**.

3. V dialogovém okně **Přidat novou položku** změňte název nového uživatelského ovládacího prvku na **MyUserControl** a potom klikněte na tlačítko **Přidat**.

     Uživatelský ovládací prvek se otevře v návrháři.

4. Přidejte jeden nebo více ovládacích prvků model Windows Forms z **panelu nástrojů** do uživatelského ovládacího prvku.

5. Otevřete soubor kódu **ThisAddIn.cs** nebo **ThisAddIn. vb** .

6. Do třídy `ThisAddIn` přidejte následující kód. Tento kód deklaruje instance `MyUserControl` a <xref:Microsoft.Office.Tools.CustomTaskPane> jako členy `ThisAddIn` třídy.

     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]

7. Přidejte následující kód do `ThisAddIn_Startup` obslužné rutiny události. Tento kód vytvoří nový <xref:Microsoft.Office.Tools.CustomTaskPane> přidáním `MyUserControl` objektu do `CustomTaskPanes` kolekce. Kód také zobrazí podokno úloh.

     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]

    > [!NOTE]
    > Tento kód přidruží vlastní podokno úloh k aktivnímu oknu v aplikaci. U některých aplikací je vhodné upravit tento kód, aby se zobrazilo podokno úloh s dalšími dokumenty nebo položkami v aplikaci. Další informace najdete v tématu [vlastní podokna úloh](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Viz také
- [Přizpůsobení uživatelského rozhraní systému Office](../vsto/office-ui-customization.md)
- [Vlastní podokna úloh](../vsto/custom-task-panes.md)
- [Návod: automatizace aplikace z vlastního podokna úloh](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
