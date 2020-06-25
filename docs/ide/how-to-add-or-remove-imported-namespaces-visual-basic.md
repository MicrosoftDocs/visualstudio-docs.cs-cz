---
title: 'Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)'
ms.date: 06/21/2017
ms.topic: how-to
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a50fdb643029bed8a44ce6999d4a8ce062ba3dcf
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284736"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)

Import oboru názvů umožňuje použít prvky z tohoto oboru názvů ve vašem kódu bez úplného zařazení prvku. Například pokud chcete získat přístup k `Create` metodě ve `System.Messaging.MessageQueue` třídě, můžete importovat `System.Messaging` obor názvů a pouze odkazovat na prvek, který potřebujete v kódu jako `MessageQueue.Create` .

Importované obory názvů jsou spravovány na stránce **odkazy** v **Návrháři projektu**. Importy, které zadáte v tomto dialogovém okně, jsou předány přímo kompilátoru (*/Imports*) a platí pro všechny soubory v projektu. Použijte `Imports` příkaz pro použití oboru názvů v jednom souboru zdrojového kódu.

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
Importy uživatelů umožňují importovat konkrétní třídu v rámci oboru názvů, nikoli celý obor názvů. Například vaše aplikace může mít import pro <xref:System.Diagnostics> obor názvů, ale jediná třída v rámci tohoto oboru názvů, které vás zajímá, je `Debug` Třída. Můžete definovat <xref:System.Diagnostics.Debug> jako import uživatele a pak odebrat import pro <xref:System.Diagnostics> .

Pokud se později rozhodnete, že jste si sami mysleli, že skutečně jste `EventLog` potřebovali, můžete zadat <xref:System.Diagnostics.EventLog> jako import a přepsat uživatele <xref:System.Diagnostics.Debug> pomocí funkce aktualizace.

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

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
