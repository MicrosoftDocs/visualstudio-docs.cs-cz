---
title: Konfigurace projektu pro vytváření | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706733"
---
# <a name="project-configuration-for-building"></a>Konfigurace projektu pro sestavení
Seznam konfigurací řešení pro dané řešení spravuje dialogové okno Konfigurace řešení.

 Uživatel může vytvořit další konfigurace řešení, z nichž každá má svůj vlastní jedinečný název. Když uživatel vytvoří novou konfiguraci řešení, rozhraní IDE výchozí odpovídající název konfigurace v projektech nebo ladění, pokud neexistuje žádný odpovídající název. Uživatel může v případě potřeby změnit výběr tak, aby splňoval konkrétní požadavky. Jedinou výjimkou z tohoto chování je, když projekt podporuje konfiguraci, která odpovídá názvu nové konfigurace řešení. Předpokládejme například, že řešení obsahuje Project1 a Project2. Project1 má konfigurace projektu Ladění, Maloobchod a MyConfig1. Project2 má konfigurace projektu Ladění, Maloobchod a MyConfig2.

 Pokud uživatel vytvoří novou konfiguraci řešení s názvem MyConfig2, Project1 sváže svou konfiguraci ladění s konfigurací řešení ve výchozím nastavení. Project2 také ve výchozím nastavení sváže konfiguraci MyConfig2 s konfigurací řešení.

> [!NOTE]
> Vazba nerozlišuje malá a velká písmena.

 Když uživatel vybere položku **Vícenásobný výběr** v seznamu konfigurace, prostředí zobrazí dialogové okno, které poskytuje seznam dostupných konfigurací.

 ![Více konfigurací](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Více konfigurací

 V tomto dialogovém okně může uživatel vybrat jednu nebo více konfigurací. Po výběru budou hodnoty vlastností zobrazené v dialogovém okně stránek vlastností odrážet průsečík hodnot pro vybrané konfigurace.

 Informace týkající se přidávání a přejmenování konfigurací řešení a projektů najdete v tématu [Konfigurace řešení.](../../extensibility/internals/solution-configuration.md)

 Závislosti projektu a pořadí sestavení jsou nezávislé na konfiguraci řešení: to znamená, že můžete nastavit pouze jeden strom závislostí pro všechny projekty v řešení. Kliknutím pravým tlačítkem myši na řešení nebo projekt a výběrem **možnosti Závislosti projektu** nebo **pořadí sestavení projektu** se otevře dialogové okno Závislosti **projektu.** Lze jej také otevřít z nabídky **Projekt.**

 ![Závislosti projektu](../../extensibility/internals/media/vsprojdependencies.gif "vsProjZávislosti") Závislosti projektu

 Závislosti projektu určují pořadí, ve kterém se sestavení projektů. Pomocí karty Pořadí sestavení v dialogovém okně můžete zobrazit přesné pořadí, ve kterém budou projekty v rámci řešení vytvářet, a pomocí karty Závislosti upravit pořadí sestavení.

> [!NOTE]
> Projekty v seznamu, u kterých jsou zaškrtnuta políčka zaškrtnutá, ale zobrazují <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> se <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> šedě, byly přidány prostředím z důvodu explicitních závislostí určených rozhraním nebo rozhranía a nelze je změnit. Například přidání odkazu na [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekt z projektu do jiného projektu automaticky přidá závislost sestavení, kterou lze odebrat pouze odstraněním odkazu. Projekty, jejichž zaškrtávací políčka jsou vymazány a jsou zobrazeny šedě, nelze vybrat, protože by to vytvořilo smyčku závislostí (například Projekt1 by byl závislý na projektu Project2 a Project2 by byl závislý na projektu Project1), který by zastavil sestavení.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sestavení procesy zahrnují typické kompilace a propojení operace, které jsou vyvolány pomocí jednoho příkazu Sestavení. Podporovány mohou být také dva další procesy sestavení: čistá operace pro odstranění všech výstupních položek z předchozího sestavení a aktuální kontrola, která určuje, zda se změnila výstupní položka v konfiguraci.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>objekty vrátí <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>(vrácené z ) spravovat své procesy sestavení. Chcete-li ohlásit stav operace sestavení, zatímco k ní <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>dochází, konfigurace volat , rozhraní implementované prostředí a jakýkoli jiný objekt zájem o události stavu sestavení.

 Po spuštění nastavení konfigurace lze určit, zda mohou být spuštěny pod kontrolou ladicího programu. Konfigurace implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> pro podporu ladění.

 Po implementaci závislostí projektu můžete programově manipulovat se závislostmi prostřednictvím modelu automatizace. Můžete <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> volat v modelu automatizace. Nejsou k dispozici žádná rozhraní na úrovni rozhraní API VSIP, která by umožňovala přímou manipulaci s konfiguracemi správce sestavení řešení a jejich vlastnostmi.

 Kromě toho můžete poskytnout mřížku v okně závislostí projektu. Další informace naleznete v [tématu Properties Display Grid](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro správu nasazení](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)
