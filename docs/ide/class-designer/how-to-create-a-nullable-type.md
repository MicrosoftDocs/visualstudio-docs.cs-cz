---
title: 'Postupy: Vytváření typů s povolenou hodnotou Null (návrhář tříd)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5ef167e83bc8f27a53405ef6ab7a3f9271863b4d
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38785834"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Postupy: vytvoření typu s možnou hodnotou Null v Návrháři tříd

Některé typy hodnot ne vždy mají (nebo potřebujete) definovanou hodnotu. To je běžný postup v databázích, ve kterém některá pole nemůže být přiřazen žádnou hodnotu. Můžete například přiřadit hodnotu null do pole databáze místo, že ho nebyl dosud byla přiřazena hodnota.

A *typ připouštějící hodnotu Null* je hodnotový typ, který jste rozšířit tak, aby trvá Typická rozsah hodnot pro daný typ a také hodnotu null. Například s povolenou hodnotou NULL z `Int32`, také označeny jako s možnou hodnotou Null\<Int32 >, je možné přiřadit libovolnou hodnotu od -2147483648 do 2147483647 nebo je možné přiřadit hodnotu null. Nullable\<bool > je možné přiřadit hodnoty `True`, `False`, nebo hodnota null (žádná hodnota vůbec).

Typy s možnou hodnotou Null jsou instance <xref:System.Nullable%601> struktury. Každá instance typu s možnou hodnotou Null má dvě veřejné vlastnosti jen pro čtení `HasValue` a `Value`:

-   `HasValue` je typu `bool` a určuje, zda je proměnná obsahuje definovanou hodnotu. `True` znamená to, že proměnná obsahuje hodnotu než null. Můžete otestovat pomocí příkazu pro definovanou hodnotou `if (x.HasValue)` nebo `if (y != null)`.

-   `Value` je stejného typu jako základní typ. Pokud `HasValue` je `True`, `Value` obsahuje smysluplnou hodnotu. Pokud `HasValue` je `False`, přístup k `Value` vyvolá výjimku neplatná operace.

Ve výchozím nastavení, pokud deklarujete proměnnou jako typ s možnou hodnotou Null nemá žádné definované hodnoty (`HasValue` je `False`), jiné než výchozí hodnotu jeho základní typ hodnoty.

Návrhář tříd zobrazí typ připouštějící hodnotu Null, stejně jako zobrazí jeho nadřízeného typu.

Další informace o typech s povolenou hodnotou Null v jazyce C# najdete v tématu [typy připouštějící hodnotu Null](/dotnet/csharp/programming-guide/nullable-types/index). Další informace o typech s povolenou hodnotou Null v jazyce Visual Basic najdete v tématu [hodnotové typy s možnou hodnotou Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Chcete-li přidat typ připouštějící hodnotu Null pomocí návrháře tříd

1.  V diagramu tříd rozšiřte existující třídy nebo vytvořte novou třídu.

2.  Přidání třídy do projektu, na **Diagram tříd** nabídky, klikněte na tlačítko **přidat** > **přidat třídu**.

3.  Rozbalte obrazec třídy na **Diagram tříd** nabídky, klikněte na tlačítko **Rozbalit**.

4.  Vyberte obrazec třídy. Na **Diagram tříd** nabídky, klikněte na tlačítko **přidat** > **pole**. Nové pole, která má výchozí název **pole** se zobrazí na obrazec třídy a také **podrobností třídy** okna.

5.  V **název** sloupec **podrobností třídy** okna (nebo ve třídě obrazce samotné), změňte název nového pole na platný a smysluplný název.

6.  V **typ** sloupec **podrobností třídy** okna, deklarujte typ jako typ s možnou hodnotou Null tak, že zadáte následující:

    - `int?` (Visual C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Chcete-li přidat typ připouštějící hodnotu Null pomocí editoru kódu

1.  Přidání třídy do projektu. Vyberte uzel projektu v **Průzkumníku řešení**a dále **projektu** nabídky, klikněte na tlačítko **přidat třídu**.

2.  V souboru .cs nebo .vb pro novou třídu přidejte jeden nebo více typů s povolenou hodnotou Null v této nové třídě do deklarace třídy.

    ```csharp
    // Declare a nullable type in Visual C#:
    class Test
    {
       int? building_number = 5;
    }
    ```

    ```vb
    ' Declare a nullable type in Visual Basic:
    Class Test
       Dim buildingNumber As Nullable(Of Integer) = 5
    End Class
    ```

3.  Ze zobrazení tříd přetáhněte přes novou ikonu třídy na návrhové ploše návrháře tříd. Tvar třídy se zobrazí v diagramu tříd.

4.  Rozbalit podrobnosti pro třídu tvar a přesuňte ukazatel myši nad členy třídy. Popisek zobrazí deklarace každého člena.

5.  Pravým tlačítkem myši na obrazec třídy a klikněte na tlačítko **podrobností třídy**. Můžete zobrazit nebo upravit vlastnosti nového typu **podrobností třídy** okna.

## <a name="see-also"></a>Viz také:

- <xref:System.Nullable%601>
- [Typy s povolenou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/index)
- [Použití typů s povolenou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Postupy: Identifikace typu s povolenou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Typy hodnot s povolenou hodnotou Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
