---
title: Návrhář aktivity trvalého Návrhář postupu provádění
description: Přečtěte si o aktivitě trvalé aktivity a o tom, jak pomocí návrháře trvalé aktivity vytvořit a nakonfigurovat aktivitu trvalé aktivity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 988c080b7b6c89baa4151858fcaf4e3320582e09
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968720"
---
# <a name="persist-activity-designer"></a>Návrhář aktivity Persist

Návrhář **trvalé** aktivity se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Persist> aktivity.

## <a name="the-persist-activity"></a>Aktivita trvalosti

<xref:System.Activities.Statements.Persist>Pokud je to možné, aktivita ukládá pracovní postup na disk. <xref:System.Activities.Statements.Persist>Aktivitu nelze provést v zóně bez trvalého uložení, například v rámci <xref:System.Activities.Statements.TransactionScope> aktivity. Pokud použijete <xref:System.Activities.Statements.Persist> aktivitu v oboru, který není trvalý, výjimka je vyvolána v době běhu.

### <a name="using-the-persist-activity-designer"></a>Použití návrháře trvalé aktivity

Návrháře **trvalých** aktivit lze najít v kategorii **runtime** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat možnost **Sada nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).)

Návrhář **trvalé** aktivity lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence> . Tím se vytvoří <xref:System.Activities.Statements.Persist> aktivita s výchozím **názvem DisplayName** trvalého. <xref:System.Activities.Activity.DisplayName%2A>Lze upravit v záhlaví návrháře **trvalé** aktivity nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-persist-properties"></a>Trvalé vlastnosti

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Persist> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Ne|Popisný název <xref:System.Activities.Statements.Persist> aktivity Výchozí hodnota je trvalá. I když zobrazovaný název není nezbytně nutný, je vhodné použít zobrazovaný název.|

## <a name="see-also"></a>Viz také

- [Runtime (Modul runtime)](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
