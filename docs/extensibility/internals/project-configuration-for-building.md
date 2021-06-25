---
title: Konfigurace projektu pro sestavení | Microsoft Docs
description: Přečtěte si, jak se seznam konfigurací řešení pro konkrétní řešení spravuje v dialogovém okně konfigurace řešení v novém typu projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf98698d3527220c4bc25cdf36132f0088ae4ea7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899924"
---
# <a name="project-configuration-for-building"></a>Konfigurace projektu pro sestavení
Seznam konfigurací řešení pro dané řešení je spravován v dialogovém okně konfigurace řešení.

 Uživatel může vytvořit další konfigurace řešení, z nichž každý má vlastní jedinečný název. Když uživatel vytvoří novou konfiguraci řešení, rozhraní IDE bude standardně odpovídající název konfigurace v projektech nebo bude ladit, pokud neexistuje žádný odpovídající název. Uživatel může v případě potřeby změnit výběr tak, aby splňoval konkrétní požadavky. Jedinou výjimkou z tohoto chování je, když projekt podporuje konfiguraci, která odpovídá názvu nové konfigurace řešení. Předpokládejme například, že řešení obsahuje Project1 a "Project2". Project1 má konfigurace projektu ladění, maloobchod a MyConfig1. "Project2" má konfigurace projektu ladění, maloobchod a MyConfig2.

 Pokud uživatel vytvoří novou konfiguraci řešení s názvem MyConfig2, Project1 ve výchozím nastavení sváže svou konfiguraci ladění s konfigurací řešení. "Project2" také ve výchozím nastavení váže svou konfiguraci MyConfig2 na konfiguraci řešení.

> [!NOTE]
> Vazba rozlišuje malá a velká písmena.

 Když uživatel vybere položku **vícenásobného výběru** v rozevíracím seznamu konfigurace, prostředí zobrazí dialogové okno, které poskytuje seznam dostupných konfigurací.

 ![Více konfigurací](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Více konfigurací

 V tomto dialogovém okně může uživatel vybrat jednu nebo více konfigurací. Po výběru hodnoty vlastností, které se zobrazují v dialogovém okně stránky vlastností, odrážejí průsečík hodnot pro vybrané konfigurace.

 Informace týkající se přidání a přejmenování konfigurací pro řešení a projekty najdete v tématu [Konfigurace řešení](../../extensibility/internals/solution-configuration.md) .

 Závislosti projektu a pořadí sestavení jsou nezávisle na konfiguraci řešení: to znamená, že můžete nastavit pouze jeden strom závislosti pro všechny projekty v řešení. Kliknutím pravým tlačítkem myši na řešení nebo projekt a výběrem možnosti **závislosti projektu** nebo **pořadí sestavení projektu** otevřete dialogové okno **závislosti projektu** . Lze jej také otevřít z nabídky **projekt** .

 ![Závislosti projektu](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Závislosti projektu

 Závislosti projektu určují pořadí, ve kterém se projekty sestavují. Pomocí karty pořadí sestavení v dialogovém okně můžete zobrazit přesné pořadí, ve kterém budou projekty v rámci řešení sestaveny, a použít kartu závislosti pro úpravu pořadí sestavení.

> [!NOTE]
> Projekty v seznamu, které mají zaškrtnutá políčka, ale jsou neaktivní, jsou přidány do prostředí z důvodu explicitních závislostí zadaných v <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> rozhraních nebo a nelze je změnit. Například přidání odkazu na projekt z [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu do jiného projektu automaticky přidá závislost sestavení, která může být odebrána pouze odstraněním odkazu. Projekty, jejichž zaškrtávací políčka jsou jasné a zobrazují se šedě, nelze vybrat, protože by to vedlo k vytvoření smyčky závislosti (například Project1 by měla být závislá na "Project2" a "Project2" by měla být závislá na Project1), která by zastavila sestavení.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] procesy sestavení obsahují typické operace kompilace a propojení, které jsou vyvolány jediným příkazem sestavení. Lze také podporovat dva další procesy sestavení: čistou operaci pro odstranění všech výstupních položek z předchozího sestavení a aktuální kontrolu, která určuje, zda se výstupní položka v konfiguraci změnila.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> objekty vracejí odpovídající <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (vrácený z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ) pro správu procesů sestavení. Chcete-li ohlásit stav operace sestavení, když k ní dojde, konfigurace provádí volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> , rozhraní implementované prostředím a jakýkoli jiný objekt, který zajímá události stavu sestavení.

 Po sestavení lze nastavení konfigurace použít k určení, zda mohou být spuštěny pod ovládacím prvkem ladicího programu. Konfigurace implementují <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> pro podporu ladění.

 Po implementaci závislostí projektu můžete programově manipulovat se závislostmi prostřednictvím modelu automatizace. Zavoláte <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> se do modelu automatizace. Nejsou k dispozici žádná rozhraní API na úrovni VSIP, která umožňují přímou manipulaci s konfiguracemi správce sestavení řešení a jejich vlastnostmi.

 Kromě toho můžete v okně závislosti projektu zadat mřížku. Další informace najdete v tématu [zobrazovaná Mřížka vlastností](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Viz také
- [Správa možností konfigurace](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurace projektu pro správu nasazení](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Konfigurace projektu pro výstup](../../extensibility/internals/project-configuration-for-output.md)
