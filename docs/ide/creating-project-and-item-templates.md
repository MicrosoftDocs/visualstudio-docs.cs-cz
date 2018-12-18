---
title: Šablony projektů a souborů
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], project
- templates [Visual Studio], item
- item templates [Visual Studio]
- project templates [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 04aa647d378e956c7a2394b7c3fc2a187a7c5963
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049276"
---
# <a name="project-and-item-templates"></a>Šablony projektů a položek

Šablony projektů a položek poskytují opakovaně použitelný, která uživatelům umožňují základní kód a strukturu, který můžete přizpůsobit pro vlastní účely.

## <a name="visual-studio-templates"></a>šablony sady Visual Studio

Několik předdefinovaných projektů a šablon položek je nainstalováno pomocí sady Visual Studio. Například Visual Basic a C# **aplikace Windows Forms** a **knihovny tříd** šablony, které jsou uvedeny v **nový projekt** dialogové okno se šablony projektu. Položka zobrazení šablony v **přidat novou položku** dialogové okno pole a zahrnují položky jako soubory kódu, souborů XML, HTML stránky a šablony stylů.

Tyto šablony představují výchozí bod pro uživatele a začněte vytvářet projekty nebo rozšířit projekty stávající. Šablony projektů poskytují soubory, které jsou požadovány pro konkrétní typ projektu, zahrnují standardní odkazy na sestavení a nastavují výchozí vlastnosti projektu a možnosti kompilátoru. Šablony položek mohou být v rozsahu od jednoho prázdný soubor, který má určitá příponu souboru, do více souborů se zdrojovým kódem se zakázaným inzerováním kódem, informační soubory pro návrháře a vložené prostředky.

Můžete použít nainstalovaných šablon v **nový projekt** a **přidat novou položku** dialogových oknech, vytvořit vlastní šablony, nebo stáhnout a použít šablonu vytvořenou komunitou. Další informace najdete v tématu [postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md) a [postup: Tvorba šablon položek s](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Obsah šablony

Všechny šablony projektů a položek, zda je nainstalován se sadou Visual Studio nebo vytvořené vámi, pracovat na stejných principech a mají podobný obsah. Všechny šablony obsahují následující položky:

- Soubory, které mají být vytvořeny při použití této šablony. Tyto soubory zahrnují soubory zdrojového kódu, vložené prostředky, soubory projektu a tak dále.

- Jeden *.vstemplate* soubor, který obsahuje metadata potřebná k zobrazení šablony v **nový projekt** a **přidat novou položku** dialogová okna a vytvořte projekt nebo položku z Šablona. Další informace o *.vstemplate* soubory, naleznete v tématu [parametry šablony](../ide/template-parameters.md).

Když jsou tyto soubory zkomprimovány do *ZIP* soubor a uložte do správné složky, Visual Studio automaticky zobrazí na následujících místech:

- Šablony projektu se zobrazí v **nový projekt** dialogové okno.

- Položka šablony se zobrazí v **přidat novou položku** dialogové okno.

Další informace o adresářích pro šablony najdete v tématu [postupy: hledání a organizace šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Viz také:

- [Postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md)
- [Postupy: Tvorba šablon položek](../ide/how-to-create-item-templates.md)
- [Parametry šablony](../ide/template-parameters.md)
- [Přizpůsobení šablony](../ide/customizing-project-and-item-templates.md)
- [Balíčky NuGet ve šablony sady Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)