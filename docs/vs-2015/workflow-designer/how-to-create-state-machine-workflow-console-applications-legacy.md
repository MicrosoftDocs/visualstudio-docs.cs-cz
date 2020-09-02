---
title: 'Postupy: vytváření konzolových aplikací pracovního postupu stavového stroje (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 48c7e06c2cb0e59de754b1ab36b693c4c9872985
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662713"
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Postupy: Vytvoření konzolových aplikací pracovních postupů stavového stroje (starší verze)
Postupujte podle těchto kroků a vytvořte projekt konzolové aplikace pracovního postupu stavového stroje pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] , kterou poskytuje [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud potřebujete cílit buď na, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

### <a name="to-create-a-state-machine-application-project"></a>Vytvoření projektu aplikace stavového počítače

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V rozevíracím seznamu v horní části okna **Nový projekt** vyberte buď možnost **.NET Framework 3,0** nebo možnost **.NET Framework 3,5** pro přístup ke staršímu návrháři.

    > [!NOTE]
    > Výchozí možnost v nástroji [!INCLUDE[vs2010](../includes/vs2010-md.md)] je **.NET Framework 4**. Tato možnost slouží k vytváření [!INCLUDE[wf](../includes/wf-md.md)] aplikací, které cílí na [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] a nepoužívá starší verzi návrháře.

4. V podokně **typy projektů** vyberte možnost Visual C# nebo Visual Basic (v části **jiné jazyky**) a pak vyberte možnost **pracovní postup**.

5. V podokně **šablony** vyberte **Konzolová aplikace pracovního postupu stavového stroje**.

6. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

7. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

     Pokud chcete vytvořit adresář řešení pro projekt, zaškrtněte políčko **vytvořit adresář pro řešení** a zadejte název do pole **název řešení** .

8. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
 [Vytváření projektů pracovních postupů starší verze](../workflow-designer/creating-legacy-workflow-projects.md) [Postupy: Vytvoření knihovny pracovního postupu stavového stroje (starší verze)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)