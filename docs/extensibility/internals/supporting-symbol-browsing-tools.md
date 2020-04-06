---
title: Podpůrné nástroje pro procházení symbolů | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704769"
---
# <a name="supporting-symbol-browsing-tools"></a>Podpůrné nástroje procházení symbolů
**Nástroje Prohlížeč objektů** **, Zobrazení tříd**, Prohlížeč **volání** a Nástroje pro hledání **výsledků symbolů** poskytují možnosti procházení symbolů v sadě Visual Studio. Tyto nástroje zobrazují hierarchické stromové pohledy symbolů a vztahy mezi symboly ve stromu. Symboly mohou představovat obory názvů, objekty, třídy, členy třídy a další prvky jazyka obsažené v různých součástech. Součásti zahrnují projekty sady Visual Studio, externí součásti rozhraní .NET Framework a knihovny typu (.tlb). Další informace naleznete [v tématu Zobrazení struktury kódu](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Knihovny procházení symbolů
 Jako implementátor jazyka můžete rozšířit možnosti procházení symbolů sady Visual Studio vytvořením knihoven, které sledují symboly ve vašich součástech a poskytují seznamy symbolů správci objektů sady Visual Studio prostřednictvím sady rozhraní. Knihovna je popsána <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> rozhraním. Správce objektů sady Visual Studio reaguje na požadavky na nová data z nástrojů pro procházení symbolů získáním dat z knihoven a jejich uspořádáním. Následně naplní nebo aktualizuje nástroje s požadovanými daty. Chcete-li získat odkaz na správce <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>objektů <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> sady Visual Studio, předajte metodě ID služby. `GetService`

 Každá knihovna se musí zaregistrovat u správce objektů sady Visual Studio, který shromažďuje informace o všech knihovnách. Chcete-li zaregistrovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> knihovnu, zavolejte metodu. V závislosti na tom, který nástroj iniciuje požadavek, správce objektů sady Visual Studio najde příslušnou knihovnu a požádá o data. Data putují mezi knihovnami a správcem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objektů v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> seznamech symbolů popsaných rozhraním.

 Správce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objektů je zodpovědný za pravidelné aktualizace nástrojů pro procházení symbolů tak, aby odrážely nejaktuálnější data obsažená v knihovnách.

 Následující diagram obsahuje ukázku klíčových prvků procesu výměny požadavků a dat mezi knihovnou a správcem objektů sady Visual Studio. Rozhraní v diagramu jsou součástí aplikace spravovaného kódu.

 ![Tok dat mezi knihovnou a správcem objektů](../../extensibility/internals/media/callbrowserdiagram.gif "Diagram volání prohlížeče")

 Chcete-li poskytnout seznamy symbolů správci objektů sady Visual Studio, musíte nejprve <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> zaregistrovat knihovnu u správce objektů sady Visual Studio voláním metody. Po registraci knihovny visual studio správce objektů požaduje určité informace o možnostech knihovny. Například požaduje příznaky knihovny a podporované kategorie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> voláním metody a. V určitém okamžiku, když jeden z nástrojů požaduje data z této knihovny, správce objektů <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> požaduje seznam symbolů nejvyšší úrovně voláním metody. V reakci na to knihovna vyrobí seznam symbolů a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> zpřístupní jej správce objektů sady Visual Studio prostřednictvím rozhraní. Správce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objektů určí, kolik položek je v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> seznamu voláním metody. Všechny následující požadavky se vztahují k dané položce v seznamu a zadávají číslo indexu položky v každé žádosti. Visual Studio správce objektů pokračuje shromažďovat informace o typu, usnadnění přístupu a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> další vlastnosti položky voláním metody.

 Určuje název položky voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> metody a požaduje informace o ikonách voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> metody. Ikona se zobrazí vlevo od názvu položky a zobrazuje typ položky, usnadnění přístupu a další vlastnosti.

 Správce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objektů volá <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> metodu k určení, zda je daná položka seznamu rozbalitelná a má podřízené položky. Pokud uI odešle požadavek na rozbalení prvku, správce objektů požaduje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> podřízený seznam symbolů voláním metody. Proces pokračuje s různými částmi stromu, které jsou postaveny na vyžádání.

> [!NOTE]
> Chcete-li implementovat poskytovatele symbolu nativního <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> kódu, použijte rozhraní a. <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2>

## <a name="see-also"></a>Viz také
- [Postupy: Registrace knihovny pomocí správce objektů](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Postupy: Zveřejnění seznamů symbolů poskytovaných knihovnou správci objektů](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Postupy: Identifikace symbolů v knihovně](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
