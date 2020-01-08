---
title: Návrhář aktivity Návrhář postupu provádění-WriteLine
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e3b4da69a2d9154f36e42d3b20657e204767872
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593021"
---
# <a name="writeline-activity-designer"></a>Návrhář aktivity WriteLine

Návrhář aktivity **WriteLine** slouží k vytvoření a konfiguraci aktivity <xref:System.Activities.Statements.WriteLine>.

## <a name="the-writeline-activity"></a>Aktivita WriteLine

Aktivita <xref:System.Activities.Statements.WriteLine> zapisuje text do zadaného objektu <xref:System.IO.TextWriter>. Pokud není zadán žádný <xref:System.IO.TextWriter>, <xref:System.Activities.Statements.WriteLine> zapíše text do konzoly.

### <a name="using-the-writeline-activity-designer"></a>Použití návrháře aktivity WriteLine

Přístup k Návrháři aktivity **WriteLine** v kategorii **primitivních** prvků sady **nástrojů** Návrhář aktivity **WriteLine** lze přetáhnout ze **sady nástrojů** a vyřadit na Návrhář postupu provádění plochu všude, kde jsou obvykle umístěny aktivity, například uvnitř <xref:System.Activities.Statements.Sequence>. Tím se vytvoří aktivita <xref:System.Activities.Statements.WriteLine> s výchozím <xref:System.Activities.Activity.DisplayName%2A>em WriteLine. <xref:System.Activities.Activity.DisplayName%2A> lze upravit v záhlaví návrháře aktivity **WriteLine** nebo v poli **DisplayName** v mřížce vlastností.

### <a name="the-writeline-properties"></a>Vlastnosti WriteLine

V následující tabulce jsou uvedeny vlastnosti <xref:System.Activities.Statements.WriteLine> a popisuje, jak se používají v návrháři. Tyto vlastnosti se dají upravovat v mřížce vlastností a některé z nich je možné upravovat na Návrhář postupu provádění povrchu.

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Nepravda|Popisný název aktivity <xref:System.Activities.Statements.WriteLine>. Výchozí hodnota je WriteLine. I když <xref:System.Activities.Activity.DisplayName%2A> není nezbytně nutné, je vhodné použít jeden.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Nepravda|Text, který se má zapsat Chcete-li nastavit vlastnost, zadejte výraz Visual Basic do **textového** pole v Návrháři aktivity **WriteLine** nebo v mřížce vlastností.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Nepravda|<xref:System.IO.TextWriter>, na kterou <xref:System.Activities.Statements.WriteLine> zapisuje <xref:System.Activities.Statements.WriteLine.Text%2A>. Výchozím nastavením je konzola.|

## <a name="see-also"></a>Viz také:

- [Primitiva](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
