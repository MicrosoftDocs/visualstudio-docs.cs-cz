---
title: Vytvoření projektu AI ze šablony
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: de0d2521f73da21ca7b6fc40edaecfadd5d703ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85371557"
---
# <a name="create-an-ai-project-from-a-template-in-visual-studio"></a>Vytvoření projektu AI ze šablony v aplikaci Visual Studio

Po [instalaci Visual Studio Tools for AI](installation.md)je snadné vytvořit nový projekt AI pomocí nejrůznějších šablon.

1. Spusťte Visual Studio.

2. Vyberte **soubor > nový > projekt** (Ctrl + Shift + N). V dialogovém okně **Nový projekt** vyhledejte "**nástroje AI**" a vyberte šablonu, kterou chcete. Všimněte si, že výběr šablony zobrazuje krátký popis toho, co šablona poskytuje.

    ![Dialogové okno Nový projekt VS2017 se šablonou Pythonu](media/create-project/new-ai-project.png)

3. Pro tento rychlý Start vyberte šablonu "**TensorFlow Application**", zadejte název projektu (například "mnist ručně zapsaných") a umístění a vyberte **OK**.

4. Visual Studio vytvoří soubor projektu ( `.pyproj` soubor na disku) spolu s dalšími soubory, jak je popsáno v šabloně. S šablonou "TensorFlow Application" obsahuje projekt jeden soubor nazvaný stejný jako váš projekt. Soubor je ve výchozím nastavení otevřen v editoru sady Visual Studio.

    ![Výsledný projekt při použití šablony aplikace Pythonu](media/create-project/new-tensorflowapp.png)

5. Všimněte si, že kód již importuje několik knihoven, včetně TensorFlow, numpy, sys a OS. Navíc spustí aplikaci, která je připravená na některé vstupní argumenty, aby bylo možné snadno povolit přepínání umístění vstupních dat školení, výstupních modelů a souborů protokolů. Tyto parametry jsou užitečné, když odesíláte úlohy do více výpočetních kontextů (v různých adresářích aplikace Internet Explorer na místním vývojářském poli než ve sdílené složce Azure).

6. Projekt má také vytvořené některé vlastnosti, které usnadňují ladění aplikace tím, že do těchto vstupních parametrů automaticky předává argumenty příkazového řádku. Klikněte **pravým tlačítkem na** projekt a pak vyberte **vlastnosti** .

    ![Vlastnosti](media/create-project/project-properties.png)

7. Kliknutím na kartu **ladění** zobrazíte automaticky přidané argumenty skriptu. v případě potřeby je můžete podle potřeby změnit na místo, kde se vaše vstupní data nacházejí a kde se mají ukládat výstup.

    ![Vlastnosti](media/create-project//project-properties_1.png)

8. Spusťte program stisknutím kombinace kláves CTRL + F5 nebo výběrem možnosti **ladění > spustit bez ladění** v nabídce. Výsledky se zobrazí v okně konzoly.
