---
title: Příručka správce sady Visual Studio
titleSuffix: ''
description: Přečtěte si další informace o nasazení Visual Studio v podnikovém prostředí.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ba41c545c2af2e0490ef0410fde7849706123940
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306706"
---
# <a name="visual-studio-administrator-guide"></a>Příručka správce sady Visual Studio

V podnikových prostředích správci systému obvykle nasadí instalace koncovým uživatelům ze sdílené síťové složky nebo pomocí softwaru pro správu systémů. Modul pro nastavení Visual Studio jsme navrhli pro podporu podnikového nasazení tím, že správcům systému poskytujeme možnost vytvořit umístění síťové instalace, předem nakonfigurovat výchozí nastavení instalace, nasadit kód Product Key během procesu instalace a spravovat aktualizace produktů po úspěšném zavedení.

Tato příručka pro správce poskytuje pokyny založené na scénářích pro podnikové nasazení v síťových prostředích.

## <a name="before-you-begin"></a>Než začnete

Než nasadíte Visual Studio ve vaší organizaci, musíte udělat několik rozhodnutí a provést úkoly:

::: moniker range=">=vs-2019"

* Ujistěte se, že každý cílový počítač splňuje [minimální požadavky na instalaci.](/visualstudio/releases/2019/system-requirements/)

::: moniker-end

::: moniker range="vs-2017"

* Ujistěte se, že každý cílový počítač splňuje [minimální požadavky na instalaci.](/visualstudio/productinfo/vs2017-system-requirements-vs/)

::: moniker-end

* Rozhodněte se o potřebách údržby.

  Pokud vaše společnost potřebuje mít nastavenou sadu funkcí déle, ale přesto chce pravidelně dostávat servisní aktualizace, naplánujte si použití servisního směrného plánu. Další informace najdete v části Možnosti podpory pro zákazníky s produkty [Enterprise Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers) ***Professional*** na stránce životního cyklu [a](update-servicing-baseline.md) údržby produktu Visual Studio také v části Aktualizace Visual Studio na stránce směrného plánu údržby.

