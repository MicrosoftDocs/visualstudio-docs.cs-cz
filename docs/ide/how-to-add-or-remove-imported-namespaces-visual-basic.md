---
title: 'Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)'
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df39b7867cd4c7baa2206b2c63634810b2f29dde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944645"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)

Import oboru názvů umožňuje používat elementy z daného oboru názvů v kódu bez plně kvalifikovaného elementu. Například, pokud chcete získat přístup `Create` metoda v `System.Messaging.MessageQueue` třídu, můžete importovat `System.Messaging` obor názvů a právě odkazovat na prvek, je nutné v kódu jako `MessageQueue.Create`.

 Importované obory názvů jsou spravovány v **odkazy** stránky **Návrhář projektu**. Importy, které zadáte v tomto dialogovém jsou předávány přímo kompilátoru (*/importuje*) a použít pro všechny soubory v projektu. Použít `Imports` příkaz k použití oboru názvů v jediném souboru kódu.

### <a name="to-add-an-imported-namespace"></a>Chcete-li přidat importovaný obor názvů

1.  V **Průzkumníku řešení**, dvakrát klikněte **Můj projekt** uzel pro projekt.

2.  V **Návrhář projektu**, klikněte **odkazy** karta.

3.  V **importované obory názvů** seznamu, zaškrtněte políčko pro obor názvů, který chcete přidat.

    > [!NOTE]
    >  Aby bylo možné importovat, musí být obor názvů v odkazované součásti. Pokud obor názvů v seznamu nezobrazí, musíte přidat odkaz na komponentu, který jej obsahuje. Další informace najdete v tématu [Správa odkazů v projektu](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>Chcete-li odebrat importovaný obor názvů

1.  V **Průzkumníku řešení**, dvakrát klikněte **Můj projekt** uzel pro projekt.

2.  V **Návrhář projektu**, klikněte **odkazy** karta.

3.  V **importované obory názvů** seznamu, zrušte zaškrtnutí políčka pro obor názvů, který chcete odebrat.

## <a name="user-imports"></a>Importy uživatele
 Importy uživatele umožňují importovat konkrétní třídu v rámci oboru názvů, nikoli celý obor názvů. Například aplikace může mít například import pro <xref:System.Diagnostics> obor názvů, ale pouze – třída v daném oboru názvů, které vás zajímají je `Debug` třídy. Můžete definovat <xref:System.Diagnostics.Debug> jako uživatel importovat a pak odeberte importu pro <xref:System.Diagnostics>.

 Pokud později změníte názor a rozhodnout, který je skutečně v `EventLog` třídu, která je potřeba, můžete zadat <xref:System.Diagnostics.EventLog> jako uživatel importovat a přepsat <xref:System.Diagnostics.Debug> pomocí funkce aktualizace.

### <a name="to-add-a-user-import"></a>Chcete-li přidat import uživatelů

1.  V **Průzkumníku řešení**, dvakrát klikněte **Můj projekt** uzel pro projekt.

2.  V **Návrhář projektu**, klikněte **odkazy** karta.

3.  Do textového pole níže **importované obory názvů** seznamu, zadejte úplný název pro obor názvů, které chcete importovat, včetně kořenového oboru názvů.

4.  Klikněte na tlačítko **přidat import uživatelů** tlačítko přidáte oboru názvů **importované obory názvů** seznamu.

    > [!NOTE]
    > **Přidat import uživatelů** tlačítko bude zakázáno, pokud obor názvů odpovídá jednomu již v seznamu; nelze přidat importu dvakrát.

### <a name="to-update-a-user-import"></a>Chcete-li aktualizovat import uživatelů

1.  V **Průzkumníku řešení**, dvakrát klikněte **Můj projekt** uzel pro projekt.

2.  V **Návrhář projektu**, klikněte **odkazy** karta.

3.  V **importované obory názvů** seznamu, vyberte obor názvů, které chcete změnit.

4.  Do textového pole níže **importované obory názvů** seznamu, zadejte název pro nový obor názvů.

5.  Klikněte na tlačítko **aktualizovat import uživatelů** tlačítko Aktualizovat v oboru názvů **importované obory názvů** seznamu.

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../ide/managing-references-in-a-project.md)