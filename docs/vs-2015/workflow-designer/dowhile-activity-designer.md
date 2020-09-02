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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656770"
---
# <a name="dowhile-activity-designer"></a>Návrhář aktivity DoWhile
<xref:System.Activities.Statements.DoWhile>Aktivita spustí aktivitu obsaženou <xref:System.Activities.Statements.DoWhile.Body%2A> alespoň jednou, dokud není zadaná podmínka vyhodnocena jako **NEPRAVDA**. Pokud potřebujete, aby aktivita obsažená v těle smyčky byla provedena nula nebo vícekrát, použijte <xref:System.Activities.Statements.While> místo toho aktivitu.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile vlastnosti v Návrhář postupu provádění
 Následující tabulka uvádí nejužitečnější <xref:System.Activities.Statements.DoWhile> vlastnosti aktivity a popisuje jejich použití v návrháři.

|Název vlastnosti|Požaduje se|Využití|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Ne|Aktivita, která se má provést, když je podmínka **pravdivá** Chcete-li přidat <xref:System.Activities.Statements.DoWhile.Body%2A> aktivitu, přetáhněte aktivitu ze sady nástrojů do pole **text** v Návrháři aktivity **DoWhile** s textem nápovědy "Sem přetáhněte aktivitu".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Ano|Podmínka, která má být vyhodnocena po každé iteraci smyčky. Chcete-li nastavit <xref:System.Activities.Statements.DoWhile.Condition%2A> , zadejte [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] výraz do pole **Podmínka** v Návrháři aktivity **DoWhile** nebo v mřížce vlastností.|

## <a name="see-also"></a>Viz také
 [While](../workflow-designer/while-activity-designer.md) [Tok řízení](../workflow-designer/control-flow-activity-designers.md)