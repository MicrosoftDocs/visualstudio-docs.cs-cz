---
title: Výběr umístění instalací
description: Zjistěte, jak snížit nároky na instalaci Visual Studio na systémové jednotce změnou umístění mezipaměti pro stahování, sdílených komponent, sady SDK a nástrojů na různé jednotky. Přesuňte například některé soubory z jednotky C na jednotku D.
ms.date: 03/30/2019
ms.custom: acquisition
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0e780cca2515118b92b71c406368d29424f7017c
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307619"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Vyberte umístění instalace v Visual Studio

::: moniker range=">=vs-2019"

Změnou umístění některých Visual Studio můžete snížit nároky na instalaci systému na systémové jednotce. Konkrétně můžete použít jiné umístění pro mezipaměť pro stahování, sdílené komponenty, sady SDK a soubory nástrojů.

::: moniker-end

::: moniker range="vs-2017"

**Novinka ve verzi 15.7:** Změnou umístění některých svých souborů můžete snížit nároky na instalaci Visual Studio na systémové jednotce. Konkrétně můžete použít jiné umístění pro mezipaměť pro stahování, sdílené komponenty, sady SDK a soubory nástrojů.

::: moniker-end

   > [!NOTE]
   > Existuje několik nástrojů a sady SDK, které mají různá pravidla pro jejich instalaci. Takové nástroje a sady SDK se na systémové jednotce instaluje i v případě, že zvolíte jiné umístění.

Jste připraveni začít? Jak na to:

::: moniker range="vs-2017"

1. Při instalaci Visual Studio zvolte kartu **Umístění** instalace.

   ![Visual Studio 2017 – Výběr umístění instalace](media/vs-installation-locations.png "Vyberte umístění instalace.")

1. V části **Visual Studio IDE** přijměte výchozí nastavení. Visual Studio nainstaluje základní produkt a obsahuje soubory specifické pro tuto verzi Visual Studio.

   ![Visual Studio integrovaného vývojového prostředí (IDE) na kartě Umístění instalace](media/vs-installation-locations-ide.png "Přijměte výchozí hodnotu pro Visual Studio IDE na kartě Umístění instalace.")

   > [!TIP]
   > Pokud je vaše systémová jednotka SSD (solid-state drive), doporučujeme přijmout výchozí umístění na systémové jednotce. Důvod? Když vyvíjíte s Visual Studio, čtete z a zapisujete do mnoha souborů, což zvyšuje aktivitu V/V disku. Pro zvládnutí zatížení je nejlepší zvolit nejrychlejší jednotku.

1. V části **Download cache** (Stáhnout mezipaměť) rozhodněte, jestli chcete zachovat mezipaměť pro stahování, a pak se rozhodněte, kam chcete ukládat soubory.

     ![Část Stáhnout mezipaměť na kartě Umístění instalace](media/vs-installation-locations-cache.png "Zvolte, jestli se má mezipaměť pro stahování po instalaci zachovat, a pak určete jednotku, do které chcete ukládat soubory.")

    1. Zaškrtněte nebo zrušte zaškrtnutí políčka Keep download cache after the installation (Zachovat **mezipaměť pro stahování po instalaci).**

       Pokud se rozhodnete neuchovat mezipaměť pro stahování, umístění se použije pouze dočasně. Tato akce neovlivní nebo odstraní soubory z předchozích instalací.

    1. Určete jednotku, do které chcete ukládat instalační soubory a manifesty z mezipaměti pro stahování.

        Pokud například vyberete úlohu Vývoj desktopových aplikací pomocí C++, dočasně požadovaná velikost je 1,58 GB na systémové jednotce, která se pak po dokončení instalace uchová.

       > [!IMPORTANT]
       > Toto umístění se nastaví při první instalaci a později ho nebude možné změnit v uživatelském rozhraní instalačního programu. Místo toho musíte [k přesunutí mezipaměti pro stahování](use-command-line-parameters-to-install-visual-studio.md) použít parametry příkazového řádku.

1. V části **Sdílené součásti, nástroje** a sady SDK určete jednotku, kam chcete uložit soubory, které jsou sdíleny vedle sebe, Visual Studio instalace. V tomto adresáři jsou také uložené sady SDK a nástroje.

   ![Část Sdílené komponenty, nástroje a sady SDK na kartě Umístění instalace](media/vs-installation-locations-shared.png "Zadejte umístění, kam chcete ukládat sdílené komponenty, nástroje a sady SDK.")

::: moniker-end

::: moniker range=">=vs-2019"

1. Při instalaci Visual Studio zvolte kartu **Umístění** instalace.

   ![Visual Studio 2019 – Výběr umístění instalace](media/vs-2019/vs-installer-installation-locations.png "Vyberte umístění instalace.")

1. V části **Visual Studio IDE** přijměte výchozí nastavení. Visual Studio nainstaluje základní produkt a obsahuje soubory specifické pro tuto verzi Visual Studio.

   > [!TIP]
   > Pokud je vaše systémová jednotka SSD (solid-state drive), doporučujeme přijmout výchozí umístění na systémové jednotce. Důvod? Když vyvíjíte s Visual Studio, čtete z a zapisujete do mnoha souborů, což zvyšuje aktivitu V/V disku. Pro zvládnutí zatížení je nejlepší zvolit nejrychlejší jednotku.

1. V části **Download cache** (Stáhnout mezipaměť) rozhodněte, jestli chcete zachovat mezipaměť pro stahování, a pak se rozhodněte, kam chcete ukládat soubory.

    * Zaškrtněte nebo zrušte zaškrtnutí políčka Keep download cache after the installation (Zachovat **mezipaměť pro stahování po instalaci).**

       Pokud se rozhodnete neuchovat mezipaměť pro stahování, umístění se použije pouze dočasně. Tato akce neovlivní nebo odstraní soubory z předchozích instalací.

    * Určete jednotku, do které chcete ukládat instalační soubory a manifesty z mezipaměti pro stahování.

        Pokud například vyberete úlohu Vývoj desktopových aplikací pomocí C++, dočasně požadovaná velikost je 1,58 GB na systémové jednotce, která se pak po dokončení instalace uchová.

       > [!IMPORTANT]
       > Toto umístění se nastaví při první instalaci a později ho nebude možné změnit v uživatelském rozhraní instalačního programu. Místo toho musíte [k přesunutí mezipaměti pro stahování](use-command-line-parameters-to-install-visual-studio.md) použít parametry příkazového řádku.

1. V části **Sdílené komponenty, nástroje** a sady SDK se používá stejná jednotka, kterou jste zvolili v části Stažení mezipaměti. Adresář \Microsoft\VisualStudio\Shared Visual Studio ukládá soubory, které jsou sdíleny vedle sebe, Visual Studio instalace. V tomto adresáři jsou také uložené sady SDK a nástroje.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](update-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
