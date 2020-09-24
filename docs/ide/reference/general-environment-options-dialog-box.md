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
ms.openlocfilehash: dfd1b876e58c05c668fd74087d5131bb1e9fcd40
ms.sourcegitcommit: bccc6503542e1517e0e96a9f02f5a89d69c60c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2020
ms.locfileid: "91135089"
---
# <a name="options-dialog-box-environment--general"></a>Dialogové okno Možnosti: \> Obecné prostředí

Tato stránka slouží ke změně barevných motivů, nastavení stavového řádku a přidružení přípon souborů mezi další možnosti pro integrované vývojové prostředí (IDE). K dialogovému oknu **Možnosti** můžete přistupovat otevřením nabídky **nástroje** , výběrem **Možnosti**, otevřením složky **prostředí** a kliknutím na stránku **Obecné** .

## <a name="visual-experience"></a>Vizuální prostředí

**Color Theme**

Vyberte barevný motiv **Blue**, **světlý**, **tmavý**nebo **modrý (extra Contrast)** pro rozhraní IDE.

Můžete nainstalovat další předdefinované motivy a vytvořit vlastní motivy stažením a instalací **editoru barevných motivů sady Visual Studio** z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po instalaci tohoto nástroje se v seznamu **barevný motiv** zobrazí další barevné motivy.

**Použití stylu případu nadpisu na řádku nabídek**

Nabídky používají ve výchozím nastavení styl písmen názvů. Zrušte tuto možnost, chcete-li místo toho použít všechny styly velkých a malých písmen.

::: moniker range=">=vs-2019"

**Optimalizovat vykreslování pro obrazovky s různou hustotou pixelů (vyžaduje restart)**

Tato možnost povoluje nebo zakazuje sledování bodů monitorování a DPI (nebo *PMA*) na palec. Když je povolený PMA, uživatelské rozhraní sady Visual Studio se zobrazí ostře v jakémkoli monitorování a konfigurace rozlišení DPI, včetně různých monitorů. K povolení PMA potřebujete Windows 10 Update 2018 nebo novější a .NET Framework 4,8 nebo novější. (Tato možnost se zobrazí šedě, pokud tyto dva požadavky nejsou splněny.)

> [!TIP]
> - Windows 10 obsahuje nastavení, které říká, že se **Windows snaží opravit aplikace, aby se rozmazaný**. **Zapnutí nastavení systému** Windows má zanedbatelný efekt, pokud máte zaškrtnuté políčko **optimalizovat vykreslování pro obrazovky s různou hustotou pixelů** .
> - Windows 10 zahrnuje také **Poradce při potížích s kompatibilitou programů**. Nedoporučujeme řešit vzhled sady Visual Studio pomocí tohoto poradce při potížích.

::: moniker-end

**Automatické přizpůsobení vizuálního prostředí na základě výkonu klienta**

Určuje, zda sada Visual Studio nastaví automatické nastavení pro vizuální prostředí nebo zda je nastavení explicitně nastaveno. Tato úprava může měnit zobrazení barev z přechodů na ploché barvy, nebo může omezit použití animací v nabídkách nebo v automaticky otevíraných oknech.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 obsahuje nastavení, které říká, že se **Windows snaží opravit aplikace, aby se rozmazaný**. Zapnutí tohoto nastavení se doporučuje, **Pokud se Visual** Studio na monitoru neostří. Zvažte upgrade na [Visual Studio 2019](https://visualstudio.microsoft.com/downloads), který výrazně vylepšuje přehlednost zobrazení, protože se jedná o každou monitorovanou aplikaci pro monitorování bodů na palec.

::: moniker-end

**Povolit komplexní klientské prostředí**

Umožňuje plné vizuální prostředí sady Visual Studio, včetně přechodů a animací. Tuto možnost zrušte, pokud používáte připojení ke vzdálené ploše nebo starší grafické adaptéry, protože tyto funkce mohou mít v těchto případech špatný výkon. Tato možnost je dostupná, jenom když zrušíte zaškrtnutí políčka **automaticky upravit vizuální prostředí na základě možnosti klienta** .

**Použít hardwarovou akceleraci grafiky, pokud je k dispozici**

Používá hardwarovou akceleraci grafiky, je-li k dispozici, nikoli při akceleraci softwaru.

## <a name="other"></a>Jiné

**Položky, které se mají zobrazit v nabídce okna**

Přizpůsobuje počet oken, která se zobrazí v seznamu Windows v nabídce **okna** . Zadejte číslo od 1 do 24. Výchozí hodnota je 10.

**Položky zobrazené v seznamu naposledy použitých položek**

Přizpůsobuje počet naposledy použitých projektů a souborů, které se zobrazí v nabídce **soubor** . Zadejte číslo od 1 do 24. Výchozí hodnota je 10. Toto je snadný způsob, jak načíst nedávno použité projekty a soubory.

**Zobrazit stavový řádek**

Zobrazí stavový řádek. Stavový řádek je umístěný v dolní části okna IDE a zobrazí informace o průběhu probíhajících operací.

**Tlačítko Zavřít ovlivní pouze aktivní okno nástrojů**

Určuje, že když se klikne na tlačítko **Zavřít** , zavře se jenom okno nástroje, které má fokus, a ne všechna okna nástrojů v ukotvené sadě. Tato možnost je vybrána ve výchozím nastavení.

**Tlačítko automaticky skrýt ovlivní pouze aktivní okno nástrojů**

Určuje, že po kliknutí na tlačítko pro **automatické skrývání** bude automaticky skryto okno nástroje, které má fokus, a ne všechna okna nástrojů v ukotvené sadě. Ve výchozím nastavení není tato možnost vybrána.

## <a name="see-also"></a>Viz také

- [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
