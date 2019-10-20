---
title: 'Postupy: vytvoření přidružení (vztahu) mezi LINQ to SQL třídy (Návrhář O-R) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c2f6f6f65410336eacf72967c8360a56e8fa5ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610005"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Postupy: vytvoření přidružení (relace) mezi třídami LINQ to SQL (Návrhář O/R)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přidružení mezi třídami entit v [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] jsou podobná vztahům mezi tabulkami v databázi. Přidružení mezi třídami entit můžete vytvořit pomocí dialogového okna **Editor přidružení** .

 Je nutné vybrat nadřazenou třídu a podřízenou třídu při použití dialogového okna **Editor přidružení** k vytvoření přidružení. Nadřazená třída je třída entity, která obsahuje primární klíč; podřízená třída je třída entity, která obsahuje cizí klíč. Například pokud byly vytvořeny třídy entit, které jsou mapovány k tabulkám zákazníků a objednávek Northwind, třída Customer by byla nadřazenou třídou a třída ORDER by byla podřízenou třídou.

> [!NOTE]
> Když přetáhnete tabulky z **Průzkumník serveru** /**průzkumníku databáze** na [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), přidružení se automaticky vytvoří na základě stávajících vztahů cizího klíče v databázi.

 Když při vytváření přidružení vyberete přidružení v Návrháři pro/R, v okně **vlastnosti** jsou některé konfigurovatelné vlastnosti. (Přidružení je čára mezi souvisejícími třídami.) Následující tabulka uvádí popisy vlastností přidružení.

|Vlastnost|Popis|
|--------------|-----------------|
|**Kardinalita**|Určuje, zda je přidružení typu 1: n nebo 1:1.|
|**Podřízená vlastnost**|Určuje, zda se má vytvořit vlastnost u nadřazené položky, která je kolekcí nebo odkazem na podřízené záznamy na straně cizího klíče asociace. Například v přidružení mezi zákazníkem a objednávkou, pokud je **Podřízená vlastnost** nastavena na **hodnotu true**, je vytvořena vlastnost s názvem Orders v nadřazené třídě.|
|**Nadřazená vlastnost**|Vlastnost u podřízené třídy, která odkazuje na přidruženou nadřazenou třídu. Například při přidružení mezi zákazníkem a objednávkou se vytvoří vlastnost s názvem zákazník, která odkazuje na přidruženého zákazníka pro objednávku ve třídě Order.|
|**Zúčastněné vlastnosti**|Zobrazí vlastnosti přidružení a poskytne tlačítko se **třemi tečkami** (...), které znovu otevře dialogové okno **Editor přidružení** .|
|**Tabulka**|Určuje, zda mají sloupce cizího cíle omezení jedinečnosti.|

### <a name="to-create-an-association-between-entity-classes"></a>Vytvoření přidružení mezi třídami entit

1. Klikněte pravým tlačítkem na třídu entity, která představuje nadřazenou třídu v přidružení, přejděte na **Přidat**a pak klikněte na **přidružení**.

2. Ověřte, zda je v dialogovém okně **Editor přidružení** vybrána správná **nadřazená třída** .

3. V poli se seznamem vyberte **podřízenou třídu** .

4. Vyberte **Vlastnosti přidružení** , které se vztahují ke třídám. Obvykle se tato mapa mapuje na vztah cizího klíče definovaného v databázi. Například v přidružení zákazníků a objednávek jsou **Vlastnosti přidružení** KódZákazníka pro každou třídu.

5. Kliknutím na tlačítko **OK** vytvořte přidružení.

## <a name="see-also"></a>Viz také
 [LINQ to SQL Tools v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [– Návod: vytváření tříd LINQ to SQL (o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [metod DataContext (o/r Designer](../data-tools/datacontext-methods-o-r-designer.md) ) [Postupy: reprezentace primárních klíčů](https://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)
