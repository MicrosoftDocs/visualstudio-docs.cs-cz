---
title: Dialogové okno definice vlastnosti CorrelatesOn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656942"
---
# <a name="correlateson-definition-dialog-box"></a>Dialogové okno Definice vlastnosti CorrelatesOn
Dialogové okno **vlastnosti CorrelatesOn** se používá v [!INCLUDE[wfd1](../includes/wfd1-md.md)] pro úpravu <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> vlastnosti <xref:System.ServiceModel.Activities.Receive> aktivity. [!INCLUDE[crdefault](../includes/crdefault-md.md)] téma [Receive](../workflow-designer/receive-activity-designer.md) .

 Korelace mezi <xref:System.ServiceModel.Activities.Receive> aktivitami určuje, jak se různé operace služby vzájemně spojují v pracovním postupu.

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **vlastnosti CorrelatesOn** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Popisovač CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle>, Který se používá ke směrování zprávy do příslušné instance pracovního postupu.|
|**Dotazy XPath**|Pár klíč/hodnota, který obsahuje dotazy použité k extrakci korelačních dat z příchozích zpráv. To odpovídá <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Vlastnosti. Dotazy XPath jsou obsaženy v <xref:System.ServiceModel.MessageQuerySet> objektu.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Spuštění dialogového okna vlastnosti CorrelatesOn
 Návrhář aktivity **Receive** je možné přetáhnout ze **sady nástrojů** a vyřadit na plochu, [!INCLUDE[wfd2](../includes/wfd2-md.md)] kde jsou obvykle umístěni aktivity. Tím se vytvoří <xref:System.ServiceModel.Activities.Receive> aktivita s výchozím nastavením <xref:System.Activities.Activity.DisplayName%2A> Receive. Vyberte návrháře aktivity **Receive** a klikněte na tlačítko se třemi tečkami vedle textu (kolekce) pro vlastnost **vlastnosti CorrelatesOn** v tabulce vlastností pro zobrazení dialogového okna **definice vlastnosti CorrelatesOn** .

## <a name="see-also"></a>Viz také
 <xref:System.ServiceModel.Activities.Receive>Dialogová okna pro [Přidání Inicializátoři CorrelationInitializers dialogového](../workflow-designer/add-correlationinitializers-dialog-box.md) okna [inicializace korelace](../workflow-designer/initialize-correlation-dialog-box.md)