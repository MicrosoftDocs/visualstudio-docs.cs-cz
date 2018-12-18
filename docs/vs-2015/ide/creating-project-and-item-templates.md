---
title: Vytváření šablon projektů a položek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32c1c66484d5bdaff6ba37b8b37f7f86cb513e44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851657"
---
# <a name="creating-project-and-item-templates"></a>Vytváření šablon projektů a položek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablony projektů a položek aplikace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytují opakovaně použitelný kód, který uživatelům dává základní kód a strukturu, což mohou využít pro vlastní účely.  
  
## <a name="visual-studio-templates"></a>Šablony aplikace Visual Studio  
 Několik předdefinovaných šablon projektů a položek je nainstalováno již po instalaci aplikace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikace Windows Forms a knihovny tříd šablon, které jsou k dispozici v **nový projekt** dialogové okno jsou příkladem šablony projektu. Nainstalované šablony položek jsou k dispozici v **přidat novou položku** dialogové okno pole a zahrnují položky jako soubory kódu, souborů XML, HTML stránky a šablony stylů.  
  
 Tyto šablony představují výchozí bod pro uživatele, aby mohli začít projekty vytvářet nebo rozšířit projekty stávající. Šablony projektů poskytují soubory, které jsou požadovány pro konkrétní typ projektu, zahrnují standardní odkazy na sestavení a nastavují výchozí vlastnosti projektu a možnosti kompilátoru. Šablony položek mohou mít různou strukturu od jednoho prázdného souboru, který má správnou příponu, až k vícesouborové položce, která například obsahuje zdrojové soubory se základním kódem, informační soubory pro návrháře a vložené prostředky.  
  
 Vedle nainstalovaných šablon v **nový projekt** a **přidat novou položku** dialogová okna, můžete vytvářet svoje vlastní šablony nebo stáhnout a použít šablonu vytvořenou komunitou. Další informace najdete v tématu [postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md) a [postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md).  
  
## <a name="contents-of-a-template"></a>Obsah šablony  
 Všechny šablony projektů a položek, ať už instalované spolu s aplikací [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo vytvořené vámi, fungují na stejných principech a mají podobný obsah. Všechny šablony obsahují následující položky:  
  
- Soubory, které mají být vytvořeny při použití této šablony. To zahrnuje zdrojové soubory, vložené prostředky, soubory projektu a tak dále.  
  
- Jeden soubor .vstemplate. Tento soubor obsahuje metadata, která poskytuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] informace potřebné k zobrazení šablony **nový projekt** a **přidat novou položku** dialogová okna a vytvořte projekt nebo položku z Šablona. Další informace o souborech .vstemplate naleznete v tématu [parametry šablony](../ide/template-parameters.md).  
  
  Když jsou tyto soubory zkomprimovány do souboru .zip a vloženy do správné složky, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automaticky zobrazí je. Šablony projektu se zobrazí v **šablony** část **nový projekt** dialogová okna a šablon položek se zobrazí v **přidat novou položku** dialogových oknech. Další informace o adresářích pro šablony najdete v tématu [postupy: vyhledání a uspořádat šablony](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="starter-kits"></a>startovní sady  
 Startovní sady jsou zdokonalené šablony, které lze veřejně sdílet s ostatními členy komunity. Startovní sada obsahuje ukázky kódu s kompilací, dokumentaci a další prostředky, které mají za úkol pomoci uživatelům naučit se nové nástroje a programovací techniky, aby mohli tvořit užitečné a opravdové aplikace. Základní obsah a postupy pro startovní sady jsou stejné jako pro šablony. Další informace najdete v tématu [postupy: vytváření Startovních sad](../ide/how-to-create-starter-kits.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytváření šablon projektu](../ide/how-to-create-project-templates.md)   
 [Postupy: vytváření šablon položek](../ide/how-to-create-item-templates.md)   
 [Parametry šablony](../ide/template-parameters.md)   
 [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)   
 [Postupy: Vytváření startovních sad](../ide/how-to-create-starter-kits.md)



