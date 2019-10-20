---
title: Aktualizovat existující šablony položek projektu
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee0118ce4181a12ca4c199b8174a28fb4b431063
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656532"
---
# <a name="how-to-update-existing-templates"></a>Postupy: Aktualizace existujících šablon

Po vytvoření šablony a komprimaci souborů do souboru s *příponou. zip* budete možná chtít šablonu upravit. To můžete provést ručně změnou souborů v šabloně nebo exportováním nové šablony z projektu, který je založen na šabloně.

## <a name="use-the-export-template-wizard"></a>Použití Průvodce exportem šablony

Visual Studio poskytuje **Průvodce exportem šablony** , který se dá použít k aktualizaci existující šablony:

1. Z řádku nabídek vyberte **soubor**  > **Nový**  > **projekt** .

1. Vyberte šablonu, kterou chcete aktualizovat, a pokračujte postupem vytvoření nového projektu.

1. Upravte projekt v aplikaci Visual Studio. Například změňte typ výstupu nebo přidejte nový soubor do projektu.

1. V nabídce **projekt** vyberte položku **Exportovat šablonu**.

    Otevře se **Průvodce exportem šablony** .

1. Postupujte podle pokynů v průvodci a exportujte šablonu jako soubor *. zip* .

1. Volitelné Uložte soubor *. zip* do následujícího adresáře: *%USERPROFILE%\Documents\Visual Studio \<version \> \templates\projecttemplates* , aby byl k dispozici pro výběr. Tento krok bude nutné provést, pokud jste nevybrali možnost **automaticky importovat šablonu do sady Visual Studio** v **Průvodci exportem šablony**.

1. Odstraňte starý soubor template *. zip* .

## <a name="manually-update-an-existing-template"></a>Ruční aktualizace existující šablony

Existující šablonu můžete aktualizovat bez použití **Průvodce exportem šablony**úpravou souborů v komprimovaném souboru *zip* .

### <a name="to-manually-update-an-existing-template"></a>Ruční aktualizace stávající šablony

1. Vyhledejte soubor *. zip* , který obsahuje šablonu. Šablony projektu uživatele jsou umístěny v *%UserProfile%\Documents\Visual studiu \<version \> \templates\projecttemplates*.

1. Extrahujte soubor *. zip* .

1. Upravte nebo odstraňte aktuální soubory šablon nebo přidejte nové soubory do šablony.

1. Otevřete, upravte a uložte soubor XML *. vstemplate* pro zpracování aktualizovaných chování nebo nových souborů.

    Další informace o schématu *. vstemplate* naleznete v tématu [Referenční dokumentace schématu šablon sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md). Další informace o tom, co můžete ve zdrojových souborech parametrizovat, najdete v tématu [parametry šablony](../ide/template-parameters.md).

1. Vyberte soubory v šabloně a klikněte pravým tlačítkem nebo místní nabídku a zvolte **Odeslat do**  > **Komprimovaná složka (ZIP)** .

    Soubory, které jste vybrali, se komprimují do souboru *zip* .

1. Vložte nový soubor *. zip* do stejného adresáře jako starý soubor *. zip* .

1. Odstraňte extrahované soubory šablon a starý soubor template *. zip* .

## <a name="see-also"></a>Viz také:

- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parametry šablony](../ide/template-parameters.md)