---
title: Uvnitř základní Editor | Dokumentace Microsoftu
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
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9aca4bb8ad55dbd4cac0a6f899731711ccb6db8f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798544"
---
# <a name="inside-the-core-editor"></a>Uvnitř základní Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Core editor je sada několik komponent, které vám umožní změnit a dotazování textové informace. Pokud jste upravili základní editor pomocí starší verze rozhraní API, můžou dál používat tyto úpravy, které se budou směrovat přes adaptéry editoru. Doporučujeme však, že můžete přizpůsobit vlastní nastavení do nového editoru rozhraní API.  
  
 Tyto oblasti jsou některé důležité aspekty základní editor:  
  
-   Vyrovnávací paměť textu  
  
-   Zobrazení textu  
  
-   Okno kódu  
  
-   Text značky  
  
-   Textový správce  
  
-   Integrace se službami jazyka  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření instance základního editoru pomocí zastaralého rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Obsahuje podrobné pokyny o tom, jak používat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> k vytvoření instance základní editor.  
  
 [Přístup k vyrovnávací paměti textu pomocí zastaralého rozhraní API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Tento článek popisuje role vyrovnávací paměť textu v editoru core, vysvětluje související systémy, které se používají pro přístup k vyrovnávací paměti a poskytuje seznam rozhraní implementovaných objekt vyrovnávací paměti textu <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Události vyrovnávací paměti textu v zastaralém rozhraní API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Obsahuje seznam rozhraní, které se používají pro oznámení události vyrovnávací paměti textu.  
  
 [Postupy: Registrace událostí vyrovnávací paměti textu pomocí zastaralého rozhraní API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Popisuje, jak dokáží události vyrovnávací paměti textu.  
  
 [Použití textového správce k monitorování globálního nastavení](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Tento článek popisuje použití Správce text sdílet informace globální předvoleb se základní součásti editoru a jak přijmout oznámení o události Správce textu.  
  
 [Přístup k textovému zobrazení pomocí zastaralého rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Popisuje roli zobrazení textu v editoru core a obsahuje seznam rozhraní implementovaných <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objektu.  
  
 [Přizpůsobení oken s kódem pomocí zastaralého rozhraní API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Poskytuje informace o způsobu okně kódu slouží k zobrazení textu uzavření, popisuje, jak správce oken kódu slouží k poskytování dekorace do okna kódu a oznámení pro nová zobrazení.  
  
 [Změna nastavení zobrazení pomocí zastaralého rozhraní API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Obsahuje podrobné pokyny o tom, jak vynutit nastavení zobrazení a odebrání nastavení vynucené.  
  
 [Jazykové služby a základní editor](../extensibility/language-services-and-the-core-editor.md)  
 Popisuje vytvoření instance služby jazyka pro ovládací prvek kódu dekorace.  
  
## <a name="related-sections"></a>Související oddíly  
 [Návod: Vytvoření základního editoru a registrace typu souboru editoru](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Obsahuje podrobné pokyny o tom, jak spustit základní editor ze spravovaného kódu.  
  
 [Rozevírací panel](../extensibility/drop-down-bar.md)  
 Tento článek popisuje, jak na panelu rozevíracího seznamu se používá v okně kódu a popisuje rozhraní, které se používají při implementaci panel rozevíracího seznamu.  
  
 [Použití textových značek pomocí zastaralého rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Vysvětluje pojem text značky a jak se používají v základní editor a seznam rozhraní, které se používají k přístupu a správě text značky.  
  
 [Postupy: Přidání standardních textových značek](../extensibility/how-to-add-standard-text-markers.md)  
 Obsahuje podrobné pokyny o tom, jak vytvořit text značky a jak přidat vlastní příkaz do místní nabídky.  
  
 [Postupy: Vytvoření vlastních textových značek](../extensibility/how-to-create-custom-text-markers.md)  
 Obsahuje podrobné pokyny o tom, jak vytvořit vlastní text značky a k poskytování typ značky jako služba.

