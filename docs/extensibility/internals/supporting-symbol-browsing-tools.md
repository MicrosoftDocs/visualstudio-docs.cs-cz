---
title: Podpůrné nástroje pro procházení symbolů | Microsoft Docs
ms.date: 11/04/2016
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
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca171fa75adda3deef5b941852fc3e6c648c84c6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723085"
---
# <a name="supporting-symbol-browsing-tools"></a>Podpůrné nástroje procházení symbolů
Nástroje výsledků hledání symbolů **Prohlížeč objektů**, **zobrazení tříd**, **prohlížeč volání** a **hledání symbolů** poskytují možnosti procházení symbolů v aplikaci Visual Studio. Tyto nástroje zobrazují hierarchické stromové zobrazení symbolů a zobrazují vztahy mezi symboly ve stromové struktuře. Symboly mohou představovat obory názvů, objekty, třídy, členy třídy a další prvky jazyka obsažené v různých součástech. Součástí jsou projekty aplikace Visual Studio, externí .NET Framework komponenty a knihovny typů (. tlb). Další informace naleznete v tématu [zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Knihovny procházení symbolů
 Jako implementátor jazyka můžete roztáhnout možnosti procházení symbolů sady Visual Studio tak, že vytvoříte knihovny, které sledují symboly ve vašich komponentách, a poskytnete seznamy symbolů pro správce objektů sady Visual Studio prostřednictvím sady rozhraní. Knihovna je popsána rozhraním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2>. Správce objektů sady Visual Studio reaguje na požadavky na nová data z nástrojů pro procházení symbolů tím, že získá data z knihoven a organizuje je. Následně naplní nebo aktualizuje nástroje s požadovanými daty. Chcete-li získat odkaz na správce objektů aplikace Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, předejte ID služby <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> do metody `GetService`.

 Každá knihovna se musí zaregistrovat pomocí Správce objektů sady Visual Studio, který shromažďuje informace o všech knihovnách. Chcete-li zaregistrovat knihovnu, zavolejte metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. V závislosti na tom, který nástroj iniciuje požadavek, vyhledá správce objektů sady Visual Studio příslušnou knihovnu a požadavky na data. Mezi knihovnami a správcem objektů [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se přenáší data v seznamech symbolů popsaných rozhraním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>.

 Správce objektů [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zodpovídá za pravidelnou aktualizaci nástrojů pro procházení symbolů tak, aby odrážela nejaktuálnější data obsažená v knihovnách.

 Následující diagram obsahuje ukázku klíčových prvků procesu požadavků/výměny dat mezi knihovnou a správcem objektů aplikace Visual Studio. Rozhraní v diagramu jsou součástí aplikace spravovaného kódu.

 ![Tok dat mezi knihovnou a správcem objektů](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Chcete-li poskytnout seznam symbolů pro správce objektů sady Visual Studio, musíte nejprve zaregistrovat knihovnu pomocí Správce objektů sady Visual Studio voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A>. Po registraci knihovny aplikace Visual Studio Object Manager požaduje určité informace o schopnostech knihovny. Například požaduje příznaky knihovny a podporované kategorie voláním metod <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A>. V určitém okamžiku, když jeden z nástrojů požaduje data z této knihovny, správce objektů požaduje seznam symbolů nejvyšší úrovně voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A>. V reakci knihovna vyrábí seznam symbolů a zpřístupňuje ji správci objektů aplikace Visual Studio prostřednictvím rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2>. Správce objektů [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] určuje, kolik položek se nachází v seznamu voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A>. Všechny následující požadavky se vztahují k dané položce v seznamu a poskytují číslo indexu položky v každé žádosti. Správce objektů sady Visual Studio pokračuje ve shromažďování informací o typu, přístupnosti a dalších vlastnostech položky voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A>.

 Určuje název položky voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> a požádá o informace ikony voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A>. Ikona se zobrazí vlevo od názvu položky a znázorňuje typ položky, přístupnost a další vlastnosti.

 Správce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objektů volá metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> a určí, zda je daná položka seznamu rozšiřitelná a má podřízené položky. Pokud uživatelské rozhraní odešle požadavek na rozbalení prvku, správce objektů vyžádá podřízený seznam symbolů voláním metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A>. Proces pokračuje s různými částmi stromu sestavenými na vyžádání.

> [!NOTE]
> Chcete-li implementovat poskytovatele nativních symbolů kódu, použijte rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>.

## <a name="see-also"></a>Viz také:
- [Postupy: Registrace knihovny pomocí správce objektů](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Postupy: Zveřejnění seznamů symbolů poskytovaných knihovnou správci objektů](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Postupy: Identifikace symbolů v knihovně](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)