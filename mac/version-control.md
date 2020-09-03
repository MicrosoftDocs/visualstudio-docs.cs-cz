---
title: Správa verzí
description: Použití Gitu a podverze v Visual Studio pro Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 9206ab892ef125706ab16f9a739fe88a52f5c242
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "70108100"
---
# <a name="version-control"></a>Správa verzí

Správa verzí je systém pro správu souborů v mnoha různých verzích a vývoj softwaru – obecně přispívá mnoha vývojáři. Hlavním účelem jakéhokoli systému správy verzí (_VCS_) je najít řešení, které umožňuje všem uživatelům pracovat v základu kódu.

V jádru libovolného systému správy verzí je _úložiště_, které funguje jako centrální úložiště dat pro všechny různé soubory, podobně jako u souborového serveru. Na rozdíl od souborového serveru však úložiště obsahuje celou historii projektu a všechny revize, které byly provedeny.

Pokud je úložiště centrálním úložištěm dat, je pro každého uživatele logická úložiště, která jim umožní pracovat. Nazývá se _pracovní kopie_. V Visual Studio pro Mac vaše pracovní kopie se zobrazí stejně jako všechny ostatní místní adresáře na vašem počítači, což vám umožní číst soubory a zapisovat do nich. Protože ale Visual Studio pro Mac má integraci systému správy verzí, můžete použít podverze a Git bez nutnosti opustit rozhraní IDE.

Podverze je centralizovaný systém správy verzí, což znamená, že existuje jediný server, který obsahuje všechny soubory a revize, ze kterých mohou uživatelé rezervovat jakoukoli verzi libovolného souboru. Když jsou soubory rezervovány ze vzdáleného úložiště podverze, uživatel získá snímek úložiště v daném časovém okamžiku.

Git je distribuovaný systém správy verzí, který umožňuje týmům současně pracovat na stejných dokumentech. V případě Git se může jednat o jediný server, který obsahuje všechny soubory, ale celé úložiště se naklonuje místně do vašeho počítače, kdykoli je úložiště rezervované z tohoto centrálního zdroje.

## <a name="basic-concepts"></a>Základní koncepty

Visual Studio pro Mac poskytuje podporu pro systémy správy verzí Git i podverze. Následující články procházejí nastavení úložiště Git a podverze prostřednictvím Visual Studio pro Mac a také jednoduché funkce, jako je například kontrola, potvrzení a doručování změn.

* [Nastavení úložiště Git](set-up-git-repository.md)
* [Práce s úložištěm Git](working-with-git.md)
* [Nastavení úložiště Subversion](set-up-subversion-repository.md)
* [Práce s úložištěm Subversion](working-with-subversion.md)

## <a name="see-also"></a>Viz také

* [Správa verzí v aplikaci Visual Studio (ve Windows)](/visualstudio/version-control/)