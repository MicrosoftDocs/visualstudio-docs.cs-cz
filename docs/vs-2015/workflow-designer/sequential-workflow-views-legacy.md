---
title: Zobrazení sekvenčního pracovního postupu (starší verze) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 76d357c1f6ebc770d0e625e60bae237e37e0a6aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846218"
---
# <a name="sequential-workflow-views-legacy"></a>Zobrazení sekvenčního pracovního postupu (starší verze)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] poskytuje starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] , které lze použít k cílení [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [!INCLUDE[wfd2](../includes/wfd2-md.md)]Poskytuje způsob, jak vytvářet [!INCLUDE[wf](../includes/wf-md.md)] aplikace pomocí známého [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uživatelského rozhraní. [!INCLUDE[wf](../includes/wf-md.md)] aplikace se skládají z kroků procesu pracovního postupu nazývaných aktivity. Chcete-li vytvořit pracovní postup, sestavte aktivity na návrhové ploše přetažením jejich příslušných návrhářů aktivit ze **sady nástrojů** na návrhovou plochu.

 Když vytvoříte sekvenční pracovní postup, což je [SequentialWorkflowActivity](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx), jsou k dispozici tři zobrazení pracovního postupu. Tato zobrazení jsou přístupná z nabídky **pracovní postup** a z kontextové nabídky na návrhové ploše.

 V následující tabulce je uveden seznam názvů a popisů jednotlivých zobrazení.

|Možnost nabídky/karty|Popis|
|----------------------|-----------------|
|**Zobrazit sekvenčního pracovního postupu**|Klikněte pravým tlačítkem myši na návrhovou plochu a v místní nabídce vyberte možnost **Zobrazit sekvenčního pracovního postupu** a zobrazte tak zobrazení **sekvenčního pracovního postupu** , které zobrazuje grafické znázornění sekvenčního pracovního postupu na základě aktivity. Nebo v nabídce **pracovní postup** vyberte **Zobrazit sekvenčního pracovního postupu** .|
|**Zobrazit obslužnou rutinu pro zrušení**|Klikněte pravým tlačítkem myši na návrhovou plochu a v místní nabídce vyberte možnost **zobrazení zrušení obslužné rutiny** a zobrazte tak zobrazení **sekvenčního pracovního postupu** , které zobrazuje aktivitu [CancellationHandlerActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.cancellationhandleractivity.aspx) přidruženou k pracovnímu postupu. Nebo vyberte **Zobrazit obslužné rutiny zrušit** z nabídky **pracovní postup** .|
|**Zobrazit obslužnou rutinu chyb**|Klikněte pravým tlačítkem myši na návrhovou plochu a v místní nabídce vyberte možnost **Zobrazit obslužnou rutinu selhání** , která zobrazuje zobrazení **chyb** , která zobrazují aktivitu [FaultHandlersActivity](https://msdn2.microsoft.com/library/system.workflow.componentmodel.faulthandlersactivity.aspx) spojenou s pracovním postupem. Nebo vyberte možnost **Zobrazit obslužnou rutinu chyb** z nabídky **pracovní postup** .|

 Další informace o podobných zobrazeních naleznete v tématu [zobrazení aktivit (starší verze)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Viz také
 [Zobrazení aktivit (starší verze)](../workflow-designer/activity-views-legacy.md) vytváření pracovních postupů pro [projekty starší verze](../workflow-designer/creating-legacy-workflow-projects.md) [workflowu – režimy vytváření](https://msdn2.microsoft.com/library/bb628440.aspx)
