---
title: Zobrazení aktivit (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c7d8a13890814b56865200acf95c8e0565b52b5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655211"
---
# <a name="activity-views-legacy"></a>Zobrazení aktivit (starší verze)
Mnohé z aktivit poskytovaných [!INCLUDE[wf](../includes/wf-md.md)], ze kterých se skládají pracovní postupy, mají ve starších [!INCLUDE[wfd1](../includes/wfd1-md.md)]ch k dispozici několik zobrazení návrhu. Když přetáhnete návrháře aktivity z **panelu nástrojů** na návrhovou plochu a potom kdykoli vyberete aktivitu, můžete přepínat mezi různými zobrazeními návrhu pomocí nabídky **pracovní postup** nebo kliknutím pravým tlačítkem myši na vybranou možnost. akce. I když přesunete ukazatel myši na název vybrané aktivity, zobrazí se rozevírací sada karet, kterou můžete použít k přepínání mezi různými zobrazeními.

 Každá aktivita má alespoň jedno zobrazení; Toto je výchozí zobrazení zobrazené při přetahování návrháře aktivit ze sady **nástrojů** na návrhovou plochu. Toto výchozí zobrazení aktivity je k dispozici jako možnost **zobrazení [typ aktivity]** v nabídkách a na kartě, například **Zobrazit paralelní**. Většina aktivit má další zobrazení a různé aktivity mohou mít různá zobrazení. Například aktivita [aktivitě typu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) má zobrazení kompenzace a aktivita [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) má zobrazení události. Mnohé z aktivit, které se dodávají s programovací model Windows Workflow Foundation, mají zobrazení pro **zrušení obslužné rutiny zrušit** a zobrazení návrhu **chyb** , aby se zobrazila [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) a [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) s ním spojené.

 V následující tabulce je uveden seznam názvů a popisů jednotlivých zobrazení.

|Možnost nabídky/karty|Popis|
|----------------------|-----------------|
|**Zobrazení [typ aktivity]**|Tuto nabídku nebo možnost tabulátoru vyberte, pokud chcete zobrazit výchozí grafické znázornění vybrané aktivity.|
|**Zobrazit obslužnou rutinu pro zrušení**|Chcete-li zobrazit [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) přidružené k vybrané aktivitě, vyberte tuto nabídku nebo zobrazení možností na kartě.|
|**Zobrazit obslužnou rutinu chyb**|Chcete-li zobrazit [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) přidružené k vybrané aktivitě, vyberte tuto nabídku nebo zobrazení možností na kartě.|
|**Zobrazit obslužnou rutinu kompenzace**|Vyberte tuto nabídku nebo zobrazení možností karet k zobrazení [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) přidruženého k vybranému [aktivitě typu TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|
|**Zobrazit obslužnou rutinu událostí**|Vyberte tuto nabídku nebo zobrazení možností karet k zobrazení [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) přidruženého k vybranému [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|

 Informace o podobných zobrazeních naleznete v tématu [zobrazení sekvenčních pracovních postupů (starší verze)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Viz také
 [Starší verze](../workflow-designer/legacy-workflow-activities.md) [zobrazení pracovního postupu v pořadí zastaralých pracovních postupů (starší verze)](../workflow-designer/sequential-workflow-views-legacy.md)