---
title: Přehled multitargetingu msbuild | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eecbcd65-9fbc-4307-a321-46d3c3b79b12
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af7649a75fbf3ded0cf5d09e9063b49f4fcab1b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633327"
---
# <a name="msbuild-multitargeting-overview"></a>Přehled multitargetingu msbuild

Pomocí MSBuild můžete zkompilovat aplikaci pro spuštění na některou z několika verzí rozhraní .NET Framework a na libovolné z několika systémových platforem. Můžete například zkompilovat aplikaci, která se spustí na rozhraní .NET Framework 2.0 na 32bitové platformě, a zkompilovat stejnou aplikaci, která se bude spouštět na rozhraní .NET Framework 4.5 na 64bitové platformě.

> [!IMPORTANT]
> Navzdory názvu "multitargeting", projekt může cílit pouze na jednu architekturu a pouze jednu platformu najednou.

 Toto jsou některé z funkcí cílení MSBuild:

- Můžete vyvinout aplikaci, která se zaměřuje na starší verzi rozhraní .NET Framework, například verze 2.0, 3.5 nebo 4.

- Můžete cílit na rozhraní jiné než rozhraní .NET Framework, například rozhraní Silverlight Framework.

- Můžete cílit na *profil architektury*, což je předdefinovaná podmnožina cílového rozhraní.

- Pokud je vydána aktualizace Service Pack pro aktuální verzi rozhraní .NET Framework, můžete na něj cílit.

- Cílení na MSBuild zaručuje, že aplikace používá pouze funkce, které jsou k dispozici v cílovém rozhraní a platformě.

## <a name="target-framework-and-platform"></a>Cílový rámec a platforma

 *Cílová architektura* je verze rozhraní .NET Framework, na které je projekt vytvořen a *cílová platforma* je systémová platforma, na které je projekt vytvořen.  Můžete například chtít cílit na aplikaci rozhraní .NET Framework 2.0, která by běžela na 32bitové platformě, která je kompatibilní s řadou procesorů 802x86 (x86). Kombinace cílového rámce a cílové platformy se označuje jako *cílový kontext*. Další informace naleznete v tématu [Target framework a target platform .](../msbuild/msbuild-target-framework-and-target-platform.md)

## <a name="toolset-toolsversion"></a>Sada nástrojů (atribut ToolsVersion)

 Sada nástrojů shromažďuje společně nástroje, úkoly a cíle, které se používají k vytvoření aplikace. Sada nástrojů obsahuje kompilátory, například *csc.exe* a *vbc.exe*, soubor společných cílů (*microsoft.common.targets*) a soubor běžných úkolů (*microsoft.common.tasks*). Sadu nástrojů 4.5 lze použít k cílení na rozhraní .NET Framework verze 2.0, 3.0, 3.5, 4 a 4.5. Sadu nástrojů 2.0 lze však použít pouze k cílení na rozhraní .NET Framework verze 2.0. Další informace naleznete v [tématu Toolset (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

## <a name="reference-assemblies"></a>Referenční sestavení

 Referenční sestavení, která jsou zadána v sadě nástrojů, vám pomohou navrhnout a vytvořit aplikaci. Tato referenční sestavení nejen umožňují konkrétní cílové sestavení, ale také omezit součásti a funkce v ide sady Visual Studio na ty, které jsou kompatibilní s cílem. Další informace naleznete [v tématu Resolve assemblies at design time](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="configure-targets-and-tasks"></a>Konfigurace cílů a úkolů

 Cíle a úkoly MSBuild můžete nakonfigurovat tak, aby byly spuštěny mimo proces s msbuildem, takže můžete cílit na kontexty, které se výrazně liší od kontextu, na kterých běžíte.  Můžete například cílit na 32bitovou aplikaci rozhraní .NET Framework 2.0, zatímco vývojový počítač běží na 64bitové platformě s rozhraním .NET Framework 4.5. Další informace naleznete v [tématu Konfigurace cílů a úkolů](../msbuild/configuring-targets-and-tasks.md).

## <a name="troubleshooting"></a>Řešení potíží

 Při pokusu o odkaz na sestavení, které není součástí cílového kontextu, může dojít k chybám. Další informace o těchto chybách a o tom, co s nimi provést, naleznete [v tématu Poradce při potížích s chybami cílení rozhraní .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).
