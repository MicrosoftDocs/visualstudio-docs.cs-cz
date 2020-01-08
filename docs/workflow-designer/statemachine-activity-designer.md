---
title: Návrhář aktivity Návrhář postupu provádění-StateMachine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: e7a270780a953a6104adc7089a02ff6529106fdf
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593132"
---
# <a name="statemachine-activity-designer"></a>Návrhář aktivity StateMachine

Aktivita <xref:System.Activities.Statements.StateMachine> obsahuje kolekci stavů a pracovních postupů modelů pomocí známých stavových paradigmat počítače.

## <a name="using-the-statemachine-activity-designer"></a>Použití návrháře aktivit StateMachine

Chcete-li přidat aktivitu <xref:System.Activities.Statements.StateMachine>, přetáhněte návrháře aktivity **StateMachine** z části **Stavový počítač** v **panelu nástrojů** a přetáhněte jej na Návrhář postupu provádění plochu. Chcete-li do této aktivity <xref:System.Activities.Statements.StateMachine> přidat podřízený stav, přetáhněte <xref:System.Activities.Statements.State> nebo <xref:System.Activities.Core.Presentation.FinalState> ze **sady nástrojů** a přetáhněte ji do **StateMachine**.

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>Vlastnosti aktivity StateMachine v Návrhář postupu provádění

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.StateMachine>, které lze nastavit pomocí návrháře pracovních postupů, a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravit v mřížce vlastností a některé lze upravovat na návrhové ploše.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Určuje popisný název návrháře <xref:System.Activities.Statements.StateMachine> aktivity v hlavičce. Výchozí hodnota je **StateMachine**. Hodnotu lze upravit v mřížce vlastností nebo přímo v záhlaví návrháře aktivit. <xref:System.Activities.Activity.DisplayName%2A> se používá v navigaci s popisem cesty, které se zobrazí v horní části návrháře pracovních postupů.<br /><br /> I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je osvědčeným postupem použití jednoho.|

## <a name="see-also"></a>Viz také:

- [Vývojový diagram](../workflow-designer/flowchart-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)
