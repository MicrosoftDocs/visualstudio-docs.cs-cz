---
title: Objekty pro vytváření editoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f4dc0eca2c74161abb9cc4afe3917a160a18422
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933128"
---
# <a name="editor-factories"></a>Objekty pro vytváření editoru
Objekt pro vytváření editoru vytvoří objekty editoru a umístí je do okna rámce, označované jako fyzické zobrazení. Vytvoří data dokumentu a dokument zobrazit objekty, které jsou potřebné k vytvoření editorech a návrhářích. Objekt pro vytváření editoru je potřeba vytvořit základní editor sady Visual Studio a všechny standardní editor. Vlastní editor lze vytvořit také v případě potřeby pomocí objektu pro vytváření editoru.  
  
 Vytvoříte objekt pro vytváření editoru implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní. Následující příklad ukazuje, jak implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> pro vytváření editoru:  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 Editor je načteno při prvním otevření souboru typu zpracovat tento editor. Můžete otevřít konkrétní editoru nebo editoru výchozí. Pokud vyberete výchozí editor, integrované vývojové prostředí (IDE) určuje správný editor otevřít a pak ho otevře. Další informace najdete v tématu [určit, které editor otevře soubor v projektu](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).  
  
## <a name="register-editor-factories"></a>Zaregistrovat objekty pro vytváření editoru  
 Předtím, než je můžete použít editor, který jste vytvořili, nejprve musíte zaregistrovat informace o tom, včetně přípony souborů, které dokáže zpracovat.  
  
 Pokud vaše VSPackage je zapsána ve spravovaném kódu, můžete použít metodu Managed Package Framework (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> zaregistrovat objekt pro vytváření editoru po načtení vašeho balíčku VSPackage. Pokud je vaše VSPackage napsanou v nespravovaném kódu, pak musí zaregistrovat objekt pro vytváření editoru pomocí <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> služby.  
  
### <a name="register-an-editor-factory-by-using-managed-code"></a>Zaregistrovat objekt pro vytváření editoru pomocí spravovaného kódu  
 Objekt pro vytváření editoru musí registrovat v vašeho balíčku VSPackage `Initialize` metody. Nejprve volat `base.Initialize`a pak vyvolejte <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> pro každý objekt factory editoru  
  
 Ve spravovaném kódu není nutné zrušit registraci objektu pro vytváření editoru, protože sady VSPackage to postarají za vás. Také pokud objekt pro vytváření editoru implementuje <xref:System.IDisposable>, je automaticky odstraněn, když se registrace.  
  
### <a name="register-an-editor-factory-by-using-unmanaged-code"></a>Zaregistrovat objekt pro vytváření editoru pomocí nespravovaného kódu  
 V <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementace editor balíčku, použijte `QueryService` metodu chce volat `SVsRegisterEditors`. To vrací ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> metodu předáním vaši implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní. Je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> v samostatné třídě.  
  
## <a name="the-editor-factory-registration-process"></a>Proces registrace factory editoru  
 Když Visual Studio načte objekt pro vytváření editoru pomocí editoru se spustí následující proces:  
  
1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektu systémových volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
2. Tato metoda vrátí objekt pro vytváření editoru. Načítání balíčku editoru, ale dokud bude systém projektu skutečně potřebuje editoru sady Visual Studio zpoždění.  
  
3. Když bude systém projektu potřebuje editoru, Visual Studio volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, specializované metodu, která vrátí zobrazení dokumentu a dokument datové objekty.  
  
4. Pokud volání pomocí sady Visual Studio pomocí objekt pro vytváření editoru <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> vrátit datový objekt dokumentu a objekt zobrazení dokument, Visual Studio pak vytvoří okno dokumentu, umístí objekt zobrazení dokumentu a vytvoří položku do spuštěného dokumentu Tabulka (r...) pro datový objekt dokumentu.  
  
## <a name="see-also"></a>Viz také:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [spuštění tabulky dokumentů](../extensibility/internals/running-document-table.md)