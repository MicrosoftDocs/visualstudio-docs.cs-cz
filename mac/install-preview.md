---
title: Nainstalovat verzi preview
description: Pokyny k aktualizaci sady Visual Studio pro Mac a přístup k preview verzí, včetně Visual Studio 2019 pro Mac verze Preview.
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 0E1EF257-9DE4-4653-9DF4-805CE007A1A1
ms.openlocfilehash: b5eea8c2c894b7eeaa13c83ae6698d1297de9297
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896754"
---
# <a name="install-a-preview-release"></a>Nainstalovat verzi preview

::: zone pivot="vsmac2019"

> [!TIP]
> 2019 Visual Studio pro Mac ve verzi preview je teď k dispozici. Poprvé se dá instalovat vedle sebe s nejnovější stabilní verze sady Visual Studio pro Mac.

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Požadavky pro Visual Studio 2019 for Mac preview

* Počítač Mac s macOS 10.13 vysokou Sierra nebo vyšší.

K vytváření aplikací Xamarin pro iOS nebo macOS, budete také potřebovat:

* Xcode 10.0 nebo vyšší. Nejnovější stabilní verze je obvykle vhodné.
* Apple ID. Pokud ještě nemáte Apple ID můžete vytvořit nový na https://appleid.apple.com. Je potřeba mít Apple ID, instalace a přihlášení do Xcode.

## <a name="installing-the-preview"></a>Instalace verze preview

1. Stažení instalačního programu preview z [Visual Studio for Mac preview stránky](https://aka.ms/vs4mac-preview).
2. Po dokončení stahování klikněte na tlačítko **VisualStudioforMacPreviewInstaller.dmg** připojit instalační program, spusťte jej dvojitým kliknutím šipku logo:

    [![Klikněte na šipku velké k zahájení instalace](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. Vám může se vám upozornění týkající se aplikace stahuje z Internetu. Klikněte na tlačítko **otevřít**.
4. Počkejte, než instalační program zkontroluje počítač:

    [![Instalační program zkontroluje váš systém nainstalované součásti.](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. Upozornění se zobrazí s výzvou k potvrzení o ochraně osobních údajů a licenční podmínky. Použijte odkazy, přečtěte si je a pak stiskněte klávesu **pokračovat** Pokud souhlasíte s tím:

    [![Na odkazech na ochranu osobních údajů a podmínky a potom pokračovat, souhlasíte s](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. Zobrazí se seznam dostupných úloh. Vyberte ty, které chcete použít:

    [![Zvolte nepovinné úlohy funkcí, které chcete nainstalovat](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    Pokud je starší než verze 7.7 aktuální sady Visual Studio pro Mac 2017, zobrazí výzva ke schválení upgrade na nejnovější stabilní verze (která je nezbytná pro podporu instalace vedle sebe). Stisknutím klávesy **pokračovat** schválit upgradu:

    ![Upgrade stabilní verzi 7.7 je povinný](media/install-preview-older-upgrade.png)

7. Po provedení výběru, stiskněte **nainstalovat** tlačítko.
8. Instalační program se zobrazí průběh, stáhne a nainstaluje sadu Visual Studio pro Mac a vybrané úlohy. Vám může zobrazit výzva k zadání hesla k udělení oprávnění pro instalaci.
9. Použití **sady Visual Studio (Preview)** kdykoli budete chtít otestovat verzi preview, nebo přepněte zpátky na nejnovější stabilní sady Visual Studio pro práci produkčního prostředí. Zde jsou uvedeny dvě ikony:

    ![Ikona rozdíly stabilní verze a preview](media/install-preview-icons-sml.png)

Pokud máte potíže s sítě při instalaci v podnikovém prostředí, přečtěte si [instalace za bránou firewall nebo proxy](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) pokyny.

Další informace o změnách v [poznámky k verzi](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes).

::: zone-end
::: zone pivot="vsmac2017"

## <a name="install-an-update-for-visual-studio-2017-for-mac"></a>Instalace aktualizace pro sadu Visual Studio 2017 pro Mac

Před oficiálním vydání nové verze sady Visual Studio pro Mac, je k dispozici ve verzi preview. Verze preview dává možnost vyzkoušet si nové funkce a získat nejnovější opravy chyb, než jsou plně součástí produktu.

Předběžné verze sady Visual Studio pro Mac se distribuují jako aktualizace, a nikoli prostřednictvím samostatný soubor ke stažení. Visual Studio for Mac obsahuje tři aktualizační kanály, jak je popsáno v [aktualizovat](update.md) článku: Stable, Beta a alfa.

Většina verze preview budou dostupné prostřednictvím i **Beta** a **alfa** kanály, ale vždy zkontrolujte [poznámky k verzi Preview](/visualstudio/releasenotes/vs2017-mac-preview-relnotes) pro nejaktuálnější informace.

Pokud chcete nainstalovat verzi preview sady Visual Studio pro Mac, postupujte následovně:

1. Přejděte na **sady Visual Studio > vyhledat aktualizace**.
2. V poli se seznamem aktualizací kanálu vyberte **Beta**.
3. Vyberte **přepínač kanál** tlačítko k přepnutí na vybraný kanál a zahájit stahování nějaké nové aktualizace.
4. Vyberte **restartovat a nainstalovat aktualizace** tlačítko Spustit instalaci aktualizací.

Další informace o aktualizaci v sadě Visual Studio pro Mac, najdete v článku [aktualizovat](update.md) článku.

::: zone-end