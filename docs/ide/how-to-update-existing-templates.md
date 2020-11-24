---
title: Aktualizovat existující šablony položek projektu
description: Naučte se, jak pomocí Průvodce exportem šablony a dalších ručních procesů aktualizovat šablony položek projektu, které jste už vytvořili.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: how-to
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e3a709070d777ebaf600fc05abf0e651eaef5b1a
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596882"
---
# <a name="how-to-update-existing-templates"></a>Postupy: Aktualizace existujících šablon

Po vytvoření šablony a komprimaci souborů do souboru s *příponou. zip* budete možná chtít šablonu upravit. To můžete provést ručně změnou souborů v šabloně nebo exportováním nové šablony z projektu, který je založen na šabloně.

## <a name="use-the-export-template-wizard"></a>Použití Průvodce exportem šablony

Visual Studio poskytuje **Průvodce exportem šablony** , který se dá použít k aktualizaci existující šablony:

1. Z řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt** .

1. Vyberte šablonu, kterou chcete aktualizovat, a pokračujte postupem vytvoření nového projektu.

1. Upravte projekt v aplikaci Visual Studio. Například změňte typ výstupu nebo přidejte nový soubor do projektu.

1. V nabídce **projekt** vyberte položku **Exportovat šablonu**.

    Otevře se **Průvodce exportem šablony** .

1. Postupujte podle pokynů v průvodci a exportujte šablonu jako soubor *. zip* .

1. Volitelné Soubor *. zip* umístěte do následujícího adresáře: *%UserProfile%\Documents\Visual Studio \<version\> \Templates\ProjectTemplates* , aby byl k dispozici pro výběr. Tento krok bude nutné provést, pokud jste nevybrali možnost **automaticky importovat šablonu do sady Visual Studio** v **Průvodci exportem šablony**.

1. Odstraňte starý soubor template *. zip* .

## <a name="manually-update-an-existing-template"></a>Ruční aktualizace existující šablony

Existující šablonu můžete aktualizovat bez použití **Průvodce exportem šablony** úpravou souborů v komprimovaném souboru *zip* .

### <a name="to-manually-update-an-existing-template"></a>Ruční aktualizace stávající šablony

1. Vyhledejte soubor *. zip* , který obsahuje šablonu. Šablony projektu uživatele jsou umístěny v *%UserProfile%\Documents\Visual studiu \<version\> \Templates\ProjectTemplates*.

1. Extrahujte soubor *. zip* .

1. Upravte nebo odstraňte aktuální soubory šablon nebo přidejte nové soubory do šablony.

1. Otevřete, upravte a uložte soubor XML *. vstemplate* pro zpracování aktualizovaných chování nebo nových souborů.

    Další informace o schématu *. vstemplate* naleznete v tématu [Referenční dokumentace schématu šablon sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md). Další informace o tom, co můžete ve zdrojových souborech parametrizovat, najdete v tématu [parametry šablony](../ide/template-parameters.md).

1. Vyberte soubory v šabloně a klikněte pravým tlačítkem nebo místní nabídku a zvolte **Odeslat do**  >  **komprimované složky (ZIP)**.

    Soubory, které jste vybrali, se komprimují do souboru *zip* .

1. Vložte nový soubor *. zip* do stejného adresáře jako starý soubor *. zip* .

1. Odstraňte extrahované soubory šablon a starý soubor template *. zip* .

## <a name="see-also"></a>Viz také

- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Referenční dokumentace schématu šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parametry šablony](../ide/template-parameters.md)
