---
title: Návrhář aktivity DoWhile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656770"
---
# <a name="dowhile-activity-designer"></a>Návrhář aktivity DoWhile
Aktivita <xref:System.Activities.Statements.DoWhile> spustí aktivitu obsaženou v jeho <xref:System.Activities.Statements.DoWhile.Body%2A> alespoň jednou, dokud není zadaná podmínka vyhodnocena jako **NEPRAVDA**. Pokud potřebujete, aby aktivita obsažená v těle smyčky byla provedena nula nebo vícekrát, použijte místo toho <xref:System.Activities.Statements.While>ovou aktivitu.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile vlastnosti v Návrhář postupu provádění
 Následující tabulka uvádí nejužitečnější vlastnosti <xref:System.Activities.Statements.DoWhile> aktivity a popisuje jejich použití v návrháři.

|Název vlastnosti|Požadováno|Použití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Aktivita, která se má provést, když je podmínka **pravdivá** Chcete-li přidat aktivitu <xref:System.Activities.Statements.DoWhile.Body%2A>, přetáhněte aktivitu ze sady nástrojů **do pole text v Návrháři** aktivity **DoWhile** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Podmínka|Podmínka, která má být vyhodnocena po každé iteraci smyčky. Chcete-li nastavit <xref:System.Activities.Statements.DoWhile.Condition%2A>, zadejte výraz [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] do pole **Podmínka** v Návrháři aktivity **DoWhile** nebo v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [](../workflow-designer/while-activity-designer.md) [Tok řízení](../workflow-designer/control-flow-activity-designers.md)