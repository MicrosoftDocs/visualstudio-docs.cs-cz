---
title: Používání písem a barev | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177234"
---
# <a name="using-fonts-and-colors"></a>Použití písem a barev
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Poskytuje podporu pro používání písma a barev k zobrazení textu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled písem a barev](../extensibility/font-and-color-overview.md)  
 Popisuje písmo textu a nastavení barev v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE). Také zavádí koncepty kategorií a zobrazení položek a popisuje, jak VSPackage a základní editor používají atributy textu.  
  
 [Získání informací o písmu a barvě pro obarvení textu](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Poskytuje pokyny pro implementaci obarvení textu v VSPackage, které spravují jiné **kategorie** než **textový editor**.  
  
 [Přístup k uloženým nastavením písem a barev](../extensibility/accessing-stored-font-and-color-settings.md)  
 Vysvětluje, jak lze uložit, načíst a použít aktuální nastavení písma a barev.  
  
 [Implementace vlastních kategorií a položek zobrazení](../extensibility/implementing-custom-categories-and-display-items.md)  
 Popisuje základní kroky, podle kterých může okno vytvořit a použít vlastní **položky zobrazení** a **kategorie** pro podporu zobrazení textu.  
  
 Tento přístup vyžaduje, aby VSPackage implementoval <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> rozhraní a související rozhraní.  
  
 [Postupy: Přístup k předdefinovaným písmům a barevnému schématu](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Popisuje, jak definovat a zaregistrovat kategorii pomocí integrovaných písem a barev a zahájit používání písem a barev poskytovaných systémem.  
  
## <a name="reference"></a>Referenční informace  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Poskytuje instanci `IVsFontAndColorDefaults` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> rozhraní nebo rozhraní, které odpovídá konkrétní položce uvedené v seznamu **Zobrazit nastavení pro** na stránce **písma a barvy** dialogového okna **Možnosti** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Umožňuje VSPackage podporovat **písma a barvy** IDE pomocí definování výchozích písem a barev pro okno nebo komponentu uživatelského rozhraní.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Poskytuje mechanismus, pomocí kterého může VSPackage, který poskytuje podporu písma a barev, určit skupinu položek zobrazení – Super kategorii, která představuje sjednocení dvou nebo více kategorií.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Umožňuje VSPackage načíst data písma a barev nebo je Uložit do registru.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Upozorňuje na VSPackage, které používají písmo a barevné informace o změnách v nastavení písma a barvy.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Poskytuje nástroje pro práci se vstupními a výstupními daty, které jsou používány metodami [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **písma a barvy** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Řídí ukládání nastavení písma a barev do mezipaměti.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vývoj služby starší verze jazyka](../extensibility/internals/developing-a-legacy-language-service.md)  
 Popisuje, jak mohou sady VSPackage používat jazykové služby k přizpůsobení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editoru.  
  
 [Barevné zvýrazňování syntaxe ve vlastních editorech](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries způsob, jakým [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor používá jazykové služby k implementaci Obarvení syntaxe.  
  
 [Rozšíření dalších částí sady Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Vysvětluje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] služby k vytvoření prvků uživatelského rozhraní, které se shodují se zbytkem z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .
