---
title: Konfigurace cílů a úloh | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb305e1c8a50c8f452ce4ee2d78620314c5d6a1f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596109"
---
# <a name="configure-targets-and-tasks"></a>Konfigurace cílů a úloh
Cíle a úlohy MSBuild můžete nakonfigurovat tak, aby se spouštěly mimo proces s nástrojem MSBuild, abyste mohli cílit na kontexty, které se liší od těch, na kterých je spuštěný. Můžete například cílit na 32 aplikaci .NET Framework 2,0, zatímco vývojový počítač běží v operačním systému 4,5 .NET Framework 64 s-bit. Můžete také cílit na počítače, které se spouštějí s .NET Framework 4 nebo starším. Kombinace 32-nebo 64-bitová verze a konkrétní verze .NET Framework je označována jako *cílový kontext*.

## <a name="installation"></a>Instalace služby
 .NET Framework 4,5 a 4.5.1 nahradí modul CLR (Common Language Runtime), cíle, úlohy a nástroje .NET Framework 4 bez jejich přejmenování. .NET Framework 4.5.1 je nainstalován jako součást [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].

 Pokud chcete nástroj MSBuild nainstalovat samostatně ze sady Visual Studio, můžete stáhnout instalační balíček z [webu MSBuild Download](https://www.microsoft.com/download/details.aspx?id=40760). Je také nutné nainstalovat .NET Framework verze, které chcete použít.

## <a name="targets-and-tasks"></a>Cíle a úkoly
 Nástroj MSBuild spouští některé úlohy sestavení mimo proces a cílí na větší sadu kontextů.  Například 32 bitový MSBuild může spustit úlohu sestavení v procesu 64 pro cílení na počítač 64. To se řídí `UsingTask` argumenty a parametry `Task`. Cíle nainstalované .NET Framework 4,5 nastavily tyto argumenty a parametry a nejsou nutné žádné změny pro sestavování aplikací pro různé cílové kontexty.

 Pokud chcete vytvořit vlastní cílový kontext, je nutné nastavit tyto argumenty a parametry odpovídajícím způsobem. Příklady najdete v souboru *Microsoft. Common. targets* pro .NET Framework 4,5 a v souboru *Microsoft. Common. Tasks* .  Informace o tom, jak vytvořit vlastní úlohu, která může pracovat s více cílovými kontexty, nebo jak upravit existující úlohy, najdete v tématu [Postupy: Konfigurace cílů a úloh](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Viz také:
- [Cílení na více verzí](../msbuild/msbuild-multitargeting-overview.md)
