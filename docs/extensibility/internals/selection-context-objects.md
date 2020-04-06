---
title: Kontextové objekty výběru | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705515"
---
# <a name="selection-context-objects"></a>Kontextové objekty výběru
Integrované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vývojové prostředí (IDE) používá objekt kontextu globálního výběru k určení, co by mělo být zobrazeno v integrovaném vývojovém prostředí. Každé okno v ide může mít svůj vlastní objekt kontextu výběru zasunut do kontextu globálního výběru. IDE aktualizuje kontext globálního výběru s hodnotami z okna, když toto okno má fokus. Další informace naleznete [v tématu Zpětná vazba pro uživatele](../../extensibility/internals/feedback-to-the-user.md).

 Každý rámec okna nebo web v ide má službu s názvem <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Objekt vytvořený vspackage, který je umístěn v rámci `QueryService` okna musí volat metodu získat ukazatel na <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> rozhraní.

 Okna rámců mohou při spuštění zabránit šíření částí kontextových informací o výběru do globálního kontextu výběru. Tato možnost je užitečná pro okna nástrojů, která mohou být začínat prázdným výběrem.

 Změna kontextu globálního výběru aktivuje události, které mohou monitorovat služby VSPackages. VSPackages můžete provádět následující úkoly implementací `IVsTrackSelectionEx` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> rozhraní:

- Aktualizujte aktuálně aktivní soubor v hierarchii.

- Sledování změn určitých typů prvků. Například pokud váš VSPackage používá speciální **vlastnosti** okna, můžete sledovat změny v aktivním okně **Vlastnosti** a restartovat vaše v případě potřeby.

  Následující sekvence ukazuje typický průběh sledování výběru.

1. Ide načte kontext výběru z nově otevřené okno a umístí jej do kontextu globálního výběru. Pokud kontext výběru používá HIERARCHY_DONTPROPAGATE nebo SELCONTAINER_DONTPROPAGATE, tyto informace nejsou šířeny do globálního kontextu. Další informace naleznete [v tématu Zpětná vazba pro uživatele](../../extensibility/internals/feedback-to-the-user.md).

2. Události oznámení jsou vysílány do všech VSPackage, který o ně požádal.

3. VSPackage funguje na události, které obdrží prováděním činností, jako je například aktualizace hierarchie, opětovná aktivace nástroje nebo jiné podobné úkoly.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Hierarchie v sadě Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Výběr a měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Typy projektů](../../extensibility/internals/project-types.md)
