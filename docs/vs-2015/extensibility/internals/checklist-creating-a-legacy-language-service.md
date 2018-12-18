---
title: 'Kontrolní seznam: Vytvoření služby starší verze jazyka | Dokumentace Microsoftu'
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
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 330270b34d55e88c883b9d8a6270b4abad02d9c1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782983"
---
# <a name="checklist-creating-a-legacy-language-service"></a>Kontrolní seznam: Vytvoření služby starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující kontrolní seznam obsahuje souhrn základní kroky nezbytné k vytvoření služby pro jazyk [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] základní editor. K integraci služby jazyka do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], je nutné vytvořit vyhodnocovací filtr výrazů ladění. Další informace najdete v tématu [zápis vyhodnocovací filtr výrazů CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) v [rozšiřitelnosti ladicího programu sady Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Kroky pro vytvoření služby jazyka  
  
1.  Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> rozhraní.  
  
    -   V VSPackage, implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> rozhraní k zajištění služeb jazyka.  
  
    -   Zpřístupnění služby jazyka pro integrované vývojové prostředí (IDE) v vaše <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementace.  
  
2.  Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> rozhraní ve třídě služby hlavní jazyk.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Výchozí bod interakce mezi základní editor a služba jazyka je rozhraní.  
  
### <a name="optional-features"></a>Volitelné funkce  
 Následující funkce jsou volitelné a je možné implementovat v libovolném pořadí. Tyto funkce zvýšit funkce služby jazyka.  
  
- Barevné zvýrazňování syntaxe  
  
   Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní. Implementace tohoto rozhraní by měl analyzátor informace mají vracet informace o příslušné barvu.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Vrátí metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní. Vytvoří instanci samostatné colorizer pro každou textovou vyrovnávací paměť, takže by měla implementovat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> rozhraní samostatně. Další informace najdete v tématu [barevné zvýraznění syntaxe ve službě starší verze jazyka](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
- Okno kódu  
  
   Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> rozhraní pro povolení služby jazyka pro příjem oznámení o vytvoření nového okna kódu.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Vrátí metoda <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> rozhraní. Služba jazyka můžete přidat zvláštní uživatelského rozhraní do okna kódu v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Služba jazyka můžete také provést žádné speciální zpracování, jako je například přidávání filtr zobrazení textu v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
- Filtr zobrazení textu  
  
   Kvůli dokončení příkazu IntelliSense ve službě jazyka musí zachytit některé příkazy, které by jinak zpracovat zobrazení textu. Aby se zachytily tyto příkazy, proveďte následující kroky:  
  
  - Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> se účastnit řetězec a popisovač editor příkazů.  
  
  - Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metoda a předejte jí váš <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementace.  
  
  - Volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> metoda při odpojení ze zobrazení tak, aby tyto příkazy jsou již předat vám.  
  
    Příkazy, které musí být zpracován závislými na službách, které jsou k dispozici. Další informace najdete v tématu [důležité příkazy pro filtry služby jazyka](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
  > [!NOTE]
  >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Rozhraní musí být implementováno na stejný objekt jako <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní.  
  
- Dokončování příkazů  
  
   Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> rozhraní.  
  
   Podporují dokončení příkaz – příkaz (to znamená, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) a volat <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metoda ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní předání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> rozhraní. Další informace najdete v tématu [dokončování příkazů ve službě starší verze jazyka](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
- Tipy – metoda  
  
   Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní poskytující data pro okno tipů metody.  
  
   Nainstalujte do filtru textového zobrazení k odpovídajícím způsobem, zpracovat příkazy, abyste věděli, kdy se má zobrazit okno s metoda datový tip. Další informace najdete v tématu [informace o parametrech ve službě starší verze jazyka](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
- Označování chyb  
  
   Implementace <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní.  
  
   Vytvořit chybu značky objekty, které implementují <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní a volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní objektu značky chyb.  
  
   Každá značka chyby obvykle spravuje položky v okně Seznam úloh.  
  
- Položky seznamu úkolů  
  
   Implementace zadání třídy položky úkolů <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> rozhraní.  
  
   Implementovat, poskytují třídy úloha zprostředkovatele <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> rozhraní.  
  
   Implementace zadání třídy výčtu úloh <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> rozhraní.  
  
   Registrace poskytovatele úloh se seznamem úkolů <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> metody.  
  
   Získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> rozhraní voláním jazyková služba poskytovatele služeb s identifikátor GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
   Vytvoření objektů položku úkolu a volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> metoda ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> rozhraní, když jsou nové nebo aktualizovat úkoly.  
  
- Položky úkolu komentář  
  
   Použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> rozhraní a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> rozhraní pro získání komentáře úkolu tokenů.  
  
   Získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> rozhraní z <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> služby.  
  
   Získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> rozhraní z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> metody.  
  
   Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> rozhraní pro naslouchání změn v seznamu tokenů.  
  
- Sbalování  
  
   Existuje několik možností pro podporu osnovy. Například můžete podporovat **sbalit do definic** příkazu, řídit editor osnovy oblastí ani nepodporuje spravovanými klientské oblasti. Další informace najdete v tématu [jak: Zadejte rozšířit sbalování podporu ve službě starší verze jazyka](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
- Registrace služby jazyka  
  
   Další informace o postupu při registraci služba jazyka naleznete v tématu [registrace služby starší verze jazyka](../../extensibility/internals/registering-a-legacy-language-service2.md) a [Správa balíčky VSPackages](../../extensibility/managing-vspackages.md).  
  
- Kontextová nápověda  
  
   Poskytuje kontext k editoru v jednom z následujících způsobů:  
  
  -   Poskytuje kontext pro text značky implementací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> rozhraní.  
  
  Zadejte všechny uživatelský kontext implementací <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Vývoj služby starší verze jazyka](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Zápis pro vyhodnocovač výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

