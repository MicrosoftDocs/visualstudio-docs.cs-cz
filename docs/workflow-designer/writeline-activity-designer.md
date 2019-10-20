---
title: Návrhář aktivity Návrhář postupu provádění-WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 475755fed96f8341c45b8260b414658967b3284c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649756"
---
# <a name="writeline-activity-designer"></a>Návrhář aktivity WriteLine

Návrhář aktivity **WriteLine** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.WriteLine>.

## <a name="the-writeline-activity"></a>Aktivita WriteLine

Aktivita <xref:System.Activities.Statements.WriteLine> zapisuje text do zadaného objektu <xref:System.IO.TextWriter>. Pokud není zadán žádný <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> zapíše text do konzoly.

### <a name="using-the-writeline-activity-designer"></a>Použití návrháře aktivity WriteLine

Přístup k Návrháři aktivity **WriteLine** v kategorii **primitivních** prvků sady **nástrojů** Návrhář aktivity **WriteLine** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.WriteLine> s výchozím <xref:System.Activities.Activity.DisplayName%2A>em WriteLine. @No__t_0 lze upravit v záhlaví návrháře aktivity **WriteLine** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-writeline-properties"></a>Vlastnosti WriteLine

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.WriteLine> a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Popisný název aktivity <xref:System.Activities.Statements.WriteLine>. Výchozí hodnota je WriteLine. I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je vhodné použít jeden.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|Text, který se má zapsat Chcete-li nastavit vlastnost, zadejte výraz Visual Basic do **textového** pole v Návrháři aktivity **WriteLine** nebo v mřížce vlastností.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|@No__t_0, na kterou <xref:System.Activities.Statements.WriteLine> zapisuje <xref:System.Activities.Statements.WriteLine.Text%2A>. Výchozím nastavením je konzola.|

## <a name="see-also"></a>Viz také:

- [Primitivní elementy](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)