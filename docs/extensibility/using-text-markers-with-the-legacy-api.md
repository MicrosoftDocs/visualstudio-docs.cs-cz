---
title: Text značky pomocí starší verze rozhraní API | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text markers
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 62b77180858b40bf2620eaed284fa35b9a48288a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835927"
---
# <a name="using-text-markers-with-the-legacy-api"></a>Text značky pomocí starší verze rozhraní API
Text značky je plovoucí rozsah textu ve vyrovnávací paměti, může mít vliv na zobrazení a chování oblast textu. Značky zahrnují zarážky, záložek, podtržení vlnovkou a oblastí jen pro čtení. Text značky jsou v podstatě totéž barevné zvýrazňování syntaxe. Barevné zvýrazňování syntaxe je rychlý způsob, jak komunikovat syntaxi jazyka, který je spojen s oblast textu. Barevné zvýrazňování syntaxe obecně vyžádá, když Windows překreslí obrazovky, když rychlost je důležité. Barevné zvýrazňování syntaxe změní barvu textu. Text značky můžete změnit mnoho dalších vlastností textu. Text značky můžete "float" a použít zvláštní chování a obarvení.  
  
 Kvůli výkonu režii spojenou s text značky nevytvářejte mnoho značek pro vaše vyrovnávací paměti textu. Každá značka se aktualizuje pokaždé, když se, že uživatel upraví obsah vyrovnávací paměti.  
  
> [!NOTE]
>  Uživatelé mohou změnit barvu typ viditelný značky, ale ne jeho tvar a styl. Další informace najdete v tématu [písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## <a name="related-topics"></a>Související témata  
  
| Název | Popis |
| - | - |
| [Postupy: Přidání standardních textových značek](../extensibility/how-to-add-standard-text-markers.md) | Popisuje postup přidání standardní text značky typ poskytovaný modulem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] základní editor k zobrazení textu. |
| [Postupy: Implementace chybových značek](../extensibility/how-to-implement-error-markers.md) | Popisuje, jak implementovat instance [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] značky, který se používá k označení chyby pomocí červené podtržení vlnovkou. |
| [Postupy: Vytvoření vlastních textových značek](../extensibility/how-to-create-custom-text-markers.md) | Popisuje, jak vytvořit a přidat typ značky vlastní text k zobrazení textu. |
| [Postupy: Použití textových značek](../extensibility/how-to-use-text-markers.md) | Vysvětluje, jak přidat text značky. |
| [Práce v základní editoru](../extensibility/inside-the-core-editor.md) | Popisuje funkce základní editor a poskytuje podrobné informace o tom, jak přizpůsobit základní editor. |
| [Funkce editoru](https://msdn.microsoft.com/library/bdac940d-1f14-4019-a01f-fd0bb3dc7198) | Popisuje funkce dostupné v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] základní editor. |
  
## <a name="reference"></a>Odkaz  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Poskytuje jednotný mechanismus pro získání informací o typu značky určitý text, ať už předdefinovaná v nástroji editor nebo registrovaných VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Poskytuje přístup k a nastaví pozici textu značky ve vyrovnávací paměti textu pomocí dvojrozměrné souřadnice.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Poskytuje metody pro správu text značky.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Poskytuje zpětná volání, aby [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrovaného vývojového prostředí a další procesy, které se používají k úpravě text značky.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Rozšiřuje funkce, které jsou k dispozici prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní tím, že poskytuje další zpětná volání.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Rozšiřuje funkce, které jsou k dispozici prostřednictvím <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní tím, že poskytuje další zpětná volání.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Umožňuje typ značky k určení, zda jiné typy značek sdílejí stejnou sadu barev.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Poskytuje kontext pro text značky v základní editor. Pro každý typ značky text, který je v základní editor, rozhraní IDE vytvoří samostatné <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> objektu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Obslužná rutina, která je k dispozici pro značky, jehož glyfy podporovat úpravu přetahování myší. Piktogram je ikona, která indikuje pozici značku.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Vrátí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> rozhraní ze služby, které poskytuje text značky do jiné rozšíření VSPackages.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Poskytuje přístup k a nastaví pozici textu značky ve vyrovnávací paměti textu pomocí jednorozměrné souřadnice. Pokud je to možné, nepoužívejte toto rozhraní.