---
title: Podpora nástroje procházení Symbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08185f64310da610253dc35e69323b17ab0177fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134581"
---
# <a name="supporting-symbol-browsing-tools"></a>Podpůrné nástroje procházení – Symbol
**Objekt prohlížeče**, **zobrazení tříd**, **volání prohlížeče** a **Najít výsledky Symbol** nástroje poskytují symbol procházení funkce v sadě Visual Studio. Tyto nástroje zobrazovat hierarchický strom zobrazení symbolů a vztahů mezi symboly ve stromové struktuře. Symboly může představovat obory názvů, třídy, členy třídy, objektů a další jazyk elementů obsažených v různých součástí. Součásti zahrnují projektů sady Visual Studio, externí [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] součásti a knihovny typů (.tlb). Další informace najdete v tématu [zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Procházení symbol knihovny  
 Jako implementátora jazyk můžete rozšířit možnosti procházení symbol Visual Studio vytvořením knihovny, které sledují symboly v součásti vaší a poskytují seznam symbolů manager objekt sady Visual Studio prostřednictvím sadu rozhraní. Knihovny je popsán <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> rozhraní. Správce objektů sady Visual Studio odpovídá na požadavky na nová data z nástrojů pro procházení symbol získáním dat z knihoven a uspořádání ho. Následně naplní nebo aktualizuje nástroje požadovaná data. Získat odkaz na objekt nástroje Visual Studio manager <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, předat <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> služby ID, který má `GetService` metoda.  
  
 Každé knihovny, musíte zaregistrovat u object manager Visual Studio, který shromažďuje informace na všechny knihovny. Chcete-li zaregistrovat knihovnu, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metoda. V závislosti na tom, který nástroj zahájí žádost správce objektů sady Visual Studio vyhledá příslušnou knihovnu a požadavku na data. Přenáší data mezi v knihovnách a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] správce objektů v seznamech symbolů popsaného <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> rozhraní.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt manager je odpovědná za pravidelně aktualizovat procházení symbol nástroje tak, aby odrážela nejnovější data obsažená v knihovnách.  
  
 Následující diagram obsahuje ukázku klíčové prvky procesu exchange požadavky nebo dat mezi knihovny a nástroje sady Visual Studio objekt manager. Rozhraní v diagramu jsou součástí aplikace spravovaného kódu.  
  
 ![Tok dat mezi knihovnou a správce objekt](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Pokud chcete zadat seznam symbolů pro správce objektu sady Visual Studio, nejprve je nutné zaregistrovat knihovny pomocí sady Visual Studio objekt správce voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metoda. Po registraci knihovny správce objektů sady Visual Studio požadavků určité informace o možnostech knihovny. Například požadavky příznaky knihovny a nepodporuje kategorií volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metody. V určitém okamžiku, když některý z nástrojů vyžaduje data z této knihovny, správce objekt požadavky nejvyšší úrovně seznam symbolů voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metoda. V odpovědi, knihovny sestavuje seznam symbolů a zpřístupní ho do Správce objektu sady Visual Studio prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> rozhraní. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Object manager. Určuje, kolik položek v seznamu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metoda. Všechny tyto požadavky se týkají daná položka v seznamu a zadejte číslo indexu položek v každé žádosti o. Nástroje sady Visual Studio objekt manager pokračuje shromažďovat informace na typ, usnadnění přístupu a další vlastnosti položky voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metoda.  
  
 Určuje název položky voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metoda a požádá o informace ikonu voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metoda. Na ikonu se zobrazí nalevo od názvu položky a znázorňuje typ položky, usnadnění přístupu a další vlastnosti.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Objekt manager volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodu zjistit, zda je rozšíření položky daného seznamu a obsahuje podřízené položky. Pokud uživatelského rozhraní odešle požadavek na rozbalte element, správce objekt požadavky podřízený seznam symbolů voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metoda. Tento proces pokračuje různé části stromu sestavuje na vyžádání.  
  
> [!NOTE]
>  Pro implementaci nativního kódu symbol zprostředkovatele, použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: registrace knihovny pomocí Správce objektu](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Postupy: vystavení seznam symbolů poskytované knihovny ke správci objektů](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Postupy: Identifikace symbolů v knihovně](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)