---
title: Stránka Odkazy, návrhář projektu (Visual Basic)
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 719f58ff7a8fe333f43e13ddef298ba9938ad4e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815192"
---
# <a name="references-page-project-designer-visual-basic"></a>Stránka Odkazy, návrhář projektu (Visual Basic)

Použití **odkazy** stránku **Návrháře projektu** ke správě odkazy, webové odkazy a importovaných oborů názvů ve vašem projektu. Projekty mohou obsahovat odkazy na komponenty modelu COM, webové služby XML, knihovny tříd rozhraní .NET Framework nebo sestavení nebo další knihovny tříd. Další informace o použití odkazů naleznete v tématu [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md).

Pro přístup k **odkazy** zvolte uzel projektu (ne **řešení** uzlu) v **Průzkumníku řešení**. Klikněte na tlačítko **projektu**, **vlastnosti** na řádku nabídek. Jakmile se zobrazí Návrhář projektu, klikněte na tlačítko **odkazy** kartu.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

Tyto možnosti umožňují vybrat nebo odebrání odkazů a importovaných oborů názvů ve vašem projektu.

**Nepoužité odkazy**

Kliknutím na toto tlačítko přístup **nepoužité odkazy** dialogové okno.

**Nepoužité odkazy** dialogové okno umožňuje odebrat odkazy, které jsou zahrnuté ve vašem projektu, ale nejsou ve skutečnosti používá v kódu. Obsahuje tabulku, ve které jsou uvedeny **referenční název**, **cesta**a další informace o odkazech na obor názvů nepoužívané ve vašem projektu. V mřížce, vyberte odkazy na obor názvů, které chcete odebrat z projektu a klikněte na tlačítko **odebrat**.

**Cesty odkazů**

Kliknutím na toto tlačítko přístup **cesty odkazů** dialogové okno.

> [!NOTE]
> Při systém projektu nalezení odkaz na sestavení, systém vyřeší odkaz vyhledáváním v následujících umístěních, v uvedeném pořadí:
>
> 1. Složky projektu. Soubory složky projektu se zobrazí v **Průzkumníka řešení** při **zobrazit všechny soubory** není v platnosti.
> 2. Složky, které jsou určené v **cesty odkazů** dialogové okno.
> 3. Složky, které zobrazí soubory v **přidat odkaz** dialogové okno.
> 4. Složku obj projektu. (Když přidáte do svého projektu odkaz modelu COM, jeden nebo více sestavení mohou být přidány do projektu složku obj.)

 **Odkazy**

 Tento seznam obsahuje všechny odkazy v projektu použít nebo se nepoužívá.

 **Add**

 Kliknutím na Přidat odkaz nebo webový odkaz na toto tlačítko **odkazy** seznamu.

 Zvolte **odkaz** přidání odkazu do projektu pomocí dialogového okna Přidat odkaz.

 Zvolte **webový odkaz** přidat webový odkaz na projekt pomocí **přidat webový odkaz** dialogové okno.

 **odebrat**

 Vyberte jeden nebo více odkazů v **odkazy** seznamu a potom klikněte na toto tlačítko k jeho odstranění.

 **Aktualizovat webový odkaz**

 Vyberte webového odkazu **odkazy** seznamu a klikněte na toto tlačítko ji aktualizovat.

 **Importované obory názvů**

 Můžete zadat vlastní obor názvů do tohoto pole a klikněte na tlačítko **přidat Import uživatelů** ho přidat do seznamu oborů názvů.

 Můžete vytvořit aliasy pro uživatele importované obory názvů. Chcete-li to provést, zadejte ve formátu aliasu a obor názvů *alias*=*obor názvů*. To je užitečné, pokud používáte dlouhé obory názvů, třeba: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Přidat Import uživatelů**

 Kliknutím na toto tlačítko pro přidání oboru názvů určenému ve **importovat obory názvů** pole do seznamu importovaných oborů názvů. Toto tlačítko je aktivní, pouze pokud určený obor názvů ještě není v seznamu.

 **Seznam oborů názvů**

 Tento seznam obsahuje všechny dostupné obory názvů. Jsou zaškrtnuta políčka pro obory názvů zahrnuté ve vašem projektu.

 **Import uživatelů aktualizace**

 Vyberte obor názvů zadané uživatelem v seznamu oborů názvů, zadejte název, který chcete nahradit v **importovat obory názvů** pole a potom klikněte na toto tlačítko Změnit na novém oboru názvů. Je aktivní, pouze pokud vybraný obor názvů je ten, který jste přidali do seznamu pomocí tlačítka **přidat Import uživatelů** tlačítko. Můžete přidat:

-   Třídy nebo obory názvů, jako například <xref:System.Math?displayProperty=fullName>.

-   Alias importuje, jako například `VB=Microsoft.VisualBasic`.

-   Obory názvů XML, jako například `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Viz také

- [Správa odkazů v projektu](../../ide/managing-references-in-a-project.md)
- [Postupy: Přidání nebo odebrání importovaných oborů názvů (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Příkaz Imports (obor názvů XML)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
