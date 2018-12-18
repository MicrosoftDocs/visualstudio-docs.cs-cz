---
title: 'Kontrolní seznam: Vytvoření nových typů projektů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3da952e22515b48f06fdc50b34b2eb49f5709cc2
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370572"
---
# <a name="checklist-create-new-project-types"></a>Kontrolní seznam: Vytvoření nových typů projektů
Je třeba provést několik úloh, chcete-li vytvořit nový typ projektu. Následující kontrolní seznam obsahuje příručky s těmito úlohami:  
  
1.  Navrhněte funkci pro nový typ projektu. Další informace najdete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Určí, editory, které se používají pro kód a další prvky projektu. Můžete použít základní nebo standardní editory, nebo můžete vytvořit a použít editoru pro konkrétní projekt. Další informace najdete v tématu [vytváření vlastních editorů a návrhářů](../../extensibility/creating-custom-editors-and-designers.md) a [postupy: otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Určete úroveň vaší položky projektu budou mít v účasti **zobrazení tříd** a **prohlížeče objektů**. Další informace najdete v tématu [podpůrné nástroje procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Odvozovat nové třídy založené na rozhodnutí o návrhu, které jste provedli dříve pro váš projekt a položky projektu.  
  
5.  Napsání kódu pro následující typ součásti projektu:  
  
    -   Objekt factory projektu, ke správě vytváření nových projektů a otevření stávajících projektů. Další informace najdete v tématu [vytvoření instancí projektu pomocí objektů pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Zpracování příkazu a hierarchie projektu. Další informace najdete v tématu [HierUtil7 použití projektu třídy k implementaci typu projektu (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md), [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)a [ MenuCommands vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Správa položek projektů, včetně přidání projekt tak, aby **nový projekt** dialogové okno. Další informace najdete v tématu [přidat projekt a šablony položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md) a [registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Trvalost stavu projektu a jednotlivé položky. Další informace najdete v tématu [otevřít a uložit položky projektu](../../extensibility/internals/opening-and-saving-project-items.md). Trvalost informace o řešení, najdete v části [řešení](../../extensibility/internals/solutions.md).  
  
    -   Nezávislé na konfiguraci vlastnosti k zobrazení v okně Vlastnosti. Další informace najdete v tématu [rozšířit vlastnosti](../../extensibility/internals/extending-properties.md).  
  
    -   Vlastnosti konfigurace projektu, jak je implementován v stránky vlastností k zobrazení vlastností závislé na konfiguraci. Další informace najdete v tématu [spravovat možnosti konfigurace](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Vytváření výčtu výstupy pro nasazení. Další informace najdete v tématu [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Projekt po spuštění služby. Další informace najdete v tématu [prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md) a [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objekty a třídy odvozené od `IDispatch`, která je dostupná pro automatizaci.  
  
    -   Tabulky příkazů XML (*.vsct*) soubory. Další informace najdete v tématu [soubory tabulky (.vsct) příkazů sady Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testování, ladění a spusťte váš typ projektu.  
  
7.  Zobrazení projektu v **projektu** karty **přidat odkaz** dialogové okno tak, že nastavíte `VARIANT_TRUE` hodnotu `VSHPROPID_ShowProjInSolutionPage`. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Vytvořte Microsoft Installer (*MSI*) soubor pro instalaci vašich rozšíření VSPackages. Další informace najdete v tématu [instalace balíčků VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrace typu projektu](../../extensibility/internals/registering-a-project-type.md), a [rozšíření VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Viz také:  
 [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Kdy vytvořit typy projektů](../../extensibility/internals/when-to-create-project-types.md)   
 [Vytvořit typy projektů](../../extensibility/internals/creating-project-types.md)