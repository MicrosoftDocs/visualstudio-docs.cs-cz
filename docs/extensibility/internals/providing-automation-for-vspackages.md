---
title: Zajištění automatizace pro balíčky VSPackages | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6364f9cbaf3409e076eeb77365e5d793c7be96cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705951"
---
# <a name="providing-automation-for-vspackages"></a>Poskytování automatizace pro balíčky VSPackages
Existují dva hlavní způsoby, jak zajistit automatizaci pro vaše VSPackages: implementací objektů specifických pro VSPackage a implementací standardních objektů automatizace. Obecně se používají společně k rozšíření modelu automatizace prostředí.

## <a name="vspackage-specific-objects"></a>Objekty specifické pro vSPackage
 Určitá místa v rámci modelu automatizace vyžadují, abyste poskytli objekty automatizace, které jsou jedinečné pro váš VSPackage. Například nové projekty vyžadují odlišné objekty, které poskytuje pouze vaše VSPackage. Názvy těchto objektů jsou zadány v registru a `DTE` získány prostřednictvím volání objektu prostředí.

 VSPackage specifické objekty lze také získat, pokud příjemce automatizace používá objekt k dispozici prostřednictvím Object vlastnost standardní objekt. Například standardní `Window` objekt má `Object` vlastnost, běžně označovanou `Windows.Object` jako vlastnost. Když spotřebitelé `Window.Object` volání na okno implementované ve vašem VSPackage, předáte zpět konkrétní objekt automatizace vlastní návrh.

#### <a name="projects"></a>Projekty
 VSPackages můžete rozšířit model automatizace pro nové typy projektů prostřednictvím svých vlastních objektů specifických pro VSPackage. Primárním účelem poskytování nových objektů automatizace pro váš VSPackage <xref:Microsoft.VisualStudio.VCProjectEngine.VCProject> je <xref:VSLangProj80.VSProject2> odlišit vaše jedinečné objekty projektu od nebo objektu. Tato diferenciace je užitečná, pokud chcete poskytnout způsob, jak vyčlenit nebo itorizovat typ projektu na rozdíl od jiných typů projektu, pokud se zobrazí vedle sebe v řešení. Další informace naleznete v [tématu Vystavení objektů projektu](../../extensibility/internals/exposing-project-objects.md).

#### <a name="events"></a>Události
 Architektura událostí prostředí nabízí jiné místo pro připojení vlastních objektů specifických pro VSPackage. Například vytvořením vlastních jedinečných objektů událostí můžete rozšířit model událostí prostředí pro projekty. Můžete chtít poskytnout vlastní události při přidání nové položky do vlastního typu projektu. Další informace naleznete v [tématu Vystavení událostí](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md).

#### <a name="window-objects"></a>Objekty oken
 Systém Windows můžete předat zpět objekt automatizace specifické pro VSPackage zpět do prostředí, když je volána. Implementovat objekt, který je <xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject> <xref:EnvDTE.IExtensibleObject> odvozen `IDispatch` od , nebo že ruce zpět vlastnosti, rozšíření window objektu, ve kterém je umístěn. Tento přístup můžete například použít k zajištění automatizace pro ovládací prvek umístěn v rámci okna. Sémantiku tohoto objektu a všechny ostatní objekty, které by mohly rozšířit, jsou vaše návrh. Další informace naleznete v [tématu How to: Provide Automation for Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md).

#### <a name="options-pages-on-the-tools-menu"></a>Stránky možností v nabídce Nástroje
 Můžete vytvořit stránky rozšířit nástroje, možnosti automatizace model prostřednictvím provádění stránek a přidávání informací do registru vytvořit vlastní možnosti. Vaše stránky pak mohou být volány prostřednictvím objektového modelu prostředí jako všechny ostatní stránky možností. Pokud návrh funkce, kterou přidáváte do prostředí prostřednictvím VSPackages vyžaduje možnosti stránky, pak byste měli přidat podporu automatizace také. Další informace naleznete [v tématu Podpora automatizace pro stránky možností](../../extensibility/internals/automation-support-for-options-pages.md).

## <a name="standard-automation-objects"></a>Standardní automatizační objekty
 Chcete-li rozšířit automatizaci pro projekty, můžete `IDispatch`také implementovat standardní objekty automatizace (odvozené z ) které stojí vedle jiných objektů projektu a implementují standardní metody a vlastnosti. Příklady standardních objektů zahrnují objekty projektu, které jsou `Projects` `Project`vloženy do hierarchie řešení, například , , `ProjectItem`a `ProjectItems`. Každý nový typ projektu by měl implementovat tyto objekty (a případně další v závislosti na sémantiku projektu).

 V jistém smyslu tyto objekty poskytují opačnou výhodu v Objekty projektu specifické pro VSPackage. Standardní objekty automatizace umožňují, aby byl projekt použit zobecněnou stejnou pro všechny ostatní projekty podporující stejné objekty. Doplněk, který je zapsán proti `Project` obecné `ProjectItem` a objekty mohou fungovat proti projekty libovolného typu. Další informace naleznete [v tématu Project Modeling](../../extensibility/internals/project-modeling.md).