* Rozhodněte o modelu aktualizace.

  Odkud chcete získat aktualizace produktů z jednotlivých klientských počítačů? Konkrétně se rozhodněte, jestli chcete, aby klient získá aktualizace z internetu nebo z místní sdílené složky v celé společnosti. Pokud se pak rozhodnete použít místní sdílené složky, rozhodněte se, jestli mohou jednotliví uživatelé aktualizovat své vlastní klienty, nebo jestli chcete, aby klienty prostřednictvím kódu programu aktualizovat správce. Je nejlepší, když tato rozhodnutí byla učiněna před původní instalací na klientském počítači. Další informace najdete v [tématu Vytvoření síťové instalace služby Visual Studio](../install/create-a-network-installation-of-visual-studio.md).

  Je možné aktualizovat rozložení síťové instalace systému Visual Studio nejnovějšími aktualizacemi produktů, aby bylo možné ho použít jak jako instalační bod pro nejnovější aktualizaci Visual Studio, tak pro údržbu instalací, které jsou už nasazené na klientských pracovních stanicích. Další informace najdete v tématu Aktualizace síťové instalace [služby Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Organizace, které využívají nástroje podnikového nasazení, mohou využít skutečnost, Visual Studio jsou k dispozici na webu Microsoft Update Catalog a Windows Server Update Services. Další informace najdete v tématu [Povolení aktualizací pro správce a](../install/enabling-administrator-updates.md) Použití aktualizací [správce](../install/applying-administrator-updates.md).

  Pro počítače, které nejsou připojené k internetu, je vytvoření minimálního rozložení nejjednodušším a nejrychlejším způsobem, jak aktualizovat offline Visual Studio instance. Další informace najdete v tématu [Aktualizace Visual Studio s minimálním offline rozložením.](update-minimal-layout.md)

::: moniker range=">=vs-2019"

* Rozhodněte [se, jaké úlohy a komponenty](workload-and-component-ids.md?view=vs-2019&preserve-view=true) vaše společnost potřebuje.

* Rozhodněte, jestli se má [použít soubor odpovědí](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) (který zjednodušuje správu podrobností v souboru skriptu).

::: moniker-end

::: moniker range="vs-2017"

* Rozhodněte [se, jaké úlohy a komponenty](workload-and-component-ids.md?view=vs-2017&preserve-view=true) vaše společnost potřebuje.

* Rozhodněte, jestli se má [použít soubor odpovědí](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (který zjednodušuje správu podrobností v souboru skriptu).

::: moniker-end

* Rozhodněte se, jestli chcete povolit Zásady skupiny, a pokud chcete nakonfigurovat Visual Studio zakázat zpětnou vazbu zákazníků na jednotlivých počítačích.

::: moniker range=">=vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 : Stažení Visual Studio souborů produktu

* [Vyberte úlohy a komponenty,](workload-and-component-ids.md?view=vs-2019&preserve-view=true) které chcete nainstalovat.

* [Vytvořte síťovou složku pro Visual Studio produktových souborů](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Krok 2 – sestavení instalačního skriptu

* Sestavte instalační skript, který [k řízení](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) instalace používá parametry příkazového řádku.

  >[!NOTE]
  > Skripty můžete zjednodušit pomocí souboru [odpovědí](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true). Nezapomeňte vytvořit soubor odpovědí, který obsahuje výchozí možnost instalace.

* (Volitelné) [Kód Product Key multilicenční](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true) licence použijte jako součást instalačního skriptu, aby uživatelé nepou3/4ebovali aktivovat software samostatně.

* (Volitelné) Aktualizujte rozložení sítě, abyste mohli řídit, kdy a odkud se aktualizace [produktů doručí koncovým uživatelům.](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true)

* (Volitelné) Nastavte zásady [registru,](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) které mají vliv na nasazení služby Visual Studio, například kde jsou nainstalovány některé balíčky sdílené s jinými verzemi nebo instancemi, kde se balíčky uchová v mezipaměti nebo jestli jsou balíčky uložené [v mezipaměti.](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true)

* (Volitelné) Nastavte Zásady skupiny. Můžete také [nakonfigurovat, Visual Studio zakázat zpětnou vazbu od zákazníků](../ide/visual-studio-experience-improvement-program.md) na jednotlivých počítačích.

## <a name="step-3---deploy-updates"></a>Krok 3 – nasazení aktualizací

Pomocí technologie nasazení podle vaší volby můžete svůj skript spouštět na cílových vývojářských pracovních stanicích.

* [Aktualizujte umístění v síti pomocí](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) nejnovějších aktualizací Visual Studio spuštěním příkazu, který jste pravidelně použili v kroku 1 k přidání aktualizovaných komponent.

  Aktualizace můžete Visual Studio pomocí aktualizačního skriptu. K tomu použijte parametr [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) příkazového řádku.

  K nasazení aktualizací Visual Studio z webu Windows Server Update Services nebo Microsoft Update Catalog můžete použít nástroje, jako je System Center Správce konfigurace.  Další informace [najdete v tématu Instalace aktualizací pro](applying-administrator-updates.md) správce. 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Krok 4 – (volitelné) Ověření Visual Studio pomocí nástrojů pro správu

K dispozici je několik nástrojů, které vám pomůžou detekovat a [spravovat Visual Studio instancí na](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) klientských počítačích.

## <a name="advanced-configuration"></a>Pokročilá konfigurace

Ve výchozím nastavení instalace Visual Studio zahrnutí vlastního typu do vyhledávání Bingu ze seznamu chyb F1 a odkazů na kód. Můžete nakonfigurovat Visual Studio, aby mechanismus vyhledávání zakažte zahrnutí všech vlastních typů uživatelů změnou hodnoty následujícího klíče registru podle zásad:

**"PutCustomTypeInBingSearch" DWORD 0**

Registr se nachází v adresáři *Software\Microsoft\VisualStudio\16.0_{Id_instance}\Roslyn\Internal\Diagnostics vašeho privátního \* podregistru registru. Pokyny k otevření podregistru registru najdete v tématu [úprava registru pro instanci Visual Studio .](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance)

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Krok 1 : Stažení Visual Studio souborů produktu

* [Vyberte úlohy a komponenty,](workload-and-component-ids.md?view=vs-2017&preserve-view=true) které chcete nainstalovat.

* [Vytvořte síťovou složku pro Visual Studio produktových souborů](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Krok 2 – sestavení instalačního skriptu

* Sestavte instalační skript, který [k řízení](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) instalace používá parametry příkazového řádku.

  >[!NOTE]
  > Skripty můžete zjednodušit pomocí souboru [odpovědí](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true). Nezapomeňte vytvořit soubor odpovědí, který obsahuje výchozí možnost instalace.

* (Volitelné) [Kód Product Key multilicenční](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) licence použijte jako součást instalačního skriptu, aby uživatelé nepou3/4ebovali aktivovat software samostatně.

* (Volitelné) Aktualizujte rozložení sítě, abyste mohli řídit, kdy a odkud se aktualizace [produktů doručí koncovým uživatelům.](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true)

* (Volitelné) Nastavte zásady [registru,](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) které mají vliv na nasazení služby Visual Studio, například kde jsou nainstalovány některé balíčky sdílené s jinými verzemi nebo instancemi, kde se balíčky uchová v mezipaměti nebo jestli jsou balíčky uložené [v mezipaměti.](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true)

* (Volitelné) Nastavte Zásady skupiny. Můžete také [nakonfigurovat, Visual Studio zakázat zpětnou vazbu od zákazníků](../ide/visual-studio-experience-improvement-program.md) na jednotlivých počítačích.

## <a name="step-3---deploy-updates"></a>Krok 3 – nasazení aktualizací

Pomocí technologie nasazení podle vaší volby můžete svůj skript spouštět na cílových vývojářských pracovních stanicích.

* [Aktualizujte umístění v síti pomocí](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) nejnovějších aktualizací Visual Studio spuštěním příkazu, který jste pravidelně použili v kroku 1 k přidání aktualizovaných komponent.

  Aktualizace můžete Visual Studio pomocí aktualizačního skriptu. K tomu použijte parametr [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) příkazového řádku.

  K nasazení aktualizací Visual Studio z webu Windows Server Update Services nebo Microsoft Update Catalog můžete použít nástroje, jako je System Center Správce konfigurace. Další informace najdete v tématu [Instalace aktualizací pro správce.](applying-administrator-updates.md)

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Krok 4 – (volitelné) Ověření Visual Studio pomocí nástrojů pro správu

K dispozici je několik nástrojů, které vám pomůžou detekovat a [spravovat Visual Studio instancí na](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) klientských počítačích.

## <a name="advanced-configuration"></a>Pokročilá konfigurace

Ve výchozím nastavení instalace Visual Studio zahrnutí vlastního typu do vyhledávání Bingu ze seznamu chyb F1 a odkazů na kód. Můžete nakonfigurovat Visual Studio, aby mechanismus vyhledávání zakažte zahrnutí všech vlastních typů uživatelů změnou hodnoty následujícího klíče registru podle zásad:

**"PutCustomTypeInBingSearch" DWORD 0**

Registr se nachází v `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` adresáři vašeho privátního podregistru registru. Pokyny k otevření podregistru registru najdete v tématu [úprava registru pro instanci Visual Studio .](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance)

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Povolení aktualizací pro správce](enabling-administrator-updates.md)
* [Instalace aktualizací správce](applying-administrator-updates.md)
* [Příklady parametrů příkazového řádku](command-line-parameter-examples.md)
* [Instalace certifikátů požadovaných pro Visual Studio offline instalaci](install-certificates-for-visual-studio-offline.md)
* [Import a export konfigurací instalace](import-export-installation-configurations.md)
* [Visual Studio nastavení archivů](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Visual Studio životního cyklu a údržby produktů](/visualstudio/releases/2019/servicing/)
* [Synchronní nastavení automatického načítání](../extensibility/synchronously-autoloaded-extensions.md)
