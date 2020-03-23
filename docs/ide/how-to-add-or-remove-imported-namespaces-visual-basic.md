---
title: 'Postup: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)'
ms.date: 06/21/2017
ms.topic: conceptual
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
ms.openlocfilehash: e636969164c4cf2526bb85add95e7cfe02ce6176
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593327"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Postup: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)

Import oboru názvů umožňuje použít prvky z tohoto oboru názvů v kódu bez úplného zařazení prvku. Například pokud chcete získat `Create` přístup k `System.Messaging.MessageQueue` metodě ve `System.Messaging` třídě, můžete importovat obor názvů a `MessageQueue.Create`stačí odkazovat na prvek, který potřebujete v kódu jako .

Importované obory názvů jsou **spravovány** na stránce Reference **návrháře projektu**. Importy zadané v tomto dialogovém okně jsou předány přímo kompilátoru (*/importy*) a platí pro všechny soubory v projektu. Pomocí `Imports` příkazu můžete použít obor názvů v jediném souboru zdrojového kódu.

### <a name="to-add-an-imported-namespace"></a>Přidání importovaného oboru názvů

1. V **Průzkumníku řešení**poklepejte na uzel **Můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **Reference.**

3. V seznamu **Importované obory názvů** zaškrtněte políčko u oboru názvů, který chcete přidat.

    > [!NOTE]
    > Aby bylo možné importovat, musí být obor názvů v odkazované součásti. Pokud se obor názvů v seznamu nezobrazí, bude nutné přidat odkaz na komponentu, která jej obsahuje. Další informace naleznete [v tématu Správa odkazů v projektu](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>Odebrání importovaného oboru názvů

1. V **Průzkumníku řešení**poklepejte na uzel **Můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **Reference.**

3. V seznamu **Importované obory názvů** zrušte zaškrtnutí políčka u oboru názvů, který chcete odebrat.

## <a name="user-imports"></a>Importy uživatelů
Importy uživatelů umožňují importovat určitou třídu v oboru názvů, nikoli v celém oboru názvů. Aplikace může mít například import <xref:System.Diagnostics> pro obor názvů, ale jedinou třídou v rámci `Debug` tohoto oboru názvů, která vás zajímá, je třída. Můžete definovat <xref:System.Diagnostics.Debug> import uživatele a potom import <xref:System.Diagnostics>pro .

Pokud později změníte názor a `EventLog` rozhodnete se, že to <xref:System.Diagnostics.EventLog> byla opravdu třída, <xref:System.Diagnostics.Debug> kterou jste potřebovali, můžete zadat jako import uživatele a přepsat pomocí funkce aktualizace.

### <a name="to-add-a-user-import"></a>Přidání importu uživatele

1. V **Průzkumníku řešení**poklepejte na uzel **Můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **Reference.**

3. Do textového pole pod seznamem **Importované obory názvů** zadejte úplný název oboru názvů, který chcete importovat, včetně kořenového oboru názvů.

4. Klepnutím na tlačítko **Přidat import uživatele** přidejte obor názvů do seznamu **Importované obory názvů.**

    > [!NOTE]
    > Tlačítko **Přidat import uživatele** bude zakázáno, pokud se obor názvů shoduje s prostorem názvů, který je již v seznamu; import nelze přidat dvakrát.

### <a name="to-update-a-user-import"></a>Aktualizace importu uživatele

1. V **Průzkumníku řešení**poklepejte na uzel **Můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **Reference.**

3. V seznamu **Importované obory názvů** vyberte obor názvů, který chcete změnit.

4. Do textového pole pod seznamem **Importované obory názvů** zadejte název nového oboru názvů.

5. Klepnutím na tlačítko **Aktualizovat import uživatele** aktualizujte obor názvů v seznamu **Importované obory názvů.**

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
