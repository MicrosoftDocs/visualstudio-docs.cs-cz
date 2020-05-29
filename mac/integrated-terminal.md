---
title: Visual Studio pro Mac – integrovaný terminál
description: Visual Studio pro Mac poskytuje integrované vývojové prostředí pro sestavování aplikací .NET na macOS, včetně ASP.NET Core webů a projektů Xamarin pro iOS, Android, Mac a Xamarin. Forms.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: d362938e8f0075591ea5d4ed8461d11395680b5c
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185201"
---
# <a name="integrated-terminal"></a>Integrovaný terminál
V Visual Studio pro Mac můžete otevřít integrované okno terminálu, zpočátku začínáte v kořenovém adresáři vašeho řešení. Terminál může být užitečný pro různé druhy situací – spouští se úlohy front-end (například: NPM, NG nebo Vue), správu kontejnerů, spouštění pokročilých příkazů Git, spouštění Entity Frameworkch příkazů, zobrazení výstupu rozhraní příkazového řádku dotnet, přidávání balíčků NuGet a další. 

Otevření terminálu:
- K zobrazení nebo skrytí okna terminálu použijte klávesovou zkratku **CTRL +** .
- Použijte **View** \> **Pads** \> nabídku **terminálu** Zobrazit nástroje.
- Použijte příkaz **terminálu** z panelu hledání.

![* Visual Studio pro Mac Integrated Terminal hned po spuštění. *](media/integrated-terminal-intro.png)

Ve výchozím nastavení se při spuštění terminálu provede:
- Nastavte pracovní adresář na cestu k aktuálnímu řešení.
- Načtěte výchozí systémové prostředí.

## <a name="search"></a>Search
Obsah okna terminálu můžete vyhledat pomocí nabídky **hledat > najít...** .

![* Možnosti vyhledávání v integrovaném terminálu Visual Studio pro Mac *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Klávesové zkratky terminálu
|Příkazy|Klávesové zkratky|
|-|-|
|Zobrazit nebo skrýt okno terminálu|**CTRL + '**|
|Vytvořit novou instanci terminálu|**Ctrl+'**|
|Posunout o stránku nahoru|**PageUp**|
|Posunout o stránku dolů|**PageDown**|
|Přepínat mezi dříve použitými příkazy|**↑**, **↓**|
|Zvětšit velikost písma|**⌘ +**|
|Zmenšit velikost písma|**⌘-**|

## <a name="multiple-instances"></a>Několik instancí
V každém okamžiku může běžet víc instancí terminálu. Novou instanci můžete vytvořit pomocí klávesové zkratky **CTRL +** . Mezi instancemi můžete přepínat kliknutím na kartu pro každou instanci nebo pomocí klávesové zkratky **CTRL + TAB** v dialogovém okně pro výběr okna.

![* Více instancí terminálů ve Visual Studio pro Mac *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Přizpůsobení okna terminálu
### <a name="configuring-the-terminal-font"></a>Konfigurace písma terminálu
Velikost písma a velikosti, která se používá pro obsah terminálu, můžete změnit v podokně předvolby > prostředí > písma. Ve výchozím nastavení bude písmo stejné jako obsah panelu výstupů, a to pomocí Menlo Regular, Size 11. Můžete ho nastavit na libovolné písmo, nezávisle na písmu v editoru.

![* Přizpůsobení nastavení písma pro integrovaný terminál *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Znovu použít vlastní nastavení terminálu systému
Integrovaný terminál používá stejné výchozí hodnoty a konfiguraci jako terminál systému macOS. To znamená, že vlastní nastavení terminálu (ZSH, Oh-moje-ZSH atd.) funguje i v integrovaném terminálu.
