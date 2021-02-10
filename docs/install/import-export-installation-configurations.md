---
title: Import a export konfigurací instalace
titleSuffix: ''
description: Naučte se Exportovat konfiguraci instalace do souboru. vsconfig, abyste mohli sdílet s ostatními a jak je naimportovat do klonování.
ms.date: 05/18/2019
ms.topic: how-to
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 043622d08b5389db8bf4cce80450f62c070a0ace
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949464"
---
# <a name="import-or-export-installation-configurations"></a>Import a export konfigurací instalace

Visual Studio můžete nakonfigurovat v celé organizaci pomocí konfiguračních souborů instalace. Pokud to chcete provést, jednoduše exportujte úlohy a informace o komponentách do souboru. vsconfig pomocí instalačního programu sady Visual Studio. Pak můžete importovat konfiguraci do nových nebo existujících instalací a sdílet je s ostatními.

Jak na to:

::: moniker range="vs-2017"

> [!NOTE]
> Tato funkce je k dispozici pouze v aplikaci Visual Studio 2017 verze 15,9 a novější.

::: moniker-end

## <a name="export-a-configuration"></a>Export konfigurace

Konfigurační soubor instalace můžete exportovat buď z dříve nainstalované instance sady Visual Studio, nebo z aplikace, kterou právě instalujete.

1. Otevřete Instalační program pro Visual Studio.

1. Na kartě Produkt klikněte na tlačítko **Další** a pak vyberte **Exportovat konfiguraci**.

   ![Export konfigurace z karty produktu v instalačním programu sady Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Vyhledejte nebo zadejte umístění, kam chcete soubor. vsconfig uložit, a pak zvolte možnost **zkontrolovat podrobnosti**.

   ![Export konfigurace z instalačního programu sady Visual Studio](../install/media/vs-2019/export-configuration-confirmation.png)

1. Ujistěte se, že máte požadované úlohy a požadované součásti, a pak zvolte **exportovat**.

## <a name="import-a-configuration"></a>Import konfigurace

Až budete připraveni k importu konfiguračního souboru instalace, postupujte podle těchto kroků.

1. Otevřete Instalační program pro Visual Studio.

1. Na kartě Produkt klikněte na tlačítko **Další** a pak vyberte **Importovat konfiguraci**.

1. Vyhledejte soubor. vsconfig, který chcete importovat, a poté zvolte možnost **zkontrolovat podrobnosti**.

1. Ujistěte se, že máte požadované úlohy a požadované součásti, a pak zvolte **Zavřít**.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Automaticky instalovat chybějící součásti

**Novinka v aplikaci Visual Studio 2019**: Když uložíte soubor. vsconfig do kořenového adresáře řešení a pak otevřete řešení, Visual Studio automaticky zjistí, které součásti chybějí, a vyzve k jejich instalaci.

![Průzkumník řešení navrhuje další komponenty](../install/media/vs-2019/solution-explorer-config-file.png)

Soubor. vsconfig můžete také vygenerovat přímo z Průzkumník řešení.

1. Klikněte pravým tlačítkem na soubor řešení.

1. Vyberte **Přidat** > **konfigurační soubor instalace**.

1. Potvrďte umístění, kam chcete soubor. vsconfig uložit, a pak zvolte **zkontrolovat podrobnosti**.

1. Ujistěte se, že máte požadované úlohy a požadované součásti, a pak zvolte **exportovat**.

::: moniker-end

> [!NOTE]
> Další informace najdete v blogovém příspěvku věnovaném [konfiguraci sady Visual Studio v rámci vaší organizace](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Řízení aktualizací nasazení sady Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Nastavení výchozích hodnot pro podniková nasazení](set-defaults-for-enterprise-deployments.md)
