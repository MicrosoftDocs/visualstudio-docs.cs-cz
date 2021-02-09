---
title: Dialogová okna Návrhář postupu provádění-inicializace korelace
description: Přečtěte si, jak můžete použít dialogové okno inicializovat korelaci v Návrhář postupu provádění k úpravě vlastnosti CorrelationData aktivity InitializeCorrelation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a41511f9bfb381eeb422cc9cf7ec015d55ceff70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931510"
---
# <a name="initialize-correlation-dialog-box"></a>Dialogové okno Inicializace korelace

Dialogové okno **inicializovat korelaci** se používá v Návrhář postupu provádění pro úpravu <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> vlastnosti <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity. Další informace najdete v tématu [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **inicializace korelace** :

|Prvek uživatelského rozhraní (UI)|Description|
|-|-----------------|
|**Korelace**|Korelace, <xref:System.ServiceModel.Activities.CorrelationHandle> která má být inicializována.|
|**Inicializovat na**|Pár klíč/hodnota, který obsahuje data k inicializaci. Tato hodnota odpovídá <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Vlastnosti. Příkladem platného páru klíč/hodnota je klíč pojmenovaný "ČísloObjednávky" spárovaný s proměnnou s názvem KódObjednávky.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Otevření dialogového okna inicializovat korelaci

Klikněte na **Zobrazit** v Návrháři aktivity **InitializeCorrelation** nebo vyberte <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivitu v Návrhář postupu provádění. Potom klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> vlastnosti v mřížce vlastností.

## <a name="see-also"></a>Viz také

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
