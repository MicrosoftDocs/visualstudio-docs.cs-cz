---
title: Nastavení výchozích hodnot pro podniková nasazení
description: Přečtěte si o zásadách domény a dalších operacích konfigurace pro podniková nasazení sady Visual Studio.
ms.date: 04/13/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: cc88e6ffe91b111626fa76057742233527bf203f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306901"
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Nastavení výchozích hodnot pro podniková nasazení sady Visual Studio

Můžete nastavit zásady registru, které mají vliv na nasazení sady Visual Studio. Tyto zásady jsou globální pro počítač a ovlivňují:

- Kde jsou nainstalovány některé balíčky sdílené s jinými verzemi nebo instancemi
- Kde a zda jsou balíčky ukládány do mezipaměti
- Jak by se měly použít aktualizace správců

Některé z těchto zásad můžete nastavit pomocí [možností příkazového řádku](use-command-line-parameters-to-install-visual-studio.md), nastavením hodnot registru na počítači nebo jejich distribucí pomocí Zásady skupiny napříč organizací.

## <a name="registry-keys"></a>Klíče registru

K dispozici je několik míst, kde můžete nastavit výchozí nastavení podniku, a to buď prostřednictvím Zásady skupiny, nebo přímo v registru. Visual Studio vypadá sekvenčně a zjistí, jestli jsou nastavené nějaké podnikové zásady. Jakmile je v níže uvedeném pořadí zjištěna hodnota zásad, zbývající klíče se ignorují.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (v 64ech operačních systémech)

Některé hodnoty registru se nastaví automaticky při prvním použití, pokud už nejsou nastavené. Tento postup zajistí, že následné instalace budou používat stejné hodnoty. Tyto hodnoty jsou uloženy v druhém klíči registru `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` .

Můžete nastavit následující hodnoty registru:

::: moniker range="vs-2017"

