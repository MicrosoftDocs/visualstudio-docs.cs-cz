---
title: Přizpůsobení oken kódu pomocí starší verze rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556114"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Přizpůsobení oken s kódem pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno kódu je objekt okna dokumentu, který podporuje jedno nebo více textových zobrazení. Přesné funkce okna kódu závisí na přidružené jazykové službě. V režimu MDI (Multiple Document Interface) je okno Code podřízeného rámce MDI.  
  
 Okna Code jsou řízena jazykovými službami a každá služba jazyka může poskytovat vlastní správce oken kódu. To umožňuje, aby služba jazyka přidala vlastní Doplňky do okna kódu, jako jsou vlnovky, barvy a další. Další informace o tom, jak vytvořit základní okno, najdete v tématu [Vytvoření základního editoru pomocí starší verze rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Okno kódu je <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objekt, který má textové zobrazení a jakékoli doplňky v objektu. Při vytváření okna kódu během vytváření instance základního editoru může vaše jazyková služba připojit <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> k oknu Code (kód), jak je znázorněno na následujícím obrázku.  
  
 ![Obrázek CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Okno kódu  
  
 Jazyková služba implementuje správce oken kódu a zodpovídá za správu doplňků, jako je například rozevírací seznam. Okno Code volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> metodu při inicializaci okna kódu. Když je toto volání vytvořeno, služba jazyka může přidat rozevírací panel nebo panel tlačítek ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> ) do okna kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 `Customizing Code Windows by Using the Legacy API`  
 Vysvětluje, jak přizpůsobit okna kódu pomocí starší verze rozhraní API.  
  
 [Postupy: Hostování editoru v jiném editoru](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Vysvětluje, jak hostovat druhý Editor v okně editoru.  
  
 [Postupy: Aktivace událostí, když editor ztratí fokus](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Vysvětluje, jak připojit zobrazení dokumentu k datovému objektu dokumentu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Vytvoření instance základního editoru pomocí starší verze rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Přístup k textovému zobrazení pomocí zastaralého rozhraní API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
