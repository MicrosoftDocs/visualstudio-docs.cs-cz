---
title: 'Postupy: Vytvoření knihovny pracovního postupu stavového stroje (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- projects, state machine workflow library
- state machine workflow libraries
- workflows, state machine workflow library
ms.assetid: 5bd68c6e-6a98-47d9-826d-9bb7a4fd72f8
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d3cff5d6aaa28915524b7699affdf41d3bebef4a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663382"
---
# <a name="how-to-create-a-state-machine-workflow-library-legacy"></a>Postupy: Vytvoření knihovny pracovního postupu stavového stroje (starší verze)
Postupujte podle těchto kroků a vytvořte projekt knihovny pracovního postupu stavového stroje pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytované [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Starší verze [!INCLUDE[wfd2](../includes/wfd2-md.md)] použijte, pokud potřebujete cílit buď na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)], nebo na [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-state-machine-workflow-library-project"></a>Vytvoření projektu knihovny pracovního postupu stavového stroje

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V rozevíracím seznamu v horní části okna **Nový projekt** vyberte buď možnost **.NET Framework 3,0** nebo možnost **.NET Framework 3,5** pro přístup ke staršímu návrháři.

    > [!NOTE]
    > Výchozí možnost v [!INCLUDE[vs2010](../includes/vs2010-md.md)] je **.NET Framework 4**. Tato možnost slouží k vytváření [!INCLUDE[wf](../includes/wf-md.md)] aplikací cílících na [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] a nepoužívá starší verze návrháře.

4. V podokně **typy projektů** vyberte možnost Visual C# nebo Visual Basic (v části **jiné jazyky**) a pak vyberte možnost **pracovní postup**.

5. V podokně **šablony** vyberte možnost **Knihovna pracovního postupu stavového stroje**.

6. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

7. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

     Pokud chcete vytvořit adresář řešení pro projekt, zaškrtněte políčko **vytvořit adresář pro řešení** a zadejte název do pole **název řešení** .

8. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také
 [Vytváření](../workflow-designer/creating-legacy-workflow-projects.md) [pracovních postupů stavového stroje](https://msdn.microsoft.com/library/344caacd-bf3b-4716-bd5a-eca74fc5a61d) projektů pro starší verze