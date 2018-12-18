---
title: Návrhář aktivity Interop | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 587f9017e7f2c76018fbb5eb98645f5e4c19216c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283024"
---
# <a name="interop-activity-designer"></a>Návrhář aktivity Interop
**Interop** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.Interop> aktivity.  
  
## <a name="the-interop-activity"></a>Aktivity interoperability  
 <xref:System.Activities.Statements.Interop> Aktivita řídí spuštění typy, které jsou odvozeny z <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> v rámci pracovního postupu.  
  
### <a name="using-the-interop-activity-designer"></a>Pomocí návrháře aktivity interoperability  
 **Zprostředkovatele komunikace s objekty** návrháře aktivit najdete v **migrace** kategorii **nástrojů**, který přistupuje po kliknutí **nástrojů**kartu (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  
  
 [Migrace](../workflow-designer/migration-activity-designers.md) kategorii, která obsahuje <xref:System.Activities.Statements.Interop> aktivitu zobrazí jen v **nástrojů** Pokud váš projekt cílí úplné [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)].  
  
 Pro projekty jazyka C#, můžete znovu cílit projekt na používání úplné [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete **vlastnosti**. Na **aplikace** kartu, vyberte **NET Framework 4** možnost **Cílová architektura**. Vyberte **Ano** tlačítko **změnit cílové rozhraní Framework** dialogové okno s dotazem, budete vyzváni k potvrzení této změny.  
  
 Pro projekty jazyka Visual Basic, můžete znovu cílit projekt na používání úplné [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete **vlastnosti**. Na **kompilaci** klikněte na tlačítko **Upřesnit možnosti kompilace** tlačítko. Vyberte **rozhraní .net Framework 4** z **cílového rozhraní framework seznamu** a potom klikněte na tlačítko **OK**. Klikněte na tlačítko **Ano** tlačítko **změnit cílové rozhraní Framework** dialogové okno s dotazem, budete vyzváni k potvrzení této změny.  
  
 **Interop** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface všude, kde aktivity jsou obvykle umístěny, například jako uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří <xref:System.Activities.Statements.Interop> aktivity s výchozím **DisplayName** ze zprostředkovatele komunikace s objekty. <xref:System.Activities.Activity.DisplayName%2A> Můžete upravovat v záhlaví **zprostředkovatele komunikace s objekty** Návrhář aktivity nebo v **DisplayName** pole mřížku vlastností.  
  
 Klikněte na tlačítko **klikněte na tlačítko Procházet...** text v **ActivityType** pole na **zprostředkovatele komunikace s objekty** aktivity návrháře nebo v mřížce vlastností, abyste vyvolali **Procházet a vyberte .net typ** dialogové okno. Jsou zobrazeny pouze typů pro pracovní postup 3.0 nebo aktivity pracovního postupu 3.5 (to znamená, že pouze typy odvozené z <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] Pomocí tohoto pole zadat typ, najdete v článku [Procházet a vybrat typ dialogovému oknu rozhraní .NET](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) tématu.  
  
### <a name="the-interop-properties"></a>Vlastnosti definiční  
 Následující tabulka ukazuje <xref:System.Activities.Statements.Interop> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravit v mřížce vlastností nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu.  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název <xref:System.Activities.Statements.Interop> aktivity. Výchozí hodnota je zprostředkovatel komunikace s objekty. I když zobrazovaný název není bezpodmínečně nutné, je osvědčeným postupem použít zobrazovaný název.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Hodnota TRUE|Určuje typ aktivity obsažených <xref:System.Activities.Statements.Interop> aktivity. Tento typ zadán musí být odvozen od <xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>Viz také  
 [Migrace](../workflow-designer/migration-activity-designers.md)