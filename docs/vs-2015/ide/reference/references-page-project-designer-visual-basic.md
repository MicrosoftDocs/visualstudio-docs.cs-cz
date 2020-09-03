---
title: Stránka odkazy, Návrhář projektu (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8bb18ec8dd12431d650d844e3698c1986c8d8bd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665632"
---
# <a name="references-page-project-designer-visual-basic"></a>Stránka Odkazy, návrhář projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Použijte stránku **odkazy** **Návrháře projektu** ke správě odkazů, webových odkazů a importovaných oborů názvů v projektu. Projekty mohou obsahovat odkazy na komponenty modelu COM, webové služby XML, .NET Framework knihovny tříd, sestavení nebo jiné knihovny tříd. Další informace o použití odkazů naleznete v tématu [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md).

 Pro přístup na stránku **odkazy** vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **projekt**, **vlastnosti** na řádku nabídek. Když se zobrazí Návrhář projektu, klikněte na kartu **odkazy** .

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 Následující možnosti umožňují vybrat nebo odebrat odkazy a importované obory názvů v projektu.

 **Nepoužité odkazy** Kliknutím na toto tlačítko otevřete dialogové okno **nepoužité odkazy** .

 Dialogové okno **nepoužité odkazy** umožňuje odebrat odkazy, které jsou zahrnuty v projektu, ale nejsou ve skutečnosti používány kódem. Obsahuje mřížku, která obsahuje **název odkazu**, **cestu**a další informace o nepoužívaných odkazech na obor názvů v projektu. V mřížce vyberte odkazy na obor názvů, které chcete odebrat z projektu, a klikněte na tlačítko **Odebrat**.

 **Cesty odkazů** Kliknutím na toto tlačítko otevřete dialogové okno **cesty odkazů** .

> [!NOTE]
> Když systém projektu najde odkaz na sestavení, systém tento odkaz vyřeší tak, že v následujícím pořadí prohlíží následující umístění:
>
> 1. Složka projektu. Soubory složek projektu se zobrazí v **Průzkumník řešení** , když **Zobrazit všechny soubory** nejsou platné.
>    2. Složky, které jsou uvedeny v dialogovém okně **cesty odkazů** .
>    3. Složky, které zobrazují soubory v dialogovém okně **Přidat odkaz** .
>    4. Složka obj projektu. (Pokud do projektu přidáte odkaz modelu COM, jedno nebo více sestavení může být přidáno do složky obj projektu.)

 **Odkazy** Tento seznam obsahuje všechny odkazy v projektu, použité nebo nepoužívané.

 **Přidat** Kliknutím na toto tlačítko přidáte odkaz nebo webový odkaz do seznamu **odkazů** .

 Vyberte **odkaz** pro přidání odkazu na projekt pomocí dialogového okna Přidat odkaz.

 Vyberte **webový odkaz** a přidejte webový odkaz do projektu pomocí dialogového okna Přidat webový odkaz.

 **Odebrat** V seznamu **odkazy** vyberte jeden nebo více odkazů a kliknutím na toto tlačítko jej odstraňte.

 **Aktualizovat webový odkaz** Vyberte webový odkaz v seznamu **odkazy** a kliknutím na toto tlačítko ho aktualizujte.

 **Importované obory názvů** V tomto poli můžete zadat vlastní obor názvů a kliknutím na **Přidat import uživatele** ho přidat do seznamu oborů názvů.

 Můžete vytvořit aliasy pro uživatelem importované obory názvů. Provedete to tak, že zadáte alias a obor názvů *alias*do = *oboru názvů*aliasu formátu. To je užitečné, pokud používáte dlouhé obory názvů, například: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http` .

 **Přidat import uživatele** Kliknutím na toto tlačítko přidáte obor názvů zadaný v poli **importované obory názvů** do seznamu importovaných oborů názvů. Tlačítko je aktivní pouze v případě, že zadaný obor názvů již není v seznamu.

 **Seznam oborů názvů** V tomto seznamu jsou uvedeny všechny dostupné obory názvů. Jsou vybrána zaškrtávací políčka pro obory názvů zahrnuté ve vašem projektu.

 **Aktualizovat import uživatele** V seznamu obory názvů vyberte obor názvů zadaný uživatelem, zadejte název, který chcete nahradit, v poli **importované obory názvů** a potom kliknutím na toto tlačítko přejděte na nový obor názvů. Tlačítko je aktivní pouze v případě, že vybraný obor názvů je ten, který jste přidali do seznamu pomocí tlačítka **Přidat import uživatele** . Můžete přidat:

- Třídy nebo obory názvů, například <xref:System.Math?displayProperty=fullName> .

- Import s aliasy, například `VB=Microsoft.VisualBasic` .

- Obory názvů XML, například `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">` .

## <a name="see-also"></a>Viz také
 [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md) [NIB: Přidat webový odkaz –](https://msdn.microsoft.com/bdf05776-c591-40af-bfd7-e1e2aa1e87b5) [příkaz Imports (obor názvů XML)](https://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)
