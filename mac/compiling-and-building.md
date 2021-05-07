---
title: Kompilace a sestavení
description: Tento článek popisuje, jak kompilovat a sestavovat projekty a řešení v Visual Studio pro Mac
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2021
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: a24c57907afedb4f02068a071d2c9f81eb8962bb
ms.sourcegitcommit: dd2fc6e03a789c044f8438096b8f112e4dba5557
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108640971"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Kompilace a sestavování v Visual Studio pro Mac

Visual Studio pro Mac lze použít k sestavování aplikací a vytváření sestavení během vývoje projektu. Je důležité sestavit kód často, abyste mohli rychle identifikovat neshody typu, chybnou syntaxi, nesprávně napsaná klíčová slova a další chyby při kompilaci. Sestavou potom ladění můžete také vyhledat a opravit chyby za běhu, jako je například logika, vstupně-výstupní operace a dělení nulou.

Úspěšné sestavení znamená, že zdrojový kód obsahuje správnou syntaxi a všechny statické odkazy na knihovny, sestavení a další součásti mohou vyřešit. Proces sestavení generuje spustitelný soubor aplikace. Tento spustitelný soubor lze následně otestovat pomocí ladění a různých druhů manuálních a automatizovaných testů pro ověření kvality kódu. Po úplném otestování aplikace můžete zkompilovat vydanou verzi pro nasazení na vaše zákazníky.

Na Macu můžete k sestavení aplikace použít kteroukoli z následujících metod: Visual Studio pro Mac, nástroje příkazového řádku MSBuild nebo Azure Pipelines.

| Metoda sestavení | Výhody |
| --- |--- | --- |
| Visual Studio pro Mac |– Vytvářejte sestavení hned a otestujte je v ladicím programu.<br />-Spustit sestavení s více procesory pro projekty v jazyce C#.<br />-Přizpůsobení různých aspektů systému sestavení. |
| Příkazový řádek nástroje MSBuild| -Sestavit projekty bez instalace Visual Studio pro Mac.<br />-Spustit sestavení s více procesory pro všechny typy projektů.<br />-Přizpůsobit většinu oblastí systému sestavení.|
| Azure Pipelines | – Automatizujte proces sestavení jako součást kanálu průběžné integrace nebo průběžného doručování.<br />– Použít automatizované testy u každého sestavení.<br />– Využívat prakticky neomezené cloudové prostředky pro procesy sestavení.<br />– Upravte pracovní postup sestavení a vytvořte aktivity sestavení, abyste mohli provádět hluboko přizpůsobené úkoly.|

Dokumentace v této části se podrobněji popisuje procesu sestavení založeného na rozhraní IDE. Pokud chcete vytvářet aplikace z příkazového řádku bez instalace Visual Studio pro Mac, můžete nainstalovat nejnovější [.NET Core SDK](https://dotnet.microsoft.com/download). Další informace o vytváření aplikací prostřednictvím příkazového řádku naleznete v tématu [MSBuild](/visualstudio/msbuild/msbuild). Podrobnosti o sestavování aplikací pomocí Azure Pipelines najdete v tématu [Azure Pipelines](/azure/devops/pipelines).


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


## <a name="see-also"></a>Viz také

- [Kompilovat a sestavovat (Visual Studio ve Windows)](/visualstudio/ide/compiling-and-building-in-visual-studio)
