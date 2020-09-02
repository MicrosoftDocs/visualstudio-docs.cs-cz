---
title: Podpůrné nástroje pro procházení symbolů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
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
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b85e8bf500364587af4c3891d7d39f069af9953
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815663"
---
# <a name="supporting-symbol-browsing-tools"></a>Podpůrné nástroje procházení symbolů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nástroje výsledků hledání symbolů **Prohlížeč objektů**, **zobrazení tříd**, **prohlížeč volání** a **hledání symbolů** poskytují možnosti procházení symbolů v aplikaci Visual Studio. Tyto nástroje zobrazují hierarchické stromové zobrazení symbolů a zobrazují vztahy mezi symboly ve stromové struktuře. Symboly mohou představovat obory názvů, objekty, třídy, členy třídy a další prvky jazyka obsažené v různých součástech. Součástí jsou projekty aplikace Visual Studio, externí [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] komponenty a knihovny typů (. tlb). Další informace naleznete v tématu [zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).  
  
## <a name="symbol-browsing-libraries"></a>Knihovny procházení symbolů  
 Jako implementátor jazyka můžete roztáhnout možnosti procházení symbolů sady Visual Studio tak, že vytvoříte knihovny, které sledují symboly ve vašich komponentách, a poskytnete seznamy symbolů pro správce objektů sady Visual Studio prostřednictvím sady rozhraní. Knihovna je popsána v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> rozhraní. Správce objektů sady Visual Studio reaguje na požadavky na nová data z nástrojů pro procházení symbolů tím, že získá data z knihoven a organizuje je. Následně naplní nebo aktualizuje nástroje s požadovanými daty. Chcete-li získat odkaz na správce objektů aplikace Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> předejte <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID služby `GetService` metodě.  
  
 Každá knihovna se musí zaregistrovat pomocí Správce objektů sady Visual Studio, který shromažďuje informace o všech knihovnách. Chcete-li zaregistrovat knihovnu, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodu. V závislosti na tom, který nástroj iniciuje požadavek, vyhledá správce objektů sady Visual Studio příslušnou knihovnu a požadavky na data. Přenášená data mezi knihovnami a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] správcem objektů v seznamech symbolů popsaných v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> rozhraní.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Správce objektů zodpovídá za pravidelnou aktualizaci nástrojů pro procházení symbolů, aby odrážel nejaktuálnější data obsažená v knihovnách.  
  
 Následující diagram obsahuje ukázku klíčových prvků procesu požadavků/výměny dat mezi knihovnou a správcem objektů aplikace Visual Studio. Rozhraní v diagramu jsou součástí aplikace spravovaného kódu.  
  
 ![Tok dat mezi knihovnou a správcem objektů](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Chcete-li poskytnout seznam symbolů pro správce objektů sady Visual Studio, musíte nejprve zaregistrovat knihovnu pomocí Správce objektů sady Visual Studio voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody. Po registraci knihovny aplikace Visual Studio Object Manager požaduje určité informace o schopnostech knihovny. Například požaduje příznaky knihovny a podporované kategorie voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metod a. V určitém okamžiku, když jeden z nástrojů požaduje data z této knihovny, správce objektů požaduje seznam symbolů na nejvyšší úrovni voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metody. V reakci knihovna vyrábí seznam symbolů a zpřístupňuje je správci objektů aplikace Visual Studio prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> rozhraní. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Správce objektů určuje, kolik položek je v seznamu, voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metody. Všechny následující požadavky se vztahují k dané položce v seznamu a poskytují číslo indexu položky v každé žádosti. Správce objektů sady Visual Studio pokračuje ve shromažďování informací o typu, přístupnosti a dalších vlastnostech položky voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metody.  
  
 Určuje název položky voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metody a požádá o informace ikony voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metody. Ikona se zobrazí vlevo od názvu položky a znázorňuje typ položky, přístupnost a další vlastnosti.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Správce objektů volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodu k určení, zda je daná položka seznamu rozšiřitelná a má podřízené položky. Pokud uživatelské rozhraní odešle požadavek na rozšíření elementu, správce objektů vyžádá podřízený seznam symbolů voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metody. Proces pokračuje s různými částmi stromu sestavenými na vyžádání.  
  
> [!NOTE]
> Chcete-li implementovat poskytovatele nativních symbolů kódu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> rozhraní a.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: registrace knihovny pomocí Správce objektů](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Postupy: vystavení seznamů symbolů poskytovaných knihovnou správci objektů](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Postupy: Identifikace symbolů v knihovně](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
