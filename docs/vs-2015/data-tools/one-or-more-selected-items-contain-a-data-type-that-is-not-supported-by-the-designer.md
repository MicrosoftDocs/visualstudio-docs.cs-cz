---
title: Jedna nebo více vybraných položek obsahuje datový typ, který není podporován návrhářem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e208b697da1c25dfa2e152ad08096f61c876ebe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658042"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Minimálně jedna vybraná položka obsahuje datový typ, který návrhář nepodporuje.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jedna nebo více položek přetažených z **Průzkumník serveru** / **Průzkumník databáze** na [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] obsahuje datový typ, který není podporován [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (například [uživatelsky definované typy CLR](https://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)).

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Vytvořte zobrazení založené na požadované tabulce a nezahrnuje datový typ, který není podporován.

2. Přetáhněte zobrazení z **Průzkumník serveru** / **Průzkumníku databáze** do návrháře.

## <a name="see-also"></a>Viz také
 [LINQ to SQL Tools v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [– návod: vytváření LINQ to SQLch tříd (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
