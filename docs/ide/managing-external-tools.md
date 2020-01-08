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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591291"
---
# <a name="manage-external-tools"></a>Správa externích nástrojů

Externí nástroje můžete volat v rámci sady Visual Studio pomocí nabídky **nástroje** . V nabídce **nástroje** je k dispozici několik výchozích nástrojů a nabídku můžete přizpůsobit přidáním dalších vlastních spustitelných souborů.

## <a name="tools-available-on-the-tools-menu"></a>Nástroje dostupné v nabídce nástroje

Nabídka **nástroje** obsahuje několik integrovaných příkazů, včetně:

::: moniker range="vs-2017"

* **Rozšíření a aktualizace** pro [správu rozšíření sady Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Správce fragmentů kódu** pro [uspořádání fragmentů kódu](code-snippets.md)
* **Přizpůsobení** pro [přizpůsobení nabídek a panelů nástrojů](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Možnosti** pro [Nastavení nejrůznějších různých možností pro integrované vývojové prostředí (IDE) sady Visual Studio a další nástroje](reference/options-dialog-box-visual-studio.md)

::: moniker-end

::: moniker range=">=vs-2019"

* **Správce fragmentů kódu** pro [uspořádání fragmentů kódu](code-snippets.md)
* **Přizpůsobení** pro [přizpůsobení nabídek a panelů nástrojů](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Možnosti** pro [Nastavení nejrůznějších různých možností pro integrované vývojové prostředí (IDE) sady Visual Studio a další nástroje](reference/options-dialog-box-visual-studio.md)

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>Přidání nových nástrojů do nabídky nástroje

Můžete přidat externí nástroj, který se zobrazí v nabídce **nástroje** .

1. Otevřete dialogové okno **externí nástroje** výběrem **nástrojů** > **externích nástrojů**.

1. Klikněte na **Přidat**a potom zadejte informace. Například následující položka způsobí, že **Průzkumník Windows** se otevře v adresáři souboru, který aktuálně máte otevřený v aplikaci Visual Studio:

   * Název: `Open File Location`

   * Příkaz: `explorer.exe`

   * Argumenty: `/root, "$(ItemDir)"`

   ![Dialog externích nástrojů – dialogové okno](media/external-tools-dialog.png)

Následuje úplný seznam argumentů, které lze použít při definování externího nástroje:

|Name|Argument|Popis|
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
|Název cíle|$(TargetName)|Název souboru položky, která má být sestavena.|
|Cílová Přípona|$(TargetExt)|Přípona názvu souboru položky, která má být sestavena.|
|Binární složka|$(BinDir)|Konečné umístění binárního souboru, který má být sestaven (definované jako jednotka + cesta).|
|Adresář projektu|$(ProjectDir)|Adresář aktuálního projektu (jednotka + cesta).|
|Název souboru projektu|$(ProjectFileName)|Název souboru aktuálního projektu (jednotka + cesta + název souboru).|
|Adresář řešení|$(SolutionDir)|Adresář aktuálního řešení (jednotka + cesta).|
|Název souboru řešení|$(SolutionFileName)|Název souboru aktuálního řešení (jednotka + cesta + název souboru).|

> [!NOTE]
> Stavový řádek IDE zobrazuje **aktuální řádek** a **aktuální proměnné sloupce** , které označují, kde je kurzor umístěn v aktivním **editoru kódu**. **Aktuální textová** proměnná vrátí text nebo kód vybraný v tomto umístění.

## <a name="see-also"></a>Viz také:

- [Nástroje CC++ /Build](/cpp/build/reference/c-cpp-build-tools)
