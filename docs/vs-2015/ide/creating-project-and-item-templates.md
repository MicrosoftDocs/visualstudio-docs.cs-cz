---
title: Vytváření šablon projektů a položek | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], projects
- item templates, about item templates
- templates [Visual Studio], item
- Visual Studio templates, item
- Visual Studio templates, about templates
- project templates [Visual Studio], about project templates
- Visual Studio templates, project
- templates [Visual Studio], about templates
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 995696dafce64cdcb1fbb11d0788bbe13453c440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619304"
---
# <a name="creating-project-and-item-templates"></a>Vytváření šablon projektů a položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] šablony projektů a položek poskytují opakovaně použitelné zástupné procedury, které uživatelům poskytují základní kód a strukturu, které mohou používat pro vlastní účely.

## <a name="visual-studio-templates"></a>Šablony aplikace Visual Studio
 Několik předdefinovaných šablon projektů a položek je nainstalováno již po instalaci aplikace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Jako [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../includes/csprcs-md.md)] příklady šablon projektů jsou k dispozici šablony aplikace a model Windows Forms a knihovny tříd, které jsou k dispozici v dialogovém okně **Nový projekt** . Šablony nainstalované položky jsou k dispozici v dialogovém okně **Přidat novou položku** a zahrnují položky jako soubory kódu, soubory XML, stránky HTML a šablony stylů.

 Tyto šablony představují výchozí bod pro uživatele, aby mohli začít projekty vytvářet nebo rozšířit projekty stávající. Šablony projektů poskytují soubory, které jsou požadovány pro konkrétní typ projektu, zahrnují standardní odkazy na sestavení a nastavují výchozí vlastnosti projektu a možnosti kompilátoru. Šablony položek mohou mít různou strukturu od jednoho prázdného souboru, který má správnou příponu, až k vícesouborové položce, která například obsahuje zdrojové soubory se základním kódem, informační soubory pro návrháře a vložené prostředky.

 Kromě nainstalovaných šablon v dialogových oknech **Nový projekt** a **Přidat novou položku** můžete vytvářet vlastní šablony nebo stahovat a používat šablony vytvořené komunitou. Další informace naleznete v tématu [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md) a [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md).

## <a name="contents-of-a-template"></a>Obsah šablony
 Všechny šablony projektů a položek, ať už instalované spolu s aplikací [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo vytvořené vámi, fungují na stejných principech a mají podobný obsah. Všechny šablony obsahují následující položky:

- Soubory, které mají být vytvořeny při použití této šablony. To zahrnuje zdrojové soubory, vložené prostředky, soubory projektu a tak dále.

- Jeden soubor .vstemplate. Tento soubor obsahuje metadata, která poskytují [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] informace potřebné k zobrazení šablony v dialogových oknech **Nový projekt** a **Přidat novou položku** a vytvoření projektu nebo položky ze šablony. Další informace o souborech. vstemplate naleznete v tématu [template Parameters](../ide/template-parameters.md).

  Když jsou tyto soubory komprimovány do souboru zip a vloženy do správné složky, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky je zobrazí. Šablony projektu se zobrazí v části **Moje šablony** v dialogových oknech **Nový projekt** a šablony položek se zobrazí v dialogových oknech **Přidat novou položku** . Další informace o složkách šablon naleznete v tématu [How to: vyhledání a uspořádání šablon](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="starter-kits"></a>startovní sady
 Startovní sady jsou zdokonalené šablony, které lze veřejně sdílet s ostatními členy komunity. Startovní sada obsahuje ukázky kódu s kompilací, dokumentaci a další prostředky, které mají za úkol pomoci uživatelům naučit se nové nástroje a programovací techniky, aby mohli tvořit užitečné a opravdové aplikace. Základní obsah a postupy pro startovní sady jsou stejné jako pro šablony. Další informace najdete v tématu [Postupy: Vytváření startovních sad](../ide/how-to-create-starter-kits.md).

## <a name="see-also"></a>Viz také
 [Postupy: vytváření šablon projektů](../ide/how-to-create-project-templates.md) [Postupy: vytvoření šablon položek](../ide/how-to-create-item-templates.md) šablony [parametry](../ide/template-parameters.md) [přizpůsobení šablon](../ide/customizing-project-and-item-templates.md) [Postupy: Vytváření startovních sad](../ide/how-to-create-starter-kits.md)
