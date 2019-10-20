---
title: 'Postupy: vytváření projektů pracovních postupů (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668677"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Postupy: vytváření projektů pracovních postupů (starší verze)
Postupujte podle těchto kroků a vytvořte [!INCLUDE[wf](../includes/wf-md.md)] projekt, který cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. Tato procedura používá starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytované [!INCLUDE[vs2010](../includes/vs2010-md.md)].

### <a name="to-create-a-workflow-project"></a>Vytvoření projektu pracovního postupu

1. Spusťte [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V rozevíracím seznamu v horní části okna **Nový projekt** vyberte buď možnost **.NET Framework 3,0** nebo možnost **.NET Framework 3,5** pro přístup ke staršímu návrháři.

    > [!NOTE]
    > Výchozí možnost v [!INCLUDE[vs2010](../includes/vs2010-md.md)] je **.NET Framework 4**. Tato možnost slouží k vytváření [!INCLUDE[wf](../includes/wf-md.md)] aplikací cílících na [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] a nepoužívá starší verze návrháře.

4. V podokně **typy projektů** vyberte možnost Visual C# projekty nebo projekty Visual Basic a pak vyberte možnost **pracovní postup**.

5. V podokně **šablony** vyberte jednu z nainstalovaných šablon projektu:

    - Konzolová aplikace sekvenčního pracovního postupu

    - Knihovna sekvenčního pracovního postupu

    - Knihovna aktivit pracovního postupu

    - Konzolová aplikace pracovního postupu stavového stroje

    - Knihovna pracovního postupu stavového stroje

    - Prázdný projekt pracovního postupu

6. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

7. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte do adresáře.

     Pokud chcete vytvořit adresář řešení pro projekt, zaškrtněte políčko **vytvořit adresář pro řešení** a zadejte název do pole **název řešení** .

8. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také
 [Vytváření projektů pracovních postupů starších verzí](../workflow-designer/creating-legacy-workflow-projects.md)