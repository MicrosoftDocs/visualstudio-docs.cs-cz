---
title: Návrhář aktivity Návrhář postupu provádění – DoWhile
description: Přečtěte si, jak aktivita DoWhile spustí aktivitu obsaženou v těle alespoň jednou, dokud není zadaná podmínka vyhodnocena jako NEPRAVDA.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6e117fcbea0488c4b6a42125971984b86cf78251
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894254"
---
# <a name="dowhile-activity-designer"></a>Návrhář aktivity DoWhile

<xref:System.Activities.Statements.DoWhile>Aktivita spustí aktivitu obsaženou <xref:System.Activities.Statements.DoWhile.Body%2A> alespoň jednou, dokud není zadaná podmínka vyhodnocena jako **NEPRAVDA**. Pokud potřebujete, aby aktivita obsažená v těle smyčky byla provedena nula nebo vícekrát, použijte <xref:System.Activities.Statements.While> místo toho aktivitu.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile vlastnosti v Návrhář postupu provádění

Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.DoWhile> vlastnosti aktivity a popisuje jejich použití v Návrháři:

|Název vlastnosti|Požaduje se|Využití|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Ne|Aktivita, která se má provést, když je podmínka **pravdivá** Chcete-li přidat <xref:System.Activities.Statements.DoWhile.Body%2A> aktivitu, přetáhněte aktivitu ze sady nástrojů do pole **text** v Návrháři aktivity **DoWhile** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Ano|Podmínka, která má být vyhodnocena po každé iteraci smyčky. Chcete-li nastavit <xref:System.Activities.Statements.DoWhile.Condition%2A> , zadejte výraz Visual Basic do pole **Podmínka** v Návrháři aktivity **DoWhile** nebo v mřížce vlastností.|

## <a name="see-also"></a>Viz také

- [Chybě](../workflow-designer/while-activity-designer.md)
- [Tok řízení](../workflow-designer/control-flow-activity-designers.md)