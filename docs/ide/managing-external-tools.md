---
title: Správa externích nástrojů
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eeeee2e6e7ae5d043124faaa79bc6bad7c527702
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945880"
---
# <a name="manage-external-tools"></a>Správa externích nástrojů

Můžete volat z externích nástrojů v sadě Visual Studio pomocí **nástroje** nabídky. Několik výchozí nástroje jsou k dispozici na **nástroje** nabídce a můžete upravit v nabídce přidáním další spustitelné soubory vlastní.

## <a name="tools-available-on-the-tools-menu"></a>Nástroje dostupné v nabídce Nástroje

**Nástroje** nabídky obsahuje několik předdefinovaných příkazy, jako například:

* **Rozšíření a aktualizace** k [spravovat rozšíření Visual Studia](finding-and-using-visual-studio-extensions.md)
* **Správce fragmentů kódu** k [uspořádání fragmenty kódu](code-snippets.md)
* **Preemptivní ochrana – Dotfuscatoru** spustíte [Dotfuscatoru Community Edition (CE)](dotfuscator/index.md) Pokud je [nainstalován](dotfuscator/install.md)
* **Přizpůsobit** k [přizpůsobení nabídek a panelů nástrojů](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Možnosti** k [nastavit celou řadu různých volbách pro Visual Studio IDE a dalších nástrojů](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Přidání nových nástrojů do nabídky Nástroje

Můžete přidat externího nástroje se objevily na **nástroje** nabídky.

1. Otevřete **externích nástrojů** dialogové okno a vybrat **nástroje** > **externích nástrojů**.

1. Klikněte na tlačítko **přidat**a pak zadejte informace. Například následující položku způsobí **Průzkumníka Windows** otevřete v adresáři souboru, které máte aktuálně otevřete v sadě Visual Studio:

   * Název: `Open File Location`

   * příkaz: `explorer.exe`

   * Argumenty: `/root, "$(ItemDir)"`

   ![Dialogové okno externí nástroje](media/external-tools-dialog.png)

Následuje úplný seznam argumentů, které lze použít při definování externího nástroje:

|Název|Argument|Popis|
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
|Přípona cílového|$(TargetExt)|Přípona názvu souboru položky, která má být sestavena.|
|Binární složka|$(BinDir)|Konečné umístění binárního souboru, který má být sestaven (definované jako jednotka + cesta).|
|Adresář projektu|$(ProjDir)|Adresář aktuálního projektu (jednotka + cesta).|
|Název souboru projektu|$(ProjFileName)|Název souboru aktuálního projektu (jednotka + cesta + název souboru).|
|Adresář řešení|$(SolutionDir)|Adresář aktuálního řešení (jednotka + cesta).|
|Název souboru řešení|$(SolutionFileName)|Název souboru aktuálního řešení (jednotka + cesta + název souboru).|

> [!NOTE]
> Stavový řádek IDE zobrazí **aktuálního řádku** a **aktuální sloupec** proměnné k označení umístění kurzoru v aktivním **Editor kódu**. **Aktuální Text** proměnné vrátí text nebo kódu vybraného v tomto umístění.

## <a name="see-also"></a>Viz také

- [Nástroje sestavení C/C++](/cpp/build/reference/c-cpp-build-tools)
