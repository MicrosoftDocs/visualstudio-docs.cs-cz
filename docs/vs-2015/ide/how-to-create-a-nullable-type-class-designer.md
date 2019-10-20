---
title: 'Postupy: vytvoření typu s možnou hodnotou null (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 438f84a172c7e0a2d0dc957c578adc568a46495f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668148"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>Postupy: Vytváření typů s povolenou hodnotou Null (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Některé typy hodnot nemají vždy (nebo potřebují) definovanou hodnotu. To je běžný postup v databázích, kde některá pole nemusí mít přiřazenou žádnou hodnotu. Například můžete přiřadit hodnotu null poli databáze a označit tak, že ještě nebyla přiřazena hodnota.

 *Typ s povolenou hodnotou null* je typ hodnoty, který rozšíříte tak, aby přebírá typický rozsah hodnot pro daný typ a také hodnotu null. Například `Int32` s možnou hodnotou null, která se také označuje jako Nullable \<Int32 >, se dá přiřadit jakákoli hodnota od-2147483648 do 2147483647 nebo se jí dá přiřadit hodnota null. Hodnotám \<bool s možnou hodnotou null > lze přiřadit hodnoty `True`, `False` nebo null (žádná hodnota vůbec).

 Typy s možnou hodnotou null jsou instancemi <xref:System.Nullable%601> struktury. Každá instance typu s možnou hodnotou null má dvě veřejné vlastnosti jen pro čtení `HasValue` a `Value`:

- `HasValue` je typu `bool` a označuje, zda proměnná obsahuje definovanou hodnotu. `True` znamená, že proměnná obsahuje hodnotu, která není null. Můžete testovat definovanou hodnotu pomocí příkazu, jako je `if (x.HasValue)` nebo `if (y != null)`.

- `Value` je stejného typu jako nadřízený typ. Pokud je `HasValue` `True`, `Value` obsahuje smysluplnou hodnotu. Pokud je `HasValue` `False`, bude při přístupu k `Value` vyvolána výjimka neplatné operace.

  Ve výchozím nastavení, pokud deklarujete proměnnou jako typ s možnou hodnotou null, nemá žádnou definovanou hodnotu (`HasValue` je `False`), kromě výchozí hodnoty svého základního typu hodnoty.

  Návrhář tříd zobrazí typ s možnou hodnotou null, stejně jako zobrazuje jeho nadřízený typ.

  Další informace o typech s možnou hodnotou C#null v vizuálu naleznete v tématu [typy s možnou hodnotou null](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6). Další informace o typech s možnou hodnotou null v Visual Basic naleznete v tématu [typy hodnot s možnou hodnotou null](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>Přidání typu s možnou hodnotou null pomocí Návrhář tříd

1. V diagramu tříd rozbalte existující třídu nebo vytvořte novou třídu.

2. Chcete-li přidat třídu do projektu, v nabídce **Diagram tříd** klikněte na možnost **Přidat**a poté klikněte na možnost **Přidat třídu**.

3. Chcete-li rozbalit obrazec třídy, v nabídce **Diagram tříd** klikněte na tlačítko **Rozbalit**.

4. Vyberte obrazec třídy. V nabídce **Diagram tříd** klikněte na tlačítko **Přidat**a potom klikněte na tlačítko **pole**. Nové pole, které má výchozí **pole** název, se zobrazí v obrazci třídy a také v okně **podrobností třídy** .

5. Ve sloupci **název** okna **podrobností třídy** (nebo v samotném tvaru třídy) změňte název nového pole na platný a smysluplný název.

6. Ve sloupci **typ** okna **podrobností třídy** deklarujte typ jako typ s možnou hodnotou null, jak je znázorněno v následujícím kódu:

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

### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>Přidání typu s možnou hodnotou null pomocí editoru kódu

1. Přidejte do projektu třídu. Vyberte uzel projektu v **Průzkumník řešení**a v nabídce **projekt** klikněte na **Přidat třídu**.

2. V souboru. cs nebo. vb pro novou třídu přidejte do nové třídy jeden nebo více typů s možnou hodnotou null do deklarace třídy.

3. Z Zobrazení tříd přetáhněte ikonu Nová třída na návrhovou plochu Návrhář tříd. V diagramu tříd se zobrazí obrazec třídy.

4. Rozbalíte podrobnosti pro tvar třídy a přesunete ukazatel myši nad členy třídy. Popisek zobrazí deklaraci každého člena.

5. Klikněte pravým tlačítkem myši na obrazec třídy a klikněte na **Podrobnosti třídy**. Můžete zobrazit nebo upravit vlastnosti nového typu v okně **podrobností třídy** .

## <a name="see-also"></a>Viz také
 <xref:System.Nullable%601> [typy](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6) s možnou hodnotou null [s použitím typů s možnou hodnotou](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28) null [: identifikace](https://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387) [typů hodnot](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6) s možnou hodnotou null
