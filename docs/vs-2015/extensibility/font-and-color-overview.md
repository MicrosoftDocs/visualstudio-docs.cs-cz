---
title: Písma a barvy – přehled | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d849d93bdab481cecbb7d1f0f862f1db8eb3c181
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769446"
---
# <a name="font-and-color-overview"></a>Písma a barvy – přehled
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje nastavení písem a barev textu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE). Se také seznámíte se základními pojmy kategorií a zobrazit položky, a popisuje jak použít rozšíření VSPackages a základní editor atributů textu.  
  
## <a name="the-fonts-and-colors-property-page"></a>Písma a barvy stránky vlastností  
 Můžete spravovat atributy zobrazeného textu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE) až **písma a barvy** stránku vlastností. Najít **písma a barvy** vlastnost na stránce **nástroje** nabídky, klikněte na tlačítko **možnosti**. Rozbalte **prostředí**a potom klikněte na tlačítko **písma a barvy**.  
  
## <a name="categories-and-display-items"></a>Kategorie a zobrazení položky  
 Písma a barvy, které jsou uspořádány do **kategorie** a **zobrazit položky**.  
  
- A **kategorie** je logický operátor or funkční kontejner pro celou řadou **zobrazit položky**.  
  
   Seznam **kategorie** probíhá **zobrazit nastavení pro** z rozevíracího seznamu **písma a barvy** stránku vlastností.  
  
- A **položky zobrazení** je dobře definovaný textu entity jako komentář, řetězec nebo ovládací prvek strukturu, která má být barevně zvýrazněné při zobrazení.  
  
  Každý **položky zobrazení** je jednoznačně definována v rámci **kategorie** , který jej obsahuje. V důsledku toho více než jeden **kategorie** může mít **položky zobrazení** se stejným názvem.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Ovládací prvek VSPackage písma a barvy  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Umožňuje rozšíření VSPackages na:  
  
- Definování písma a barvy **kategorie**.  
  
- Zadejte písma a barvy použité k zobrazení **zobrazit položky**.  
  
- Pracovat **písma a barvy** stránku vlastností.  
  
- Agregace více **kategorie** do skupin.  
  
- Zachovat změny ve výchozím nastavení.  
  
  Existují dva způsoby, jak pracovat s výběry písma a barev v rámci [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
- Jedním ze způsobů, se označuje jako *barevné zvýraznění syntaxe*. Je používána VSPackage, která upraví stávající [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor k implementaci služby jazyka a vytvoření zdroje editoru.  
  
   Pouze jeden **kategorie** podporuje tento mechanismus, a to, **textový Editor**.  
  
- Další obecné alternativní podporuje všechny ostatní **kategorie** a součásti uživatelského rozhraní než při zobrazování textového editoru zdrojového kódu. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Nastavení základní Editor textu  
 Řídí nastavení písem a barev pro základní editor objekt služby jazyka **Text EditorCategory** součástí **zobrazit nastavení pro** z rozevíracího seznamu **písma a barvy** stránku vlastností.  
  
 Při práci s editory, měli byste použít specializované písmo a barvu ovládacího prvku mechanismus, který poskytuje služba jazyka pro řízení a rozšíření **textový Editor** nastavení. Mechanismu, který se označuje jako *barevné zvýrazňování syntaxe* a poskytuje:  
  
- Zjednodušený postup pro správu písma a barvy položky zobrazení.  
  
   Další informace naleznete v tématu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Dobře definovaný a optimalizované zabarvení mechanismus.  
  
   Další informace naleznete v tématu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- Možnost použít předdefinované zobrazení položek z **Text EditorCategory** a k jejich rozšíření.  
  
   Další informace najdete v tématu [postupy: používání předdefinovaných které lze zabarvit položky](../extensibility/internals/how-to-use-built-in-colorable-items.md) a [vlastní, které lze zabarvit položky](../extensibility/internals/custom-colorable-items.md).  
  
- Automatickou trvalost aktuálního stavu z předdefinovaných a vlastních zobrazit položky, které **textový Editor** kategorie.  
  
  Další informace o viz barevné zvýrazňování syntaxe [barevné zvýrazňování syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Viz také  
 [Starší verze rozhraní v editoru](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

