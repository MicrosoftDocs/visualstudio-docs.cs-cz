---
title: Kompilace a sestavení
description: Tento článek popisuje, jak kompilovat a sestavovat projekty a řešení v Visual Studio pro Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/29/2019
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: b4f1cfc3dfdffcc3dd4cb90cd7d29d4333578b9a
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128410"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilace a sestavování v Visual Studio pro Mac

Visual Studio pro Mac lze použít k sestavování aplikací a vytváření sestavení během vývoje projektu. Je důležité sestavit kód často, abyste mohli rychle identifikovat neshody typu, chybnou syntaxi, nesprávně napsaná klíčová slova a další chyby při kompilaci. Sestavou potom ladění můžete také vyhledat a opravit chyby za běhu, jako je například logika, vstupně-výstupní operace a dělení nulou.

Úspěšné sestavení znamená, že zdrojový kód obsahuje správnou syntaxi a všechny statické odkazy na knihovny, sestavení a další součásti mohou vyřešit. Proces sestavení generuje spustitelný soubor aplikace. Tento spustitelný soubor lze následně otestovat pomocí ladění a různých druhů manuálních a automatizovaných testů pro ověření kvality kódu. Po úplném otestování aplikace můžete zkompilovat vydanou verzi pro nasazení na vaše zákazníky.

Na Macu můžete k sestavení aplikace použít kteroukoli z následujících metod: Visual Studio pro Mac, nástroje příkazového řádku MSBuild nebo Azure Pipelines.

| Metoda sestavení | Výhody |
| --- |--- | --- |
| Visual Studio for Mac |-Okamžité sestavení a testování v ladicí program.<br />-Spustit sestavení s více procesory C# pro projekty.<br />-Přizpůsobení různé aspekty systému sestavení. |
| Příkazového řádku MSBuild| -Sestavit projekty bez instalace Visual Studio pro Mac.<br />-Spustit víceprocesorová sestavení pro všechny typy projektů.<br />-Přizpůsobte většinu oblastí systému sestavení.|
| Kanály Azure | -Automatizujte proces sestavení jako součást kanálu průběžné integrace a doručování.<br />-Použijte automatizované testy s každým sestavením.<br />-Využívejte skoro neomezené cloudové prostředky pro procesy sestavení.<br />-Upravte pracovní postup sestavení a vytvořit aktivity sestavení, chcete-li provést hluboce přizpůsobené úkoly.|

Dokumentace v této části platí další podrobnosti o procesu sestavení na základě integrovaného vývojového prostředí. Další informace o vytváření aplikací prostřednictvím příkazového řádku naleznete v tématu [MSBuild](/visualstudio/msbuild/msbuild). Podrobnosti o sestavování aplikací pomocí Azure Pipelines najdete v tématu [Azure Pipelines](/azure/devops/pipelines).


> [!NOTE]
> Toto téma se týká Visual Studio pro Mac. V případě sady Visual Studio ve Windows, přečtěte si téma [kompilace a sestavení v aplikaci Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).


## <a name="building-from-the-ide"></a>Sestavení v prostředí IDE

Visual Studio pro Mac umožňuje okamžité vytváření a spouštění sestavení a zároveň vám poskytuje kontrolu nad funkcemi sestavení. Při vytváření projektu Visual Studio pro Mac definuje výchozí konfiguraci sestavení, která nastaví kontext pro sestavení. Můžete upravit výchozí konfigurace sestavení a také vytvořit vlastní. Vytvořením nebo úpravou těchto konfigurací dojde k automatické aktualizaci souboru projektu, který je poté použit nástrojem MSBuild k sestavení projektu.

Další informace o tom, jak sestavit projekty a řešení v integrovaném vývojovém prostředí, najdete v tématu Příručka pro [sestavení a čištění projektů a řešení](building-and-cleaning-projects-and-solutions.md) .

Visual Studio pro Mac můžete použít také k následujícím akcím:

* Změňte výstupní cestu. To je upraveno v možnostech projektu:

    ![Změnit výstupní cestu](media/compiling-and-building-image4.png)

* Změnit podrobnosti výstupu sestavení:

    ![Změnit podrobnosti sestavení](media/compiling-and-building-image5.png)

* Přidat vlastní příkazy před, během nebo po sestavení nebo vyčištění:

    ![Přidat vlastní příkazy](media/compiling-and-building-image6.png)


## <a name="see-also"></a>Viz také:

- [Kompilovat a sestavovat (Visual Studio ve Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
