---
title: Minimálně jedna vybraná položka obsahuje datový typ, který návrhář nepodporuje.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e2f4911c79ac6d44d2553f3db15c5649dd7160f9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586351"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Minimálně jedna vybraná položka obsahuje datový typ, který návrhář nepodporuje.

Jedna nebo více položek přetažených z **Průzkumník serveru** nebo **Průzkumníka databáze** do **návrháře o/r** obsahuje datový typ, který není podporován **návrhářem o/r**, například [uživatelsky definované typy CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Vytvořte zobrazení založené na požadované tabulce a nezahrnuje datový typ, který není podporován.

2. Přetáhněte zobrazení z **Průzkumník serveru** nebo **Průzkumníka databáze** do návrháře.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
