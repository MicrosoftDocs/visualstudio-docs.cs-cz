---
title: Správa verzí
description: Použití Gitu a Subversion ve Visual Studiu pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 47b51306f8d0916eccd7db3a4740843bb7efba85
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984738"
---
# <a name="version-control"></a>Správa verzí

Správa verzí je systém pro správu souborů v mnoha různých verzích a - ve vývoji softwaru - je obecně přispívá na mnoho vývojářů. Hlavním účelem každého systému správy verzí (_VCS_) je najít řešení, které umožňuje všem uživatelům pracovat na základu kódu ve stejnou dobu.

Jádrem každého systému správy verzí je _úložiště_, které funguje jako centrální úložiště dat pro všechny různé soubory - podobně jako souborový server. Na rozdíl od souborového serveru však úložiště obsahuje celou historii projektu a všechny revize, které byly provedeny.

Pokud úložiště je centrální úložiště dat, je logické, aby každý uživatel měl místní úložiště dat, což mu umožňuje pracovat na něm. Tomu se říká _pracovní kopie_. V sadě Visual Studio for Mac se vaše pracovní kopie zobrazí stejně jako jakýkoli jiný místní adresář v počítači, což vám umožní číst z libovolného souboru a zapisovat do nich. Protože však Visual Studio for Mac má integraci systému správy verzí, můžete použít Subversion a Git bez opuštění rozhraní IDE.

Subversion je centralizovaný systém správy verzí, což znamená, že existuje jediný server, který obsahuje všechny soubory a revize, ze kterých mohou uživatelé rezervovat libovolnou verzi libovolného souboru. Když jsou soubory rezervovány ze vzdáleného úložiště Subversion, uživatel získá snímek úložiště v tomto okamžiku.

Git je distribuovaný systém správy verzí, který umožňuje týmům pracovat na stejných dokumentech současně. S Gitem může existovat jeden server, který obsahuje všechny soubory, ale celé úložiště je klonováno místně do vašeho počítače, kdykoli je úložiště rezervováno z tohoto centrálního zdroje.

## <a name="basic-concepts"></a>Základní koncepty

Visual Studio pro Mac poskytuje podporu pro systémy pro správu verzí Git i Subversion. Následující články zkoumají nastavení úložišť Git a Subversion prostřednictvím Visual Studia for Mac a také jednoduché funkce, jako je revize, potvrzení a odesílání změn.

* [Nastavení úložiště Git](set-up-git-repository.md)
* [Práce s úložištěm Git](working-with-git.md)
* [Nastavení úložiště Subversion](set-up-subversion-repository.md)
* [Práce s úložištěm Subversion](working-with-subversion.md)

## <a name="see-also"></a>Viz také

* [Správa verzí v sadě Visual Studio (ve Windows)](/visualstudio/version-control/)