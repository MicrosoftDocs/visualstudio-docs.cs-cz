---
title: Nejde zrušit změnu návratového typu.
description: Změna návratového typu metody DataContext se nedá vrátit zpátky. Zobrazit informace o této zprávě aplikace Visual Studio Návrhář relací objektů (Návrhář O/R).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 71112b90f45fbc2b86aeb3f7e1935c38974a3694
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867305"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Změnu návratového typu metody DataContext nelze vrátit zpět.

Změna návratového typu metody DataContext se nedá vrátit zpátky. Chcete-li se vrátit k automaticky vygenerovanému typu, je třeba přetáhnout položku z okna **Průzkumník serveru** nebo **Průzkumníka databáze** do návrháře o/R. Opravdu chcete změnit návratový typ?

Návratový typ <xref:System.Data.Linq.DataContext> metody se liší v závislosti na tom, kde vyřadíte položku v [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] . Pokud přetáhnete položku přímo na existující třídu entity, vytvoří <xref:System.Data.Linq.DataContext> se metoda, která má návratový typ třídy entity. Pokud přetáhnete položku do prázdné oblasti [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , <xref:System.Data.Linq.DataContext> je vytvořena metoda, která vrací automaticky generovaný typ. Návratový typ metody lze změnit <xref:System.Data.Linq.DataContext> poté, co ji přidáte do podokna metody. Chcete-li zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metody, vyberte ji a klikněte na vlastnost **návratový typ** v okně **vlastnosti** .

## <a name="to-change-the-return-type-of-a-datacontext"></a>Změna návratového typu DataContext

- Klikněte na **Ano**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Zavření okna se zprávou a ponechání návratového typu beze změny

- Klikněte na tlačítko **ne**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Pro návrat k původnímu návratový typ po změně návratového typu

1. Vyberte <xref:System.Data.Linq.DataContext> metodu v [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] a odstraňte ji.

2. Vyhledejte položku v **průzkumníku Průzkumník serveru/databáze** a přetáhněte ji na [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] .

    <xref:System.Data.Linq.DataContext>Metoda je vytvořena s původní výchozí návratový typ.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)