---
title: Příručka správce sady Visual Studio
titleSuffix: ''
description: Přečtěte si další informace o nasazení sady Visual Studio v podnikovém prostředí.
ms.date: 03/09/2020
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
ms.openlocfilehash: bda9a73a7a1aabb2d288653ff4d7b20b1c40db8c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79190277"
---
# <a name="visual-studio-administrator-guide"></a>Příručka správce sady Visual Studio

V podnikových prostředích správci systému obvykle nasazují instalace koncovým uživatelům ze sdílené síťové složky nebo pomocí softwaru pro správu systémů. Navrhli jsme instalační modul sady Visual Studio pro podporu podnikového nasazení tím, že správcům systému umožňujeme vytvořit umístění instalace sítě, předkonfigurovat výchozí nastavení instalace, nasadit kódy Product Key během procesu instalace a pro správu aktualizací produktů po úspěšném zavedení.

Tato příručka pro správce poskytuje pokyny založené na scénářích pro nasazení v rozlehlé síti v síťových prostředích.

## <a name="before-you-begin"></a>Než začnete

Před nasazením sady Visual Studio v celé organizaci je třeba provést několik rozhodnutí a úkolů:

::: moniker range="vs-2019"

* Ujistěte se, že každý cílový počítač splňuje [minimální požadavky na instalaci](/visualstudio/releases/2019/system-requirements/).

* Rozhodněte se o svých servisních potřebách.

  Pokud vaše společnost potřebuje zůstat na sadu funkcí déle, ale přesto chce získat pravidelné aktualizace údržby, naplánujte použít směrný plán údržby. Další informace naleznete v části ***Možnosti podpory pro podnikové a profesionální zákazníky*** na stránce [životního cyklu a údržby produktu sady Visual Studio a](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) také v tématu Postup: Aktualizace sady Visual Studio na stránce [směrného plánu obsluhy.](update-servicing-baseline.md)

  Pokud plánujete použít aktualizace údržby spolu s kumulativními aktualizacemi funkcí, můžete zvolit nejnovější bity.

* Rozhodněte o modelu aktualizace.

  Kde chcete, aby jednotlivé klientské počítače získaly aktualizace? Konkrétně se rozhodněte, zda chcete získat aktualizace z internetu nebo z místního podílu v celé společnosti. Pokud se pak rozhodnete použít místní sdílenou složku, rozhodněte se, zda jednotliví uživatelé mohou aktualizovat své vlastní klienty, nebo zda chcete, aby správce aktualizoval klienty programově.

* Rozhodněte se, které [úlohy a součásti](workload-and-component-ids.md?view=vs-2019) vaše společnost potřebuje.

* Rozhodněte se, zda chcete použít [soubor odpovědí](automated-installation-with-response-file.md?view=vs-2019) (který zjednodušuje správu podrobností v souboru skriptu).

* Rozhodněte se, zda chcete povolit zásady skupiny a zda chcete nakonfigurovat visual studio tak, aby zakázalo zpětnou vazbu zákazníků v jednotlivých počítačích.

::: moniker-end

::: moniker range="vs-2017"

