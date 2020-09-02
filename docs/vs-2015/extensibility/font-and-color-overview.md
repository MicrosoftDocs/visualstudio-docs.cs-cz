---
title: Přehled písma a barev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a20cfa2372b1e55652ffcebe6d173cff86140a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204345"
---
# <a name="font-and-color-overview"></a>Přehled písem a barev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje písmo textu a nastavení barev v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE). Zavádí také koncepty kategorií a zobrazení položek a popisuje, jak VSPackage a základní editor používají atributy textu.  
  
## <a name="the-fonts-and-colors-property-page"></a>Stránka vlastností písma a barvy  
 Můžete spravovat atributy zobrazeného textu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE) prostřednictvím stránky vlastností **písma a barvy** . Chcete-li najít stránku vlastností **písma a barvy** , v nabídce **nástroje** klikněte na položku **Možnosti**. Rozbalte položku **prostředí**a potom klikněte na možnost **písma a barvy**.  
  
## <a name="categories-and-display-items"></a>Kategorie a zobrazované položky  
 Písma a barvy jsou uspořádány do **kategorií** a **zobrazují položky**.  
  
- **Kategorie** je logický nebo funkční kontejner pro řadu **položek zobrazení**.  
  
   Seznam **kategorií** je v rozevíracím seznamu **Zobrazit nastavení pro** stránku vlastností **písma a barvy** .  
  
- **Položka zobrazení** je dobře definovaná textová entita, jako je například komentář, řetězec nebo struktura ovládacího prvku, která má být zabarvení, je-li zobrazena.  
  
  Každá **položka zobrazení** je definována jedinečně v rámci **kategorie** , která ji obsahuje. V důsledku toho může mít **Category** více než jedna kategorie **zobrazovanou položku** se stejným názvem.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>Ovládací prvek VSPackage písma a barev  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Umožňuje VSPackage:  
  
- Definujte **kategorie**písma a barev.  
  
- Určete písma a barvy použité pro **zobrazení položek**.  
  
- Interakce se stránkou vlastností **písma a barvy** .  
  
- Agregace více **kategorií** do skupin  
  
- Zachovat změny ve výchozím nastavení.  
  
  Existují dva způsoby, jak pracovat s výběry písma a barev v rámci [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] .  
  
- Jedním ze způsobů se říká *zvýraznění syntaxe*. Používá jej VSPackage, který přizpůsobí existující [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor pro implementaci jazykové služby a vytvoří Editor zdrojového kódu.  
  
   Jenom jedna **kategorie** podporuje tento mechanismus, konkrétně **textový editor**.  
  
- Obecnější alternativa podporuje všechny ostatní **kategorie** a jiné součásti uživatelského rozhraní než Editor zdrojového kódu při zobrazení textu. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Základní nastavení textu v editoru  
 Nastavení písma a barev pro základní editor objektu jazykové služby se řídí **textem EditorCategory** , který se nachází v rozevíracím seznamu **Zobrazit nastavení pro** stránku vlastností **písma a barvy** .  
  
 Při práci s editory byste měli použít specializovaný mechanismus pro kontrolu písma a barev, který služba jazyka poskytuje k řízení a rozšiřování nastavení **textového editoru** . Mechanizmus je označován jako *zbarvení syntaxe* a poskytuje:  
  
- Zjednodušená metoda pro správu písem a barev zobrazených položek.  
  
   Další informace naleznete v tématech <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- Dobře definovaný a optimalizovaný mechanismus vybarvení.  
  
   Další informace naleznete v tématu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- Možnost použít vestavěné položky zobrazení z **textu EditorCategory** a roztáhnout je.  
  
   Další informace naleznete v tématu [How to: use](../extensibility/internals/how-to-use-built-in-colorable-items.md) a Recolored Items a [Custom Colored Items](../extensibility/internals/custom-colorable-items.md).  
  
- Automatické uchovávání aktuálního stavu vestavěných i vlastních položek zobrazení pomocí kategorie **textový editor** .  
  
  Další informace o Obarvení syntaxe naleznete [v tématu barvy syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Viz také  
 [Starší rozhraní v editoru](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Barevné zvýrazňování syntaxe ve službě starší verze jazyka](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
