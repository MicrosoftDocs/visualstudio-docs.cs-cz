---
title: Nepodporovaný datový typ
description: Jedna nebo více vybraných položek obsahuje datový typ, který Návrhář nepodporuje. Zobrazit informace o této zprávě návrháře sady Visual Studio O/R.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c50d47363217a87147275a406d5370cc8736c10b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866642"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Minimálně jedna vybraná položka obsahuje datový typ, který návrhář nepodporuje.

Jedna nebo více položek přetažených z **Průzkumník serveru** nebo **Průzkumníka databáze** do **návrháře o/r** obsahuje datový typ, který není podporován **návrhářem o/r**, například [uživatelsky definované typy CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Oprava této chyby

1. Vytvořte zobrazení založené na požadované tabulce a nezahrnuje datový typ, který není podporován.

2. Přetáhněte zobrazení z **Průzkumník serveru** nebo **Průzkumníka databáze** do návrháře.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
