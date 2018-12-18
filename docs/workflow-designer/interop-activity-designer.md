---
title: Návrhář postupu provádění – Návrhář aktivity Interop
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f3b5fd2674d63fad6398eeaee082862c4cf6476
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809126"
---
# <a name="interop-activity-designer"></a>Návrhář aktivity Interop

**Interop** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.Interop> aktivity.

## <a name="the-interop-activity"></a>Aktivity interoperability

<xref:System.Activities.Statements.Interop> Aktivita řídí spuštění typy, které jsou odvozeny z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> v rámci pracovního postupu.

### <a name="use-the-interop-activity-designer"></a>Použijte Návrhář aktivity Interop

**Zprostředkovatele komunikace s objekty** návrháře aktivit najdete v **migrace** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů**kartu. Můžete také vybrat **nástrojů** z **zobrazení** nabídky nebo stisknutím klávesy **Ctrl**+**Alt** + **X**.

[Migrace](../workflow-designer/migration-activity-designers.md) kategorii, která obsahuje <xref:System.Activities.Statements.Interop> aktivitu zobrazí jen v **nástrojů** Pokud váš projekt cílí na úplné rozhraní .NET Framework 4.

Pro projekty jazyka C#, můžete znovu cílit projekt na používání úplné rozhraní .NET Framework 4 kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete **vlastnosti**. Na **aplikace** kartu, vyberte **NET Framework 4** možnost **Cílová architektura**. Vyberte **Ano** potvrďte tuto změnu.

Pro projekty jazyka Visual Basic, můžete znovu cílit projekt na používání úplné rozhraní .NET Framework 4 kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete **vlastnosti**. Na **kompilaci** klikněte na tlačítko **Upřesnit možnosti kompilace** tlačítko. Vyberte **rozhraní .net Framework 4** z **cílového rozhraní framework seznamu**a potom klikněte na tlačítko **OK**. Vyberte **Ano** potvrďte tuto změnu.

**Interop** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřadit na plochu návrháře postupu provádění bez ohledu na to aktivity jsou obvykle umístěny, například jako uvnitř <xref:System.Activities.Statements.Sequence>. Vyřazení **zprostředkovatele komunikace s objekty** vytvoří Návrhář aktivity <xref:System.Activities.Statements.Interop> aktivity s výchozím **DisplayName** ze zprostředkovatele komunikace s objekty. Můžete upravit <xref:System.Activities.Activity.DisplayName%2A> v záhlaví **zprostředkovatele komunikace s objekty** návrháře aktivit, nebo **DisplayName** pole mřížku vlastností.

Klikněte na tlačítko **kliknutím Procházet** textu v **ActivityType** pole na **zprostředkovatele komunikace s objekty** aktivity návrháře nebo v mřížce vlastností, chcete-li otevřít **Procházet a Vyberte .net typ** dialogové okno. Jsou zobrazeny pouze typů pro pracovní postup 3.0 nebo 3.5 pracovního postupu aktivity. To znamená, že pouze typy odvozené z <xref:System.Workflow.ComponentModel.Activity> jsou uvedeny. Další informace o použití tohoto pole zadat typ najdete v tématu [Procházet a vybrat typ dialogovému oknu rozhraní .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Vlastnosti definiční

Následující tabulka ukazuje <xref:System.Activities.Statements.Interop> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na povrchu návrháře postupu provádění.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název <xref:System.Activities.Statements.Interop> aktivity. Výchozí hodnota je **Interop**. I když není potřeba zobrazovaného názvu, doporučujeme poskytnout.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Hodnota TRUE|Určuje typ aktivity obsažených <xref:System.Activities.Statements.Interop> aktivity. Tento typ zadán musí být odvozen od <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Viz také:

- [Migrace](../workflow-designer/migration-activity-designers.md)