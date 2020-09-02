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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89313793"
---
# <a name="project-and-item-templates"></a>Šablony projektů a položek

Šablony projektů a položek poskytují opakovaně použitelné zástupné procedury, které uživatelům poskytují základní kód a strukturu, které mohou přizpůsobit svým účelům.

## <a name="visual-studio-templates"></a>šablony sady Visual Studio

V aplikaci Visual Studio je nainstalováno několik předdefinovaných šablon projektů a položek. Tyto šablony, jako je **Webová aplikace ASP.NET** a šablony **knihovny tříd** , jsou k dispozici pro výběr při vytváření nového projektu. Šablony položek, jako jsou soubory kódu, soubory XML, stránky HTML a šablony stylů, se zobrazí v okně **Přidat novou položku** .

Tyto šablony poskytují výchozí bod pro uživatele pro zahájení vytváření projektů nebo pro rozbalení stávajících projektů. Šablony projektů poskytují soubory, které jsou požadovány pro konkrétní typ projektu, zahrnují standardní odkazy na sestavení a nastavují výchozí vlastnosti projektu a možnosti kompilátoru. Šablony položek mohou mít složitost od jednoho prázdného souboru, který má určitou příponu, do více souborů zdrojového kódu se zástupným kódem, soubory informací návrháře a integrované prostředky.

Můžete použít nainstalované šablony, vytvářet vlastní šablony nebo stahovat a používat šablony vytvořené komunitou. Další informace naleznete v tématu [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md) a [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Obsah šablony

Všechny šablony projektů a položek, ať už nainstalované se sadou Visual Studio nebo vytvořené vámi, fungují podle stejných principů a mají podobný obsah. Všechny šablony obsahují následující položky:

- Soubory, které mají být vytvořeny při použití této šablony. Tyto soubory zahrnují soubory zdrojového kódu, vložené prostředky, soubory projektu a tak dále.

::: moniker range="vs-2017"

- Soubor *. vstemplate* obsahující metadata potřebná k vytvoření projektu nebo položky ze šablony a k zobrazení šablony v **novém projektu** a **Přidání nových položek** okna.

::: moniker-end

::: moniker range=">=vs-2019"

- Soubor *. vstemplate* obsahující metadata potřebná k vytvoření projektu nebo položky ze šablony a k zobrazení šablony na stránce **vytvořit nový projekt** nebo v dialogovém okně **Přidat novou položku** .

::: moniker-end

   Další informace o souborech *. vstemplate* naleznete v tématu [Tagy šablony](template-tags.md) a [parametry šablony](../ide/template-parameters.md).

Když jsou tyto soubory komprimovány do souboru *zip* a vloženy do správné složky, Visual Studio je automaticky zobrazí v následujících umístěních:

::: moniker range="vs-2017"

- Šablony projektu se zobrazí v okně **Nový projekt** .

::: moniker-end

::: moniker range=">=vs-2019"

- Šablony projektu se zobrazí na stránce **vytvořit nový projekt** .

::: moniker-end

- Šablony položek se zobrazí v okně **Přidat novou položku** .

Další informace o složkách šablon naleznete v tématu [How to: vyhledání a uspořádání šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Viz také

- [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md)
- [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md)
- [Značky šablon](template-tags.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Balíčky NuGet v šablonách sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
