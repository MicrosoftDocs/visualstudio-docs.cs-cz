---
title: Import a export konfigurací instalace
titleSuffix: ''
description: Přečtěte si, jak exportovat konfiguraci instalace do souboru .vsconfig, který chcete sdílet s ostatními, a jak ji importovat do klonování.
ms.date: 05/18/2019
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- import installation configuration
- export installation configuration
- install Visual Studio
- Visual Studio installer
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 12d22334094b848350d44d245685532fed196389
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114840"
---
# <a name="import-or-export-installation-configurations"></a>Import a export konfigurací instalace

Visual Studio můžete nakonfigurovat v celé organizaci pomocí konfiguračních souborů instalace. Chcete-li tak učinit, jednoduše exportujte informace o pracovním vytížení a součásti do souboru .vsconfig pomocí instalačního programu sady Visual Studio. Konfiguraci pak můžete importovat do nových nebo existujících instalací a sdílet je také s ostatními.

Jak na to:

::: moniker range="vs-2017"

> [!NOTE]
> Tato funkce je k dispozici pouze ve Visual Studiu 2017 verze 15.9 a novější.

::: moniker-end

## <a name="export-a-configuration"></a>Export konfigurace

Můžete exportovat instalační konfigurační soubor z dříve nainstalované instance sady Visual Studio nebo z instance, kterou právě instalujete.

1. Otevřete Instalační službu sady Visual Studio.

1. Na kartě produktu zvolte tlačítko **Další** a pak vyberte **Exportovat konfiguraci**.

   ![Export konfigurace z karty produktu v instalačním programu sady Visual Studio](../install/media/vs-2019/vs-installer-export-config.png)

1. Vyhledejte nebo zadejte umístění, kam chcete uložit soubor .vsconfig, a pak zvolte **Zkontrolovat podrobnosti**.

   ![Export konfigurace z instalačního programu sady Visual Studio](../install/media/vs-2019/export-configuration-confirmation.png)

1. Ujistěte se, že máte požadované úlohy a součásti, a pak zvolte **Exportovat**.

## <a name="import-a-configuration"></a>Import konfigurace

Až budete připraveni importovat konfigurační soubor instalace, postupujte takto.

1. Otevřete Instalační službu sady Visual Studio.

1. Na kartě produktu zvolte tlačítko **Další** a pak vyberte **Importovat konfiguraci**.

1. Vyhledejte soubor .vsconfig, který chcete importovat, a pak zvolte **Zkontrolovat podrobnosti**.

1. Ujistěte se, že máte požadované úlohy a součásti a pak zvolte **Zavřít**.

::: moniker range="vs-2019"

## <a name="automatically-install-missing-components"></a>Automatická instalace chybějících součástí

**Novinka ve Visual Studiu 2019**: Když uložíte soubor .vsconfig do kořenového adresáře řešení a pak otevřete řešení, Visual Studio automaticky zjistí, které součásti chybí, a vyzve vás k jejich instalaci.

![Průzkumník řešení navrhuje další součásti](../install/media/vs-2019/solution-explorer-config-file.png)

Soubor .vsconfig můžete také vygenerovat přímo z Průzkumníka řešení.

1. Klikněte pravým tlačítkem myši na soubor řešení.

1. Zvolte **Přidat** > **konfigurační soubor instalace**.

1. Potvrďte umístění, kam chcete soubor .vsconfig uložit, a pak zvolte **Zkontrolovat podrobnosti**.

1. Ujistěte se, že máte požadované úlohy a součásti, a pak zvolte **Exportovat**.

::: moniker-end

> [!NOTE]
> Další informace naleznete v tématu Konfigurace sady Visual Studio v celé organizaci pomocí příspěvku blogu [.vsconfig.](https://devblogs.microsoft.com/setup/configure-visual-studio-across-your-organization-with-vsconfig/)

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Vytvoření síťové instalace sady Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Řízení aktualizací nasazení sady Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Nastavení výchozích hodnot pro podniková nasazení](set-defaults-for-enterprise-deployments.md)
