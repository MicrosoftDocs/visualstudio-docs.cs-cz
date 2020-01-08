---
title: Výběr umístění instalací
description: Zjistěte, jak snížit nároky na instalaci sady Visual Studio na systémovou jednotku tak, že změníte umístění mezipaměti pro stahování, sdílených komponent, sady SDK a nástroje na jiné jednotky. Například přesuňte některé soubory z jednotky C do jednotky D.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3ea0651ee1cfde14d5ef7b422095707d8f81cb2f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590147"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Vybrat umístění instalace v aplikaci Visual Studio

::: moniker range="vs-2019"

Nároky na instalaci sady Visual Studio můžete snížit na systémové jednotce změnou umístění některých z jeho souborů. Konkrétně můžete použít jiné umístění pro mezipaměť pro stahování, sdílených komponent, sady SDK a soubory nástroje.

::: moniker-end

::: moniker range="vs-2017"

**Novinka ve verzi 15,7**: můžete snížit nároky na instalaci sady Visual Studio na systémové jednotce změnou umístění některých z jeho souborů. Konkrétně můžete použít jiné umístění pro mezipaměť pro stahování, sdílených komponent, sady SDK a soubory nástroje.

::: moniker-end

   > [!NOTE]
   > Existují některé nástroje a sady SDK, které mají různá pravidla, na kterém lze nainstalovat. Tyto nástroje a sady SDK jsou nainstalovány na systémovou jednotku i v případě zvolte jiné umístění.

Jste připraveni? Tady je způsob.

::: moniker range="vs-2017"

1. Při instalaci sady Visual Studio, zvolte **umístění instalací** kartu.

   ![Visual Studio 2017 – výběr umístění instalace](media/vs-installation-locations.png "Vyberte umístění instalace.")

1. V **Visual Studio IDE** části, přijměte výchozí nastavení. Visual Studio nainstaluje základním produktu a obsahuje soubory, které jsou specifické pro tuto verzi sady Visual Studio.

   ![Část IDE sady Visual Studio na kartě umístění instalace](media/vs-installation-locations-ide.png "V části rozhraní IDE sady Visual Studio na kartě umístění instalace přijměte výchozí hodnotu.")

   > [!TIP]
   > Systémová jednotka jednotky SSD (Solid-State Drive), doporučujeme přijmout výchozí umístění na systémovou jednotku. Důvod? Při vývoji v sadě Visual Studio, číst a zapisovat do velké množství souborů, což zvyšuje úroveň vstupně-výstupní aktivitu disku. Doporučujeme zvolit nejrychlejší jednotky pro zpracování zátěže.

1. V **mezipaměť pro stahování** části, rozhodněte, zda chcete zachovat mezipaměť pro stahování a následně se rozhodnete, kam chcete uložit své soubory.

     ![Část mezipaměti pro stahování na kartě umístění instalace](media/vs-installation-locations-cache.png "Zvolte, zda má být po instalaci uchovávána mezipaměť pro stahování, a pak zadejte jednotku, kam chcete ukládat soubory.")

    1. Zaškrtněte nebo zrušte zaškrtnutí políčka **zachovat mezipaměť pro stahování po instalaci**.

       Pokud nechcete zachovat mezipaměť pro stahování, umístění se používá jenom dočasně. Tato akce nebude mít vliv na a odstraňovat soubory z předchozí instalace.

    1. Určete taky jednotku, kam chcete uložit instalační soubory a manifesty z mezipaměti pro stahování.

        Pokud vyberete úlohy "Vývoj desktopových aplikací pomocí C++", dočasně požadovaná velikost je 1.58 GB na systémovou jednotku, která je uvolněna poté, co nejdříve po dokončení instalace.

       > [!IMPORTANT]
       > Toto umístění se nastaví pomocí při první instalaci a není možné později změnit z uživatelského rozhraní instalačního programu. Místo toho je potřeba [použít parametry příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) přesunout do mezipaměti pro stahování.

1. V **sdílené komponenty, nástroje a sady SDK** části, určete taky jednotku, ve které chcete ukládat soubory, které jsou sdíleny instalace sady Visual Studio vedle sebe. Sady SDK a nástroje jsou také uloženy v tomto adresáři.

   ![Část sdílené součásti, nástroje a sady SDK na kartě umístění instalace](media/vs-installation-locations-shared.png "Zadejte umístění, kam chcete uložit sdílené součásti, nástroje a sady SDK.")

::: moniker-end

::: moniker range="vs-2019"

1. Při instalaci sady Visual Studio, zvolte **umístění instalací** kartu.

   ![Visual Studio 2019 – výběr umístění instalace](media/vs-2019/vs-installer-installation-locations.png "Vyberte umístění instalace.")

1. V **Visual Studio IDE** části, přijměte výchozí nastavení. Visual Studio nainstaluje základním produktu a obsahuje soubory, které jsou specifické pro tuto verzi sady Visual Studio.

   > [!TIP]
   > Systémová jednotka jednotky SSD (Solid-State Drive), doporučujeme přijmout výchozí umístění na systémovou jednotku. Důvod? Při vývoji v sadě Visual Studio, číst a zapisovat do velké množství souborů, což zvyšuje úroveň vstupně-výstupní aktivitu disku. Doporučujeme zvolit nejrychlejší jednotky pro zpracování zátěže.

1. V **mezipaměť pro stahování** části, rozhodněte, zda chcete zachovat mezipaměť pro stahování a následně se rozhodnete, kam chcete uložit své soubory.

    * Zaškrtněte nebo zrušte zaškrtnutí políčka **zachovat mezipaměť pro stahování po instalaci**.

       Pokud nechcete zachovat mezipaměť pro stahování, umístění se používá jenom dočasně. Tato akce nebude mít vliv na a odstraňovat soubory z předchozí instalace.

    * Určete taky jednotku, kam chcete uložit instalační soubory a manifesty z mezipaměti pro stahování.

        Pokud vyberete úlohy "Vývoj desktopových aplikací pomocí C++", dočasně požadovaná velikost je 1.58 GB na systémovou jednotku, která je uvolněna poté, co nejdříve po dokončení instalace.

       > [!IMPORTANT]
       > Toto umístění se nastaví pomocí při první instalaci a není možné později změnit z uživatelského rozhraní instalačního programu. Místo toho je potřeba [použít parametry příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) přesunout do mezipaměti pro stahování.

1. V části **sdílené komponenty, nástroje a sady SDK** si všimněte, že používá stejnou jednotku, jakou jste zvolili v části "mezipaměť pro stahování". Adresář \Microsoft\VisualStudio\Shared je místo, kde aplikace Visual Studio ukládá soubory, které jsou sdíleny souběžnými instalacemi sady Visual Studio. Sady SDK a nástroje jsou také uloženy v tomto adresáři.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](update-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
