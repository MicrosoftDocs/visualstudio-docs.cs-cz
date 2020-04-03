---
title: Vytvoření projektu AI ze šablony
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 759ee562e5d3648cf831c6a1247bc660596336a1
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638594"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Vytvoření projektu AI ze šablony v Sadě Visual Studio

Po instalaci [nástrojů Visual Studio pro umělou přípravu](installation.md)je snadné vytvořit nový projekt AI pomocí různých šablon.

1. Spusťte Visual Studio.

2. Vyberte **Soubor > Nový > projektu** (Ctrl+Shift+N). V dialogovém okně **Nový projekt** vyhledejte "**Nástroje AI**" a vyberte požadovanou šablonu. Všimněte si, že výběr šablony zobrazí krátký popis toho, co šablona poskytuje.

    ![VS2017 Dialogové okno Nový projekt se šablonou Pythonu](media/create-project/new-ai-project.png)

3. Pro tento rychlý start vyberte šablonu "**TensorFlow Application**", pojmenujte projekt (například "MNIST") a umístění a vyberte **OK**.

4. Visual Studio vytvoří soubor `.pyproj` projektu (soubor na disku) spolu s dalšími soubory, jak je popsáno v šabloně. Se šablonou "TensorFlow Application" projekt obsahuje jeden soubor s názvem stejný jako váš projekt. Soubor je ve výchozím nastavení otevřen v editoru sady Visual Studio.

    ![Výsledný projekt při použití šablony aplikace Pythonu](media/create-project/new-tensorflowapp.png)

5. Všimněte si, že kód již importuje několik knihoven včetně TensorFlow, numpy, sys a os. Navíc spustí aplikaci připravenou s některými vstupními argumenty, které snadno umožňují přepínání umístění vstupních trénovacích dat, výstupních modelů a souborů protokolu. Tyto params jsou užitečné při odesílání úloh do více výpočetních kontextů (tj. jiný adresář v místním poli pro spuštění než ve sdílené složce Azure).

6. Váš projekt má také některé vlastnosti vytvořené pro snadné ladění aplikace automatickým předáním argumentů příkazového řádku těmto vstupním parametrům. **Klikněte pravým tlačítkem myši na** projekt a vyberte **vlastnosti**

    ![Vlastnosti](media/create-project/project-properties.png)

7. Kliknutím na kartu **Ladění** zobrazíte automaticky přidané argumenty skriptu. můžete je podle potřeby změnit na místo, kde jsou umístěna vaše vstupní data a kde chcete, aby byl výstup uložen.

    ![Vlastnosti](media/create-project//project-properties_1.png)

8. Spusťte program stisknutím ctrl+f5 nebo výběrem **možnosti Ladění > Spustit bez ladění** v nabídce. Výsledky se zobrazí v okně konzoly.
