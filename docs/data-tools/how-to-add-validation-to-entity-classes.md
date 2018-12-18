---
title: 'Postupy: přidávání ověření do tříd entit'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d102bdf20349d6bd4efdecd1c460f1e46646eb37
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089335"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Postupy: přidávání ověření do tříd entit
*Ověřování* tříd entit je proces ověření, že hodnot zadaných do datových objektů v souladu s omezeními ve schématu objektu a také pravidel stanovených pro aplikaci. Ověřování dat, ještě před odesláním aktualizací do základní databáze je dobrým zvykem, která snižuje chyby. Také snižuje potenciální počet odezev mezi aplikace a databáze.

 [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytuje částečné metody, které uživatelům umožňují rozšířit návrhářem generovaný kód, který spouští při vložení, aktualizace a odstraní dokončení entit a také během a po jednotlivých sloupců změny.

> [!NOTE]
>  Toto téma obsahuje základní kroky pro přidání ověření do tříd entit s použitím **Návrhář relací objektů**. Vzhledem k tomu může být obtížné tyto obecné pokyny, bez ohledu na konkrétní entitu třídu, je k dispozici návod, který používá skutečná data.

## <a name="add-validation-for-changes-to-the-value-in-a-specific-column"></a>Přidat ověřování změny na hodnotu v určitém sloupci
 Tento postup ukazuje, jak ověřit data při změně hodnoty ve sloupci. Protože ověřování se provádí v definici třídy (místo v uživatelském rozhraní), je vyvolána výjimka, pokud hodnota způsobí selhání ověření. Implementace zpracování chyb pro kód ve vaší aplikaci, která se pokusí změnit hodnoty ve sloupcích.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-validate-data-during-a-columns-value-change"></a>Ověřit data během změna hodnoty sloupci

1.  Otevřít nebo vytvořit nové technologie LINQ to SQL třídy souboru (**dbml** souboru) v **Návrhář relací objektů**. (Dvakrát klikněte **dbml** souboru v **Průzkumníku řešení**.)

2.  V **Návrhář relací objektů**, klikněte pravým tlačítkem na třídu, pro který chcete přidat ověřování a potom klikněte na **kód zobrazení**.

     Otevře se Editor kódu s konkrétní třídu pro třídu vybrané entity.

3.  Umístěte kurzor třídu.

4.  Pro projekty Visual Basic:

    1.  Rozbalte **název metody** seznamu.

    2.  Vyhledejte **OnCOLUMNNAMEChanging** metodu sloupce, které chcete přidat k ověření.

    3.  `OnCOLUMNNAMEChanging` Metody se přidá třídu.

    4.  Přidejte následující kód, který nejdřív ověřte, zda byla zadána hodnota, a pak zajistit, aby hodnota zadaná pro sloupec je přijatelné pro vaši aplikaci. `value` Argument obsahuje navrhované hodnotu, proto přidejte logiku pro potvrzení, že se jedná o platnou hodnotu:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Pro projekty C#:

    Protože projektů C# nevydávají automaticky obslužné rutiny událostí, můžete vytvořit sloupec změna částečné metody IntelliSense. Typ `partial` a pak prostor pro přístup k seznamu dostupných částečné metody. Klikněte na tlačítko metodu Změna sloupce pro sloupec, který chcete přidat ověřování. Kód, který se vygeneruje, když vyberete metodu částečné změna sloupec se podobá následující kód:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="add-validation-for-updates-to-an-entity-class"></a>Přidat ověřování aktualizací třídu Entity
 Kromě kontroly hodnoty během změny, můžete také ověřit data, když je proveden pokus o aktualizaci třídu úplnou entitu. Ověření při pokusu o aktualizaci můžete porovnat hodnoty do více sloupců, pokud to vyžadují obchodní pravidla. Následující postup ukazuje, jak ověřit, pokud je proveden pokus o aktualizaci třídu úplnou entitu.

> [!NOTE]
>  Kód pro ověření aktualizací k dokončení tříd entit, které se spouštějí v tom s částečným <xref:System.Data.Linq.DataContext> – třída (místo v třídu třídy konkrétní entity).

### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Ověřit data během aktualizace třídu entity

1.  Otevřít nebo vytvořit nové technologie LINQ to SQL třídy souboru (**dbml** souboru) v **Návrhář relací objektů**. (Dvakrát klikněte **dbml** souboru v **Průzkumníku řešení**.)

2.  Klikněte pravým tlačítkem na prázdnou oblast na **Návrhář relací objektů** a klikněte na tlačítko **kód zobrazení**.

     Editor kódu otevře pro konkrétní třídu `DataContext`.

3.  Umístěte kurzor do třídu pro `DataContext`.

4.  Pro projekty Visual Basic:

    1.  Rozbalte **název metody** seznamu.

    2.  Klikněte na tlačítko **UpdateENTITYCLASSNAME**.

    3.  `UpdateENTITYCLASSNAME` Metody se přidá třídu.

    4.  Přístup pomocí hodnoty jednotlivých sloupců `instance` argument, jak je znázorněno v následujícím kódu:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Pro projekty C#:

    Protože projektů C# nevydávají automaticky obslužné rutiny událostí, IntelliSense můžete vytvořit s částečným `UpdateCLASSNAME` metoda. Typ `partial` a pak prostor pro přístup k seznamu dostupných částečné metody. Klikněte na tlačítko aktualizační metody pro třídu, na který chcete přidat ověřování. Kód, který se vygeneruje, když vyberete se podobá následující kód `UpdateCLASSNAME` částečné metoda:

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

## <a name="see-also"></a>Viz také:

- [Technologie LINQ to SQL nástroje v sadě Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Ověřování dat](../data-tools/validate-data-in-datasets.md)
- [Technologie LINQ to SQL (rozhraní .NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)