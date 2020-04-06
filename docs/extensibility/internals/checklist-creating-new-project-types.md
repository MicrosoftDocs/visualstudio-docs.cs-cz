---
title: 'Kontrolní seznam: Vytváření nových typů projektů | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709754"
---
# <a name="checklist-create-new-project-types"></a>Kontrolní seznam: Vytvoření nových typů projektů
Chcete-li vytvořit nový typ projektu, musíte dokončit několik úkolů. Následující kontrolní seznam poskytuje průvodce těmito úkoly:

1. Navrhněte funkce pro nový typ projektu. Další informace naleznete v [tématu Rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).

2. Určete, které editory se používají pro kód a další prvky projektu. Můžete použít základní nebo standardní editory nebo můžete vytvářet a používat editory specifické pro projekt. Další informace naleznete v [tématu Vytvoření vlastních editorů a návrhářů](../../extensibility/creating-custom-editors-and-designers.md) a [Postup: Otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md).

3. Určete úroveň účasti položek projektu v **zobrazení tříd a** prohlížeči **objektů**. Další informace naleznete v [tématu Podpora nástrojů pro procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Odvodit nové třídy na základě rozhodnutí o návrhu, které jste provedli dříve pro položky projektu a projektu.

5. Napište kód pro následující součásti typu projektu:

    - Projektová továrna, pro správu vytváření nových projektů a otevírání stávajících projektů. Další informace naleznete v [tématu Vytváření instancí projektu pomocí továren projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Hierarchie projektu a zpracování příkazů. Další informace naleznete [v tématech Použití tříd projektu HierUtil7 k implementaci typu projektu (C++),](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346) [prvků modelu projektu](../../extensibility/internals/elements-of-a-project-model.md), základních komponent modelu [projektu](../../extensibility/internals/project-model-core-components.md)a [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

    - Správa položek projektu, včetně přidání projektu do dialogového okna **Nový projekt.** Další informace naleznete v [tématu Přidání šablon položek projektu a projektu](../../extensibility/internals/adding-project-and-project-item-templates.md) a Registrace šablon projektů a [položek](../../extensibility/internals/registering-project-and-item-templates.md).

    - Trvalá stav projektu a jednotlivé položky. Další informace naleznete v tématu [Otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md). Trvalá informace o řešení naleznete v tématu [Solutions](../../extensibility/internals/solutions-overview.md).

    - Vlastnosti nezávislé na konfiguraci, které se mají zobrazit v okně Vlastnosti. Další informace naleznete v tématu [Rozšíření vlastností](../../extensibility/internals/extending-properties.md).

    - Vlastnosti konfigurace projektu, jak jsou implementovány na stránkách vlastností, aby se zobrazily vlastnosti závislé na konfiguraci. Další informace naleznete v [tématu Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).

    - Výčet výstupů pro nasazení. Další informace naleznete v [tématu Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).

    - Služby spuštění projektu. Další informace naleznete [v tématu Prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md) a [součásti jádra modelu projektu](../../extensibility/internals/project-model-core-components.md).

    - Objekty nebo třídy `IDispatch`odvozené z , k dispozici pro automatizaci.

    - Soubory příkazů XML (*.vsct*). Další informace naleznete v tématu [Visual Studio příkaz tabulka (.vsct) soubory](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Testování, ladění a spuštění typu projektu.

7. Zobrazení projektu na kartě **Projekt** v dialogovém `VARIANT_TRUE` okně Přidat `VSHPROPID_ShowProjInSolutionPage` **odkaz** nastavením hodnoty pro aplikaci . Další informace naleznete v tématech <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Vytvořte soubor Instalační služby společnosti Microsoft (*MSI)* pro instalaci balíčků VSPackages. Další informace naleznete [v tématech Instalace balíčků VSPackages s Instalační službou systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), Registrace typu [projektu](../../extensibility/internals/registering-a-project-type.md)a [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Viz také
- [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Kdy vytvořit typy projektů](../../extensibility/internals/when-to-create-project-types.md)
- [Vytvořit typy projektů](../../extensibility/internals/creating-project-types.md)
