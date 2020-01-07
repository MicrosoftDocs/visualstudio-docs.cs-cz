---
title: Aktualizovat existující šablony položek projektu
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591356"
---
# <a name="how-to-update-existing-templates"></a>Postupy: aktualizace existujících šablon

Po vytvoření šablony a soubory do komprimovat *ZIP* soubor, můžete upravit šablonu. To můžete provést ručně změnou souborů v šabloně nebo exportováním nové šablony z projektu, který je založen na šabloně.

## <a name="use-the-export-template-wizard"></a>Použití Průvodce exportem šablony

Visual Studio poskytuje **Průvodce exportem šablony** , který slouží k aktualizaci existující šablony:

1. Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .

1. Vyberte šablonu, kterou chcete aktualizovat, a pokračujte postupem vytvoření nového projektu.

1. Upravte projekt v sadě Visual Studio. Například změňte typ výstupu nebo přidejte nový soubor do projektu.

1. Na **projektu** nabídce zvolte **exportovat šablonu**.

    **Průvodce exportem šablony** otevře.

1. Postupujte podle pokynů v průvodci export šablony jako *ZIP* souboru.

1. Volitelné Soubor *. zip* umístěte do následujícího adresáře: *%UserProfile%\Documents\Visual Studio \<verze\>\Templates\ProjectTemplates* , aby byl k dispozici pro výběr. Bude potřeba tento krok proveďte, pokud jste nevybrali možnost **automaticky importovat šablonu do sady Visual Studio** v **Průvodce exportem šablony**.

1. Odstranit starou šablonu *ZIP* souboru.

## <a name="manually-update-an-existing-template"></a>Ručně aktualizovat existující šablony

Bez použití můžete aktualizovat existující šablonu **Průvodce exportem šablony**, tak, že upravíte soubory komprimované *ZIP* souboru.

### <a name="to-manually-update-an-existing-template"></a>Chcete-li ručně aktualizovat existující šablony

1. Vyhledejte *ZIP* soubor, který obsahuje šablonu. Šablony projektů uživatele jsou umístěné na *%USERPROFILE%\Documents\Visual Studio \<verze\>\Templates\ProjectTemplates*.

1. Extrahovat *ZIP* souboru.

1. Upravit nebo odstranit aktuální soubory šablon nebo přidejte nové soubory do šablony.

1. Otevřít, upravit a uložit *.vstemplate* soubor XML pro zpracování chování aktualizované nebo nové soubory.

    Další informace o *.vstemplate* schématu, naleznete v tématu [odkaz na schéma šablon sady Visual Studio (rozšiřitelnost)](../extensibility/visual-studio-template-schema-reference.md). Další informace o můžete parametrizovat ve zdrojových souborech najdete v tématu [parametry šablony](../ide/template-parameters.md).

1. Vyberte soubory v šabloně a v nabídce klepněte pravým tlačítkem nebo kontextu a zvolte **odeslat** > **komprimovanou složku (ZIP)** .

    Do jsou komprimované soubory, které jste vybrali *ZIP* souboru.

1. Vložit nový *ZIP* souboru ve stejném adresáři jako původní *ZIP* souboru.

1. Odstranit extrahované soubory šablony a starou šablonu *ZIP* souboru.

## <a name="see-also"></a>Viz také:

- [Přizpůsobení šablony](../ide/customizing-project-and-item-templates.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md)
- [Parametry šablony](../ide/template-parameters.md)
