---
title: Dialogové okno Definice Návrhář postupu provádění – vlastnosti CorrelatesOn
description: Přečtěte si, jak můžete pomocí dialogového okna vlastnosti CorrelatesOn v Návrhář postupu provádění upravit vlastnost vlastnosti CorrelatesOn aktivity Receive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b4f371da2570d5573ce84c7e29393889202ae940
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955538"
---
# <a name="correlateson-definition-dialog-box"></a>Dialogové okno Definice vlastnosti CorrelatesOn

Dialogové okno **vlastnosti CorrelatesOn** se používá v Návrhář postupu provádění pro úpravu <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> vlastnosti <xref:System.ServiceModel.Activities.Receive> aktivity. Další informace najdete v tématu věnovaném [nástroji Receive Activity Designer](../workflow-designer/receive-activity-designer.md).

Korelace mezi <xref:System.ServiceModel.Activities.Receive> aktivitami určuje, jak se různé operace služby vzájemně spojují v pracovním postupu.

Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **vlastnosti CorrelatesOn** .

|Prvek uživatelského rozhraní (UI)|Description|
|-|-----------------|
|**Popisovač CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle>, Který se používá ke směrování zprávy do příslušné instance pracovního postupu.|
|**Dotazy XPath**|Pár klíč/hodnota, který obsahuje dotazy použité k extrakci korelačních dat z příchozích zpráv. Tato hodnota odpovídá <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Vlastnosti. Dotazy XPath jsou obsaženy v <xref:System.ServiceModel.MessageQuerySet> objektu.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Spuštění dialogového okna vlastnosti CorrelatesOn

Návrhář aktivity **Receive** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu, kde jsou obvykle umístěny aktivity. Vyřazení návrháře aktivit vytvoří <xref:System.ServiceModel.Activities.Receive> aktivitu s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> Receive. Chcete-li otevřít dialogové okno **definice vlastnosti CorrelatesOn** , vyberte Návrhář aktivity **Receive** a potom v mřížce vlastností vyberte tlačítko se třemi tečkami vedle textu kolekce pro vlastnost **vlastnosti CorrelatesOn** .

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Activities.Receive>
- [Dialogové okno Přidat inicializátory korelace](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Dialogové okno Inicializace korelace](../workflow-designer/initialize-correlation-dialog-box.md)