---
title: 'Postupy: zapnutí a vypnutí funkce plural (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665937"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Postupy: Zapnutí a vypnutí pluralizace (Návrhář relací objektů)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení platí, že při přetahování databázových objektů, které mají názvy končící na s nebo z **Průzkumník serveru** / **Průzkumník databáze** na [nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), názvy generovaných tříd entit jsou změněny z hodnoty plural na číslo v čísle. To je přesnější reprezentace faktu, že třída entity s vytvořenými instancemi je mapována na jeden záznam dat. Například přidání tabulky Customers do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] výsledků v třídě entity s názvem Customer, protože třída bude obsahovat data pouze pro jednoho zákazníka.

> [!NOTE]
> Pluralita je ve výchozím nastavení zapnuta pouze v anglické verzi sady Visual Studio.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Zapnutí a vypnutí plurality

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. V dialogovém okně **Možnosti** rozbalte položku **nástroje databáze**.

> [!NOTE]
> Pokud není uzel **nástroje databáze** viditelný, vyberte **Zobrazit všechna nastavení** .

1. Klikněte na tlačítko **O/R Designer**.

2. Nastavte **pluralitu názvů** na hodnotu **povoleno**  =  **False** , pokud chcete nastavit [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] tak, aby neměnila názvy tříd.

3. Nastavte **pluralitu názvů** **na**  =  **hodnotu true** , chcete-li použít pravidla pro zámnožování na názvy tříd objektů přidaných do [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

## <a name="see-also"></a>Viz také
 [LINQ to SQL nástroje v aplikaci Visual studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [přístup k datům v aplikaci Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
