---
title: 'Postupy: Přidání ověřování do tříd entit'
description: Přečtěte si, jak přidat ověřování do tříd entit. Přidejte ověřování pro změny hodnoty v určitém sloupci. Přidejte ověřování pro aktualizace třídy entity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4f367cf799dd00b8b442870554e499e5405865cb
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435101"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Postupy: Přidání ověřování do tříd entit
*Ověřování* tříd entit je proces potvrzení, že hodnoty zadané do datových objektů vyhovují omezením ve schématu objektu a také k pravidlům stanoveným pro aplikaci. Ověřování dat před odesláním aktualizací do podkladové databáze je dobrým zvykem, který snižuje chyby. Také snižuje potenciální počet výměn mezi aplikací a databází.

[Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytují částečné metody, které uživatelům umožňují rozšiřování kódu vygenerovaného návrhářem, který se spouští během vkládání, aktualizací a odstraňování kompletních entit a také během a po změně jednotlivých sloupců.

> [!NOTE]
> Toto téma popisuje základní kroky pro přidání ověřování do tříd entit pomocí **návrháře o/R**. Vzhledem k tomu, že může být obtížné postupovat podle těchto obecných kroků bez odkazování na konkrétní třídu entity, je k dispozici návod, který používá skutečná data.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Přidat ověřování pro změny hodnoty v určitém sloupci
Tento postup ukazuje, jak ověřit data při změně hodnoty ve sloupci. Vzhledem k tomu, že se ověřování provádí uvnitř definice třídy (místo v uživatelském rozhraní), je vyvolána výjimka, pokud hodnota způsobí selhání ověřování. Implementujte zpracování chyb pro kód ve vaší aplikaci, který se pokusí změnit hodnoty sloupce.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Ověření dat během změny hodnoty sloupce

1. Otevřete nebo vytvořte nový soubor LINQ to SQLch tříd (soubor **. dbml** ) v **Návrháři o/R**. (Poklikejte na soubor **. dbml** v **Průzkumník řešení**.)

2. V **Návrháři o/R** klikněte pravým tlačítkem na třídu, pro kterou chcete přidat ověřování, a pak klikněte na **Zobrazit kód**.

     Otevře se Editor kódu s částečnou třídou pro vybranou třídu entity.

3. Umístěte kurzor do částečné třídy.

4. Pro Visual Basic projekty:

    1. Rozbalte seznam **název metody** .

    2. Vyhledejte metodu **OnCOLUMNNAMEChanging** pro sloupec, do kterého chcete přidat ověřování.

    3. `OnCOLUMNNAMEChanging`Do částečné třídy je přidána metoda.

    4. Přidejte následující kód, který nejprve ověří, zda byla zadána hodnota, a poté pro zajištění, že hodnota zadaná pro sloupec je pro vaši aplikaci přijatelná. `value`Argument obsahuje navrhovanou hodnotu, takže přidejte logiku pro potvrzení, že je platná hodnota:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Pro projekty v jazyce C#:

    Vzhledem k tomu, že projekty C# negenerují automaticky obslužné rutiny událostí, lze pomocí technologie IntelliSense vytvořit částečné metody měnící sloupce. Zadejte `partial` a potom místo pro přístup k seznamu dostupných částečných metod. Klikněte na metodu měnící sloupce pro sloupec, pro který chcete přidat ověřování. Následující kód se podobá kódu, který je generován při výběru částečné metody změny sloupce:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Přidání ověření pro aktualizace třídy entity
Kromě kontroly hodnot během změn můžete také ověřit data při pokusu o aktualizaci celé třídy entity. Ověřování při pokusu o aktualizaci umožňuje porovnat hodnoty v několika sloupcích, pokud to obchodní pravidla vyžadují. Následující postup ukazuje, jak ověřit, kdy je proveden pokus o aktualizaci kompletní třídy entity.

> [!NOTE]
> Ověřovací kód pro aktualizace pro kompletní třídy entit je spuštěn v částečné <xref:System.Data.Linq.DataContext> třídě (namísto částečné třídy konkrétní třídy entity).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Ověření dat během aktualizace na třídu entity

1. Otevřete nebo vytvořte nový soubor LINQ to SQLch tříd (soubor **. dbml** ) v **Návrháři o/R**. (Poklikejte na soubor **. dbml** v **Průzkumník řešení**.)

2. Klikněte pravým tlačítkem myši na prázdnou oblast v **Návrháři o/R** a pak klikněte na **Zobrazit kód**.

     Editor kódu se otevře s částečnou třídou pro `DataContext` .

3. Umístěte kurzor do částečné třídy pro `DataContext` .

4. Pro Visual Basic projekty:

    1. Rozbalte seznam **název metody** .

    2. Klikněte na **UpdateENTITYCLASSNAME**.

    3. `UpdateENTITYCLASSNAME`Do částečné třídy je přidána metoda.

    4. Přístup k jednotlivým hodnotám sloupců pomocí `instance` argumentu, jak je znázorněno v následujícím kódu:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Pro projekty v jazyce C#:

    Vzhledem k tomu, že projekty C# negenerují automaticky obslužné rutiny událostí, lze pomocí technologie IntelliSense vytvořit částečnou `UpdateCLASSNAME` metodu. Zadejte `partial` a potom místo pro přístup k seznamu dostupných částečných metod. Klikněte na metodu aktualizace pro třídu, na kterou chcete přidat ověřování. Následující kód se podobá kódu, který je generován při výběru `UpdateCLASSNAME` částečné metody:

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>Viz také

- [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Ověřování dat](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
