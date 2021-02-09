---
title: Výběr umístění instalací
description: Zjistěte, jak omezit nároky na instalaci sady Visual Studio na systémovou jednotku tím, že změníte umístění mezipaměti pro stahování, sdílené komponenty, sady SDK a nástroje na různé jednotky. Například přesuňte některé soubory z jednotky C do jednotky D.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 4db3a31c8baa578a17d14b3a740ff40a444ba208
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868631"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Vybrat umístění instalace v aplikaci Visual Studio

::: moniker range="vs-2019"

Nároky na instalaci sady Visual Studio můžete snížit na systémové jednotce změnou umístění některých z jeho souborů. Konkrétně můžete použít jiné umístění pro mezipaměť pro stahování, sdílené komponenty, sady SDK a soubory nástrojů.

::: moniker-end

::: moniker range="vs-2017"

**Novinka ve verzi 15,7**: můžete snížit nároky na instalaci sady Visual Studio na systémové jednotce změnou umístění některých z jeho souborů. Konkrétně můžete použít jiné umístění pro mezipaměť pro stahování, sdílené komponenty, sady SDK a soubory nástrojů.

::: moniker-end

   > [!NOTE]
   > Existují některé nástroje a sady SDK, které mají různá pravidla, na jejichž základě je možné je nainstalovat. Tyto nástroje a sady SDK jsou nainstalovány na systémové jednotce i v případě, že zvolíte jiné umístění.

Jste připraveni začít? Jak na to:

::: moniker range="vs-2017"

1. Při instalaci sady Visual Studio vyberte kartu **umístění instalace** .

   ![Visual Studio 2017 – výběr umístění instalace](media/vs-installation-locations.png "Vyberte umístění instalace.")

1. V části **Visual Studio IDE** přijměte výchozí nastavení. Visual Studio nainstaluje základní produkt a obsahuje soubory, které jsou specifické pro tuto verzi sady Visual Studio.

   ![Část IDE sady Visual Studio na kartě umístění instalace](media/vs-installation-locations-ide.png "V části rozhraní IDE sady Visual Studio na kartě umístění instalace přijměte výchozí hodnotu.")

   > [!TIP]
   > Pokud je systémová jednotka SSD (Solid-State Drive), doporučujeme, abyste přijali výchozí umístění na systémové jednotce. Důvod? Při vývoji v aplikaci Visual Studio můžete číst a zapisovat do velkého množství souborů, které zvyšují aktivitu v/v disku. Nejlepší je zvolit nejrychlejší disk pro zpracování zatížení.

1. V části **mezipaměť pro stahování** se rozhodněte, jestli chcete uchovat mezipaměť pro stahování, a pak se rozhodněte, kam chcete ukládat soubory.

     ![Část mezipaměti pro stahování na kartě umístění instalace](media/vs-installation-locations-cache.png "Zvolte, zda má být po instalaci uchovávána mezipaměť pro stahování, a pak zadejte jednotku, kam chcete ukládat soubory.")

    1. Zrušte nebo zrušte kontrolu **po instalaci zachovat mezipaměť pro stahování**.

       Pokud se rozhodnete, že nechcete uchovávat mezipaměť pro stahování, umístění se použije jenom dočasně. Tato akce neovlivní ani neodstraní soubory z předchozích instalací.

    1. Zadejte jednotku, do které chcete uložit instalační soubory a manifesty z mezipaměti pro stahování.

        Pokud například vyberete úlohu vývoj desktopových aplikací s C++, je dočasně požadovaná velikost na systémové jednotce 1,58 GB, která se pak uvolní ihned po dokončení instalace.

       > [!IMPORTANT]
       > Toto umístění je nastavené na první instalaci a nedá se později změnit z uživatelského rozhraní instalačního programu. Místo toho je nutné [použít parametry příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) pro přesunutí mezipaměti pro stahování.

1. V části **sdílené komponenty, nástroje a sady SDK** určete jednotku, kam chcete uložit soubory, které jsou sdíleny souběžnými instalacemi sady Visual Studio. Sady SDK a nástroje jsou také uloženy v tomto adresáři.

   ![Část sdílené součásti, nástroje a sady SDK na kartě umístění instalace](media/vs-installation-locations-shared.png "Zadejte umístění, kam chcete uložit sdílené součásti, nástroje a sady SDK.")

::: moniker-end

::: moniker range="vs-2019"

1. Při instalaci sady Visual Studio vyberte kartu **umístění instalace** .

   ![Visual Studio 2019 – výběr umístění instalace](media/vs-2019/vs-installer-installation-locations.png "Vyberte umístění instalace.")

1. V části **Visual Studio IDE** přijměte výchozí nastavení. Visual Studio nainstaluje základní produkt a obsahuje soubory, které jsou specifické pro tuto verzi sady Visual Studio.

   > [!TIP]
   > Pokud je systémová jednotka SSD (Solid-State Drive), doporučujeme, abyste přijali výchozí umístění na systémové jednotce. Důvod? Při vývoji v aplikaci Visual Studio můžete číst a zapisovat do velkého množství souborů, které zvyšují aktivitu v/v disku. Nejlepší je zvolit nejrychlejší disk pro zpracování zatížení.

1. V části **mezipaměť pro stahování** se rozhodněte, jestli chcete uchovat mezipaměť pro stahování, a pak se rozhodněte, kam chcete ukládat soubory.

    * Zrušte nebo zrušte kontrolu **po instalaci zachovat mezipaměť pro stahování**.

       Pokud se rozhodnete, že nechcete uchovávat mezipaměť pro stahování, umístění se použije jenom dočasně. Tato akce neovlivní ani neodstraní soubory z předchozích instalací.

    * Zadejte jednotku, do které chcete uložit instalační soubory a manifesty z mezipaměti pro stahování.

        Pokud například vyberete úlohu vývoj desktopových aplikací s C++, je dočasně požadovaná velikost na systémové jednotce 1,58 GB, která se pak uvolní ihned po dokončení instalace.

       > [!IMPORTANT]
       > Toto umístění je nastavené na první instalaci a nedá se později změnit z uživatelského rozhraní instalačního programu. Místo toho je nutné [použít parametry příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) pro přesunutí mezipaměti pro stahování.

1. V části **sdílené komponenty, nástroje a sady SDK** si všimněte, že používá stejnou jednotku, jakou jste zvolili v části "mezipaměť pro stahování". Adresář \Microsoft\VisualStudio\Shared je místo, kde aplikace Visual Studio ukládá soubory, které jsou sdíleny souběžnými instalacemi sady Visual Studio. Sady SDK a nástroje jsou také uloženy v tomto adresáři.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](update-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
