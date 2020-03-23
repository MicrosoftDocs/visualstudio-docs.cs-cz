---
title: 'Postupy: Vytváření typů s povolenou hodnotou Null (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5be8b553dfead4b8c05f29bbd18c16fcef847130
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592227"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Postup: Vytvoření typu s možnou hodnotou null v Návrháři tříd

Některé typy hodnot nemají vždy (nebo potřebují) definovanou hodnotu. To je běžná praxe v databázích, kde některá pole nemusí být přiřazena žádná hodnota. Můžete například přiřadit hodnotu null k databázovému poli, což znamená, že mu ještě nebyla přiřazena hodnota.

*Typ s možnou hodnotou null* je typ hodnoty, který rozšiřujete tak, aby přebírá typický rozsah hodnot pro tento typ a také hodnotu null. Například nullable of `Int32`, také označené\<jako Nullable Int32>, lze přiřadit libovolnou hodnotu od -2147483648 do 2147483647 nebo může být přiřazena hodnota null. Nullable\<bool> lze přiřadit `True` `False`hodnoty , nebo null (žádná hodnota vůbec).

Null lze typy jsou <xref:System.Nullable%601> instance struktury. Každá instance typu s možnou hodnotou null `HasValue` `Value`má dvě veřejné vlastnosti jen pro čtení a :

- `HasValue`je typu `bool` a označuje, zda proměnná obsahuje definovanou hodnotu. `True`znamená, že proměnná obsahuje hodnotu bez hodnoty null. Definovanou hodnotu můžete otestovat pomocí `if (x.HasValue)` příkazu, například nebo `if (y != null)`.

- `Value`je stejného typu jako základní typ. Pokud `HasValue` `True`je `Value` , obsahuje smysluplnou hodnotu. Pokud `HasValue` `False`je , `Value` přístup vyvolá neplatnou výjimku operace.

Ve výchozím nastavení, když deklarujete proměnnou jako`HasValue` `False`typ s možnou hodnotou null, nemá žádnou definovanou hodnotu ( je ), kromě výchozí hodnoty jejího základního typu hodnoty.

Návrhář třídzobrazí typ s možnou hodnotou null stejně jako jeho základní typ.

Další informace o typech s možnou hodnotou null v systému C#naleznete v [tématu Nullable Types](/dotnet/csharp/programming-guide/nullable-types/index). Další informace o typech s možnou hodnotou null v jazyce Visual Basic naleznete v [tématu Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Přidání typu s možnou hodnotou null pomocí Návrháře tříd

1. V diagramu třídy rozbalte existující třídu nebo vytvořte novou třídu.

2. Chcete-li přidat třídu do projektu, klikněte v nabídce **Diagram tříd** na **tlačítko Přidat** > **třídu**.

3. Chcete-li rozšířit obrazec třídy, klepněte v nabídce **Diagram třídna** na **rozbalit**.

4. Vyberte obrazec třídy. V nabídce **Diagram tříd** klepněte na tlačítko **Přidat** > **pole**. Nové pole s výchozím názvem **Pole** se zobrazí v obrazci třídy a také v okně **Podrobnosti třídy.**

5. Ve sloupci **Název** okna **Podrobnosti třídy** (nebo v samotném obrazci třídy) změňte název nového pole na platný a smysluplný název.

6. Ve sloupci **Typ** okna **Podrobnosti třídy** deklarujte typ jako typ s hodnotou null zadáním následujícího:

    - `int?`(Vizuální C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Přidání typu s možnou hodnotou null pomocí Editoru kódu

1. Přidejte třídu do projektu. Vyberte uzel projektu v **Průzkumníku řešení**a v nabídce **Projekt** klepněte na **tlačítko Přidat třídu**.

2. V souboru .cs nebo .vb pro novou třídu přidejte jeden nebo více typů s možnou hodnotou null v nové třídě do deklarace třídy.

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

3. Ze zobrazení tříd přetáhněte novou ikonu třídy na návrhovou plochu Návrháře tříd. V diagramu třídy se zobrazí obrazec třídy.

4. Rozbalte podrobnosti pro obrazec třídy a přesuňte ukazatel myši nad členy třídy. Popisek zobrazuje deklaraci každého člena.

5. Klepněte pravým tlačítkem myši na obrazec třídy a klepněte na **položku Podrobnosti třídy**. Vlastnosti nového typu můžete zobrazit nebo upravit v okně **Podrobnosti třídy.**

## <a name="see-also"></a>Viz také

- <xref:System.Nullable%601>
- [Typy s možnou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/index)
- [Použití typů s povolenou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Postupy: Identifikace typu s povolenou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Typy hodnot s povolenou hodnotou Null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
