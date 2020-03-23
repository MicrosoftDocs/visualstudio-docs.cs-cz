---
title: Šablony pro projekty a soubory
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2cc932a2407aeb4951bab970a0edc6e2b2a5fcc9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301949"
---
# <a name="project-and-item-templates"></a>Šablony projektů a položek

Šablony projektů a položek poskytují opakovaně použitelné zástupné procedury, které uživatelům poskytují základní kód a strukturu, které mohou přizpůsobit pro své vlastní účely.

## <a name="visual-studio-templates"></a>šablony sady Visual Studio

V sadě Visual Studio je nainstalována řada předdefinovaných šablon projektů a položek. Tyto šablony, například **ASP.NET šablony webové aplikace** a **knihovny tříd,** jsou k dispozici pro výběr při vytváření nového projektu. Šablony položek, jako jsou soubory kódu, soubory XML, stránky HTML a šablony stylů, se zobrazí v okně **Přidat novou položku.**

Tyto šablony poskytují uživatelům výchozí bod, aby začali vytvářet projekty nebo rozbalovat existující projekty. Šablony projektů poskytují soubory, které jsou požadovány pro konkrétní typ projektu, zahrnují standardní odkazy na sestavení a nastavují výchozí vlastnosti projektu a možnosti kompilátoru. Šablony položek se mohou pohybovat ve složitosti od jednoho prázdného souboru, který má určitou příponu souboru, až po více souborů zdrojového kódu se zakázaným inzerováním, informačními soubory návrháře a vloženými prostředky.

Můžete použít nainstalované šablony, vytvořit vlastní šablony nebo stáhnout a používat šablony vytvořené komunitou. Další informace naleznete v [tématu How to: Create project templates](../ide/how-to-create-project-templates.md) and [How to: Create item templates](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Obsah šablony

Všechny šablony projektu a položek, ať už jsou nainstalované v sadě Visual Studio nebo vytvořené vámi, fungují pomocí stejných principů a mají podobný obsah. Všechny šablony obsahují následující položky:

- Soubory, které mají být vytvořeny při použití této šablony. Tyto soubory zahrnují soubory zdrojového kódu, vložené prostředky, soubory projektu a tak dále.

::: moniker range="vs-2017"

- Soubor *.vstemplate,* který obsahuje metadata potřebná k vytvoření projektu nebo položky ze šablony a k zobrazení šablony v oknech **Nový projekt** a Přidat novou **položku.**

::: moniker-end

::: moniker range=">=vs-2019"

- Soubor *.vstemplate,* který obsahuje metadata potřebná k vytvoření projektu nebo položky ze šablony a k zobrazení šablony na stránce **Vytvořit nový projekt** nebo v dialogovém okně Přidat novou **položku.**

::: moniker-end

   Další informace o *souborech .vstemplate* naleznete v [tématu Šablony tagy](template-tags.md) a [parametry šablony](../ide/template-parameters.md).

Pokud jsou tyto soubory komprimovány do souboru *ZIP* a vloženy do správné složky, aplikace Visual Studio je automaticky zobrazí na následujících místech:

::: moniker range="vs-2017"

- Šablony projektů se zobrazí v okně **Nový projekt.**

::: moniker-end

::: moniker range=">=vs-2019"

- Šablony projektů se zobrazí na stránce **Vytvořit nový projekt.**

::: moniker-end

- Šablony položek se zobrazí v okně **Přidat novou položku.**

Další informace o složkách šablon naleznete v [tématu Postup: Vyhledání a uspořádání šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Viz také

- [Postup: Vytvoření šablon projektů](../ide/how-to-create-project-templates.md)
- [Postup: Vytvoření šablon položek](../ide/how-to-create-item-templates.md)
- [Značky šablon](template-tags.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Balíčky NuGet v šablonách sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
