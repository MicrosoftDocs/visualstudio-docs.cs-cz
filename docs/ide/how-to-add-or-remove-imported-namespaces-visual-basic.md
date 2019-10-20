---
title: 'Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)'
ms.date: 06/21/2017
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ff6ad1a07440b27b679fa3f749c24a6d3157dbd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654658"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)

Import oboru názvů umožňuje použít prvky z tohoto oboru názvů ve vašem kódu bez úplného zařazení prvku. Například pokud chcete získat přístup k metodě `Create` ve třídě `System.Messaging.MessageQueue`, můžete importovat `System.Messaging` obor názvů a pouze odkazovat na prvek, který potřebujete v kódu jako `MessageQueue.Create`.

Importované obory názvů jsou spravovány na stránce **odkazy** v **Návrháři projektu**. Importy, které zadáte v tomto dialogovém okně, jsou předány přímo kompilátoru ( */Imports*) a platí pro všechny soubory v projektu. Použijte příkaz `Imports` pro použití oboru názvů v jednom souboru zdrojového kódu.

### <a name="to-add-an-imported-namespace"></a>Přidání importovaného oboru názvů

1. V **Průzkumník řešení**dvakrát klikněte na uzel **můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **odkazy** .

3. V seznamu **importované obory názvů** zaškrtněte políčko pro obor názvů, který chcete přidat.

    > [!NOTE]
    > Aby bylo možné importovat, musí být obor názvů v odkazované součásti. Pokud se obor názvů v seznamu nezobrazí, budete muset přidat odkaz na komponentu, která ho obsahuje. Další informace naleznete v tématu [Správa odkazů v projektu](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>Odebrání importovaného oboru názvů

1. V **Průzkumník řešení**dvakrát klikněte na uzel **můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **odkazy** .

3. V seznamu **importované obory názvů** zrušte zaškrtnutí políčka pro obor názvů, který chcete odebrat.

## <a name="user-imports"></a>Importy uživatelů
Importy uživatelů umožňují importovat konkrétní třídu v rámci oboru názvů, nikoli celý obor názvů. Například vaše aplikace může mít import pro obor názvů <xref:System.Diagnostics>, ale jediná třída v rámci tohoto oboru názvů, o kterou vás zajímá, je `Debug` třída. Můžete definovat <xref:System.Diagnostics.Debug> jako import uživatele a pak odebrat import pro <xref:System.Diagnostics>.

Pokud se později rozhodnete, že jste si sami rozmysleli, že se skutečně `EventLog` třída, kterou jste potřebovali, mohli byste do <xref:System.Diagnostics.EventLog> zadat import a přepsat <xref:System.Diagnostics.Debug> pomocí funkce aktualizace.

### <a name="to-add-a-user-import"></a>Přidání importu uživatele

1. V **Průzkumník řešení**dvakrát klikněte na uzel **můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **odkazy** .

3. Do textového pole pod seznamem **importované obory názvů** zadejte úplný název oboru názvů, který chcete importovat, včetně kořenového oboru názvů.

4. Kliknutím na tlačítko **Přidat import uživatele** přidejte obor názvů do seznamu **importovaných oborů názvů** .

    > [!NOTE]
    > Tlačítko **Přidat uživatelský import** bude zakázáno, pokud obor názvů odpovídá jednomu, který je již v seznamu. Import nemůžete přidat dvakrát.

### <a name="to-update-a-user-import"></a>Aktualizace importu uživatelů

1. V **Průzkumník řešení**dvakrát klikněte na uzel **můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **odkazy** .

3. V seznamu **importované obory názvů** vyberte obor názvů, který chcete změnit.

4. Do textového pole pod seznamem **importované obory názvů** zadejte název nového oboru názvů.

5. Kliknutím na tlačítko **aktualizovat import uživatele** aktualizujete obor názvů v seznamu **importovaných oborů názvů** .

## <a name="see-also"></a>Viz také:

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)