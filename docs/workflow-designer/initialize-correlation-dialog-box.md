---
title: Dialogová okna Návrhář postupu provádění-inicializace korelace
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04f0a3bb70dbab31e0faa5c38caac9b54c6154fe
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114785"
---
# <a name="initialize-correlation-dialog-box"></a>Dialogové okno Inicializace korelace

Dialogové okno **inicializovat korelaci** se používá v Návrhář postupu provádění k úpravě vlastnosti <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> aktivity <xref:System.ServiceModel.Activities.InitializeCorrelation>. Další informace najdete v tématu [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **inicializace korelace** :

|Prvek uživatelského rozhraní (UI)|Popis|
|-|-----------------|
|**Korelace**|<xref:System.ServiceModel.Activities.CorrelationHandle> korelace, která se má inicializovat|
|**Inicializovat na**|Pár klíč/hodnota, který obsahuje data k inicializaci. Tato hodnota odpovídá vlastnosti <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Příkladem platného páru klíč/hodnota je klíč pojmenovaný "ČísloObjednávky" spárovaný s proměnnou s názvem KódObjednávky.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Otevření dialogového okna inicializovat korelaci

Klikněte na **Zobrazit** v Návrháři aktivity **InitializeCorrelation** nebo vyberte aktivitu <xref:System.ServiceModel.Activities.InitializeCorrelation> v Návrhář postupu provádění. Potom klikněte na tlačítko se třemi tečkami vedle vlastnosti <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> v mřížce vlastností.

## <a name="see-also"></a>Viz také:

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
