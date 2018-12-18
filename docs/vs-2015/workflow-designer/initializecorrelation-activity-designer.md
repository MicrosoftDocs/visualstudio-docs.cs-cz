---
title: Návrhář aktivity Initializecorrelation | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9dd9d622785fbfebd8560daf9bf459716381ddbf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234023"
---
# <a name="initializecorrelation-activity-designer"></a>Návrhář aktivity InitializeCorrelation
**InitializeCorrelation** Návrhář aktivity se používá k vytvoření a konfigurace <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivitu, která se používá k navázání korelace mezi zprávy před odesláním nebo jejich přijetí.  
  
## <a name="the-initializecorrelation-activity"></a>Aktivity InitializeCorrelation  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivita slouží k inicializaci korelace bez odesílání nebo přijímání zprávy. Korelace je obvykle inicializován při odesílání nebo přijímání zprávy. Pokud korelace musí vytvořit předtím, než je odeslání nebo přijetí zprávy, použijte <xref:System.ServiceModel.Activities.InitializeCorrelation> inicializace korelace.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Pomocí aktivity Initializecorrelation  
 **InitializeCorrelation** návrháře aktivit najdete v **zasílání zpráv** kategorii **nástrojů**, který přistupuje po kliknutí **sady nástrojů**  kartě [!INCLUDE[wfd2](../includes/wfd2-md.md)] (případně vyberte možnost **nástrojů** z **zobrazení** nabídky nebo CTRL + ALT + X.)  
  
 **InitializeCorrelation** návrháře aktivit můžete přetáhnout z **nástrojů** a vyřazené k [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu. Tím se vytvoří <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity s výchozím <xref:System.Activities.Activity.DisplayName%2A> z InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> můžete upravovat v záhlaví **InitializeCorrelation** Návrhář aktivity nebo v  **DisplayName** pomocí boxingu **vlastnosti** okna.  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> Může být určuje v **korelace** pole **vlastnosti** na okno **InitializeCorrelation** povrch návrháře aktivit.  
  
 Kliknutím na tlačítko se třemi tečkami vedle **initalizecorrelation CorrelationData** pole **vlastnosti** okna nebo "Zobrazit …" pomocného parametru text na **InitializeCorrelation** návrhové aktivity se zobrazí **inicializace korelace** dialogovému oknu, ve kterém můžete zadat popisovač korelace a páry klíč hodnota pro Inicializujte. [!INCLUDE[crabout](../includes/crabout-md.md)] Pomocí tohoto dialogového, najdete v článku [dialogové okno Editor typu kolekce](../workflow-designer/type-collection-editor-dialog-box.md) tématu.  
  
### <a name="the-initializecorrelation-properties"></a>Vlastnosti InitializeCorrelation  
 Následující tabulka ukazuje <xref:System.ServiceModel.Activities.InitializeCorrelation> vlastnosti a popisuje, jak se používají v návrháři. Tyto vlastnosti můžete upravovat v **vlastnosti** okně nebo na [!INCLUDE[wfd2](../includes/wfd2-md.md)] povrchu.  
  
|Název vlastnosti|Požadováno|Použití|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity. Výchozí hodnota je InitializeCorrelation.<br /><br /> Ačkoli použití jinou než výchozí hodnotu pro popisný <xref:System.Activities.Activity.DisplayName%2A> není bezpodmínečně nutné, je vhodné použít taková hodnota.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> Použito k přidružení pracovního postupu aktivit v korelaci.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Slovník korelace dat, které se týkají zprávy instance pracovního postupu.<br /><br /> Použití **inicializace korelace** dialogové okno Konfigurace <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] použití tomto dialogovém okně najdete v článku [dialogové okno Editor typu kolekce](../workflow-designer/type-collection-editor-dialog-box.md) tématu.|  
  
## <a name="see-also"></a>Viz také  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Zobrazit](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Odeslat](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)