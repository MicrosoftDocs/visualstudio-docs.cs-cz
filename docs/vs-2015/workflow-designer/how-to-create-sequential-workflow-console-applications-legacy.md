---
title: 'Postupy: vytváření konzolových aplikací sekvenčních pracovních postupů (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662731"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Postupy: Vytvoření konzolových aplikací sekvenčních pracovních postupů (starší verze)
Postupujte podle těchto kroků a vytvořte projekt konzolové aplikace sekvenčního pracovního postupu pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] , kterou poskytuje [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Použijte starší verze, [!INCLUDE[wfd2](../includes/wfd2-md.md)] Pokud potřebujete cílit buď na, [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

### <a name="to-create-a-sequential-workflow-console-application"></a>Vytvoření konzolové aplikace sekvenčního pracovního postupu

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V rozevíracím seznamu v horní části okna **Nový projekt** vyberte buď možnost **.NET Framework 3,0** nebo možnost **.NET Framework 3,5** pro přístup ke staršímu návrháři.

    > [!NOTE]
    > Výchozí možnost v nástroji [!INCLUDE[vs2010](../includes/vs2010-md.md)] je **.NET Framework 4**. Tato možnost slouží k vytváření [!INCLUDE[wf](../includes/wf-md.md)] aplikací, které cílí na [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] a nepoužívá starší verzi návrháře.

4. V podokně **typy projektů** vyberte projekty Visual C# nebo Visual Basic projekty (v části **jiné jazyky**) a pak vyberte **pracovní postup**.

5. V podokně **šablony** vyberte **Konzolová aplikace sekvenčního pracovního postupu**.

6. Do pole **název** zadejte popisný název projektu, který usnadňuje identifikaci.

7. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

     Návrhář formulářů otevře a zobrazí Form1 projektu, který jste vytvořili.

8. Klikněte na **OK**.

     Otevře se Návrhář postupu provádění a zobrazí se návrhová plocha pracovního postupu sekvenčního pracovního postupu, který jste vytvořili.

9. Přetáhněte aktivitu ze **sady nástrojů** na návrhovou plochu v určené oblasti **odkládací aktivity** .

## <a name="see-also"></a>Viz také
 [Vytváření projektů se staršími pracovními](../workflow-designer/creating-legacy-workflow-projects.md) [postupy pro vývoj pracovních postupů](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)