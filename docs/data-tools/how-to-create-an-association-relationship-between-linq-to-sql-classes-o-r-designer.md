---
title: Vztahy mezi třídami LINQ to SQL (Návrhář O/R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fb81cf17de86a11d2373f6a545b3efc78e65ada9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586468"
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Postupy: vytvoření přidružení mezi třídami LINQ to SQL (Návrhář O/R)
Přidružení mezi třídami entit v [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] jsou podobná vztahům mezi tabulkami v databázi. Přidružení mezi třídami entit můžete vytvořit pomocí dialogového okna **Editor přidružení** .

Je nutné vybrat nadřazenou třídu a podřízenou třídu při použití dialogového okna **Editor přidružení** k vytvoření přidružení. Nadřazená třída je třída entity, která obsahuje primární klíč; podřízená třída je třída entity, která obsahuje cizí klíč. Například pokud byly vytvořeny třídy entit, které jsou mapovány na tabulky `Northwind Customers` a `Orders`, třída `Customer` bude nadřazenou třídou a třída `Order` by byla podřízenou třídou.

> [!NOTE]
> Když přetáhnete tabulky z **Průzkumník serveru** nebo **průzkumníka databáze** do **Návrhář relací objektů** (**O/R Designer**), vytvoří se přidružení automaticky na základě stávajících vztahů cizího klíče v databázi.

## <a name="association-properties"></a>Vlastnosti přidružení
Když při vytváření přidružení vyberete přidružení v **Návrháři pro/R**, v okně **vlastnosti** jsou některé konfigurovatelné vlastnosti. (Přidružení je čára mezi souvisejícími třídami.) Následující tabulka uvádí popisy vlastností přidružení.

|Vlastnost|Popis|
|--------------|-----------------|
|**Kardinalita**|Určuje, zda je přidružení typu 1: n nebo 1:1.|
|**Podřízená vlastnost**|Určuje, zda se má vytvořit vlastnost u nadřazené položky, která je kolekcí nebo odkazem na podřízené záznamy na straně cizího klíče asociace. Například v přidružení mezi `Customer` a `Order`, pokud je **Podřízená vlastnost** nastavena na **hodnotu true**, je v nadřazené třídě vytvořená vlastnost s názvem `Orders`.|
|**Nadřazená vlastnost**|Vlastnost u podřízené třídy, která odkazuje na přidruženou nadřazenou třídu. Například při přidružení mezi `Customer` a `Order`se vytvoří vlastnost s názvem `Customer`, která odkazuje na přidruženého zákazníka pro objednávku na `Order` třídě.|
|**Zúčastněné vlastnosti**|Zobrazí vlastnosti přidružení a poskytne tlačítko se **třemi tečkami** (...), které znovu otevře dialogové okno **Editor přidružení** .|
|**Tabulka**|Určuje, zda mají sloupce cizího cíle omezení jedinečnosti.|

## <a name="to-create-an-association-between-entity-classes"></a>Vytvoření přidružení mezi třídami entit

1. Klikněte pravým tlačítkem na třídu entity, která představuje nadřazenou třídu v přidružení, přejděte na **Přidat**a pak klikněte na **přidružení**.

2. Ověřte, zda je v dialogovém okně **Editor přidružení** vybrána správná **nadřazená třída** .

3. V poli se seznamem vyberte **podřízenou třídu** .

4. Vyberte **Vlastnosti přidružení** , které se vztahují ke třídám. Obvykle se tato mapa mapuje na vztah cizího klíče definovaného v databázi. Například v přidružení `Customers` a `Orders` jsou **Vlastnosti přidružení** `CustomerID` pro každou třídu.

5. Kliknutím na tlačítko **OK** vytvořte přidružení.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: vytváření tříd LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metody DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Postupy: reprezentace primárních klíčů](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)
