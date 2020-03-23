---
title: Konfigurace cílů a úkolů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a3d6ba3eff6a01c2d0ff68b4132d883eadb90f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634393"
---
# <a name="configure-targets-and-tasks"></a>Konfigurace cílů a úkolů

Cíle a úlohy MSBuild můžete nakonfigurovat tak, aby byly spuštěny mimo proces s msbuildem, takže můžete cílit na kontexty, které se liší od kontextu, na kterých běžíte. Můžete například cílit na 32bitovou aplikaci rozhraní .NET Framework 2.0, zatímco vývojový počítač je spuštěn v 64bitovém operačním systému rozhraní .NET Framework 4.5. Můžete také cílit na počítače, které běží s rozhraním .NET Framework 4 nebo starší. Kombinace 32- nebo 64 bitness a konkrétní verze rozhraní .NET Framework se označuje jako *cílový kontext*.

## <a name="installation"></a>Instalace

  Pokud chcete nainstalovat MSBuild odděleně od sady Visual Studio, můžete stáhnout instalační balíček z [msbuild download](https://www.microsoft.com/download/details.aspx?id=40760). Musíte také nainstalovat verze rozhraní .NET Framework, které chcete použít.

## <a name="targets-and-tasks"></a>Cíle a úkoly

 MSBuild spouští určité úlohy sestavení mimo proces a zaměřuje se na větší sadu kontextů.  Například 32bitové msbuild může spustit úlohu sestavení v 64bitovém procesu za cílna 64bitový počítač. To je `UsingTask` řízeno `Task` argumenty a parametry. Cíle nainstalované rozhraním .NET Framework 4.5 nastavují tyto argumenty a parametry a k vytváření aplikací pro různé cílové kontexty nejsou nutné žádné změny.

 Pokud chcete vytvořit vlastní cílový kontext, musíte správně nastavit tyto argumenty a parametry. Podívejte se do souboru .NET Framework 4.5 *Microsoft.Common.targets* a *microsoft.common.tasks* souboru pro příklady.  Informace o vytvoření vlastního úkolu, který může pracovat s více cílovými kontexty nebo jak upravit existující úkoly, naleznete v [tématu Postup: Konfigurace cílů a úkolů](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Viz také

- [Multicílení](../msbuild/msbuild-multitargeting-overview.md)
