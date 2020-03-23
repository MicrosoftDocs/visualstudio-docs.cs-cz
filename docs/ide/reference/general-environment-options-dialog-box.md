---
title: Obecné, prostředí, dialogové okno Možnosti
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 973e08ca6555f7da7873d3068e2794b8d34e3640
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569436"
---
# <a name="options-dialog-box-environment--general"></a>Dialogové okno Možnosti: Obecné prostředí \>

Na této stránce můžete mimo jiné změnit barevné motivy, nastavení stavového řádku a přidružení příponek souborů pro integrované vývojové prostředí (IDE). Dialogové okno **Možnosti** můžete získat tak, že otevřete nabídku **Nástroje,** zvolíte **Možnosti**, otevřete složku **Prostředí** a pak zvolíte stránku **Obecné.** Pokud se tato stránka v seznamu nezobrazí, zaškrtněte políčko **Zobrazit všechna nastavení** v dialogovém okně **Možnosti.**

## <a name="visual-experience"></a>Vizuální zážitek

**Color Theme**

Zvolte barevný motiv **Modrá,** **Světlá**, **Tmavá**nebo **Modrá (Extra Kontrast)** pro ide.

Můžete nainstalovat další předdefinované motivy a vytvořit vlastní motivy stažením a instalací **Editoru motivů barev sady Visual Studio** z webu Visual Studio [Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po instalaci tohoto nástroje se v seznamu **Barevný motiv** zobrazí další barevné motivy.

**Použití stylu titulního případu na řádek nabídek**

Nabídky používají styl titulního případu ve výchozím nastavení. Chcete-li místo toho použít veškerý styl velkých písmen, zaškrtněte tuto možnost.

::: moniker range=">=vs-2019"

**Optimalizace vykreslování pro obrazovky s různými hustotami pixelů (vyžaduje restart)**

Tato možnost povolí nebo zakáže povědomí o sledování na palec (DPI) (nebo *PMA).* Pokud je povoleno PMA, uživatelské rozhraní sady Visual Studio se zobrazí ostré v každém měřítku zobrazení monitoru faktor a konfigurace DPI, včetně více monitorů. Chcete-li povolit PMA, potřebujete aktualizaci windows 10 z dubna 2018 nebo novější a rozhraní .NET Framework 4.8 nebo novější. (Tato možnost se zobrazí šedě, pokud tyto dva požadavky nejsou splněny.)

> [!TIP]
> - Windows 10 má nastavení, které **říká, aby se Systém Windows pokusil opravit aplikace, aby nebyly rozmazané**. Zapnutí tohoto nastavení **systému** Windows má zanedbatelný účinek, pokud máte zaškrtnutou volbu **Optimalizovat vykreslování pro obrazovky s různými hustotami obrazových bodů.**
> - Windows 10 také obsahuje **Poradce při potížích s kompatibilitou programů**. Nedoporučujeme se pokoušet opravit vzhled sady Visual Studio pomocí tohoto poradce při potížích.

::: moniker-end

**Automatické nastavení vizuálního prostředí na základě výkonu klienta**

Určuje, zda visual studio nastaví úpravu vizuálního prostředí automaticky nebo zda nastavení nastavíte explicitně. Toto nastavení může změnit zobrazení barev z přechodů na ploché barvy nebo může omezit použití animací v nabídkách nebo vyskakovacích oknech.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 má nastavení, které **říká, aby se Systém Windows pokusil opravit aplikace, aby nebyly rozmazané**. Pokud se visual studio na monitoru zobrazí rozmazaně, **doporučujeme** toto nastavení zapnout. Zvažte upgrade na [Visual Studio 2019](https://visualstudio.microsoft.com/downloads), který výrazně zlepšila přehlednost zobrazení, protože se jedná o aplikace na monitor uvědoměla.

::: moniker-end

**Povolení bohatého klientského prostředí**

Umožňuje úplné vizuální prostředí sady Visual Studio, včetně přechodů a animací. Zrušte zaškrtnutí této možnosti při použití připojení ke vzdálené ploše nebo starších grafických adaptérů, protože tyto funkce mohou mít v těchto případech nízký výkon. Tato možnost je k dispozici pouze v případě, že vymažete možnost Automaticky upravit vizuální prostředí na základě možnosti **klienta.**

**Použití hardwarové grafické akcelerace, pokud je k dispozici**

Používá hardwarovou grafickou akceleraci, pokud je k dispozici, nikoli akceleraci softwaru.

## <a name="other"></a>Ostatní

**Položky, které se mají zobrazit v nabídce Okno**

Přizpůsobí počet oken, které se zobrazí v seznamu systému Windows v nabídce **Okno.** Zadejte číslo mezi 1 a 24. Výchozí hodnota je 10.

**Položky zobrazené v naposledy použitých seznamech**

Přizpůsobí počet naposledy použitých projektů a souborů, které se zobrazí v nabídce **Soubor.** Zadejte číslo mezi 1 a 24. Výchozí hodnota je 10. Toto je snadný způsob, jak načíst nedávno použité projekty a soubory.

**Zobrazit stavový řádek**

Zobrazí stavový řádek. Stavový řádek se nachází v dolní části okna ide a zobrazuje informace o průběhu probíhajících operací.

**Tlačítko Zavřít ovlivní pouze okno aktivního nástroje**

Určuje, že po klepnutí na tlačítko **Zavřít** je zavřeno pouze okno nástroje, které má fokus, a ne všechna okna nástrojů v ukotvené sadě. Tato možnost je vybrána ve výchozím nastavení.

**Tlačítko Automatické skrytí ovlivní pouze okno aktivního nástroje**

Určuje, že po klepnutí na tlačítko **Automaticky skrýt** se automaticky skryje pouze okno nástroje, které má fokus, a ne všechna okna nástrojů v ukotvené sadě. Ve výchozím nastavení není tato možnost vybrána.

## <a name="see-also"></a>Viz také

- [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
