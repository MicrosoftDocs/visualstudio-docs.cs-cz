---
title: Vytvoření instance základní Editor pomocí starší verze rozhraní API | Dokumentace Microsoftu
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
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d092994ad66d96a3fe7141cb898c7ef9b811eaf5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765791"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Vytvoření instance základní Editor pomocí starší verze rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor je zodpovědná za funkce jako je například vložení, odstranění, zkopírování a vložení pro úpravy textu. Je kombinací těchto funkcí s těmi, která poskytuje služby jazyka, jako je text barvy, odsazení a dokončování příkazů IntelliSense.  
  
 Můžete vytvořit instanci instance základní editor v jednom ze tří způsobů:  
  
- Explicitní vytvoření instance základní editoru v okně.  
  
- Zadejte objekt factory editoru, který vrátí instance základní editor  
  
- Otevřete soubor z hierarchie projektu.  
  
  Následující části popisují, jak vytvořit instanci editoru pomocí starší verze rozhraní API.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Explicitně otevírání instanci základním editoru  
 Při získávání explicitně instance základní editor:  
  
- Získání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> pro uchování objektu data dokumentu, který právě upravujete.  
  
- Vytvořit řádek orientovaný reprezentace datového objektu dokumentu vytvořením <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> rozhraní z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> rozhraní.  
  
- Nastavte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> jako datový objekt dokumentu pro instanci výchozí implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> rozhraní, pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> metody.  
  
   Hostitele <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> instance v <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> rozhraní pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> metoda.  
  
  V tomto okamžiku zobrazení <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> poskytuje rozhraní představující instanci základní editor.  
  
  Ale to není velmi užitečné instance, protože ho neobsahuje klávesové zkratky, nebo přístup k pokročilým funkcím. Chcete-li získat přístup k klávesové zkratky a další funkce:  
  
- Použití <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metoda, jak přidružit služba jazyka a datový objekt dokumentu, který používá editoru.  
  
- Vytvořit vlastní klávesové zkratky, nebo použít výchozí systémové hodnoty tak, že nastavíte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objekty zobrazení vlastností. Chcete-li to provést, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> metodou <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> vlastnost.  
  
   Chcete-li získat a používat nestandardní klávesové zkratky, vygenerujte pomocí souboru .vsct. Další informace najdete v tématu [tabulky příkazů aplikace Visual Studio (. Vsct) soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Způsob použití objektu pro vytváření editoru získat základní Editor  
 Při implementaci základní editor se objekt pro vytváření editoru pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodu, postupujte podle všech kroků uvedených v předchozí části explicitně hostovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> data dokumentu v objektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objektu.  
  
 Chcete-li zobrazit text, získat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objektu a volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 K zajištění služeb jazyka do editoru, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> metody v rámci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metoda.  
  
 Získat výchozí klávesové zkratky, na rozdíl od předchozí části, použijte příkaz kontextu vrácené <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metoda při získávání základní editor z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody.  
  
 Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metoda vrátí identifikátor GUID stejný příkaz jako textový editor, instance základní editor automaticky získá výchozí klávesové zkratky.  
  
 Obecné informace najdete v tématu [návod: vytvoření základní Editor a registrace typu souboru Editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Uvnitř základní Editor](../extensibility/inside-the-core-editor.md)   
 [Otevření a uložení položek projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Návod: Vytvoření základního editoru a registrace typu souboru editoru](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)

