---
title: Změnu návratového typu metody DataContext nelze vrátit zpět.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 95d75e084b4824cf7cc8e717b1ce9174e76aa2e7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648695"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Změnu návratového typu metody DataContext nelze vrátit zpět.

Změna návratového typu metody DataContext se nedá vrátit zpátky. Chcete-li se vrátit k automaticky vygenerovanému typu, je třeba přetáhnout položku z okna **Průzkumník serveru** nebo **Průzkumníka databáze** do návrháře o/R. Opravdu chcete změnit návratový typ?

Návratový typ metody <xref:System.Data.Linq.DataContext> se liší v závislosti na tom, kde vyřadíte položku v [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Pokud přetáhnete položku přímo na existující třídu entity, vytvoří se <xref:System.Data.Linq.DataContext> metoda, která má návratový typ třídy entity. Pokud položku vyřadíte do prázdné oblasti [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vytvoří se <xref:System.Data.Linq.DataContext> metoda, která vrací automaticky generovaný typ. Můžete změnit návratový typ metody <xref:System.Data.Linq.DataContext> poté, co ji přidáte do podokna metody. Chcete-li zkontrolovat nebo změnit návratový typ metody <xref:System.Data.Linq.DataContext>, vyberte ji a klikněte na vlastnost **návratový typ** v okně **vlastnosti** .

## <a name="to-change-the-return-type-of-a-datacontext"></a>Změna návratového typu DataContext

- Klikněte na tlačítko **Ano**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Zavření okna se zprávou a ponechání návratového typu beze změny

- Klikněte na tlačítko **ne**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Pro návrat k původnímu návratový typ po změně návratového typu

1. V [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] vyberte metodu <xref:System.Data.Linq.DataContext> a odstraňte ji.

2. Vyhledejte položku v **průzkumníku Průzkumník serveru/databáze** a přetáhněte ji do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    Metoda <xref:System.Data.Linq.DataContext> je vytvořena s původní výchozí návratový typ.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)