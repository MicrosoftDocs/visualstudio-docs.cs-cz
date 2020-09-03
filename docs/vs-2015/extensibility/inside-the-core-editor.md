---
title: Uvnitř základního editoru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203957"
---
# <a name="inside-the-core-editor"></a>Práce v základním editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Základní editor je sada několika komponent, které umožňují upravovat a dotazovat se na textové informace. Pokud jste upravili základní editor pomocí starší verze rozhraní API, můžete tato přizpůsobení používat i v případě, že budou směrovány prostřednictvím adaptérů editoru. Doporučuje se ale, abyste přizpůsobili vlastní nastavení editoru rozhraní API pro nové editory.  
  
 V následujících oblastech jsou některé důležité aspekty základního editoru:  
  
- Vyrovnávací paměť textu  
  
- Textové zobrazení  
  
- Okno kódu  
  
- Textové značky  
  
- Správce textu  
  
- Integrace s jazykovými službami  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření instance základního editoru pomocí zastaralého rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Poskytuje podrobné pokyny, jak použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> k vytvoření instance základního editoru.  
  
 [Přístup k vyrovnávací paměti textu pomocí zastaralého rozhraní API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Popisuje roli vyrovnávací paměti textu v základním editoru, vysvětluje přidružené systémy, které se používají pro přístup k vyrovnávací paměti, a poskytuje seznam rozhraní implementovaných objektem textové vyrovnávací paměti <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 [Události vyrovnávací paměti textu v zastaralém rozhraní API](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Poskytuje seznam rozhraní, která se používají pro oznamování událostí vyrovnávací paměti textu.  
  
 [Postupy: Registrace událostí vyrovnávací paměti textu pomocí zastaralého rozhraní API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Popisuje, jak lze poradit s událostmi pro ukládání textu do vyrovnávací paměti.  
  
 [Použití textového správce k monitorování globálního nastavení](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Popisuje, jak se správce textu používá ke sdílení globálních informací o preferencích s komponentami základního editoru a jak dostávat oznámení o událostech nástroje text Manager.  
  
 [Přístup k textovému zobrazení pomocí zastaralého rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Popisuje roli zobrazení textu v základním editoru a obsahuje seznam rozhraní implementovaných <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objektem.  
  
 [Přizpůsobení oken s kódem pomocí zastaralého rozhraní API](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Obsahuje informace o tom, jak se používá okno kódu k uzavření textového zobrazení, popisuje, jak se správce oken kódu používá k poskytnutí dekorace v okně kódu a poskytuje oznámení o nových zobrazeních.  
  
 [Změna nastavení zobrazení pomocí zastaralého rozhraní API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Poskytuje podrobné pokyny, jak vynutit nastavení zobrazení a jak odebrat vynucená nastavení.  
  
 [Jazykové služby a základní editor](../extensibility/language-services-and-the-core-editor.md)  
 Popisuje vytváření instancí jazykové služby pro řízení dekorace kódu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Návod: Vytvoření základního editoru a registrace typu souboru editoru](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Poskytuje podrobné pokyny, jak spustit základní editor ze spravovaného kódu.  
  
 [Rozevírací panel](../extensibility/drop-down-bar.md)  
 Popisuje, jak se rozevírací panel používá v okně kódu a popisuje rozhraní, která se používají při implementaci rozevíracího seznamu.  
  
 [Použití textových značek pomocí zastaralého rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Vysvětluje koncept značek textu a jejich použití v základním editoru a uvádí rozhraní, která se používají pro přístup k textovým značkám a jejich správu.  
  
 [Postupy: Přidání standardních textových značek](../extensibility/how-to-add-standard-text-markers.md)  
 Poskytuje podrobné pokyny, jak vytvořit značku textu a jak přidat vlastní příkaz do místní nabídky.  
  
 [Postupy: Vytvoření vlastních textových značek](../extensibility/how-to-create-custom-text-markers.md)  
 Obsahuje podrobné pokyny, jak vytvořit vlastní značku textu a jak zadat typ značky jako službu.
