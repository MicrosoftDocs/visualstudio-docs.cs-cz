---
title: Návrhář aktivity Návrhář postupu provádění – DoWhile
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85f8d6c442982fff47a679e8fc2ccc04ee515a9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650520"
---
# <a name="dowhile-activity-designer"></a>Návrhář aktivity DoWhile

Aktivita <xref:System.Activities.Statements.DoWhile> spustí aktivitu obsaženou v jeho <xref:System.Activities.Statements.DoWhile.Body%2A> alespoň jednou, dokud není zadaná podmínka vyhodnocena jako **NEPRAVDA**. Pokud potřebujete, aby aktivita obsažená v těle smyčky byla provedena nula nebo vícekrát, použijte místo toho <xref:System.Activities.Statements.While>ovou aktivitu.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile vlastnosti v Návrhář postupu provádění

Následující tabulka obsahuje nejužitečnější vlastnosti <xref:System.Activities.Statements.DoWhile> aktivity a popisuje jejich použití v Návrháři:

|Název vlastnosti|Požadováno|Použití|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Aktivita, která se má provést, když je podmínka **pravdivá** Chcete-li přidat aktivitu <xref:System.Activities.Statements.DoWhile.Body%2A>, přetáhněte aktivitu ze sady nástrojů **do pole text v Návrháři** aktivity **DoWhile** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Podmínka|Podmínka, která má být vyhodnocena po každé iteraci smyčky. Chcete-li nastavit <xref:System.Activities.Statements.DoWhile.Condition%2A>, zadejte výraz Visual Basic do pole **Podmínka** v Návrháři aktivity **DoWhile** nebo v mřížce vlastností.|

## <a name="see-also"></a>Viz také:

- [While](../workflow-designer/while-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)