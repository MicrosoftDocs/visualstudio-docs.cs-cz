---
title: 'Postupy: Přidání ověření do tříd entit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a68b0314f3c64ce9196b8d48a78844bc81990a92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665985"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Postupy: Přidání ověřování do tříd entit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Ověřování* tříd entit je proces potvrzení, že hodnoty zadané do datových objektů vyhovují omezením ve schématu objektu a také k pravidlům stanoveným pro aplikaci. Ověřování dat před odesláním aktualizací do podkladové databáze je dobrým zvykem, který snižuje chyby. Také snižuje potenciální počet výměn mezi aplikací a databází.

 [Nástroje LINQ to SQL v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) poskytují částečné metody, které uživatelům umožňují rozšiřování kódu vygenerovaného návrhářem, který se spouští během vkládání, aktualizací a odstraňování kompletních entit a také během a po změně jednotlivých sloupců.

> [!NOTE]
> Toto téma popisuje základní kroky pro přidání ověřování do tříd entit pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Vzhledem k tomu, že může být obtížné postupovat podle těchto obecných kroků bez odkazování na konkrétní třídu entity, je k dispozici návod, který používá skutečná data.

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Přidání ověřování pro změny hodnoty v určitém sloupci
 Tento postup ukazuje, jak ověřit data při změně hodnoty ve sloupci. Vzhledem k tomu, že se ověřování provádí uvnitř definice třídy (místo v uživatelském rozhraní), je vyvolána výjimka, pokud hodnota způsobí selhání ověření. Implementujte zpracování chyb pro kód ve vaší aplikaci, který se pokusí změnit hodnoty sloupce.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>Ověření dat během změny hodnoty sloupce

1. Otevřete nebo vytvořte nový soubor LINQ to SQLch tříd (soubor **. dbml** ) v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Poklikejte na soubor **. dbml** v **Průzkumník řešení**.)

2. V Návrháři O/R klikněte pravým tlačítkem na třídu, pro kterou chcete přidat ověřování, a pak klikněte na **Zobrazit kód**.

    Otevře se Editor kódu s částečnou třídou pro vybranou třídu entity.

3. Umístěte kurzor do částečné třídy.

4. Pro Visual Basic projekty:

   1. Rozbalte seznam **název metody** .

   2. Vyhledejte metodu **on**._COLUMNNAME_**Changing** pro sloupec, do kterého chcete přidat ověřování.

   3. Metoda `On` *COLUMNNAME* `Changing` je přidána do částečné třídy.

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

   5. Vzhledem k tomu, že projekty C# negenerují automaticky obslužné rutiny událostí, lze pomocí technologie IntelliSense vytvořit částečné metody měnící sloupce.

       Zadejte `partial` a potom místo pro přístup k seznamu dostupných částečných metod. Klikněte na metodu měnící sloupce pro sloupec, pro který chcete přidat ověřování. Následující kód se podobá kódu, který je generován při výběru částečné metody změny sloupce:

      ```csharp
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
          {
             throw new System.NotImplementedException();
          }

      ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>Přidání ověřování pro aktualizace pro třídu entity
 Kromě kontroly hodnot během změn můžete také ověřit data při pokusu o aktualizaci celé třídy entity. Ověřování při pokusu o aktualizaci umožňuje porovnat hodnoty v několika sloupcích, pokud to obchodní pravidla vyžadují. Následující postup ukazuje, jak ověřit, kdy je proveden pokus o aktualizaci kompletní třídy entity.

> [!NOTE]
> Ověřovací kód pro aktualizace pro kompletní třídy entit je spuštěn v částečné <xref:System.Data.Linq.DataContext> třídě (namísto částečné třídy konkrétní třídy entity).

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Ověření dat během aktualizace na třídu entity

1. Otevřete nebo vytvořte nový soubor LINQ to SQLch tříd (soubor **. dbml** ) v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Poklikejte na soubor **. dbml** v **Průzkumník řešení**.)

2. Klikněte pravým tlačítkem myši na prázdnou oblast v Návrháři O/R a pak klikněte na **Zobrazit kód**.

    Editor kódu se otevře s částečnou třídou pro `DataContext` .

3. Umístěte kurzor do částečné třídy pro `DataContext` .

4. Pro Visual Basic projekty:

   1. Rozbalte seznam **název metody** .

   2. Klikněte na **aktualizovat**_ENTITYCLASSNAME_.

   3. `Update`Do částečné třídy je přidána metoda *ENTITYCLASSNAME* .

   4. Přístup k jednotlivým hodnotám sloupců pomocí `instance` argumentu, jak je znázorněno v následujícím kódu:

      ```vb
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
          Dim ErrorMessage As String = "Invalid data!"
          Throw New Exception(ErrorMessage)
      End If
      ```

      Pro projekty v jazyce C#:

   5. Vzhledem k tomu, že projekty C# negenerují automaticky obslužné rutiny událostí, můžete pomocí technologie IntelliSense vytvořit částečnou `Update` metodu *CLASSNAME* .

   6. Zadejte `partial` a potom místo pro přístup k seznamu dostupných částečných metod. Klikněte na metodu aktualizace pro třídu, pro kterou chcete přidat ověřování. Následující kód se podobá kódu, který je generován při výběru `Update` částečné metody *CLASSNAME* :

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
 [LINQ to SQL nástroje v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [ověřování dat](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
