---
title: Vytvoření instance základního editoru pomocí starší verze rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203912"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Vytvoření instance základního editoru pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor zodpovídá za funkce pro úpravu textu, jako je vložení, odstranění, kopírování a vložení. Kombinuje tyto funkce s funkcemi poskytovanými jazykovými službami, jako jsou barvy textu, odsazení a dokončování příkazů IntelliSense.  
  
 Instanci základního editoru lze vytvořit jedním ze tří způsobů:  
  
- Explicitní vytvoření instance základního editoru v okně.  
  
- Poskytněte objekt pro vytváření editoru, který vrací instanci základního editoru.  
  
- Otevřete soubor z hierarchie projektu.  
  
  Následující části popisují, jak používat starší rozhraní API k vytvoření instance editoru.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Explicitní otevření základní instance editoru  
 Při explicitním získání instance základního editoru:  
  
- Získejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pro uchování upravovaného datového objektu dokumentu.  
  
- Vytvořte datovou reprezentaci objektu dat dokumentu vytvořením <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> rozhraní z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> rozhraní.  
  
- Nastavte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> jako datový objekt dokumentu pro instanci výchozí implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> rozhraní pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> metody.  
  
   Hostování <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> instance v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> rozhraní pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> metody.  
  
  V tomto okamžiku zobrazení <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> rozhraní poskytuje okno, které obsahuje instanci základního editoru.  
  
  Nejedná se však o velmi užitečnou instanci, protože nemá klávesové zkratky ani přístup k pokročilým funkcím. Získání přístupu k klávesovým zkratkám a pokročilým funkcím:  
  
- Použijte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodu k přidružení jazykové služby a datového objektu dokumentu, který používá editor.  
  
- Buď vytvořte vlastní klávesové zkratky, nebo použijte výchozí nastavení systému nastavením <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> vlastností zobrazení objektů. Chcete-li to provést, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> metodu s <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> vlastností.  
  
   Chcete-li získat a použít nestandardní klávesové zkratky, vygenerujte je pomocí souboru. vsct. Další informace naleznete v tématu [tabulka příkazů sady Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Získání základního editoru pomocí objektu pro vytváření editoru  
 Při implementaci základního editoru s objektem pro vytváření editoru pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody použijte všechny kroky popsané v předchozí části k explicitnímu hostování aplikace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> datového objektu dokumentu v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objektu.  
  
 Chcete-li zobrazit text, Získejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objektu a zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodu.  
  
 Pro poskytnutí jazykové služby editoru volejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metodu v rámci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Chcete-li získat výchozí klávesové zkratky, na rozdíl od předchozí části, použijte kontext příkazu vrácený <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodou při získávání základního editoru z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Metoda vrátí stejný identifikátor GUID příkazu jako textový editor, instance základního editoru automaticky získá výchozí klávesové zkratky.  
  
 Obecné informace najdete v tématu [Návod: Vytvoření základního editoru a registrace typu souboru editoru](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Uvnitř základního editoru](../extensibility/inside-the-core-editor.md)   
 [Otevírání a ukládání položek projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Návod: Vytvoření základního editoru a registrace typu souboru editoru](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)