* Ujistěte se, že každý cílový počítač splňuje [minimální požadavky na instalaci](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Rozhodněte se o svých servisních potřebách.

  Pokud vaše společnost potřebuje zůstat na sadu funkcí déle, ale přesto chce získat pravidelné aktualizace údržby, naplánujte použít směrný plán údržby. Další informace naleznete ***v části Podpora starších verzí sady Visual Studio*** na stránce životního cyklu a [údržby produktu sady Visual Studio a](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio) také v tématu Postup: Aktualizace sady Visual Studio na stránce [směrného plánu obsluhy.](update-servicing-baseline.md)

  Pokud plánujete použít aktualizace údržby spolu s kumulativními aktualizacemi funkcí, můžete zvolit nejnovější bity.

* Rozhodněte o modelu aktualizace.

  Kde chcete, aby jednotlivé klientské počítače získaly aktualizace? Konkrétně se rozhodněte, zda chcete získat aktualizace z internetu nebo z místního podílu v celé společnosti. Pokud se pak rozhodnete použít místní sdílenou složku, rozhodněte se, zda jednotliví uživatelé mohou aktualizovat své vlastní klienty, nebo zda chcete, aby správce aktualizoval klienty programově.

* Rozhodněte se, které [úlohy a součásti](workload-and-component-ids.md?view=vs-2017) vaše společnost potřebuje.

* Rozhodněte se, zda chcete použít [soubor odpovědí](automated-installation-with-response-file.md?view=vs-2017) (který zjednodušuje správu podrobností v souboru skriptu).

* Rozhodněte se, zda chcete povolit zásady skupiny a zda chcete nakonfigurovat visual studio tak, aby zakázalo zpětnou vazbu zákazníků v jednotlivých počítačích.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 – Stažení souborů produktů sady Visual Studio

* [Vyberte úlohy a součásti,](workload-and-component-ids.md?view=vs-2019) které chcete nainstalovat.

* [Vytvořte sdílenou síťovou složku pro soubory produktů sady Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>Krok 2 – Vytvoření instalačního skriptu

* Vytvořte instalační skript, který k řízení instalace používá [parametry příkazového řádku.](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019)

  >[!NOTE]
  > Skripty můžete zjednodušit pomocí [souboru odpovědí](automated-installation-with-response-file.md?view=vs-2019). Nezapomeňte vytvořit soubor odpovědí, který obsahuje výchozí možnost instalace.

* (Nepovinné) [Použijte kód Product Key pro hromadnou licenci](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) jako součást instalačního skriptu, aby uživatelé nemuseli aktivovat software samostatně.

* (Nepovinné) Aktualizujte rozložení sítě a [můžete určit, kdy a odkud budou aktualizace produktu doručovány koncovým uživatelům](controlling-updates-to-visual-studio-deployments.md?view=vs-2019).

* (Nepovinné) Nastavte zásady registru, které ovlivňují nasazení sady Visual Studio, například kde jsou nainstalovány některé balíčky sdílené s jinými verzemi nebo instancemi, [kde jsou balíčky ukládány do mezipaměti](set-defaults-for-enterprise-deployments.md?view=vs-2019) nebo [zda jsou balíčky ukládány do mezipaměti](disable-or-move-the-package-cache.md?view=vs-2019).

* (Nepovinné) Nastavte zásady skupiny. Můžete také [nakonfigurovat visual studio zakázat zpětnou vazbu zákazníků](../ide/visual-studio-experience-improvement-program.md) na jednotlivých počítačích.

## <a name="step-3---deploy"></a>Krok 3 – nasazení

* Pomocí zvolené technologie nasazení můžete skript spustit na cílových vývojářských pracovních stanicích.

## <a name="step-4---deploy-updates"></a>Krok 4 – nasazení aktualizací

* [Aktualizujte své síťové umístění nejnovějšími aktualizacemi](update-a-network-installation-of-visual-studio.md?view=vs-2019) sady Visual Studio spuštěním příkazu, který jste v kroku 1 používali pravidelně, abyste přidali aktualizované součásti.

  Visual Studio můžete aktualizovat pomocí aktualizačního skriptu. Chcete-li tak [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) učinit, použijte parametr příkazového řádku.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 – (volitelné) Použití nástrojů sady Visual Studio

Máme k dispozici několik nástrojů, které vám pomohou [zjistit a spravovat nainstalované instance sady Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019) v klientských počítačích.

## <a name="advanced-configuration"></a>Pokročilá konfigurace

Ve výchozím nastavení umožňuje instalace sady Visual Studio vlastní zahrnutí typu do vyhledávání Bingze ze seznamu chyb F1 a odkazů na kód. Aplikaci Visual Studio můžete nakonfigurovat tak, aby zakázala mechanismus vyhledávání, aby nezahrnul a nezahrnul všechny vlastní typy uživatelů, a to změnou hodnoty následujícího klíče registru podle zásad:

**"PutCustomTypeInbingSearch" DWORD 0**

Registr je umístěn v adresáři *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\* v podregistru soukromého registru. Pokyny k otevření podregistru naleznete v [tématu úpravy registru instance sady Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 – Stažení souborů produktů sady Visual Studio

* [Vyberte úlohy a součásti,](workload-and-component-ids.md?view=vs-2017) které chcete nainstalovat.

* [Vytvořte sdílenou síťovou složku pro soubory produktů sady Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>Krok 2 – Vytvoření instalačního skriptu

* Vytvořte instalační skript, který k řízení instalace používá [parametry příkazového řádku.](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017)

  >[!NOTE]
  > Skripty můžete zjednodušit pomocí [souboru odpovědí](automated-installation-with-response-file.md?view=vs-2017). Nezapomeňte vytvořit soubor odpovědí, který obsahuje výchozí možnost instalace.

* (Nepovinné) [Použijte kód Product Key pro hromadnou licenci](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017) jako součást instalačního skriptu, aby uživatelé nemuseli aktivovat software samostatně.

* (Nepovinné) Aktualizujte rozložení sítě a [můžete určit, kdy a odkud budou aktualizace produktu doručovány koncovým uživatelům](controlling-updates-to-visual-studio-deployments.md?view=vs-2017).

* (Nepovinné) Nastavte zásady registru, které ovlivňují nasazení sady Visual Studio, například kde jsou nainstalovány některé balíčky sdílené s jinými verzemi nebo instancemi, [kde jsou balíčky ukládány do mezipaměti](set-defaults-for-enterprise-deployments.md?view=vs-2019) nebo [zda jsou balíčky ukládány do mezipaměti](disable-or-move-the-package-cache.md?view=vs-2017).

* (Nepovinné) Nastavte zásady skupiny. Můžete také [nakonfigurovat visual studio zakázat zpětnou vazbu zákazníků](../ide/visual-studio-experience-improvement-program.md) na jednotlivých počítačích.

## <a name="step-3---deploy"></a>Krok 3 – nasazení

* Pomocí zvolené technologie nasazení můžete skript spustit na cílových vývojářských pracovních stanicích.

## <a name="step-4---deploy-updates"></a>Krok 4 – nasazení aktualizací

* [Aktualizujte své síťové umístění nejnovějšími aktualizacemi](update-a-network-installation-of-visual-studio.md?view=vs-2017) sady Visual Studio spuštěním příkazu, který jste v kroku 1 používali pravidelně, abyste přidali aktualizované součásti.

  Visual Studio můžete aktualizovat pomocí aktualizačního skriptu. Chcete-li tak [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) učinit, použijte parametr příkazového řádku.

## <a name="step-5---optional-use-visual-studio-tools"></a>Krok 5 – (volitelné) Použití nástrojů sady Visual Studio

Máme k dispozici několik nástrojů, které vám pomohou [zjistit a spravovat nainstalované instance sady Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017) v klientských počítačích.

## <a name="advanced-configuration"></a>Pokročilá konfigurace

Ve výchozím nastavení umožňuje instalace sady Visual Studio vlastní zahrnutí typu do vyhledávání Bingze ze seznamu chyb F1 a odkazů na kód. Aplikaci Visual Studio můžete nakonfigurovat tak, aby zakázala mechanismus vyhledávání, aby nezahrnul a nezahrnul všechny vlastní typy uživatelů, a to změnou hodnoty následujícího klíče registru podle zásad:

**"PutCustomTypeInbingSearch" DWORD 0**

Registr je umístěn v adresáři *Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\* v podregistru soukromého registru. Pokyny k otevření podregistru naleznete v [tématu úpravy registru instance sady Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Instalace certifikátů požadovaných pro offline instalaci sady Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Import a export konfigurací instalace](import-export-installation-configurations.md)
* [Archiv nastavení sady Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Životní cyklus produktu Visual Studio a servis](/visualstudio/releases/2019/servicing/)
* [Synchronní nastavení automatického načtení](../extensibility/synchronously-autoloaded-extensions.md)
