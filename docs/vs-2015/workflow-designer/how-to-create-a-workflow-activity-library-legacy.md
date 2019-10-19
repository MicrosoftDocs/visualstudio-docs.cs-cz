---
title: 'Postupy: Vytvoření knihovny aktivity pracovního postupu (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5bc4566c1ea520ac1050227ac8e4c0aee22e617
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604965"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Postupy: Vytvoření knihovny aktivity pracovního postupu (starší verze)
Postupujte podle těchto kroků a vytvořte projekt knihovny aktivit pracovního postupu pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytované [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Starší verze [!INCLUDE[wfd2](../includes/wfd2-md.md)] použijte, pokud potřebujete cílit buď na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)], nebo na [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-workflow-activity-library-project"></a>Vytvoření projektu knihovny aktivity pracovního postupu

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V rozevíracím seznamu v horní části okna **Nový projekt** vyberte buď možnost **.NET Framework 3,0** nebo možnost **.NET Framework 3,5** pro přístup ke staršímu návrháři.

    > [!NOTE]
    > Výchozí možnost v [!INCLUDE[vs2010](../includes/vs2010-md.md)] je **.NET Framework 4**. Tato možnost slouží k vytváření [!INCLUDE[wf](../includes/wf-md.md)] aplikací cílících na [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] a nepoužívá starší verze návrháře.

4. V podokně **typy projektů** vyberte možnost Visual C# nebo Visual Basic (v části **jiné jazyky**) a pak vyberte možnost **pracovní postup**.

5. V podokně **šablony** vyberte možnost **Knihovna aktivit pracovního postupu**.

6. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

7. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

     Pokud chcete vytvořit adresář řešení pro projekt, zaškrtněte políčko **vytvořit adresář pro řešení** a zadejte název do pole **název řešení** .

8. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také
 [Vytváření projektů pro starší](../workflow-designer/creating-legacy-workflow-projects.md) verze pracovního postupu pomocí starších aktivit pracovních postupů [návrháře aktivit](../workflow-designer/using-the-legacy-activity-designer.md) [](../workflow-designer/legacy-workflow-activities.md) [vývoj aktivit pracovních postupů](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52) [programovací model Windows Workflow Foundation aktivitách](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)