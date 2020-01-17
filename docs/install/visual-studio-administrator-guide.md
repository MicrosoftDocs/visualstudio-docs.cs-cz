---
title: Příručka správce sady Visual Studio
titleSuffix: ''
description: Další informace o tom, jak nasadit aplikaci Visual Studio v podnikovém prostředí.
ms.date: 06/02/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9f4b044cddee59254e0b4f5198e75e3fa774aab7
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114203"
---
# <a name="visual-studio-administrator-guide"></a>Příručka správce sady Visual Studio

V podnikových prostředích správci systému obvykle nasazují instalace koncovým uživatelům ze sdílené síťové složky nebo pomocí softwaru pro správu systému. Navrhli jsme modul instalačního programu sady Visual Studio pro podporu podnikového nasazení tím, že správcům systému umožníte vytvořit umístění síťové instalace, předem nakonfigurovat výchozí nastavení instalace, nasadit kódy Product Key během procesu instalace a Správa aktualizací produktů po úspěšném uvedení.

Tato příručka pro správce poskytuje pokyny založené na scénářích pro rozsáhlá nasazení v síťovém prostředí.

## <a name="before-you-begin"></a>Než začnete

Před nasazením sady Visual Studio napříč vaší organizací je potřeba provést několik rozhodnutí, aby se dokončily úlohy a:

::: moniker range="vs-2019"

* Ujistěte se, že každý cílový počítač splňuje [minimální požadavky na instalaci](/visualstudio/releases/2019/system-requirements/).

* Rozhodněte se o potřebě údržby.

  Pokud vaše společnost potřebuje zůstat v sadě funkcí delší, ale stále chce získávat pravidelné aktualizace, naplánujte použití standardních hodnot údržby. Další informace najdete v části ***Možnosti podpory pro zákazníky v Enterprise a Professional*** na stránce [životní cyklus a údržba produktu Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) a také v tématu [Postupy: aktualizace sady Visual Studio na stránce směrného plánu údržby](update-servicing-baseline.md) .

  Pokud plánujete použít aktualizace pro údržbu spolu s kumulativními aktualizacemi funkcí, můžete zvolit nejnovější bity.

* Určete model aktualizace.

  Kam chcete, aby jednotlivé klientské počítače získaly aktualizace? Konkrétně se rozhodněte, jestli chcete získávat aktualizace z Internetu nebo z místní sdílené složky v rámci společnosti. Pokud se pak rozhodnete použít místní sdílenou složku, rozhodněte se, jestli jednotliví uživatelé můžou aktualizovat svoje vlastní klienty, nebo jestli chcete, aby správce aktualizoval klienty programově.

* Rozhodněte, jaké [úlohy a komponenty](workload-and-component-ids.md?view=vs-2019) vaše společnost potřebuje.

* Rozhodněte, jestli se má použít [soubor odpovědí](automated-installation-with-response-file.md?view=vs-2019) (který zjednodušuje správu podrobností v souboru skriptu).

* Rozhodněte, jestli chcete povolit Zásady skupiny, a pokud chcete sadu Visual Studio nakonfigurovat tak, aby na jednotlivých počítačích vypnula zpětnou vazbu zákazníků.

::: moniker-end

::: moniker range="vs-2017"

