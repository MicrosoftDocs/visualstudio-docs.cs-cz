---
title: Aktualizace existujících šablon položek projektu
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 44f99646330d3c8a75bd94310bc0adf9073f9d49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591356"
---
# <a name="how-to-update-existing-templates"></a>Postup: Aktualizace existujících šablon

Po vytvoření šablony a kompresi souborů do souboru *ZIP* můžete šablonu upravit. To lze provést ruční změnou souborů v šabloně nebo exportem nové šablony z projektu, který je založen na šabloně.

## <a name="use-the-export-template-wizard"></a>Použití Průvodce exportem šablony

Visual Studio poskytuje **Průvodce exportem šablony,** který lze použít k aktualizaci existující šablony:

1. Z řádku nabídek zvolte **Soubor** > **nového** > **projektu.**

1. Vyberte šablonu, kterou chcete aktualizovat, a pokračujte kroky k vytvoření nového projektu.

1. Upravte projekt v sadě Visual Studio. Můžete například změnit typ výstupu nebo přidat nový soubor do projektu.

1. V nabídce **Project** zvolte **Exportovat šablonu**.

    Otevře se **Průvodce exportem šablony.**

1. Podle pokynů v průvodci exportujte šablonu jako soubor *ZIP.*

1. (Nepovinné) Soubor *ZIP* umístěte do následujícího adresáře: *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates,* aby byl k dispozici pro výběr. Tento krok budete muset provést, pokud jste nevybrali možnost **Automaticky importovat šablonu do sady Visual Studio** v **Průvodci exportem šablony**.

1. Odstraňte starý soubor *ZIP* šablony.

## <a name="manually-update-an-existing-template"></a>Ruční aktualizace existující šablony

Existující šablonu můžete aktualizovat bez použití **Průvodce exportem šablony**úpravou souborů v komprimovaném souboru *ZIP.*

### <a name="to-manually-update-an-existing-template"></a>Ruční aktualizace existující šablony

1. Vyhledejte soubor *ZIP* obsahující šablonu. Šablony uživatelských projektů jsou umístěny na adrese *%USERPROFILE%\Documents\Visual Studio \<version\>\Templates\ProjectTemplates*.

1. Extrahujte soubor *ZIP.*

1. Upravte nebo odstraňte aktuální soubory předlohy nebo přidejte do šablony nové soubory.

1. Otevřete, upravte a uložte soubor *XML .vstemplate* pro zpracování aktualizovaného chování nebo nových souborů.

    Další informace o schématu *.vstemplate* naleznete v tématu Visual Studio odkaz na schéma [šablony (rozšiřitelnost).](../extensibility/visual-studio-template-schema-reference.md) Další informace o parametrizaci ve zdrojových souborech naleznete v [tématu Parametry šablony](../ide/template-parameters.md).

1. Vyberte soubory v šabloně a v nabídce pravým tlačítkem nebo v místní nabídce a zvolte **Odeslat** > **komprimovně (zip) složku**.

    Vybrané soubory jsou komprimovány do souboru *ZIP.*

1. Vložte nový soubor *ZIP* do stejného adresáře jako starý soubor *ZIP.*

1. Odstraňte extrahované soubory šablon a starý soubor *ZIP* šablony.

## <a name="see-also"></a>Viz také

- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Odkaz na schéma šablony sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Parametry šablony](../ide/template-parameters.md)
