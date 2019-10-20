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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656942"
---
# <a name="correlateson-definition-dialog-box"></a>Dialogové okno Definice vlastnosti CorrelatesOn
Dialogové okno **vlastnosti CorrelatesOn** se používá v [!INCLUDE[wfd1](../includes/wfd1-md.md)] k úpravě vlastnosti <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> aktivity <xref:System.ServiceModel.Activities.Receive>. [!INCLUDE[crdefault](../includes/crdefault-md.md)] téma [Receive](../workflow-designer/receive-activity-designer.md) .

 Korelace mezi <xref:System.ServiceModel.Activities.Receive> aktivitami určuje, jak se různé operace služby vzájemně spojují v pracovním postupu.

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **vlastnosti CorrelatesOn** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Popisovač CorrelatesWith**|@No__t_0, která se používá ke směrování zprávy do příslušné instance pracovního postupu.|
|**Dotazy XPath**|Pár klíč/hodnota, který obsahuje dotazy použité k extrakci korelačních dat z příchozích zpráv. To odpovídá vlastnosti <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Dotazy XPath jsou obsaženy v objektu <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Spuštění dialogového okna vlastnosti CorrelatesOn
 Návrhář aktivity **Receive** lze přetáhnout ze **sady nástrojů** a vyřadit na [!INCLUDE[wfd2](../includes/wfd2-md.md)] plochu všude, kde jsou obvykle umístěny aktivity. Tím se vytvoří aktivita <xref:System.ServiceModel.Activities.Receive> s výchozím <xref:System.Activities.Activity.DisplayName%2A> příjmu. Vyberte návrháře aktivity **Receive** a klikněte na tlačítko se třemi tečkami vedle textu (kolekce) pro vlastnost **vlastnosti CorrelatesOn** v tabulce vlastností pro zobrazení dialogového okna **definice vlastnosti CorrelatesOn** .

## <a name="see-also"></a>Viz také
 [dialogová okna pro inicializaci korelace](../workflow-designer/initialize-correlation-dialog-box.md) dialogového okna <xref:System.ServiceModel.Activities.Receive> [Přidat inicializátoři CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md)