---
title: 'Kontrolní seznam: vytváření nových typů projektů | Microsoft Docs'
description: Seznamte se s úkoly, které je třeba dokončit pro vytvoření a zobrazení nového typu projektu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a8cdeb250b81a39a5d9350da61a872ef43ae23b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944495"
---
# <a name="checklist-create-new-project-types"></a>Kontrolní seznam: vytvoření nových typů projektů
Chcete-li vytvořit nový typ projektu, je nutné provést několik úloh. Následující kontrolní seznam poskytuje pokyny k těmto úlohám:

1. Navrhněte funkci pro nový typ projektu. Další informace naleznete v tématu [rozhodnutí o návrhu typu projektu](../../extensibility/internals/project-type-design-decisions.md).

2. Určete, které editory jsou používány pro kód a jiné prvky projektu. Můžete použít editory Core nebo Standard, nebo můžete vytvořit a použít editory specifické pro projekt. Další informace naleznete v tématu [Vytvoření vlastních editorů a návrhářů](../../extensibility/creating-custom-editors-and-designers.md) a [Postupy: otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md).

3. Určete, jakou úroveň účasti budou mít vaše položky projektu v **zobrazení tříd** a **Prohlížeč objektů**. Další informace najdete v tématu [Podpora nástrojů pro procházení symbolů](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Odvozuje nové třídy na základě rozhodnutí o návrhu, která jste předtím vytvořili pro projekt a položky projektu.

5. Napište kód pro následující součásti typu projektu:

    - Objekt pro vytváření projektů, pro správu tvorby nových projektů a otevírání stávajících projektů. Další informace naleznete v tématu [vytváření instancí projektu pomocí továrny projektu](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Řízení hierarchie projektu a příkazů. Další informace naleznete v tématu [použití tříd projektu HierUtil7 k implementaci typu projektu (C++)](/previous-versions/bb166212(v=vs.100)), [prvků modelu projektu](../../extensibility/internals/elements-of-a-project-model.md), [základních komponent modelu projektu](../../extensibility/internals/project-model-core-components.md)a [MenuCommands vs. OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

    - Správa položek projektu, včetně přidání projektu do dialogového okna **Nový projekt** . Další informace naleznete v tématu [Přidání šablon projektů a položek projektů](../../extensibility/internals/adding-project-and-project-item-templates.md) a [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md).

    - Trvalost stavu projektu a jednotlivých položek. Další informace naleznete v tématu [otevření a uložení položek projektu](../../extensibility/internals/opening-and-saving-project-items.md). Informace o trvalosti informací o řešeních najdete v tématu [řešení](../../extensibility/internals/solutions-overview.md).

    - Vlastnosti nezávislé na konfiguraci, které se mají zobrazit v okno Vlastnosti. Další informace najdete v tématu věnovaném [rozšiřování vlastností](../../extensibility/internals/extending-properties.md).

    - Vlastnosti konfigurace projektu, jak jsou implementovány na stránkách vlastností, aby zobrazovaly vlastnosti závislé na konfiguraci. Další informace najdete v tématu [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md).

    - Vytváření výčtu výstupů pro nasazení. Další informace najdete v tématu [konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).

    - Služby spuštění projektu. Další informace naleznete v tématu [prvky modelu projektu](../../extensibility/internals/elements-of-a-project-model.md) a [základní komponenty modelu projektu](../../extensibility/internals/project-model-core-components.md).

    - Objekty nebo třídy odvozené z `IDispatch` , k dispozici pro automatizaci.

    - Soubory tabulek příkazů jazyka XML (*. vsct*). Další informace naleznete v tématu [soubory tabulek příkazů sady Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Otestujte, laďte a spusťte typ projektu.

7. Zobrazte projekt na kartě **projekt** dialogového okna **Přidat odkaz** nastavením `VARIANT_TRUE` hodnoty pro `VSHPROPID_ShowProjInSolutionPage` . Další informace naleznete v tématech <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Vytvořte soubor Instalační služby Microsoft (*. msi*) pro instalaci vašich VSPackage. Další informace najdete v tématu [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Registrace typu projektu](../../extensibility/internals/registering-a-project-type.md)a [VSPackage](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Viz také
- [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Kdy vytvořit typy projektů](../../extensibility/internals/when-to-create-project-types.md)
- [Vytváření typů projektů](../../extensibility/internals/creating-project-types.md)