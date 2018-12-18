---
title: 'Kontrolní seznam: Vytvoření nových typů projektů | Dokumentace Microsoftu'
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
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90b48f5969a422ab9d211bb56900cf1b3b41a78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737360"
---
# <a name="checklist-creating-new-project-types"></a>Kontrolní seznam: Vytvoření nových typů projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Je třeba provést několik úloh, chcete-li vytvořit nový typ projektu. Následující kontrolní seznam obsahuje příručky s těmito úlohami.  
  
1.  Navrhněte funkci pro nový typ projektu. Další informace najdete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Určí, editory, které se používají pro kód a další prvky projektu. Můžete použít základní nebo standardní editory, nebo můžete vytvořit a použít editoru pro konkrétní projekt. Další informace najdete v tématu [vytváření vlastních editorů a návrhářů](../../extensibility/creating-custom-editors-and-designers.md) a [jak: otevřít editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Určete úroveň vaší položky projektu budou mít v účasti **zobrazení tříd** a **prohlížeče objektů**. Další informace najdete v tématu [nástroje procházení symbolů podpora](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Odvozovat nové třídy založené na rozhodnutí o návrhu, které jste provedli dříve pro váš projekt a položky projektu.  
  
5.  Napsání kódu pro následující typ součásti projektu:  
  
    -   Objekt factory projektu, ke správě vytváření nových projektů a otevření stávajících projektů. Další informace najdete v tématu [vytváření instancí podle pomocí projektu objekty pro vytváření projektů](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Zpracování příkazu a hierarchie projektu. Další informace najdete v tématu [není v sestavení: použití třídy HierUtil7 projektu k implementaci typu projektu (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md), [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md)a [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Správa položek projektů, včetně přidání projekt tak, aby **nový projekt** dialogové okno. Další informace najdete v tématu [přidání projektů a šablon položek projektu](../../extensibility/internals/adding-project-and-project-item-templates.md) a [registrace projektů a šablon položek](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Trvalost stavu projektu a jednotlivé položky. Další informace najdete v tématu [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md). Trvalost informace o řešení, najdete v části [řešení](../../extensibility/internals/solutions.md).  
  
    -   Nezávislé vlastnosti konfigurace pro zobrazení v okně Vlastnosti. Další informace najdete v tématu [vlastnosti rozšíření](../../extensibility/internals/extending-properties.md).  
  
    -   Vlastnosti konfigurace projektu, jak je implementován v stránky vlastností k zobrazení vlastností závislé na konfiguraci. Další informace najdete v tématu [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Vytváření výčtu výstupy pro nasazení. Další informace najdete v tématu [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Projekt po spuštění služby. Další informace najdete v tématu [prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md) a [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objekty a třídy odvozené od `IDispatch`, která je dostupná pro automatizaci.  
  
    -   Souborů tabulky příkazů XML (.vsct). Další informace najdete v tématu [tabulky příkazů aplikace Visual Studio (. Vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Testování, ladění a spusťte váš typ projektu.  
  
7.  Zobrazení projektu v **projektu** karty **přidat odkaz** dialogové okno tak, že nastavíte `VARIANT_TRUE` hodnotu `VSHPROPID_ShowProjInSolutionPage`. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Vytvořte soubor Microsoft Installer (MSI) pro instalaci vašich rozšíření VSPackages. Další informace najdete v tématu [instalace rozšíření VSPackages s Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrace typu projektu](../../extensibility/internals/registering-a-project-type.md), a [rozšíření VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Viz také  
 [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Kdy vytvořit typy projektů](../../extensibility/internals/when-to-create-project-types.md)   
 [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)

