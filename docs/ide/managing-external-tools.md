---
title: Správa externích nástrojů
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f22c687f88c7736d5c088ebc28ff490c4c16b8f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591291"
---
# <a name="manage-external-tools"></a>Správa externích nástrojů

Externí nástroje můžete volat z aplikace Visual Studio pomocí nabídky **Nástroje.** V nabídce **Nástroje** je k dispozici několik výchozích nástrojů a nabídku můžete přizpůsobit přidáním dalších vlastních spustitelných souborů.

## <a name="tools-available-on-the-tools-menu"></a>Nástroje dostupné v nabídce Nástroje

Nabídka **Nástroje** obsahuje několik vestavěných příkazů, včetně:

::: moniker range="vs-2017"

* **Rozšíření a aktualizace** [pro správu rozšíření sady Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Správce výstřižků kódu** [pro uspořádání fragmentů kódu](code-snippets.md)
* **Přizpůsobení** [přizpůsobení nabídek a panelů nástrojů](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Možnosti** [nastavení různých možností pro ide visual studio a další nástroje](reference/options-dialog-box-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

* **Správce výstřižků kódu** [pro uspořádání fragmentů kódu](code-snippets.md)
* **Přizpůsobení** [přizpůsobení nabídek a panelů nástrojů](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Možnosti** [nastavení různých možností pro ide visual studio a další nástroje](reference/options-dialog-box-visual-studio.md)

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Přidání nových nástrojů do nabídky Nástroje

Můžete přidat externí nástroj, který se zobrazí v nabídce **Nástroje.**

1. Otevřete dialogové okno **Externí nástroje** výběrem **nástroje externí** > **nástroje**.

1. Klikněte na **Přidat**a vyplňte informace. Například následující položka způsobí, že se **Průzkumník Windows** otevře v adresáři aktuálně otevřeného souboru v sadě Visual Studio:

   * Název:`Open File Location`

   * Příkaz:`explorer.exe`

   * Argumenty:`/root, "$(ItemDir)"`

   ![Dialogové okno Externí nástroje](media/external-tools-dialog.png)

Následuje úplný seznam argumentů, které lze použít při definování externího nástroje:

|Name (Název)|Argument|Popis|
|----------|--------------|-----------------|
|Cesta položky|$(ItemPath)|Celý název souboru aktuálního souboru (jednotka + cesta + název souboru).|
|Adresář položky|$(ItemDir)|Adresář aktuálního souboru (jednotka + cesta).|
|Název souboru položky|$(ItemFilename)|Název aktuálního souboru (název souboru).|
|Přípona položky|$(ItemExt)|Název přípony aktuálního souboru.|
|Aktuální řádek|$(CurLine)|Pozice aktuálního řádku v kurzoru v okně kódu.|
|Aktuální sloupec|$(CurCol)|Pozice aktuálního sloupce v kurzoru v okně kódu.|
|Aktuální text|$(CurText)|Vybraný text.|
|Cílová cesta|$(TargetPath)|Úplný název souboru položky, která má být sestavena (jednotka + cesta + název souboru).|
|Cílový adresář|$(TargetDir)|Adresář položky, která má být sestavena.|
|Cílový název|$(TargetName)|Název souboru položky, která má být sestavena.|
|Rozšíření cíle|$(TargetExt)|Přípona názvu souboru položky, která má být sestavena.|
|Binární složka|$(BinDir)|Konečné umístění binárního souboru, který má být sestaven (definované jako jednotka + cesta).|
|Adresář projektu|$(Projektdir)|Adresář aktuálního projektu (jednotka + cesta).|
|Název souboru projektu|$(Název_ _ __|Název souboru aktuálního projektu (jednotka + cesta + název souboru).|
|Adresář řešení|$(SolutionDir)|Adresář aktuálního řešení (jednotka + cesta).|
|Název souboru řešení|$(SolutionFileName)|Název souboru aktuálního řešení (jednotka + cesta + název souboru).|

> [!NOTE]
> Stavový řádek IDE zobrazuje proměnné **Aktuální řádek** a **Aktuální sloupec,** které označují, kde je kurzor umístěn v aktivním **Editoru kódu**. Proměnná **Aktuální text** vrátí text nebo kód vybraný v tomto umístění.

## <a name="see-also"></a>Viz také

- [Nástroje pro sestavení C/C++](/cpp/build/reference/c-cpp-build-tools)
