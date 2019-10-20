---
title: Návrhář aktivit spolupráce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659039"
---
# <a name="interop-activity-designer"></a>Návrhář aktivity Interop
Návrhář aktivity **spolupráce** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.Interop>.

## <a name="the-interop-activity"></a>Aktivita spolupráce
 Aktivita <xref:System.Activities.Statements.Interop> spravuje spouštění typů, které jsou odvozeny z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> v rámci pracovního postupu.

### <a name="using-the-interop-activity-designer"></a>Použití návrháře aktivit spolupráce
 Návrháře aktivit **spolupráce** můžete najít v kategorii **migrace** na **panelu nástrojů**, ke které se dostanete kliknutím na kartu **panel** nástrojů (případně můžete vybrat **panel nástrojů** v nabídce **zobrazení** nebo CTRL + ALT + X).

 Kategorie [migrace](../workflow-designer/migration-activity-designers.md) obsahující <xref:System.Activities.Statements.Interop> aktivita se zobrazí v **sadě nástrojů** pouze v případě, že projekt cílí na plný [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].

 U C# projektů můžete změnit cíl projektu tak, aby používal kompletní [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení** a výběrem **vlastností**. Na kartě **aplikace** vyberte možnost **NET Framework 4** v **cílové architektuře**. Vyberte tlačítko **Ano** v dialogovém okně **změnit cílové rozhraní** , které zobrazuje výzvu k potvrzení této změny.

 V případě projektů v jazyce VB můžete změnit cíl projektu tak, aby používal kompletní [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení** a výběrem **vlastností**. Na kartě **kompilovat** klikněte na tlačítko **Pokročilé možnosti kompilace** . V **seznamu cílové rozhraní** vyberte **.NET Framework 4** a pak klikněte na **OK**. Klikněte na tlačítko **Ano** v dialogovém okně **změnit cílovou architekturu** , ve kterém se zobrazí výzva k potvrzení této změny.

 Návrhář aktivity **interoperability** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.Interop> s výchozím zobrazovaným **názvem** pro spolupráci. @No__t_0 lze upravit v záhlaví návrháře aktivit **spolupráce** nebo v poli **DisplayName** v mřížce vlastností.

 Kliknutím **kliknete na tlačítko Procházet...** text v poli **ActivityType** , a to buď v Návrháři aktivity **spolupráce** , nebo v mřížce vlastností, zobrazí se dialogové okno **Procházet a vybrat typ .NET** . Zobrazují se jenom typy aktivit Workflow 3,0 nebo Workflow 3,5 (to znamená jenom typy odvozené od <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] použití tohoto pole k určení typu, přečtěte si téma [procházení a výběr typu .NET v dialogovém okně](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) .

### <a name="the-interop-properties"></a>Vlastnosti spolupráce
 V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.Interop> a popisuje, jak se používají v návrháři. Tyto vlastnosti lze upravovat v mřížce vlastností nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] ploše.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.Interop>. Výchozí hodnota je Interop. I když zobrazovaný název není nezbytně nutný, je vhodné použít zobrazovaný název.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Podmínka|Určuje typ aktivity obsažený v aktivitě <xref:System.Activities.Statements.Interop>. Zadaný typ musí být odvozen od <xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Viz také
 [Migrace](../workflow-designer/migration-activity-designers.md)