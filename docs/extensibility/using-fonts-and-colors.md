---
title: Pomocí písma a barev | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4415d00e5a1233bfdf14dbc86a3a7ed2f7b8e770
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141207"
---
# <a name="using-fonts-and-colors"></a>Pomocí písma a barev
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Poskytuje podporu pro používání písma a barev k zobrazení textu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Písma a barev – přehled](../extensibility/font-and-color-overview.md)  
 Popisuje nastavení písma a barvy textu v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE). Také seznámíte se základními pojmy, kategorie a zobrazit položky a popisuje, jak použít VSPackages a základní editor atributů textu.  
  
 [Získávání písma a barev informace pro zabarvení textu](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Poskytuje pokyny pro implementaci zabarvení text v VSPackages, která spravovat **kategorie** jiné než **textového editoru**.  
  
 [Přístup k uložené písma a barev](../extensibility/accessing-stored-font-and-color-settings.md)  
 Vysvětluje, jak aktuální písma a barev nastavení lze ukládat, načíst a použít.  
  
 [Implementace vlastních kategorií a zobrazit položky](../extensibility/implementing-custom-categories-and-display-items.md)  
 Popisuje základní kroky, které lze vytvořit a použít vlastní, z okna **zobrazit položky** a **kategorie** pro podporu zobrazení textu.  
  
 Tento přístup vyžaduje VSPackage implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> rozhraní a související rozhraní.  
  
 [Postupy: přístup k vestavěná písma a barevné schéma](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Popisuje, jak definovat a registrovat kategorii pomocí předdefinovaných písma a barvy a zahájení používání poskytované systémem písma a barev.  
  
## <a name="reference"></a>Odkaz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Poskytuje instanci `IVsFontAndColorDefaults` nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní, která odpovídá konkrétní položky uvedené v **zobrazit nastavení pro** v seznamu **písma a barev** stránky **Možnosti** dialogové okno.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Umožňuje VSPackage pro podporu rozhraní IDE **písma a barev** stránky tak, že definujete výchozí písma a barev pro okno nebo součást uživatelského rozhraní.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Poskytuje mechanismus, pomocí kterého VSPackage, která poskytuje podporu písma a barev můžete určit skupinu položek zobrazení - nadtypem kategorii, která představuje sjednocení dvou nebo více kategorií.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Umožňuje VSPackage načíst data písma a barev, nebo uložit do registru.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Upozorní VSPackages, která používají písma a barev informace o změnách v nastavení písma a barvy.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Poskytuje nástroje pro práci s vstupní a výstupní data, která se používají metody [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **písma a barev** mechanismus.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Ovládací prvky ukládání do mezipaměti nastavení písma a barvy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)  
 Popisuje, jak můžete použít jazyk služby k přizpůsobení VSPackages [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
 [Barevné zvýrazňování syntaxe ve vlastních editorech](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor používá jazyk služby k implementaci barevné zvýrazňování syntaxe.  
  
 [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Vysvětluje, jak používat [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] services k vytvoření prvky uživatelského rozhraní, které odpovídají zbytek [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].