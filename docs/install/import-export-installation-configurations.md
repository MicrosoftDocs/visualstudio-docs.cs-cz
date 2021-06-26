---
title: Import a export konfigurací instalace
titleSuffix: ''
description: Zjistěte, jak exportovat konfiguraci instalace do souboru .vsconfig a sdílet ji s ostatními a jak ji importovat ke klonování.
ms.date: 05/18/2019
ms.topic: how-to
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 33ee25da51d5243daa67be53f68c50ede76219b2
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112925225"
---
# <a name="import-or-export-installation-configurations"></a>Import a export konfigurací instalace

V rámci organizace Visual Studio konfigurační soubory instalace. Stačí jednoduše exportovat informace o úlohách a komponentách do souboru .vsconfig pomocí instalačního Visual Studio souborů. Potom můžete konfiguraci importovat do nových nebo existujících instalací a sdílet je také s ostatními.

Jak na to:

::: moniker range="vs-2017"

> [!NOTE]
> Tato funkce je dostupná jenom v Visual Studio 2017 verze 15.9 a novější.

::: moniker-end

## <a name="export-a-configuration"></a>Export konfigurace

Můžete se rozhodnout exportovat konfigurační soubor instalace z dříve nainstalované instance Visual Studio nebo z té, kterou právě instalujete.

1. Otevřete Instalační program pro Visual Studio.

1. Na kartě product (Produkt) zvolte **tlačítko More** (Další) a pak **vyberte Export configuration (Exportovat konfiguraci).**

   ![Export konfigurace z karty produktu v instalačním Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Vyhledejte nebo zadejte umístění, kam chcete soubor .vsconfig **uložit,** a pak zvolte Zkontrolovat podrobnosti .

   ![Export konfigurace z instalačního Visual Studio serveru](../install/media/vs-2019/export-configuration-confirmation.png)

1. Ujistěte se, že máte úlohy a komponenty, které chcete, a pak zvolte **Exportovat.**

## <a name="import-a-configuration"></a>Import konfigurace

Až budete připraveni importovat konfigurační soubor instalace, postupujte podle těchto kroků.

1. Otevřete Instalační program pro Visual Studio.

1. Na kartě product (Produkt) zvolte **tlačítko More** (Další) a pak vyberte **Import configuration (Importovat konfiguraci).**

1. Vyhledejte soubor .vsconfig, který chcete importovat, a pak zvolte **Zkontrolovat podrobnosti**.

1. Ujistěte se, že máte úlohy a komponenty, které chcete, a pak zvolte **Zavřít.**

::: moniker range=">=vs-2019"

## <a name="automatically-install-missing-components"></a>Automatická instalace chybějících komponent

**Novinka v Visual Studio 2019:** Když uložíte soubor .vsconfig do kořenového adresáře řešení a pak otevřete řešení, Visual Studio automaticky zjistí, které součásti chybí, a vyzve vás k jejich instalaci.

![Průzkumník řešení navrhuje další komponenty](../install/media/vs-2019/solution-explorer-config-file.png)

Soubor .vsconfig můžete také vygenerovat přímo z Průzkumník řešení.

1. Klikněte pravým tlačítkem na soubor řešení.

1. Zvolte **Přidat** > **konfigurační soubor instalace.**

1. Potvrďte umístění, kam chcete soubor .vsconfig uložit, a pak zvolte **Zkontrolovat podrobnosti**.

1. Ujistěte se, že máte úlohy a komponenty, které chcete, a pak zvolte **Exportovat.**

::: moniker-end

> [!NOTE]
> Další informace najdete v blogovém příspěvku o konfiguraci Visual Studio v celé organizaci pomocí [.vsconfig.](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Vytvoření síťové instalace Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizace síťové instalace Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Řízení aktualizací nasazení sady Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Nastavení výchozích hodnot pro podniková nasazení](set-defaults-for-enterprise-deployments.md)
