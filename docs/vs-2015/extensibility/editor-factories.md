---
title: Objekty pro vytváření editorů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197754"
---
# <a name="editor-factories"></a>Objekty pro vytváření editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Objekt pro vytváření editoru vytvoří objekty editoru a vloží je do rámce okna, označované jako fyzické zobrazení. Vytvoří data dokumentu a objekty zobrazení dokumentu, které jsou nezbytné pro vytváření editorů a návrhářů. Objekt pro vytváření editoru je nutný k vytvoření základního editoru sady Visual Studio a libovolného standardního editoru. Vlastní editor lze také volitelně vytvořit pomocí objektu pro vytváření editoru.  
  
 Vytvořte objekt pro vytváření editoru implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní. Následující příklad ukazuje, jak implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> pro vytvoření objektu pro vytváření editoru:  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 Při prvním otevření typu souboru, který zpracovává tento editor, je načten Editor. Můžete zvolit, že chcete otevřít buď konkrétní editor, nebo výchozí editor. Pokud vyberete výchozí editor, integrované vývojové prostředí (IDE) určí správný editor pro otevření a pak ho otevře. Další informace naleznete v tématu [určení, který Editor otevře soubor v projektu](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="registering-editor-factories"></a>Registrují se objekty pro vytváření editorů.  
 Předtím, než budete moci použít editor, který jste vytvořili, musíte nejprve zaregistrovat informace o tom, včetně přípon souborů, které může zpracovat.  
  
 Pokud je vaše sada VSPackage napsaná ve spravovaném kódu, můžete <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> k registraci objektu pro vytváření editoru po načtení sady VSPackage použít metodu. Pokud je váš VSPackage napsán v nespravovaném kódu, je nutné zaregistrovat objekt pro vytváření editoru pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> služby.  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>Registrace objektu pro vytváření editoru pomocí spravovaného kódu  
 Je nutné zaregistrovat objekt pro vytváření editoru v `Initialize` metodě VSPackage. Nejprve zavolejte `base.Initialize` a potom zavolejte <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> pro každý objekt pro vytváření Editor  
  
 Ve spravovaném kódu není nutné odregistrovat objekt pro vytváření editoru, protože ho rozhraní VSPackage zpracuje za vás. Také Pokud váš objekt pro vytváření Editor implementuje <xref:System.IDisposable> , je automaticky uvolněn při zrušení registrace.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>Registrace objektu pro vytváření editoru pomocí nespravovaného kódu  
 V <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementaci pro balíček editoru použijte `QueryService` metodu pro volání `SVsRegisterEditors` . Tím se vrátí ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> . Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodu předáním implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní. Musíte mplementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> do samostatné třídy.  
  
## <a name="the-editor-factory-registration-process"></a>Proces registrace do továrního umístění editoru  
 K následujícímu procesu dochází, když Visual Studio načte váš editor pomocí objektu pro vytváření editoru:  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Systém projektu volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .  
  
2. Tato metoda vrátí objekt pro vytváření editoru. Sada Visual Studio zpozdí načítání balíčku editoru, ale do té doby, než systém projektu skutečně potřebuje Editor.  
  
3. Pokud systém projektu potřebuje editor, volání sady Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , specializované metody, která vrací zobrazení dokumentu i datové objekty dokumentu.  
  
4. Pokud aplikace Visual Studio zavolá do svého objektu pro vytváření editoru pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> vrátí objekt data dokumentu a objekt zobrazení dokumentu, aplikace Visual Studio potom vytvoří okno dokumentu, umístí do něj objekt zobrazení dokumentu a vytvoří položku do tabulky spuštěných dokumentů (RDT) pro objekt data dokumentu.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [Spuštění tabulky dokumentů](../extensibility/internals/running-document-table.md)
