---
title: Návrhář aktivity trvalého Návrhář postupu provádění
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7be70d18b1fc8ff12e2d1fb177b41775954334ed
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254852"
---
# <a name="persist-activity-designer"></a>Návrhář aktivity Persist

Návrhář **trvalé** aktivity se používá k vytvoření a konfiguraci <xref:System.Activities.Statements.Persist> aktivity.

## <a name="the-persist-activity"></a>Aktivita trvalosti

Pokud <xref:System.Activities.Statements.Persist> je to možné, aktivita ukládá pracovní postup na disk. Aktivitu nelze provést v zóně bez trvalého uložení, například <xref:System.Activities.Statements.TransactionScope> v rámci aktivity. <xref:System.Activities.Statements.Persist> Pokud použijete <xref:System.Activities.Statements.Persist> aktivitu v oboru, který není trvalý, výjimka je vyvolána v době běhu.

### <a name="using-the-persist-activity-designer"></a>Použití návrháře trvalé aktivity

Návrháře **trvalých** aktivit lze najít v kategorii **runtime** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat možnost **Sada nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).)

Návrhář **trvalé** aktivity lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například dovnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří <xref:System.Activities.Statements.Persist> aktivita s výchozím **názvem DisplayName** trvalého. Lze upravit v záhlaví návrháře **trvalé** aktivity nebo v poli DisplayName v mřížce vlastností. <xref:System.Activities.Activity.DisplayName%2A>

### <a name="the-persist-properties"></a>Trvalé vlastnosti

V následující tabulce jsou uvedeny <xref:System.Activities.Statements.Persist> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název <xref:System.Activities.Statements.Persist> aktivity Výchozí hodnota je trvalá. I když zobrazovaný název není nezbytně nutný, je vhodné použít zobrazovaný název.|

## <a name="see-also"></a>Viz také:

- [Modul runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)