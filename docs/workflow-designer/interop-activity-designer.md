---
title: Návrhář aktivity Návrhář postupu provádění-Interop
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8047df3787c0871e369b6079e4f0cc80f6d93949
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650214"
---
# <a name="interop-activity-designer"></a>Návrhář aktivity Interop

Návrhář aktivity **spolupráce** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Interop>.

## <a name="the-interop-activity"></a>Aktivita spolupráce

Aktivita <xref:System.Activities.Statements.Interop> spravuje spouštění typů, které jsou odvozeny z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> v rámci pracovního postupu.

### <a name="use-the-interop-activity-designer"></a>Použití návrháře aktivit spolupráce

Návrháře aktivit **spolupráce** můžete najít v kategorii **migrace** v **sadě nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů. případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo stisknout klávesu **CTRL.** +**ALT** +**X**.

Kategorie [migrace](../workflow-designer/migration-activity-designers.md) obsahující <xref:System.Activities.Statements.Interop> aktivita se zobrazí pouze v **sadě nástrojů** , pokud jsou cíle projektu .NET Framework 4 (úplné) nebo vyšší. V případě potřeby můžete změnit verzi rozhraní .NET Framework, na kterou projekt cílí.

Návrhář aktivity **interoperability** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení návrháře aktivit **spolupráce** vytvoří aktivitu <xref:System.Activities.Statements.Interop> s výchozím **zobrazovaným názvem** pro spolupráci. @No__t_0 můžete upravit v záhlaví návrháře aktivit **spolupráce** nebo v poli **DisplayName** v mřížce vlastností.

Kliknutím na **tlačítko Procházet** text v poli **ActivityType** , a to buď v Návrháři aktivity **spolupráce** , nebo v mřížce vlastností, otevřete dialogové okno **Procházet a vybrat typ .NET** . Zobrazují se jenom typy aktivit Workflow 3,0 nebo Workflow 3,5. To znamená, že jsou zobrazeny pouze typy odvozené z <xref:System.Workflow.ComponentModel.Activity>. Další informace o tom, jak zadat typ pomocí tohoto pole, naleznete v tématu [Procházet a vybrat typ .NET dialogového okna](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Vlastnosti spolupráce

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Interop> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na Návrhář postupu provádění ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.Interop>. Výchozí hodnota je **Interop**. I když se zobrazované jméno nepožaduje, doporučuje se ho zadat.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Podmínka|Určuje typ aktivity obsažený v aktivitě <xref:System.Activities.Statements.Interop>. Zadaný typ musí být odvozen od <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Viz také:

- [Migrace](../workflow-designer/migration-activity-designers.md)