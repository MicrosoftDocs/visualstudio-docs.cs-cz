---
title: Jak vytvořit relaci mezi třídy LINQ to SQL pomocí Návrhář relací objektů
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d247603e14f431e44aa7c1589ba2ecd7463fac02
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089526"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Postupy: vytvoření přidružení mezi technologie LINQ to SQL třídy (Návrhář relací objektů)
Přidružení mezi třídami entity v [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] se podobá se relace mezi tabulkami v databázi. Můžete vytvořit přidružení mezi tříd entit s použitím **přidružení Editor** dialogové okno.

Při použití musíte vybrat nadřazenou třídu a podřízené třídy **přidružení Editor** dialogové okno vytvořit přidružení. Nadřazené třídy je třída entity, která obsahuje primární klíč. Třída podřízené je třídu entity, která obsahuje cizí klíč. Například, pokud entity třídy byly vytvořeny, které jsou namapovány na `Northwind Customers` a `Orders` tabulky, `Customer` třída by nadřazené třídy a `Order` třídu by mít podřízené třídy.

> [!NOTE]
>  Při přetažení tabulky z **Průzkumníka serveru** nebo **Průzkumník databáze** na **Návrhář relací objektů** (**Návrhář relací objektů**), přidružení se vytvářejí automaticky podle existující relace cizího klíče v databázi.

## <a name="association-properties"></a>Vlastnosti přidružení
Po vytvoření přidružení, když vyberete přidružení v **Návrhář relací objektů**, nejsou některé konfigurovatelné vlastnosti v **vlastnosti** okno. (Přidružení je řádek mezi související třídy.) Následující tabulka obsahuje popis vlastností přidružení.

|Vlastnost|Popis|
|--------------|-----------------|
|**Mohutnost**|Určuje, zda je přidružení na více nebo 1: 1.|
|**Podřízená – vlastnost**|Určuje, zda chcete vytvořit vlastnost na nadřazeného objektu, který je kolekce nebo odkaz na podřízené záznamy na straně přidružení cizího klíče. Například v přidružení mezi `Customer` a `Order`, pokud **vlastnost podřízeného** je nastaven na **True**, vlastnost s názvem `Orders` je vytvořen v nadřazené třídy.|
|**Nadřazený klíč**|Vlastnost na podřízené třídu, která odkazuje na související nadřazené třídy. Například v přidružení mezi `Customer` a `Order`, vlastnost s názvem `Customer` , který odkazuje přidružené zákazník pro pořadí je vytvořena na `Order` třídy.|
|**Zúčastněných vlastnosti**|Zobrazí vlastnosti přidružení a poskytuje **třemi tečkami** tlačítko (...), které se znovu otevře **přidružení Editor** dialogové okno.|
|**Jedinečné**|Určuje, jestli cizí cílových sloupců mají omezení jedinečnosti.|

## <a name="to-create-an-association-between-entity-classes"></a>K vytvoření přidružení mezi třídami entity

1.  Klikněte pravým tlačítkem na třídu entity, která představuje nadřazené třídy v association, přejděte na **přidat**a potom klikněte na **přidružení**.

2.  Ověřte, že správný **nadřazené třídy** je vybraný v **přidružení Editor** dialogové okno.

3.  Vyberte **podřízené třídy** do pole se seznamem.

4.  Vyberte **vlastnosti přidružení** které se týkají třídy. Obvykle to mapuje relace cizího klíče, které jsou definované v databázi. Například v `Customers` a `Orders` přidružení, **vlastnosti přidružení** jsou `CustomerID` pro každou třídu.

5.  Klikněte na tlačítko **OK** vytváření přidružení.

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: Vytvoření LINQ na SQL třídy](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (Návrhář relací objektů)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: představují primární klíče](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)