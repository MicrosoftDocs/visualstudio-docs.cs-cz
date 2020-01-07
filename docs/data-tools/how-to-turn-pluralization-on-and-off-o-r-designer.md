---
title: 'Postupy: zapnutí a vypnutí funkce plural (Návrhář O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 54b3376f9388116f179e2b09bcd136a37f3029f5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586442"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Postupy: zapnutí a vypnutí funkce plural (O/R Designer)
Ve výchozím nastavení, když přetáhnete databázové objekty, které mají názvy končící na s nebo z **Průzkumník serveru** nebo **Průzkumník databáze** na [nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), názvy generovaných tříd entit se změní z hodnoty plural na číslo na jednotné číslo. To je přesnější reprezentace faktu, že třída entity s vytvořenými instancemi je mapována na jeden záznam dat. Například přidání tabulky `Customers` do **návrháře o/R** má za následek třídu entity s názvem `Customer`, protože třída bude obsahovat data pouze pro jednoho zákazníka.

> [!NOTE]
> Pluralita je ve výchozím nastavení zapnuta pouze v anglické verzi sady Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Zapnutí a vypnutí plurality

1. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.

2. V dialogovém okně **Možnosti** rozbalte položku **nástroje databáze**.

    > [!NOTE]
    > Pokud není uzel **nástroje databáze** viditelný, vyberte **Zobrazit všechna nastavení** .

3. Klikněte na tlačítko **O/R Designer**.

4. Nastavte **plurální názvů** na **Enabled** = **false** pro nastavení **Návrháře relací výstupů** tak, aby neměnily názvy tříd.

5. Nastavte **pluráli názvů** na **povoleno** = **hodnotu true** , pokud chcete použít pravidla pro zámnožování na názvy tříd objektů přidaných do **návrháře o/R**.

## <a name="see-also"></a>Viz také:

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
