---
title: Dialogové okno Definice Návrhář postupu provádění – vlastnosti CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401f72f55f23779f7c6257437034a4ebc294d219
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650603"
---
# <a name="correlateson-definition-dialog-box"></a>Dialogové okno Definice vlastnosti CorrelatesOn

Dialogové okno **vlastnosti CorrelatesOn** se používá v Návrhář postupu provádění k úpravě vlastnosti <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> aktivity <xref:System.ServiceModel.Activities.Receive>. Další informace najdete v tématu věnovaném [nástroji Receive Activity Designer](../workflow-designer/receive-activity-designer.md).

Korelace mezi <xref:System.ServiceModel.Activities.Receive> aktivitami určuje, jak se různé operace služby vzájemně spojují v pracovním postupu.

Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **vlastnosti CorrelatesOn** .

|Prvek uživatelského rozhraní (UI)|Popis|
|-|-----------------|
|**Popisovač CorrelatesWith**|@No__t_0, která se používá ke směrování zprávy do příslušné instance pracovního postupu.|
|**Dotazy XPath**|Pár klíč/hodnota, který obsahuje dotazy použité k extrakci korelačních dat z příchozích zpráv. Tato hodnota odpovídá vlastnosti <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Dotazy XPath jsou obsaženy v objektu <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Spuštění dialogového okna vlastnosti CorrelatesOn

Návrhář aktivity **Receive** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu, kde jsou obvykle umístěny aktivity. Vyřazení návrháře aktivit vytvoří aktivitu <xref:System.ServiceModel.Activities.Receive> s výchozím <xref:System.Activities.Activity.DisplayName%2A> příjmu. Chcete-li otevřít dialogové okno **definice vlastnosti CorrelatesOn** , vyberte Návrhář aktivity **Receive** a potom v mřížce vlastností vyberte tlačítko se třemi tečkami vedle textu kolekce pro vlastnost **vlastnosti CorrelatesOn** .

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Activities.Receive>
- [Dialogové okno Přidat inicializátory korelace](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Dialogové okno Inicializace korelace](../workflow-designer/initialize-correlation-dialog-box.md)