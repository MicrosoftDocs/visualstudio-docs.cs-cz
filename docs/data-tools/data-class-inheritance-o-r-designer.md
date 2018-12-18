---
title: Data dědičnosti tříd (Návrhář O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6c6b17ad38e9aae78975e43797931a326955712d
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756734"
---
# <a name="data-class-inheritance-or-designer"></a>Data dědičnosti tříd (Návrhář relací objektů)

Jako u jiných objektů třídy LINQ to SQL můžete použít dědičnosti a být odvozen od jiné třídy. V kódu můžete zadat dědičnosti vztahy mezi objekty podle deklarace, že jedna třída dědí z jiné. V databázi jsou vytvořit relace dědičnosti několika způsoby. **Návrhář relací objektů** (**Návrhář relací objektů**) podporuje koncept dědění jedné tabulky, jak často jsou implementované v relačním systémech.

V jedné tabulce dědičnosti je jedné databáze tabulku, která obsahuje sloupce pro základní a odvozené třídy. Pomocí relačních dat sloupce diskriminátoru obsahuje hodnotu, která určuje, které třídy patří všechny daného záznamu. Představte si třeba `Persons` tabulku, která obsahuje všechny zaměstnaní společnosti. Někteří uživatelé mají zaměstnanci a někteří uživatelé mají správci. `Persons` Tabulka obsahuje sloupec s názvem `Type` s hodnotou 1 pro správce a hodnota 2 pro zaměstnance. `Type` Sloupec je sloupce diskriminátoru. V tomto scénáři můžete vytvořit podtřídou třídy zaměstnanci a naplnit třída se pouze záznamy, které mají `Type` hodnota 2.

Když konfigurujete dědičnosti v tříd entit s použitím [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], přetáhněte jedna tabulka, která obsahuje data dědičnosti do návrháře dvakrát: jednou pro každou třídu v hierarchii dědičnosti. Po přidání tabulky do návrháře, připojte je s položku dědičnost z **Návrhář relací objektů** sada nástrojů a potom nastavit čtyři dědičnost vlastnosti v **vlastnosti** okno.

## <a name="inheritance-properties"></a>Dědičnost vlastnosti

Následující tabulka uvádí dědičnost vlastností a jejich popisy:

|Vlastnost|Popis|
|--------------|-----------------|
|**Vlastnost diskriminátoru**|Vlastnost (namapovaná na sloupec), která určuje, které třídy patří záznam na aktuální záznam.|
|**Hodnota diskriminátoru základní třídy**|Hodnota (v sloupec označený jako **diskriminátoru vlastnost**), zjistí, že záznam základní třídy.|
|**Hodnota diskriminátoru odvozené třídy**|Hodnota (v určen jako vlastnost **diskriminátoru vlastnost**), zjistí, že záznam odvozené třídy.|
|**Výchozí dědičnosti**|Třída, která se zaplní při hodnotě ve vlastnosti určený jako **diskriminátoru vlastnost** neodpovídá buď **hodnota diskriminátoru základní třídy** nebo **odvozené třídy Hodnota diskriminátoru**.|

Vytváření objektový model, který používá dědičnosti a odpovídá relačních dat může být poněkud matoucí. Toto téma obsahuje informace o základních koncepcích a jednotlivé vlastnosti, které jsou požadovány pro konfiguraci dědičnosti. Následující témata obsahují jasnější vysvětlení, jak nakonfigurovat dědičnosti s **Návrhář relací objektů**.

|Téma|Popis|
|-----------|-----------------|
|[Postupy: Konfigurace dědičnosti pomocí Návrhář relací objektů](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Popisuje postup konfigurace tříd entit, které použití jedné tabulky dědičnosti pomocí **Návrhář relací objektů**.|
|[Návod: Vytvoření LINQ na třídy SQL pomocí jedné tabulky dědičnosti (Návrhář relací objektů)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Poskytuje podrobné pokyny ke konfiguraci třídy entity, které použití jedné tabulky dědičnosti pomocí **Návrhář relací objektů**.|

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Návod: Vytvoření LINQ na SQL třídy (Návrhář O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Návod: Vytvoření LINQ na třídy SQL pomocí jedné tabulky dědičnosti (Návrhář relací objektů)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Začínáme](/dotnet/framework/data/adonet/sql/linq/getting-started)