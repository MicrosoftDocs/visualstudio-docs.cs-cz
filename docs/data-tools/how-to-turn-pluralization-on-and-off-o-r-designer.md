---
title: 'Postupy: zapnutí a vypnutí funkce plural (Návrhář O-R)'
description: Informace o tom, jak zapnout a vypnout použití v Návrhář relací objektů (O/R Designer) Výchozí nastavení převede plurální názvy na číslo v čísle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6ea872d96e59365f3dbef5dc3568641c30e51606
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434893"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Postupy: Zapnutí a vypnutí pluralizace (Návrhář relací objektů)
Ve výchozím nastavení, když přetáhnete databázové objekty, které mají názvy končící na s nebo z **Průzkumník serveru** nebo **Průzkumník databáze** na [nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), názvy generovaných tříd entit se změní z hodnoty plural na číslo na jednotné číslo. To je přesnější reprezentace faktu, že třída entity s vytvořenými instancemi je mapována na jeden záznam dat. Například přidání `Customers` tabulky do **návrháře o/R** má za následek třídu entity s názvem, `Customer` protože třída bude obsahovat data pouze pro jednoho zákazníka.

> [!NOTE]
> Pluralita je ve výchozím nastavení zapnuta pouze v anglické verzi sady Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Zapnutí a vypnutí plurality

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. V dialogovém okně **Možnosti** rozbalte položku **nástroje databáze**.

    > [!NOTE]
    > Pokud není uzel **nástroje databáze** viditelný, vyberte **Zobrazit všechna nastavení** .

3. Klikněte na tlačítko **O/R Designer**.

4. Nastavte **pluralitu názvů** na hodnotu **povoleno** ,  =  **False** Pokud chcete nastavit **Návrháře relací výstupů** tak, aby se nezměnily názvy tříd.

5. Nastavte **pluralitu názvů** **na**  =  **hodnotu true** , chcete-li použít pravidla pro zámnožování na názvy tříd objektů přidaných do **návrháře o/R**.

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Technologie LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
