---
title: Návrhář aktivity trvalého Návrhář postupu provádění
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75236d7955cba6b8c62b9a4504f02c66cebe4062
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114769"
---
# <a name="persist-activity-designer"></a>Návrhář aktivity Persist

Návrhář **trvalé** aktivity se používá k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Persist>.

## <a name="the-persist-activity"></a>Aktivita trvalosti

Aktivita <xref:System.Activities.Statements.Persist> ukládá pracovní postup na disk, pokud je to možné. Aktivitu <xref:System.Activities.Statements.Persist> nelze provést v zóně bez trvalého uložení, například v rámci aktivity <xref:System.Activities.Statements.TransactionScope>. Použijete-li <xref:System.Activities.Statements.Persist> aktivity v oboru nestálosti, je vyvolána výjimka v době běhu.

### <a name="using-the-persist-activity-designer"></a>Použití návrháře trvalé aktivity

Návrháře **trvalých** aktivit lze najít v kategorii **runtime** sady **nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat možnost **Sada nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).)

Návrhář **trvalé** aktivity lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.Persist> s výchozím **názvem DisplayName** trvalého uložení. <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře **trvalé** aktivity nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-persist-properties"></a>Trvalé vlastnosti

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Persist> a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Popisný název aktivity <xref:System.Activities.Statements.Persist>. Výchozí hodnota je trvalá. I když zobrazovaný název není nezbytně nutný, je vhodné použít zobrazovaný název.|

## <a name="see-also"></a>Viz také:

- [Modul runtime](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