| **Název**                      | **Typ**                    | **Výchozí**                                         | **Popis**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                   | `REG_SZ` nebo `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | Adresář, ve kterém jsou uloženy manifesty balíčku, volitelně i datové části. Další informace najdete v tématu [Zakázání nebo přesunutí stránky mezipaměť balíčku](disable-or-move-the-package-cache.md) .                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`      | `REG_DWORD`                 | 1                                                   | Udržujte datovou část balíčku i po jejich instalaci. Hodnotu můžete kdykoli změnit. Zakázáním této zásady odeberete všechny datové části balíčků v mezipaměti pro instanci, kterou opravíte nebo upravíte. Další informace najdete v tématu [Zakázání nebo přesunutí stránky mezipaměť balíčku](disable-or-move-the-package-cache.md) .                                                                                                                                                                             |
| `SharedInstallationPath`      | `REG_SZ` nebo `REG_EXPAND_SZ` | % ProgramFiles (x86)% \ Microsoft Visual Studio\Shared  | Adresář, ve kterém jsou nainstalovány některé balíčky sdílené mezi verzemi instancí sady Visual Studio. Hodnotu můžete kdykoli změnit, ale bude to mít vliv jenom na budoucí instalace. Jakékoli produkty, které jsou již nainstalovány do starého umístění, nesmí být přesunuty nebo nemusí fungovat správně.                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`  | `REG_DWORD`                 | 0                                                   | Zabrání instalačnímu programu stahovat aktualizace automaticky pro všechny nainstalované produkty sady Visual Studio. Hodnotu můžete kdykoli změnit.                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled` | `REG_DWORD`                 | 0                                                   | Umožňuje použít aktualizace správce na klientském počítači. Pokud tato hodnota chybí nebo je nastavená na 0, aktualizace správce se zablokují. Tato hodnota je určena pro administrativní použití. Další informace najdete v tématu [Povolení aktualizací správců](enabling-administrator-updates.md).                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`  | `REG_DWORD`                 | 0                                                   | Indikuje, že uživatel nechce dostávat aktualizace správce do sady Visual Studio. Absence hodnoty registru nebo nastavená hodnota 0 znamená, že uživatel sady Visual Studio chce dostávat aktualizace správce do sady Visual Studio. Toto je pro vývojáře uživatele (pokud mají na klientském počítači oprávnění správce). Další informace najdete v tématu [použití aktualizací správců](../install/applying-administrator-updates.md#understanding-configuration-options). |
| `UpdateConfigurationFile`     | `REG_SZ` nebo `REG_EXPAND_SZ` | % Složka ProgramData% \Microsoft\VisualStudio\updates.config | Cesta k souboru pro konfiguraci aktualizací pro správu. Další informace najdete v tématu [metody konfigurace aktualizace správce](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update).                                                                                                                                                                                                                                             |

::: moniker-end

::: moniker range="vs-2019"

| **Název**                         | **Typ**                    | **Výchozí**                                         | **Popis**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                      | `REG_SZ` nebo `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | Adresář, ve kterém jsou uloženy manifesty balíčku, volitelně i datové části. Další informace najdete v tématu [Zakázání nebo přesunutí stránky mezipaměť balíčku](disable-or-move-the-package-cache.md) .                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`         | `REG_DWORD`                 | 1                                                   | Udržujte datovou část balíčku i po jejich instalaci. Hodnotu můžete kdykoli změnit. Zakázáním této zásady odeberete všechny datové části balíčků v mezipaměti pro instanci, kterou opravíte nebo upravíte. Další informace najdete v tématu [Zakázání nebo přesunutí stránky mezipaměť balíčku](disable-or-move-the-package-cache.md) .                                                                                                                                                                             |
| `SharedInstallationPath`         | `REG_SZ` nebo `REG_EXPAND_SZ` | % ProgramFiles (x86)% \ Microsoft Visual Studio\Shared  | Adresář, ve kterém jsou nainstalovány některé balíčky sdílené mezi verzemi instancí sady Visual Studio. Hodnotu můžete kdykoli změnit, ale bude to mít vliv jenom na budoucí instalace. Jakékoli produkty, které jsou již nainstalovány do starého umístění, nesmí být přesunuty nebo nemusí fungovat správně.                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`     | `REG_DWORD`                 | 0                                                   | Zabrání instalačnímu programu stahovat aktualizace automaticky pro všechny nainstalované produkty sady Visual Studio. Hodnotu můžete kdykoli změnit.                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | Umožňuje použít aktualizace správce na klientském počítači. Pokud tato hodnota chybí nebo je nastavená na 0, aktualizace správce se zablokují. Tato hodnota je určena pro administrativní použití. Další informace najdete v tématu [Povolení aktualizací správců](enabling-administrator-updates.md).                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | Indikuje, že uživatel nechce dostávat aktualizace správce do sady Visual Studio. Absence hodnoty registru nebo nastavená hodnota 0 znamená, že uživatel sady Visual Studio chce dostávat aktualizace správce do sady Visual Studio. Toto je pro vývojáře uživatele (pokud mají na klientském počítači oprávnění správce). Další informace najdete v tématu [použití aktualizací správců](../install/applying-administrator-updates.md#understanding-configuration-options). |
| `UpdateConfigurationFile`        | `REG_SZ` nebo `REG_EXPAND_SZ` | % Složka ProgramData% \Microsoft\VisualStudio\updates.config | Cesta k souboru pro konfiguraci aktualizací pro správu. Další informace najdete v tématu [metody konfigurace aktualizace správce](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update).                                                                                                                                                                                                                                             |
| `BaselineStickinessVersions2019` | `REG_SZ` nebo `REG_EXPAND_SZ` | `16.7.0`                                            | Dílčí verze směrného plánu údržby, na které by měl klient zůstat. Další informace najdete v tématu [použití stránky aktualizace správců](../install/applying-administrator-updates.md#understanding-configuration-options) .                                                                                                                                                                                                                                                    |

::: moniker-end

::: moniker range=">=vs-2022"

| **Název**                         | **Typ**                    | **Výchozí**                                         | **Popis**                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|----------------------------------|-----------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CachePath`                      | `REG_SZ` nebo `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages       | Adresář, ve kterém jsou uloženy manifesty balíčku, volitelně i datové části. Další informace najdete v tématu [Zakázání nebo přesunutí stránky mezipaměť balíčku](disable-or-move-the-package-cache.md) .                                                                                                                                                                                                                                                                                        |
| `KeepDownloadedPayloads`         | `REG_DWORD`                 | 1                                                   | Udržujte datovou část balíčku i po jejich instalaci. Hodnotu můžete kdykoli změnit. Zakázáním této zásady odeberete všechny datové části balíčků v mezipaměti pro instanci, kterou opravíte nebo upravíte. Další informace najdete v tématu [Zakázání nebo přesunutí stránky mezipaměť balíčku](disable-or-move-the-package-cache.md) .                                                                                                                                                                             |
| `SharedInstallationPath`         | `REG_SZ` nebo `REG_EXPAND_SZ` | %ProgramFiles%\Microsoft Visual Studio\Shared       | Adresář, ve kterém jsou nainstalovány některé balíčky sdílené mezi verzemi instancí sady Visual Studio. Hodnotu můžete kdykoli změnit, ale bude to mít vliv jenom na budoucí instalace. Jakékoli produkty, které jsou již nainstalovány do starého umístění, nesmí být přesunuty nebo nemusí fungovat správně.                                                                                                                                                                                  |
| `BackgroundDownloadDisabled`     | `REG_DWORD`                 | 0                                                   | Zabrání instalačnímu programu stahovat aktualizace automaticky pro všechny nainstalované produkty sady Visual Studio. Hodnotu můžete kdykoli změnit.                                                                                                                                                                                                                                                                                                                                             |
| `AdministratorUpdatesEnabled`    | `REG_DWORD`                 | 0                                                   | Umožňuje použít aktualizace správce na klientském počítači. Pokud tato hodnota chybí nebo je nastavená na 0, aktualizace správce se zablokují. Tato hodnota je určena pro administrativní použití. Další informace najdete v tématu [Povolení aktualizací správců](enabling-administrator-updates.md).                                                                                                                                                                                      |
| `AdministratorUpdatesOptOut`     | `REG_DWORD`                 | 0                                                   | Indikuje, že uživatel nechce dostávat aktualizace správce do sady Visual Studio. Absence hodnoty registru nebo nastavená hodnota 0 znamená, že uživatel sady Visual Studio chce dostávat aktualizace správce do sady Visual Studio. Toto je pro vývojáře uživatele (pokud mají na klientském počítači oprávnění správce). Další informace najdete v tématu [použití aktualizací správců](../install/applying-administrator-updates.md#understanding-configuration-options). |
| `UpdateConfigurationFile`        | `REG_SZ` nebo `REG_EXPAND_SZ` | % Složka ProgramData% \Microsoft\VisualStudio\updates.config | Cesta k souboru pro konfiguraci aktualizací pro správu. Další informace najdete v tématu [metody konfigurace aktualizace správce](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update).                                                                                                                                                                                                                                             |
| `BaselineStickinessVersions2019` | `REG_SZ` nebo `REG_EXPAND_SZ` | `16.7.0`                                            | Dílčí verze směrného plánu údržby, na které by měl klient zůstat. Další informace najdete v tématu [použití stránky aktualizace správců](../install/applying-administrator-updates.md#understanding-configuration-options) .                                                                                                                                                                                                                                                    |

::: moniker-end

> [!IMPORTANT]
> Pokud `CachePath` zásady registru po instalaci změníte, je nutné přesunout existující mezipaměť balíčku do nového umístění a zajistit, aby byla zabezpečená, aby byla zajištěna `SYSTEM` `Administrators` Úplná kontrola a měla by mít oprávnění `Everyone` ke čtení.
> Nepovedlo se přesunout existující mezipaměť nebo ji zabezpečit, může to způsobit problémy s budoucími instalacemi.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio](install-visual-studio.md)
- [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
- [Použití aktualizací správců](applying-administrator-updates.md)
- [Zakázání nebo přesunutí mezipaměti balíčku](disable-or-move-the-package-cache.md)
- [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
