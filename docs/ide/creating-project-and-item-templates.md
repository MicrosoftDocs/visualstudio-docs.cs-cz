---
title: Šablony projektů a souborů
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589757"
---
# <a name="project-and-item-templates"></a>Šablony projektů a položek

Šablony projektů a položek poskytují opakovaně použitelný, která uživatelům umožňují základní kód a strukturu, který můžete přizpůsobit pro vlastní účely.

## <a name="visual-studio-templates"></a>šablony sady Visual Studio

Několik předdefinovaných projektů a šablon položek je nainstalováno pomocí sady Visual Studio. Tyto šablony, jako je **Webová aplikace ASP.NET** a šablony **knihovny tříd** , jsou k dispozici pro výběr při vytváření nového projektu. Šablony položek, jako jsou soubory kódu, soubory XML, stránky HTML a šablony stylů, se zobrazí v okně **Přidat novou položku** .

Tyto šablony představují výchozí bod pro uživatele a začněte vytvářet projekty nebo rozšířit projekty stávající. Šablony projektů poskytují soubory, které jsou požadovány pro konkrétní typ projektu, zahrnují standardní odkazy na sestavení a nastavují výchozí vlastnosti projektu a možnosti kompilátoru. Šablony položek mohou být v rozsahu od jednoho prázdný soubor, který má určitá příponu souboru, do více souborů se zdrojovým kódem se zakázaným inzerováním kódem, informační soubory pro návrháře a vložené prostředky.

Můžete použít nainstalované šablony, vytvářet vlastní šablony nebo stahovat a používat šablony vytvořené komunitou. Další informace najdete v tématu [postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md) a [postup: Tvorba šablon položek s](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Obsah šablony

Všechny šablony projektů a položek, zda je nainstalován se sadou Visual Studio nebo vytvořené vámi, pracovat na stejných principech a mají podobný obsah. Všechny šablony obsahují následující položky:

- Soubory, které mají být vytvořeny při použití této šablony. Tyto soubory zahrnují soubory zdrojového kódu, vložené prostředky, soubory projektu a tak dále.

::: moniker range="vs-2017"

- Soubor *. vstemplate* obsahující metadata potřebná k vytvoření projektu nebo položky ze šablony a k zobrazení šablony v **novém projektu** a **Přidání nových položek** okna.

::: moniker-end

::: moniker range=">=vs-2019"

- Soubor *. vstemplate* obsahující metadata potřebná k vytvoření projektu nebo položky ze šablony a k zobrazení šablony na stránce **vytvořit nový projekt** nebo v dialogovém okně **Přidat novou položku** .

::: moniker-end

   Další informace o souborech *. vstemplate* naleznete v tématu [Tagy šablony](template-tags.md) a [parametry šablony](../ide/template-parameters.md).

Když jsou tyto soubory zkomprimovány do *ZIP* soubor a uložte do správné složky, Visual Studio automaticky zobrazí na následujících místech:

::: moniker range="vs-2017"

- Šablony projektu se zobrazí v okně **Nový projekt** .

::: moniker-end

::: moniker range=">=vs-2019"

- Šablony projektu se zobrazí na stránce **vytvořit nový projekt** .

::: moniker-end

- Šablony položek se zobrazí v okně **Přidat novou položku** .

Další informace o adresářích pro šablony najdete v tématu [postupy: hledání a organizace šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Viz také:

- [Postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md)
- [Postupy: Tvorba šablon položek](../ide/how-to-create-item-templates.md)
- [Tagy šablony](template-tags.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Přizpůsobení šablony](../ide/customizing-project-and-item-templates.md)
- [Balíčky NuGet ve šablony sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
