---
title: Návrhář aktivity CompensableActivity | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 670d3e92b24e35979074df3817611ceff692f59d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290443"
---
# <a name="compensableactivity-activity-designer"></a>Návrhář aktivity CompensableActivity
**Aktivita CompensableActivity** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.Activities.Statements.CompensableActivity> aktivity.  
  
## <a name="the-compensableactivity-activity"></a>Aktivita CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> Definuje jednotku práce, které mohou být potvrzena nebo kompenzována po úspěšném dokončení.  
  
### <a name="using-the-compensableactivity-activity-designer"></a>Návrhář aktivity CompensableActivity pomocí  
 **Aktivita CompensableActivity** návrháře aktivit najdete v **transakce** kategorii **nástrojů**, který přistupuje po kliknutí **sady nástrojů**  karty na levé straně [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  
  
 **Aktivita CompensableActivity** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface všude, kde aktivity jsou obvykle umístěny, například jako uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří <xref:System.Activities.Statements.CompensableActivity> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> z aktivita CompensableActivity. <xref:System.Activities.Activity.DisplayName%2A> Hodnota se dá upravit v záhlaví **aktivita CompensableActivity** Návrhář aktivity nebo **DisplayName** pole mřížku vlastností.  
  
### <a name="the-compensableactivity-properties"></a>Aktivita CompensableActivity vlastnosti  
 Následující tabulka ukazuje <xref:System.Activities.Statements.CompensableActivity> vlastnosti a popisuje, jak se používají v návrháři. <xref:System.Activities.Activity.DisplayName%2A> a <xref:System.Activities.Activity%601.Result%2A> vlastnost lze upravit v mřížce vlastností, ale další vlastnosti nutné upravit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu.  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Volitelné jméno <xref:System.Activities.Statements.CompensableActivity> aktivity. Výchozí hodnota je aktivita CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Určuje návratovou hodnotu <xref:System.Activities.Statements.CompensableActivity>. Tato vlastnost je nutné upravit v mřížce vlastností.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|Hodnota TRUE|Určuje aktivity, pro který je k dispozici logiky compensation, zrušení a potvrzení. Chcete-li přidat <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivity, rozevírací aktivitu z **nástrojů** do **text** pole na **aktivita CompensableActivity** Návrhář aktivity s text nápovědy "rozevírací aktivity sem".|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Určuje, která se spustí v případě zrušení aktivity. Přidat aktivitu, vyřaďte Návrhář z **nástrojů** do **CancellationHandler** pole na **aktivita CompensableActivity** Návrhář aktivity s text nápovědy "rozevírací Aktivity sem".|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Určuje aktivity, který se spustí při kompenzaci pro <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivity. Tato obslužná rutina může být vyvolána explicitně, pomocí <xref:System.Activities.Statements.Compensate> aktivity.<br /><br /> Přidat aktivitu, přetáhněte jeho Návrhář aktivity z **nástrojů** do **CompensationHandler** pole na **aktivita CompensableActivity** Návrhář aktivity s text nápovědy " Sem přetáhněte aktivitu".|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Určuje aktivity, který se spustí při potvrzení <xref:System.Activities.Statements.CompensableActivity.Body%2A> aktivity. Tato obslužná rutina může být vyvolána explicitně, pomocí <xref:System.Activities.Statements.Confirm> aktivity.<br /><br /> Přidat aktivitu, přetáhněte jeho Návrhář aktivity z **nástrojů** do **ConfirmationHandler** pole na **aktivita CompensableActivity** Návrhář aktivity s text nápovědy " Sem přetáhněte aktivitu".|  
  
## <a name="see-also"></a>Viz také  
 [Transakce](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Kompenzace](../workflow-designer/compensate-activity-designer.md)   
 [potvrzení](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)