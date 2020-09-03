---
title: Dialogové okno Inicializace korelace | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ab913027a6a992494dad609b98ab11dbc6ae61c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659042"
---
# <a name="initialize-correlation-dialog-box"></a>Dialogové okno Inicializace korelace
Dialogové okno **inicializovat korelaci** se používá v [!INCLUDE[wfd1](../includes/wfd1-md.md)] pro úpravu <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> vlastnosti <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)]téma [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **inicializace korelace** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Korelace**|Korelace, <xref:System.ServiceModel.Activities.CorrelationHandle> která má být inicializována.|
|**Inicializovat na**|Pár klíč/hodnota, který obsahuje data k inicializaci. To odpovídá <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> Vlastnosti. Příkladem platnou dvojici klíč/hodnota by byl klíč nazvaný "ČísloObjednávky" spárovaný s proměnnou s názvem KódObjednávky.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Otevření dialogového okna inicializovat korelaci

- Klikněte na **Zobrazit** v Návrháři aktivity **InitializeCorrelation** nebo vyberte <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivitu v [!INCLUDE[wfd2](../includes/wfd2-md.md)] a potom klikněte na tlačítko se třemi tečkami vedle <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> vlastnosti v mřížce vlastností.

## <a name="see-also"></a>Viz také
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)