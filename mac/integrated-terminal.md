---
title: Visual Studio pro Mac – integrovaný terminál
description: Práce s integrovaným terminálem v Visual Studio pro Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: f91c2b1c3f06f8f1fbe54e32fde70b9fe88c5f5d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492867"
---
# <a name="integrated-terminal"></a>Integrovaný terminál
V Visual Studio pro Mac můžete otevřít integrované okno terminálu, zpočátku začínáte v kořenovém adresáři vašeho řešení. Terminál může být užitečný pro různé druhy situací – spouští se úlohy front-end (například: NPM, NG nebo Vue), správu kontejnerů, spouštění pokročilých příkazů Git, spouštění Entity Frameworkch příkazů, zobrazení výstupu rozhraní příkazového řádku dotnet, přidávání balíčků NuGet a další. 

Otevření terminálu:
- K zobrazení nebo skrytí okna terminálu použijte klávesovou zkratku **CTRL +** .
- Použijte nabídku **Zobrazit** \> **terminál** .
- Použijte příkaz **terminálu** z panelu hledání.

![* Visual Studio pro Mac Integrated Terminal hned po spuštění. *](media/integrated-terminal-intro.png)

Ve výchozím nastavení se při spuštění terminálu provede:
- Nastavte pracovní adresář na cestu k aktuálnímu řešení.
- Načtěte výchozí systémové prostředí.

## <a name="search"></a>Hledat
Obsah okna terminálu můžete vyhledat pomocí nabídky **hledat > najít...** .

![* Možnosti vyhledávání v integrovaném terminálu Visual Studio pro Mac *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Klávesové zkratky terminálu
|Příkazy|Klávesové zkratky|
|-|-|
|Zobrazit nebo skrýt okno terminálu|**CTRL + '**|
|Vytvořit novou instanci terminálu|**Ctrl+'**|
|Posunout o stránku nahoru|**PageUp**|
|Posunout o stránku dolů|**PageDown**|
|Přepínat mezi dříve použitými příkazy|**↑** , **↓**|
|Zvětšit velikost písma|**⌘ +**|
|Zmenšit velikost písma|**⌘-**|

## <a name="multiple-instances"></a>Několik instancí
V každém okamžiku může běžet víc instancí terminálu. Novou instanci můžete vytvořit pomocí klávesové zkratky **CTRL +** . Mezi instancemi můžete přepínat kliknutím na kartu pro každou instanci nebo pomocí klávesové zkratky **CTRL + TAB** v dialogovém okně pro výběr okna.

![* Více instancí terminálů ve Visual Studio pro Mac *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Přizpůsobení okna terminálu
### <a name="configuring-the-terminal-font"></a>Konfigurace písma terminálu
Velikost písma a velikosti, která se používá pro obsah terminálu, můžete změnit v podokně předvolby > prostředí > písma. Ve výchozím nastavení bude písmo stejné jako obsah okno Výstup, a to pomocí Menlo Regular, Size 11. Můžete ho nastavit na libovolné písmo, nezávisle na písmu v editoru.

![* Přizpůsobení nastavení písma pro integrovaný terminál *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Znovu použít vlastní nastavení terminálu systému
Integrovaný terminál používá stejné výchozí hodnoty a konfiguraci jako terminál systému macOS. To znamená, že vlastní nastavení terminálu (ZSH, Oh-moje-ZSH atd.) funguje i v integrovaném terminálu.
