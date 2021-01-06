---
title: Podpůrné nástroje Symbol-Browsing | Microsoft Docs
description: Visual Studio poskytuje možnosti procházení symbolů v aplikaci Visual Studio. Naučte se, jak tyto možnosti rozšíříte pomocí knihoven pro symboly ve vašich komponentách.
ms.custom: SEO-VS-2020
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0adf586831e21c2448931215d4ef4a89d16a63f8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876438"
---
# <a name="supporting-symbol-browsing-tools"></a>Podpůrné nástroje procházení symbolů
Nástroje výsledků hledání symbolů **Prohlížeč objektů**, **zobrazení tříd**, **prohlížeč volání** a **hledání symbolů** poskytují možnosti procházení symbolů v aplikaci Visual Studio. Tyto nástroje zobrazují hierarchické stromové zobrazení symbolů a zobrazují vztahy mezi symboly ve stromové struktuře. Symboly mohou představovat obory názvů, objekty, třídy, členy třídy a další prvky jazyka obsažené v různých součástech. Součástí jsou projekty aplikace Visual Studio, externí .NET Framework komponenty a knihovny typů (. tlb). Další informace naleznete v tématu [zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Knihovny Symbol-Browsing
 Jako implementátor jazyka můžete roztáhnout možnosti procházení symbolů sady Visual Studio tak, že vytvoříte knihovny, které sledují symboly ve vašich komponentách, a poskytnete seznamy symbolů pro správce objektů sady Visual Studio prostřednictvím sady rozhraní. Knihovna je popsána v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> rozhraní. Správce objektů sady Visual Studio reaguje na požadavky na nová data z nástrojů pro procházení symbolů tím, že získá data z knihoven a organizuje je. Následně naplní nebo aktualizuje nástroje s požadovanými daty. Chcete-li získat odkaz na správce objektů aplikace Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> předejte <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID služby `GetService` metodě.

 Každá knihovna se musí zaregistrovat pomocí Správce objektů sady Visual Studio, který shromažďuje informace o všech knihovnách. Chcete-li zaregistrovat knihovnu, zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodu. V závislosti na tom, který nástroj iniciuje požadavek, vyhledá správce objektů sady Visual Studio příslušnou knihovnu a požadavky na data. Přenášená data mezi knihovnami a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] správcem objektů v seznamech symbolů popsaných v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> rozhraní.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Správce objektů zodpovídá za pravidelnou aktualizaci nástrojů pro procházení symbolů, aby odrážel nejaktuálnější data obsažená v knihovnách.

 Následující diagram obsahuje ukázku klíčových prvků procesu požadavků/výměny dat mezi knihovnou a správcem objektů aplikace Visual Studio. Rozhraní v diagramu jsou součástí aplikace spravovaného kódu.

 ![Tok dat mezi knihovnou a správcem objektů](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Chcete-li poskytnout seznam symbolů pro správce objektů sady Visual Studio, musíte nejprve zaregistrovat knihovnu pomocí Správce objektů sady Visual Studio voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metody. Po registraci knihovny aplikace Visual Studio Object Manager požaduje určité informace o schopnostech knihovny. Například požaduje příznaky knihovny a podporované kategorie voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> metod a. V určitém okamžiku, když jeden z nástrojů požaduje data z této knihovny, správce objektů požaduje seznam symbolů na nejvyšší úrovni voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> metody. V reakci knihovna vyrábí seznam symbolů a zpřístupňuje je správci objektů aplikace Visual Studio prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> rozhraní. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Správce objektů určuje, kolik položek je v seznamu, voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> metody. Všechny následující požadavky se vztahují k dané položce v seznamu a poskytují číslo indexu položky v každé žádosti. Správce objektů sady Visual Studio pokračuje ve shromažďování informací o typu, přístupnosti a dalších vlastnostech položky voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> metody.

 Určuje název položky voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metody a požádá o informace ikony voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metody. Ikona se zobrazí vlevo od názvu položky a znázorňuje typ položky, přístupnost a další vlastnosti.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Správce objektů volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodu k určení, zda je daná položka seznamu rozšiřitelná a má podřízené položky. Pokud uživatelské rozhraní odešle požadavek na rozšíření elementu, správce objektů vyžádá podřízený seznam symbolů voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> metody. Proces pokračuje s různými částmi stromu sestavenými na vyžádání.

> [!NOTE]
> Chcete-li implementovat poskytovatele nativních symbolů kódu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> rozhraní a.

## <a name="see-also"></a>Viz také
- [Postupy: Registrace knihovny pomocí správce objektů](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Postupy: Zveřejnění seznamů symbolů poskytovaných knihovnou správci objektů](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Postupy: Identifikace symbolů v knihovně](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
