---
title: Stránka Odkazy, návrhář projektu (Visual Basic)
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a92523f182300c17a3e6b08ad04ba2b6049be6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655641"
---
# <a name="references-page-project-designer-visual-basic"></a>Stránka Odkazy, návrhář projektu (Visual Basic)

Použijte stránku **odkazy** **Návrháře projektu** ke správě odkazů, webových odkazů a importovaných oborů názvů v projektu. Projekty mohou obsahovat odkazy na komponenty modelu COM, webové služby XML, knihovny .NET nebo sestavení nebo jiné knihovny tříd. Další informace o použití odkazů naleznete v tématu [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md).

Pro přístup na stránku **odkazy** vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **projekt**, **vlastnosti** na řádku nabídek. Když se zobrazí Návrhář projektu, klikněte na kartu **odkazy** .

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

Následující možnosti umožňují vybrat nebo odebrat odkazy a importované obory názvů v projektu.

**Cesty odkazů**

Kliknutím na toto tlačítko otevřete dialogové okno **cesty odkazů** .

> [!NOTE]
> Když systém projektu najde odkaz na sestavení, systém tento odkaz vyřeší tak, že v následujícím pořadí prohlíží následující umístění:
>
> 1. Složka projektu. Soubory složek projektu se zobrazí v **Průzkumník řešení** , když **Zobrazit všechny soubory** nejsou platné.
> 2. Složky, které jsou uvedeny v dialogovém okně **cesty odkazů** .
> 3. Složky, které zobrazují soubory v dialogovém okně **Přidat odkaz** .
> 4. Složka obj projektu. (Pokud do projektu přidáte odkaz modelu COM, jedno nebo více sestavení může být přidáno do složky obj projektu.)

 **Odkazy**

Tento seznam obsahuje všechny odkazy v projektu, použité nebo nepoužívané.

 **Add**

Kliknutím na toto tlačítko přidáte odkaz nebo webový odkaz do seznamu **odkazů** .

Vyberte **odkaz** pro přidání odkazu na projekt pomocí dialogového okna Přidat odkaz.

Vyberte **webový odkaz** a přidejte webový odkaz do projektu pomocí dialogového okna **Přidat webový odkaz** .

 **Odebrány**

V seznamu **odkazy** vyberte jeden nebo více odkazů a kliknutím na toto tlačítko jej odstraňte.

 **Aktualizovat webový odkaz**

Vyberte webový odkaz v seznamu **odkazy** a kliknutím na toto tlačítko ho aktualizujte.

 **Importované obory názvů**

V tomto poli můžete zadat vlastní obor názvů a kliknutím na **Přidat import uživatele** ho přidat do seznamu oborů názvů.

Můžete vytvořit aliasy pro uživatelem importované obory názvů. Provedete to tak, že zadáte alias a obor názvů ve formátu *alias* =*obor názvů*. To je užitečné, pokud používáte dlouhé obory názvů, například: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Přidat import uživatele**

Kliknutím na toto tlačítko přidáte obor názvů zadaný v poli **importované obory názvů** do seznamu importovaných oborů názvů. Tlačítko je aktivní pouze v případě, že zadaný obor názvů již není v seznamu.

 **Seznam oborů názvů**

V tomto seznamu jsou uvedeny všechny dostupné obory názvů. Jsou vybrána zaškrtávací políčka pro obory názvů zahrnuté ve vašem projektu.

 **Aktualizovat import uživatele**

V seznamu obory názvů vyberte obor názvů zadaný uživatelem, zadejte název, který chcete nahradit, v poli **importované obory názvů** a potom kliknutím na toto tlačítko přejděte na nový obor názvů. Tlačítko je aktivní pouze v případě, že vybraný obor názvů je ten, který jste přidali do seznamu pomocí tlačítka **Přidat import uživatele** . Můžete přidat:

- Třídy nebo obory názvů, například <xref:System.Math?displayProperty=fullName>.

- Import s aliasy, například `VB=Microsoft.VisualBasic`.

- Obory názvů XML, například `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md)
- [Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Příkaz Imports (obor názvů XML)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
