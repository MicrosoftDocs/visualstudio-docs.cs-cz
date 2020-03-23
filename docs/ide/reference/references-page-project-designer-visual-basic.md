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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b80427999ad841c493e61cd704b64435f81c3914
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565601"
---
# <a name="references-page-project-designer-visual-basic"></a>Stránka Odkazy, návrhář projektu (Visual Basic)

Stránka **Reference** **návrháře projektu** slouží ke správě odkazů, webových odkazů a importovaných oborů názvů v projektu. Projekty mohou obsahovat odkazy na komponenty modelu COM, webové služby XML, knihovny nebo sestavení .NET nebo jiné knihovny tříd. Další informace o použití odkazů naleznete [v tématu Správa odkazů v projektu](../../ide/managing-references-in-a-project.md).

Chcete-li získat přístup ke stránce **References,** zvolte uzel projektu (nikoli uzel **řešení)** v **Průzkumníku řešení**. Pak na řádku nabídek zvolte **Projekt**, **Vlastnosti.** Po zobrazení Návrháře projektů klikněte na kartu **Reference.**

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

Následující možnosti umožňují vybrat nebo odebrat odkazy a importované obory názvů v projektu.

**Referenční cesty**

Klepnutím na toto tlačítko získáte přístup k dialogovému oknu **Referenční cesty.**

> [!NOTE]
> Když systém projektu najde odkaz na sestavení, systém tento odkaz vyřeší vyhledáním v následujících umístěních v následujícím pořadí:
>
> 1. Složka projektu. Soubory složek projektu se zobrazí v **Průzkumníku řešení,** když není aktivní **zobrazit všechny soubory.**
> 2. Složky zadané v dialogovém okně **Referenční cesty.**
> 3. Složky, které zobrazují soubory v dialogovém okně **Přidat odkaz.**
> 4. Složka obj projektu. (Přidáte-li odkaz COM do projektu, může být do složky obj projektu přidáno jedno nebo více sestavení.)

 **Odkazy**

Tento seznam zobrazuje všechny odkazy v projektu, použité nebo nepoužité.

 **Přidat**

Klepnutím na toto tlačítko přidáte odkaz nebo webový odkaz do seznamu **Reference.**

Zvolte **Odkaz,** chcete-li přidat odkaz na projekt pomocí dialogového okna Přidat odkaz.

Zvolte **Webový odkaz,** chcete-li přidat webový odkaz do projektu pomocí dialogového okna **Přidat odkaz na web.**

 **Odebrat**

Vyberte jeden nebo více odkazů v seznamu **Reference** a klepnutím na toto tlačítko je odstraňte.

 **Aktualizovat webový odkaz**

Vyberte webový odkaz v seznamu **Reference** a klepnutím na toto tlačítko jej aktualizujte.

 **Importované obory názvů**

Do tohoto pole můžete zadat vlastní obor názvů a kliknutím na **Přidat import uživatele** jej přidáte do seznamu oborů názvů.

Můžete vytvořit aliasy pro obory názvů importované uživateli. Chcete-li to provést, zadejte alias a obor názvů v*oboru názvů* *aliasu*=formátu . To je užitečné, pokud používáte dlouhé `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`obory názvů, například: .

 **Přidat import uživatele**

Klepnutím na toto tlačítko přidáte obor názvů zadaný v poli **Importované obory názvů** do seznamu importovaných oborů názvů. Tlačítko je aktivní pouze v případě, že zadaný obor názvů ještě není v seznamu.

 **Seznam oborů názvů**

V tomto seznamu jsou uvedeny všechny dostupné obory názvů. Jsou vybrána zaškrtávací políčka oborů názvů zahrnutých v projektu.

 **Aktualizovat import uživatele**

V seznamu oborů názvů vyberte obor názvů zadaný uživatelem, zadejte název, který chcete nahradit, do pole **Importované obory názvů** a klepnutím na toto tlačítko změňte nový obor názvů. Tlačítko je aktivní pouze v případě, že vybraný obor názvů je ten, který jste přidali do seznamu pomocí tlačítka **Přidat import uživatele.** Můžete přidat:

- Třídy nebo obory <xref:System.Math?displayProperty=fullName>názvů, například .

- Aliased importy, `VB=Microsoft.VisualBasic`například .

- Obory názvů XML, například `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md)
- [Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports – Příkaz (obor názvů XML)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
