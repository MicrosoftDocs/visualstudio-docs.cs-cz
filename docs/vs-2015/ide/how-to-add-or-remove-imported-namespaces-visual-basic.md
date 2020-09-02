---
title: 'Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75299dae66a07b2bc1671dbfcda935fc4af2b284
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645502"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Import oboru názvů umožňuje použít prvky z tohoto oboru názvů ve vašem kódu bez úplného zařazení prvku. Například pokud chcete získat přístup k `Create` metodě ve `System.Messaging.MessageQueue` třídě, můžete importovat `System.Messaging` obor názvů a pouze odkazovat na prvek, který potřebujete v kódu jako `MessageQueue.Create` .

 Importované obory názvů jsou spravovány na stránce **odkazy** v **Návrháři projektu**. Importy, které zadáte v tomto dialogovém okně, jsou předány přímo kompilátoru ( `/imports` ) a platí pro všechny soubory v projektu. Použijte `Imports` příkaz pro použití oboru názvů v jednom souboru zdrojového kódu.

### <a name="to-add-an-imported-namespace"></a>Přidání importovaného oboru názvů

1. V **Průzkumník řešení**dvakrát klikněte na uzel **můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **odkazy** .

3. V seznamu **importované obory názvů** zaškrtněte políčko pro obor názvů, který chcete přidat.

    > [!NOTE]
    > Aby bylo možné importovat, musí být obor názvů v odkazované součásti. Pokud se obor názvů v seznamu nezobrazí, budete muset přidat odkaz na komponentu, která ho obsahuje. Další informace naleznete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

### <a name="to-remove-an-imported-namespace"></a>Odebrání importovaného oboru názvů

1. V **Průzkumník řešení**dvakrát klikněte na uzel **můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **odkazy** .

3. V seznamu **importované obory názvů** zrušte zaškrtnutí políčka pro obor názvů, který chcete odebrat.

## <a name="user-imports"></a>Importy uživatelů
 Importy uživatelů umožňují importovat konkrétní třídu v rámci oboru názvů, nikoli celý obor názvů. Například vaše aplikace může mít import pro `Systems.Diagnostics` obor názvů, ale jediná třída v rámci tohoto oboru názvů, které vás zajímá, je `Debug` Třída. Můžete definovat `System.Diagnostics.Debug` jako import uživatele a pak odebrat import pro `System.Diagnostics` .

 Pokud se později rozhodnete, že jste si sami mysleli, že skutečně jste `EventLog` potřebovali, můžete zadat `System.Diagnostics.EventLog` jako import a přepsat uživatele `System.Diagnostics.Debug` pomocí funkce aktualizace.

#### <a name="to-add-a-user-import"></a>Přidání importu uživatele

1. V **Průzkumník řešení**dvakrát klikněte na uzel **můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **odkazy** .

3. Do textového pole pod seznamem **importované obory názvů** zadejte úplný název oboru názvů, který chcete importovat, včetně kořenového oboru názvů.

4. Kliknutím na tlačítko **Přidat import uživatele** přidejte obor názvů do seznamu **importovaných oborů názvů** .

    > [!NOTE]
    > Tlačítko **Přidat uživatelský import** bude zakázáno, pokud obor názvů odpovídá jednomu, který je již v seznamu. Import nemůžete přidat dvakrát.

#### <a name="to-update-a-user-import"></a>Aktualizace importu uživatelů

1. V **Průzkumník řešení**dvakrát klikněte na uzel **můj projekt** pro projekt.

2. V **Návrháři projektu**klikněte na kartu **odkazy** .

3. V seznamu **importované obory názvů** vyberte obor názvů, který chcete změnit.

4. Do textového pole pod seznamem **importované obory názvů** zadejte název nového oboru názvů.

5. Kliknutím na tlačítko **aktualizovat import uživatele** aktualizujete obor názvů v seznamu **importovaných oborů názvů** .

## <a name="see-also"></a>Viz také
 [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)
