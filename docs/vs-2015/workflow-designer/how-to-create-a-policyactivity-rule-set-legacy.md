---
title: 'Postupy: vytvoření sady pravidel sady (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f8599348d204d149f3e28d17d681941ddf476b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849320"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Postupy: Vytvoření sady pravidel aktivit zásad (starší verze)
Toto téma popisuje, jak vytvořit sadu pravidel aktivity zásad pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] , která cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Po přetažení položky aktivity **zásad** ze **sady nástrojů** na návrhovou plochu pracovního postupu budete chtít vybrat stávající pravidlo nebo vytvořit novou sadu pravidel pro aktivitu [sady](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) . Existující sadu pravidel vyberete pomocí [dialogového okna vybrat sadu pravidel (starší verze)](../workflow-designer/select-rule-set-dialog-box-legacy.md) a vytvoříte sady pravidel pomocí [dialogového okna editor sad pravidel (starší verze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Dialogové okno [editoru sad pravidel (starší verze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) můžete otevřít přímo Poklikáním na aktivitu [sady](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) , která je na návrhové ploše pracovního postupu.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>Výběr nebo vytvoření sady pravidel pro aktivitu sady

1. Klikněte pravým tlačítkem na [sady](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx)a potom klikněte na **vlastnosti** . tím otevřete okno **vlastnosti** .

2. Klikněte na vlastnost **RuleSetReference** .

3. Proveďte jednu z následujících akcí:

    - Klikněte na **RuleSetReference** tři tečky **[...]** a potom vyberte existující sadu pravidel v [dialogovém okně vybrat sadu pravidel (starší verze)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Přejděte ke kroku 10.

         -nebo-

    - Zadejte název sady pravidel. Klikněte na **RuleSetReference** tři tečky **[...]** a pak v **Edit** [dialogovém okně vybrat sadu pravidel vyberte Upravit (starší verze)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         -nebo-

    - Zadejte název sady pravidel. Rozbalte vlastnost **RuleSetReference** a vyberte tři tečky **[...]** ve vlastnosti **definice RuleSet** .

         Otevře se [dialogové okno Editor sady pravidel (starší verze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) .

4. V [dialogovém okně Editor sady pravidel (starší verze)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)klikněte na **Přidat pravidlo** a přidejte nové pravidlo do sady pravidel.

5. Zadejte **název**, **prioritu**a vlastnosti opětovného **vyhodnocení** nebo ponechte výchozí hodnoty.

6. Zadejte text **podmínky**.

7. Zadejte text **akcí akce** a akce **Else**.

8. Znovu klikněte na **Přidat pravidlo** a přidejte další pravidlo.

9. Jakmile budete hotovi, klikněte na **Uložit**.

## <a name="see-also"></a>Viz také
 [Sady](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) [vybrat sadu pravidel](../workflow-designer/select-rule-set-dialog-box-legacy.md) – dialogové okno Editor sady pravidel (starší verze) – [dialogové okno editoru sad pravidel](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [pro aktivity zásad](https://msdn2.microsoft.com/library/bb675229.aspx) [starší verze pracovního postupu](../workflow-designer/legacy-workflow-activities.md)
