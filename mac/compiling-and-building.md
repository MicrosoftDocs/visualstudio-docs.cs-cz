---
title: Kompilace a sestavení
description: Tento článek popisuje, jak kompilovat a vytvářet projekty a řešení v Sadě Visual Studio pro Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/29/2019
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: b4f1cfc3dfdffcc3dd4cb90cd7d29d4333578b9a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128410"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilace a vytváření v Visual Studiu pro Mac

Visual Studio pro Mac lze použít k vytváření aplikací a vytváření sestavení během vývoje projektu. Je důležité vytvářet kód často, abyste mohli rychle identifikovat neshody typů, chybnou syntaxi, chybná klíčová slova a další chyby v době kompilace. Vytvořením pak ladění, můžete také najít a opravit chyby za běhu, jako je logika, vi a dělení nulou chyby.

Úspěšné sestavení znamená, že zdrojový kód obsahuje správnou syntaxi a všechny statické odkazy na knihovny, sestavení a další součásti mohou vyřešit. Proces sestavení vytvoří spustitelný soubor aplikace. Tento spustitelný soubor pak může být testován pomocí ladění a různých druhů ručních a automatizovaných testů k ověření kvality kódu. Po úplném otestování aplikace můžete zkompilovat verzi pro nasazení pro své zákazníky.

Na Macu můžete k vytvoření aplikace použít některou z následujících metod: Visual Studio pro Mac, nástroje příkazového řádku MSBuild nebo Azure Pipelines.

| Metoda sestavení | Výhody |
| --- |--- | --- |
| Visual Studio pro Mac |- Vytvořte sestavení okamžitě a otestujte je v ladicím programu.<br />- Spusťte víceprocesorová sestavení pro projekty Jazyka C#.<br />- Přizpůsobit různé aspekty systému sestavení. |
| Příkazový řádek MSBuild| - Vytvářejte projekty bez instalace Visual Studia pro Mac.<br />- Spusťte víceprocesorová sestavení pro všechny typy projektů.<br />- Přizpůsobte většinu oblastí systému sestavení.|
| Azure Pipelines | - Automatizujte proces sestavení jako součást průběžné integrace / průběžného doručovacího kanálu.<br />- Použít automatizované testy s každým sestavením.<br />- Používejte prakticky neomezené cloudové prostředky pro procesy sestavení.<br />- Upravte pracovní postup sestavení a vytvořte aktivity sestavení k provádění hluboce přizpůsobených úkolů.|

Dokumentace v této části přejde do další podrobnosti o procesu sestavení založené na ide. Další informace o vytváření aplikací prostřednictvím příkazového řádku naleznete v tématu [MSBuild](/visualstudio/msbuild/msbuild). Podrobnosti o vytváření aplikací pomocí Azure Pipelines najdete v tématu [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Toto téma se týká Visual Studia pro Mac. Visual Studio v systému Windows najdete [v tématu Kompilace a sestavení v sadě Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>Sestavení v prostředí IDE

Visual Studio pro Mac umožňuje vytvářet a spouštět buildy okamžitě a zároveň vám dává kontrolu nad funkcemi sestavení. Při vytváření projektu Visual Studio pro Mac definuje výchozí konfiguraci sestavení, která nastaví kontext pro sestavení. Můžete upravit výchozí konfigurace sestavení a také vytvořit vlastní. Vytvoření nebo úprava těchto konfigurací automaticky aktualizuje soubor projektu, který pak používá MSBuild k vytvoření projektu.

Další informace o vytváření projektů a řešení v ide naleznete v [tématu vytváření a čištění projekty a řešení](building-and-cleaning-projects-and-solutions.md) průvodce.

Visual Studio pro Mac lze také použít k provedení následujících akcí:

* Změňte výstupní cestu. Tato možnost se upravuje v možnostech aplikace Project:

    ![Změna výstupní cesty](media/compiling-and-building-image4.png)

* Změňte podrobnost výstupu sestavení:

    ![Změna podrobností sestavení](media/compiling-and-building-image5.png)

* Přidání vlastních příkazů před, během nebo po vytváření nebo čištění:

    ![přidání vlastních příkazů](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Viz také

- [Kompilace a sestavení (Visual Studio ve Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
