---
title: 'Postupy: vypnutí pluralizační a zapnutí (Návrhář O-R)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0a2d2e44efc284c38cfc450833839776effb9936
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089380"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Postupy: vypnutí pluralizační a zapnutí (Návrhář relací objektů)
Ve výchozím nastavení při přetažení databázové objekty, které mají názvy končící na s nebo ho bloku z **Průzkumníka serveru** nebo **Průzkumník databáze** na [technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), názvy tříd generovaného entity jsou změněn z množném čísle na singulární. Důvodem je skutečnost, že třída vytvořenou instanci entity se mapuje na jeden záznam dat přesněji představují. Například přidávání `Customers` a **Návrhář relací objektů** výsledkem třídu entity s názvem `Customer` protože třída budou uložena data pro jednoho zákazníka.

> [!NOTE]
>  Pluralizační je ve výchozím nastavení pouze v anglické jazykové verzi Visual Studia.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Chcete-li pluralizační zapnout a vypnout

1.  Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.

2.  V **možnosti** dialogové okno, rozbalte seznam **databázové nástroje**.

    > [!NOTE]
    >  Vyberte **zobrazit všechna nastavení** Pokud **databázové nástroje** uzlu není viditelná.

3.  Klikněte na tlačítko **Návrhář relací objektů**.

4.  Nastavit **Pluralizační názvy** k **povoleno** = **False** nastavit **Návrhář relací objektů** tak, aby nedošlo k jeho změně názvy tříd .

5.  Nastavit **Pluralizační názvy** k **povoleno** = **True** uplatňovat pluralizační pravidla pro názvy tříd objektů, které jsou přidány do **relací objektů Návrhář**.

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)