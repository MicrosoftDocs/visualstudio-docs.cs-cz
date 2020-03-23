---
title: Výběr umístění instalací
description: Zjistěte, jak snížit nároky na instalaci sady Visual Studio na systémové jednotce změnou umístění mezipaměti pro stahování, sdílených součástí, sad SDK a nástrojů na různé jednotky. Můžete například přesunout některé soubory z jednotky C na jednotku D.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7f80d3c30c536e58811f8ca92676694b6d010010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111784"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Výběr umístění instalace v sadě Visual Studio

::: moniker range="vs-2019"

Můžete snížit nároky na instalaci sady Visual Studio na systémové jednotce změnou umístění pro některé z jeho souborů. Konkrétně můžete použít jiné umístění pro download cache, sdílené součásti, sady SDK a soubory nástrojů.

::: moniker-end

::: moniker range="vs-2017"

**Novinka ve verzi 15.7**: Můžete snížit nároky na instalaci sady Visual Studio na systémové jednotce změnou umístění pro některé jeho soubory. Konkrétně můžete použít jiné umístění pro download cache, sdílené součásti, sady SDK a soubory nástrojů.

::: moniker-end

   > [!NOTE]
   > Existují některé nástroje a sady SDK, které mají různá pravidla pro jejich instalaci. Tyto nástroje a sady SDK jsou nainstalovány na systémové jednotce, i když zvolíte jiné umístění.

Chcete začít? Jak na to:

::: moniker range="vs-2017"

1. Při instalaci sady Visual Studio zvolte kartu **Umístění instalace.**

   ![Visual Studio 2017 – výběr umístění instalace](media/vs-installation-locations.png "Vyberte umístění instalace.")

1. V části **IDE sady Visual Studio** přijměte výchozí nastavení. Visual Studio nainstaluje základní produkt a obsahuje soubory, které jsou specifické pro tuto verzi sady Visual Studio.

   ![Oddíl IDE sady Visual Studio na kartě Umístění instalace](media/vs-installation-locations-ide.png "Přijměte výchozí část pro ide sady Visual Studio na kartě Umístění instalace.")

   > [!TIP]
   > Pokud je systémová jednotka jednotka SSD, doporučujeme přijmout výchozí umístění na systémové jednotce. Důvod? Při vývoji s Visual Studio, číst z a zapisovat do mnoha souborů, což zvyšuje aktivitu vstupně-videa disku. Nejlepší je vybrat si nejrychlejší jízdu, která zvládne náklad.

1. V části **Stáhnout mezipaměť** se rozhodněte, zda chcete zachovat mezipaměť pro stahování, a pak se rozhodněte, kam chcete uložit její soubory.

     ![Stáhnout část Cache na kartě Umístění instalace](media/vs-installation-locations-cache.png "Zvolte, zda chcete zachovat mezipaměť stahování i po instalaci, a zadejte jednotku, na kterou chcete ukládat soubory.")

    1. Zaškrtněte nebo **odškrtnete políčko Zachovat mezipaměť stahování po instalaci**.

       Pokud se rozhodnete nezachovat mezipaměť ke stažení, umístění se používá pouze dočasně. Tato akce neovlivní ani neodstraní soubory z předchozích instalací.

    1. Zadejte jednotku, do které chcete uložit instalační soubory a manifesty z mezipaměti stahování.

        Pokud například vyberete úlohu "Vývoj plochy s aplikací C++", je dočasně požadovaná velikost 1,58 GB na systémové jednotce, která je uvolněna ihned po dokončení instalace.

       > [!IMPORTANT]
       > Toto umístění je nastaveno s první instalací a nelze jej později změnit z ustavičného režimu instalačního programu. Místo toho je nutné [použít parametry příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) k přesunutí mezipaměti stahování.

1. V části **Sdílené součásti, nástroje a sady SDK** určete jednotku, na kterou chcete uložit soubory sdílené souběžnými instalacemi sady Visual Studio. Sady SDK a nástroje jsou také uloženy v tomto adresáři.

   ![Sdílené součásti, nástroje a sady SDK na kartě Umístění instalace](media/vs-installation-locations-shared.png "Určete umístění, kam chcete ukládat sdílené součásti, nástroje a sady SDK.")

::: moniker-end

::: moniker range="vs-2019"

1. Při instalaci sady Visual Studio zvolte kartu **Umístění instalace.**

   ![Visual Studio 2019 – výběr umístění instalace](media/vs-2019/vs-installer-installation-locations.png "Vyberte umístění instalace.")

1. V části **IDE sady Visual Studio** přijměte výchozí nastavení. Visual Studio nainstaluje základní produkt a obsahuje soubory, které jsou specifické pro tuto verzi sady Visual Studio.

   > [!TIP]
   > Pokud je systémová jednotka jednotka SSD, doporučujeme přijmout výchozí umístění na systémové jednotce. Důvod? Při vývoji s Visual Studio, číst z a zapisovat do mnoha souborů, což zvyšuje aktivitu vstupně-videa disku. Nejlepší je vybrat si nejrychlejší jízdu, která zvládne náklad.

1. V části **Stáhnout mezipaměť** se rozhodněte, zda chcete zachovat mezipaměť pro stahování, a pak se rozhodněte, kam chcete uložit její soubory.

    * Zaškrtněte nebo **odškrtnete políčko Zachovat mezipaměť stahování po instalaci**.

       Pokud se rozhodnete nezachovat mezipaměť ke stažení, umístění se používá pouze dočasně. Tato akce neovlivní ani neodstraní soubory z předchozích instalací.

    * Zadejte jednotku, do které chcete uložit instalační soubory a manifesty z mezipaměti stahování.

        Pokud například vyberete úlohu "Vývoj plochy s aplikací C++", je dočasně požadovaná velikost 1,58 GB na systémové jednotce, která je uvolněna ihned po dokončení instalace.

       > [!IMPORTANT]
       > Toto umístění je nastaveno s první instalací a nelze jej později změnit z ustavičného režimu instalačního programu. Místo toho je nutné [použít parametry příkazového řádku](use-command-line-parameters-to-install-visual-studio.md) k přesunutí mezipaměti stahování.

1. V části **Sdílené součásti, nástroje a sady SDK** si všimněte, že používá stejnou jednotku, kterou jste zvolili v části Stáhnout mezipaměť. Adresář \Microsoft\VisualStudio\Shared je místo, kde sada Visual Studio ukládá soubory sdílené souběžnými instalacemi sady Visual Studio. Sady SDK a nástroje jsou také uloženy v tomto adresáři.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Aktualizace sady Visual Studio](update-visual-studio.md)
* [Úpravy sady Visual Studio](update-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
