---
title: Správa verzí
description: Pomocí Gitu a dílčí verze v sadě Visual Studio pro Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 0505177e01afd701fe5506df7dd0fc2a2e1f859c
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294718"
---
# <a name="version-control"></a>Správa verzí

Správa verzí je systém pro správu souborů přes mnoho různých verzí a - software development – je obecně přispěl celá řada vývojářů. Základní účel libovolný systém správy verzí (_VC_) je na vyhledání řešení, která umožňuje všem uživatelům pracovat v základu kódu ve stejnou dobu.

V jádru služby libovolný ovládací prvek verze je systém _úložiště_, které slouží jako centrální datového úložiště pro všechny různé soubory – podobně jako souborový server. Ale na rozdíl od souborový server úložiště obsahuje celou historii projektu a všechny revize, které byly provedeny.

Pokud se úložiště nachází centrální úložiště, dává smysl pro každý uživatel má místní úložiště dat, kterým chcete pracovat. Jedná se _pracovní kopie_. V sadě Visual Studio pro Mac vaše pracovní kopie se zobrazí stejně jako další místní adresáře na počítači abyste mohli číst z a zapisovat do některý ze souborů. Ale protože Visual Studio for Mac obsahuje integraci systému správy verzí, můžete dílčích verzí a Gitem bez opuštění integrovaného vývojového prostředí.

Subversion je centralizovaný systém správy verzí, což znamená, že jeden server, který obsahuje všechny soubory a ze kterých uživatelé sjednotit, zkontrolujte všechny verze všech souborů revize. Když soubory jsou rezervovány ze vzdáleného úložiště Subversion, uživatel získá snímek úložiště v tomto okamžiku v čase.

Git je distribuovaný systém správy verzí, který umožňuje týmům pracovat současně na stejném dokumenty. S Gitem může být jeden server, který obsahuje všechny soubory, ale celé úložiště naklonování místně na svém počítači pokaždé, když se z tohoto zdroje centrální úložiště rezervován.

## <a name="basic-concepts"></a>Základní koncepty

Visual Studio for Mac podporuje systémy správy verzí Git a Subversion. V následujících článcích prozkoumat nastavení úložiště Git a Subversion prostřednictvím sady Visual Studio pro Mac, stejně jako jednoduchá funkce, jako jsou revize, potvrzení a předávání změn operací push.

* [Nastavení úložiště Git](set-up-git-repository.md)
* [Práce s úložištěm Git](working-with-git.md)
* [Nastavení úložiště Subversion](set-up-subversion-repository.md)
* [Práce s úložištěm Subversion](working-with-subversion.md)

## <a name="see-also"></a>Viz také:

* [Správa verzí v sadě Visual Studio (ve Windows)](/visualstudio/version-control/)