---
title: 'Postupy: Vytvoření knihovny sekvenčních pracovních postupů (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: adc2e71678e6892d12640a3153f24bfb90dfa429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663403"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Postupy: Vytvoření knihovny sekvenčních pracovních postupů (starší verze)
Postupujte podle těchto kroků a vytvořte projekt sekvenčního pracovního postupu pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] , kterou poskytuje [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud potřebujete cílit buď na, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

### <a name="to-create-a-sequential-workflow-library-project"></a>Postup vytvoření projektu knihovny sekvenčního pracovního postupu

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V rozevíracím seznamu v horní části okna **Nový projekt** vyberte buď možnost **.NET Framework 3,0** nebo možnost **.NET Framework 3,5** pro přístup ke staršímu návrháři.

    > [!NOTE]
    > Výchozí možnost v nástroji [!INCLUDE[vs2010](../includes/vs2010-md.md)] je **.NET Framework 4**. Tato možnost slouží k vytváření [!INCLUDE[wf](../includes/wf-md.md)] aplikací, které cílí na [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] a nepoužívá starší verzi návrháře.

4. V podokně **typy projektů** vyberte možnost Visual C# nebo Visual Basic (v části **jiné jazyky**) a pak vyberte možnost **pracovní postup**.

5. V podokně **šablony** vyberte možnost postupná **Knihovna pracovních postupů**.

6. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

7. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

     Pokud chcete vytvořit adresář řešení pro projekt, zaškrtněte políčko **vytvořit adresář pro řešení** a zadejte název do pole **název řešení** .

8. Klikněte na **OK**.

## <a name="see-also"></a>Viz také
 Vytváření [stylů vytváření pracovních](https://msdn.microsoft.com/aacf4ec6-da05-4974-958a-974769dda739) postupů [projektů starší verze](../workflow-designer/creating-legacy-workflow-projects.md)