* Ujistěte se, že každý cílový počítač splňuje [minimální požadavky na instalaci](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Rozhodněte se o potřebě údržby.

  Pokud vaše společnost potřebuje zůstat v sadě funkcí delší, ale stále chce získávat pravidelné aktualizace, naplánujte použití standardních hodnot údržby. Další informace naleznete v části ***Podpora pro starší verze sady Visual Studio*** na stránce [životní cyklus a údržba produktu Visual Studio](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) a také [Postupy: aktualizace sady Visual Studio na stránce směrného plánu údržby](update-servicing-baseline.md) .

  Pokud plánujete použít aktualizace pro údržbu spolu s kumulativními aktualizacemi funkcí, můžete zvolit nejnovější bity.

* Určete model aktualizace.

  Kam chcete, aby jednotlivé klientské počítače získaly aktualizace? Konkrétně se rozhodněte, jestli chcete získávat aktualizace z Internetu nebo z místní sdílené složky v rámci společnosti. Pokud se pak rozhodnete použít místní sdílenou složku, rozhodněte se, jestli jednotliví uživatelé můžou aktualizovat svoje vlastní klienty, nebo jestli chcete, aby správce aktualizoval klienty programově.

* Rozhodněte, jaké [úlohy a komponenty](workload-and-component-ids.md?view=vs-2017) vaše společnost potřebuje.

* Rozhodněte, jestli se má použít [soubor odpovědí](automated-installation-with-response-file.md?view=vs-2017) (který zjednodušuje správu podrobností v souboru skriptu).

* Rozhodněte, jestli chcete povolit Zásady skupiny, a pokud chcete sadu Visual Studio nakonfigurovat tak, aby na jednotlivých počítačích vypnula zpětnou vazbu zákazníků.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 – stažení souborů produktu Visual Studio

* [Vyberte úlohy a součásti](workload-and-component-ids.md?view=vs-2019) , které chcete nainstalovat.

* [Vytvořte sdílenou síťovou složku pro soubory produktu Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>Krok 2 – sestavení instalačního skriptu

* Sestavte instalační skript, který používá k řízení instalace [parametry příkazového řádku](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) .

  >[!NOTE]
  > Můžete zjednodušit skripty pomocí [souboru odpovědí](automated-installation-with-response-file.md?view=vs-2019). Nezapomeňte vytvořit soubor odpovědí, který obsahuje výchozí možnost instalace.

* Volitelné [Použijte kód Product Key multilicencí](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) jako součást instalačního skriptu, aby uživatelé nemuseli software samostatně aktivovat.

* Volitelné Aktualizujte rozložení sítě, abyste mohli [řídit, kdy a odkud budou koncovým uživatelům doručovány aktualizace produktu](controlling-updates-to-visual-studio-deployments.md?view=vs-2019).

* Volitelné Nastavte zásady registru, které mají vliv na nasazení sady Visual Studio, například kde jsou nainstalovány některé balíčky sdílené s jinými verzemi nebo instancemi, [kde jsou balíčky uloženy do mezipaměti](set-defaults-for-enterprise-deployments.md?view=vs-2019) nebo [zda jsou balíčky ukládány do mezipaměti](disable-or-move-the-package-cache.md?view=vs-2019).

* Volitelné Nastavte Zásady skupiny. Můžete také [nakonfigurovat sadu Visual Studio tak, aby na jednotlivých počítačích vypnula zpětnou vazbu od zákazníků](../ide/visual-studio-experience-improvement-program.md) .

## <a name="step-3---deploy"></a>Krok 3 – nasazení

* Pomocí technologie nasazení dle vlastního výběru můžete skript spustit na cílové pracovní stanice pro vývojáře.

## <a name="step-4---deploy-updates"></a>Krok 4 – nasazení aktualizací

* [Aktualizujte vaše umístění v síti s nejnovějšími aktualizacemi](update-a-network-installation-of-visual-studio.md?view=vs-2019) do sady Visual Studio spuštěním příkazu, který jste použili v kroku 1 v pravidelných intervalech a přidejte aktualizované součásti.

  Aplikaci Visual Studio lze aktualizovat pomocí skriptu pro aktualizaci. Uděláte to tak, že použijete parametr [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) příkazového řádku.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 – (volitelné) použití nástrojů sady Visual Studio

Máme několik nástrojů, které vám pomůžou [zjišťovat a spravovat nainstalované instance sady Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019) na klientských počítačích.

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 – stažení souborů produktu Visual Studio

* [Vyberte úlohy a součásti](workload-and-component-ids.md?view=vs-2017) , které chcete nainstalovat.

* [Vytvořte sdílenou síťovou složku pro soubory produktu Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>Krok 2 – sestavení instalačního skriptu

* Sestavte instalační skript, který používá k řízení instalace [parametry příkazového řádku](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) .

  >[!NOTE]
  > Můžete zjednodušit skripty pomocí [souboru odpovědí](automated-installation-with-response-file.md?view=vs-2017). Nezapomeňte vytvořit soubor odpovědí, který obsahuje výchozí možnost instalace.

* Volitelné [Použijte kód Product Key multilicencí](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017) jako součást instalačního skriptu, aby uživatelé nemuseli software samostatně aktivovat.

* Volitelné Aktualizujte rozložení sítě, abyste mohli [řídit, kdy a odkud budou koncovým uživatelům doručovány aktualizace produktu](controlling-updates-to-visual-studio-deployments.md?view=vs-2017).

* Volitelné Nastavte zásady registru, které mají vliv na nasazení sady Visual Studio, například kde jsou nainstalovány některé balíčky sdílené s jinými verzemi nebo instancemi, [kde jsou balíčky uloženy do mezipaměti](set-defaults-for-enterprise-deployments.md?view=vs-2019) nebo [zda jsou balíčky ukládány do mezipaměti](disable-or-move-the-package-cache.md?view=vs-2017).

* Volitelné Nastavte Zásady skupiny. Můžete také [nakonfigurovat sadu Visual Studio tak, aby na jednotlivých počítačích vypnula zpětnou vazbu od zákazníků](../ide/visual-studio-experience-improvement-program.md) .

## <a name="step-3---deploy"></a>Krok 3 – nasazení

* Pomocí technologie nasazení dle vlastního výběru můžete skript spustit na cílové pracovní stanice pro vývojáře.

## <a name="step-4---deploy-updates"></a>Krok 4 – nasazení aktualizací

* [Aktualizujte vaše umístění v síti s nejnovějšími aktualizacemi](update-a-network-installation-of-visual-studio.md?view=vs-2017) do sady Visual Studio spuštěním příkazu, který jste použili v kroku 1 v pravidelných intervalech a přidejte aktualizované součásti.

  Aplikaci Visual Studio lze aktualizovat pomocí skriptu pro aktualizaci. Uděláte to tak, že použijete parametr [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) příkazového řádku.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 – (volitelné) použití nástrojů sady Visual Studio

Máme několik nástrojů, které vám pomůžou [zjišťovat a spravovat nainstalované instance sady Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017) na klientských počítačích.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Instalace certifikátů vyžadovaných pro offline instalace sady Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Import nebo export konfigurací instalace](import-export-installation-configurations.md)
* [Archivy instalačního programu sady Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
* [Nastavení synchronního automatického načtení](../extensibility/synchronously-autoloaded-extensions.md)
