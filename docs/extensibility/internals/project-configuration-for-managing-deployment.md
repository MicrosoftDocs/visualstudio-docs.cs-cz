---
title: Konfigurace projektu pro správu nasazení | Microsoft Docs
description: Seznamte se s nasazením do očekávaného umístění pro ladění a instalaci a dvěma způsoby, Visual Studio podporují projekty podporující nasazení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c6077665ccc3bbe5f87b91a1d2fc5636e08539d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899898"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfigurace projektu pro správu nasazení
Nasazení je úkon fyzického přesunutí výstupních položek z procesu sestavení do očekávaného umístění pro ladění a instalaci. Webová aplikace může být například postavena na místním počítači a poté umístěna na serveru.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje dva způsoby, jak se mohou projekty zapojit do nasazení:

- Jako předmět procesu nasazení.

- Jako vedoucí procesu nasazení.

  Než bude možné nasadit řešení, musíte nejprve přidat projekt nasazení a nakonfigurovat možnosti nasazení. Pokud projekt nasazení ještě neexistuje, zobrazí se dotaz, jestli ho  chcete vytvořit, když v nabídce Sestavení vyberete Nasadit řešení nebo kliknete pravým tlačítkem na řešení.  Kliknutím **na Ano** se otevře dialogové okno **Přidat** nový projekt s vybraným **projektem Průvodce vzdáleným** nasazením.

  Průvodce vzdáleným nasazením vás vyzve k zadání typu aplikace (Windows nebo Web), výstupních skupin projektu, které se mají zahrnout, všech dalších souborů, které chcete zahrnout, a vzdáleného počítače, do kterého chcete aplikaci nasadit. Poslední stránka průvodce zobrazí souhrn vybraných možností.

  Projekty, které jsou předmětem procesu nasazení, vytvářejí výstupní položky, které je nutné přesunout do alternativního prostředí. Tyto výstupní položky jsou popsány jako parametry pro rozhraní, jejichž primárním účelem je umožnit <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> projektům seskupit výstupy. Další informace týkající se implementace najdete v `IVsProjectCfg2` tématu Konfigurace projektu pro [výstup](../../extensibility/internals/project-configuration-for-output.md).

  Projekty nasazení, které spravují proces nasazení, povolte příkaz Nasadit a po výběru tohoto příkazu odpovíte. Projekty nasazení implementují rozhraní pro provedení nasazení a volání rozhraní za účelem <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> hlášení událostí stavu nasazení.

  Konfigurace mohou specifikovat závislosti, které mají vliv na jejich operace sestavení nebo nasazení. Závislosti sestavení nebo nasazení jsou projekty, které musí být sestaveny nebo nasazeny před nebo po sestavení nebo nasazení samotných konfigurací. Závislosti sestavení mezi projekty jsou popsány pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> rozhraní a nasazování závislostí s <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> rozhraním . Další informace najdete v tématu [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md).

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)
