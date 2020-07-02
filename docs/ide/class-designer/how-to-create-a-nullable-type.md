---
title: 'Postupy: Vytváření typů s povolenou hodnotou Null (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: ad371f987ab7ff0e50dc7d2fe4effeba5205e74e
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770982"
---
# <a name="how-to-create-a-nullable-type-in-class-designer"></a>Postupy: vytvoření typu s možnou hodnotou null v Návrhář tříd

Některé typy hodnot nemají vždy (nebo potřebují) definovanou hodnotu. To je běžný postup v databázích, kde některá pole nemusí mít přiřazenou žádnou hodnotu. Například můžete přiřadit hodnotu null poli databáze a označit tak, že ještě nebyla přiřazena hodnota.

*Typ s povolenou hodnotou null* je typ hodnoty, který rozšíříte tak, aby přebírá typický rozsah hodnot pro daný typ a také hodnotu null. Například hodnota null, která se `Int32` také označuje jako Nullable \<Int32> , může mít přiřazenou libovolnou hodnotu od-2147483648 do 2147483647 nebo může mít přiřazenou hodnotu null. Hodnotě null \<bool> lze přiřadit hodnoty `True` , `False` nebo hodnotu null (žádná hodnota vůbec).

Typy s možnou hodnotou null jsou instance <xref:System.Nullable%601> struktury. Každá instance typu s možnou hodnotou null má dvě veřejné vlastnosti jen pro čtení `HasValue` a `Value` :

- `HasValue`je typu `bool` a označuje, zda proměnná obsahuje definovanou hodnotu. `True`znamená, že proměnná obsahuje hodnotu, která není null. Můžete testovat definovanou hodnotu pomocí příkazu, například `if (x.HasValue)` nebo `if (y != null)` .

- `Value`je stejného typu jako nadřízený typ. Pokud `HasValue` je `True` , `Value` obsahuje smysluplnou hodnotu. V takovém případě `HasValue` `False` přístup `Value` vyvolá výjimku neplatné operace.

Ve výchozím nastavení, pokud deklarujete proměnnou jako typ s možnou hodnotou null, nemá žádnou definovanou hodnotu ( `HasValue` is `False` ), kromě výchozí hodnoty svého základního typu hodnoty.

Návrhář tříd zobrazí typ s možnou hodnotou null, stejně jako zobrazuje jeho nadřízený typ.

Další informace o typech s možnou hodnotou null v C# naleznete v tématu [typy s možnou hodnotou null](/dotnet/csharp/programming-guide/nullable-types/index). Další informace o typech s možnou hodnotou null v Visual Basic naleznete v tématu [typy hodnot s možnou hodnotou null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Přidání typu s možnou hodnotou null pomocí Návrhář tříd

1. V diagramu tříd rozbalte existující třídu nebo vytvořte novou třídu.

2. Chcete-li přidat třídu do projektu, v nabídce **Diagram tříd** klikněte na **Přidat**  >  **Přidat třídu**.

3. Chcete-li rozbalit obrazec třídy, v nabídce **Diagram tříd** klikněte na tlačítko **Rozbalit**.

4. Vyberte obrazec třídy. V nabídce **Diagram tříd** klikněte na možnost **Přidat**  >  **pole**. Nové pole, které má výchozí **pole** název, se zobrazí v obrazci třídy a také v okně **podrobností třídy** .

5. Ve sloupci **název** okna **podrobností třídy** (nebo v samotném tvaru třídy) změňte název nového pole na platný a smysluplný název.

6. Ve sloupci **typ** okna **podrobností třídy** deklarujte typ jako typ s možnou hodnotou null zadáním následujících možností:

    - `int?`(Visual C#)
    - `Nullable(Of Integer)` (Visual Basic)

## <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Přidání typu s možnou hodnotou null pomocí editoru kódu

1. Přidejte do projektu třídu. Vyberte uzel projektu v **Průzkumník řešení**a v nabídce **projekt** klikněte na **Přidat třídu**.

2. V souboru. cs nebo. vb pro novou třídu přidejte do nové třídy jeden nebo více typů s možnou hodnotou null do deklarace třídy.

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

3. Z Zobrazení tříd přetáhněte ikonu Nová třída na návrhovou plochu Návrhář tříd. V diagramu tříd se zobrazí obrazec třídy.

4. Rozbalíte podrobnosti pro tvar třídy a přesunete ukazatel myši nad členy třídy. Popisek zobrazí deklaraci každého člena.

5. Klikněte pravým tlačítkem myši na obrazec třídy a klikněte na **Podrobnosti třídy**. Můžete zobrazit nebo upravit vlastnosti nového typu v okně **podrobností třídy** .

## <a name="see-also"></a>Viz také:

- <xref:System.Nullable%601>
- [Typy s možnou hodnotou null](/dotnet/csharp/programming-guide/nullable-types/index)
- [Použití typů s povolenou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)
- [Postupy: Identifikace typu s povolenou hodnotou Null](/dotnet/csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type)
- [Typy hodnot s možnou hodnotou null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)
