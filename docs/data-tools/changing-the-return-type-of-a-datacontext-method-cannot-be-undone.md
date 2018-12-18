---
title: Změnu návratového typu metody DataContext nelze vrátit zpět.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: abec4dd6d5cded79e1f25a6dbb5ec2e55c2d444f
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282752"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Změnu návratového typu metody DataContext nelze vrátit zpět.

Změna návratový typ metody DataContext nelze vrátit zpět. Chcete-li vrátit zpět na automaticky generovaný typ, musí přetáhněte ji z **Průzkumníka serveru** nebo **Průzkumník databáze** na Návrhář relací objektů znovu. Opravdu že chcete změnit návratový typ?

Návratový typ <xref:System.Data.Linq.DataContext> metoda se liší v závislosti na tom, kde je vyřadit položky [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Pokud je vyřadit položku přímo do existující třídy entity, <xref:System.Data.Linq.DataContext> metodu, která má návratový typ třídy entita se vytvoří. Pokud je položka vyřadit na prázdnou oblast [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], <xref:System.Data.Linq.DataContext> metoda, která vrátí typ automaticky generované se vytvoří. Můžete změnit návratový typ <xref:System.Data.Linq.DataContext> metoda po přidání do podokna metody. Zkontrolovat nebo změnit návratový typ <xref:System.Data.Linq.DataContext> metoda, vyberte ho a klikněte na tlačítko **návratového typu** vlastnost **vlastnosti** okno.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Chcete-li změnit návratový typ DataContext

- Klikněte na tlačítko **Ano**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Chcete ukončit okno se zprávou a ponechat beze změny návratový typ

- Klikněte na tlačítko **ne**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Chcete-li vrátit k původní návratový typ po změně návratový typ

1. Vyberte <xref:System.Data.Linq.DataContext> metodu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] a odstraňte ji.

2. Vyhledání položky v **Průzkumníka serveru Průzkumníka a databáze** a přetáhněte ji do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    A <xref:System.Data.Linq.DataContext> metoda je vytvořena s původní výchozí návratovým typem.

## <a name="see-also"></a>Viz také:

- [Zprávy Návrháře relací objektů](../data-tools/o-r-designer-messages.md)
- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)