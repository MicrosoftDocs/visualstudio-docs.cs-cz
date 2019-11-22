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
ms.openlocfilehash: 859fa44b44a295dc3e9f27fc168092a9fe2beebf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292359"
---
# <a name="sequential-workflow-views-legacy"></a>Zobrazení sekvenčního pracovního postupu (starší verze)
[!INCLUDE[vs2010](../includes/vs2010-md.md)] poskytuje starší [!INCLUDE[wfd1](../includes/wfd1-md.md)], které lze použít k cílení na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)] poskytuje způsob, jak vytvořit [!INCLUDE[wf](../includes/wf-md.md)] aplikace pomocí známých [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uživatelského rozhraní. [!INCLUDE[wf](../includes/wf-md.md)] aplikace se skládají z kroků procesu pracovního postupu nazývaných aktivity. Chcete-li vytvořit pracovní postup, sestavte aktivity na návrhové ploše přetažením jejich příslušných návrhářů aktivit ze **sady nástrojů** na návrhovou plochu.

 Když vytvoříte sekvenční pracovní postup, což je [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040), jsou k dispozici tři zobrazení pracovního postupu. Tato zobrazení jsou přístupná z nabídky **pracovní postup** a z kontextové nabídky na návrhové ploše.

 V následující tabulce je uveden seznam názvů a popisů jednotlivých zobrazení.

|Možnost nabídky/karty|Popis|
|----------------------|-----------------|
|**Zobrazit sekvenčního pracovního postupu**|Klikněte pravým tlačítkem myši na návrhovou plochu a v místní nabídce vyberte možnost **Zobrazit sekvenčního pracovního postupu** a zobrazte tak zobrazení **sekvenčního pracovního postupu** , které zobrazuje grafické znázornění sekvenčního pracovního postupu na základě aktivity. Nebo v nabídce **pracovní postup** vyberte **Zobrazit sekvenčního pracovního postupu** .|
|**Zobrazit obslužnou rutinu pro zrušení**|Klikněte pravým tlačítkem myši na návrhovou plochu a v místní nabídce vyberte možnost **zobrazení zrušení obslužné rutiny** a zobrazte tak zobrazení **sekvenčního pracovního postupu** , které zobrazuje aktivitu [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) přidruženou k pracovnímu postupu. Nebo vyberte **Zobrazit obslužné rutiny zrušit** z nabídky **pracovní postup** .|
|**Zobrazit obslužnou rutinu chyb**|Klikněte pravým tlačítkem myši na návrhovou plochu a v místní nabídce vyberte možnost **Zobrazit obslužnou rutinu selhání** , která zobrazuje zobrazení **chyb** , která zobrazují aktivitu [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) spojenou s pracovním postupem. Nebo vyberte možnost **Zobrazit obslužnou rutinu chyb** z nabídky **pracovní postup** .|

 Další informace o podobných zobrazeních naleznete v tématu [zobrazení aktivit (starší verze)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Viz také
 [Zobrazení aktivit (starší verze)](../workflow-designer/activity-views-legacy.md) vytváření pracovních postupů pro [projekty starší verze](../workflow-designer/creating-legacy-workflow-projects.md) [workflowu – režimy vytváření](https://go.microsoft.com/fwlink?LinkID=65014)