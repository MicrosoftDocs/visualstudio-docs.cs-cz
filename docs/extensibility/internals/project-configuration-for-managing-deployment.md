---
title: Konfigurace projektu pro správu nasazení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706700"
---
# <a name="project-configuration-for-managing-deployment"></a>Konfigurace projektu pro správu nasazení
Nasazení je úkon fyzicképřesunutí výstupních položek z procesu sestavení do očekávaného umístění pro ladění a instalaci. Webová aplikace může být například vytvořena v místním počítači a poté umístěna na server.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]podporuje dva způsoby, jak mohou být projekty zapojeny do nasazení:

- Jako předmět procesu nasazení.

- Jako správce procesu nasazení.

  Před nasazením řešení je nutné nejprve přidat projekt nasazení ke konfiguraci možností nasazení. Pokud projekt nasazení ještě neexistuje, budete dotázáni, zda chcete vytvořit, když vyberete **nasadit řešení** z nabídky **Sestavení** nebo klikněte pravým tlačítkem myši na řešení. Klepnutím na **tlačítko Ano** se otevře dialogové okno Přidat **nový projekt** s vybraným projektem **Průvodce vzdáleným nasazením.**

  Průvodce vzdáleným nasazením vás požádá o typ aplikace (Windows nebo Web), výstupní skupiny projektu, které chcete zahrnout, všechny další soubory, které chcete zahrnout, a vzdálený počítač, do kterého chcete nasadit. Na poslední stránce průvodce se zobrazí souhrn vybraných možností.

  Projekty, které jsou předmětem procesu nasazení vyrábět výstupní položky, které musí být přesunuty do alternativního prostředí. Tyto výstupní položky jsou popsány <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> jako parametry pro rozhraní, jehož primárním účelem, pokud chcete povolit projekty seskupit výstupy. Další informace týkající se implementace `IVsProjectCfg2`aplikace naleznete v tématu [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md).

  Projekty nasazení, které spravují proces nasazení, umožňují příkaz Deploy a reagují, když je tento příkaz vybrán. Projekty nasazení <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> implementují rozhraní k provedení <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> nasazení a volání rozhraní pro hlášení událostí stavu nasazení.

  Konfigurace můžete určit závislosti, které ovlivňují jejich sestavení nebo nasazení operace. Sestavení nebo nasazení závislostí jsou projekty, které musí být sestaveny nebo nasazeny před nebo po samotné konfigurace jsou sestaveny nebo nasazeny. Sestavení závislostí mezi projekty <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> jsou popsány s <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> rozhraním a nasadit závislosti s rozhraním. Další informace naleznete v [tématu Konfigurace projektu pro vytváření .](../../extensibility/internals/project-configuration-for-building.md)

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro sestavení](../../extensibility/internals/project-configuration-for-building.md)
- [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)
