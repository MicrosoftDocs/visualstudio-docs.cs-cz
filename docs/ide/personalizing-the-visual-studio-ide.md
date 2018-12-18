---
title: Přizpůsobení integrovaného vývojového prostředí
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfd3ed3461b40f85e66d62f01e68aff4ce740031
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159500"
---
# <a name="personalize-the-visual-studio-ide"></a>Přizpůsobení prostředí IDE sady Visual Studio

Přizpůsobit Visual Studio v různé způsoby, jak nejlépe podporují vlastní stylu vývoje a požadavky. Mnoho nastavení se zpřístupní instancích sady Visual Studio&mdash;naleznete v tématu [synchronizovaná nastavení](../ide/synchronized-settings-in-visual-studio.md). Tento článek stručně popisuje různé přizpůsobení a místo, kde najdete další informace.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [přizpůsobení sady Visual Studio pro Mac IDE](/visualstudio/mac/customizing-the-ide).

## <a name="default-settings"></a>Výchozí nastavení

Můžete zvolit výchozí kolekce nastavení, která optimalizuje Visual Studio pro váš typ vývoje. Další informace najdete v tématu [nastavení prostředí](environment-settings.md).

## <a name="general-environment-options"></a>Možnosti Obecné prostředí

Mnoho možností přizpůsobení, které jsou vystaveny prostřednictvím [možnosti prostředí](../ide/reference/environment-options-dialog-box.md) dialogové okno. Existují dva způsoby přístupu k tomuto dialogovému oknu:

- V panelu nabídky zvolte **nástroje** > **možnosti**a pokud ještě není rozbalen, rozbalte **prostředí** uzlu.

- Typ `environment` v **Snadné spuštění** pole a tlačítko **prostředí--> Obecné** ze seznamu výsledků.

   > [!TIP]
   > Pokud se zobrazí dialogové okno, můžete stisknout **F1** o pomoc na různá nastavení na této stránce.

## <a name="environment-color-themes"></a>Barevné motivy prostředí

Chcete-li změnit barevný motiv mezi světla a tmavě modrá, typ `environment` v **Snadné spuštění** pole a klikněte na tlačítko **prostředí--> Obecné**. V **možnosti** dialogovém okně Změnit **barevný motiv** možnost.

Chcete-li změnit možnosti zabarvení v editoru, zadejte `environment` v **Snadné spuštění** pole a klikněte na tlačítko **prostředí--> písma a barvy**. Zobrazit [jak: Změna písma a barev](../ide/how-to-change-fonts-and-colors-in-visual-studio.md).

### <a name="main-menu-casing"></a>Hlavní nabídka malých a velkých písmen

Můžete změnit malých a velkých písmen hlavní nabídky mezi **Mena všech slov velká** ("File") a **všechna velká mají standardní** ("FILE"). Typ `environment` v **Snadné spuštění** vyberte **prostředí--> Obecné**a potom změňte **použít název případu stylů na řádku nabídek** možnost.

### <a name="customize-menus-and-toolbars"></a>Přizpůsobení nabídek a panelů nástrojů

Chcete-li přidat nebo odebrat položky nabídky nebo panelu nástrojů, přečtěte si téma [jak: Přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="start-page"></a>Úvodní stránka

Chcete-li vytvořit vlastní úvodní stránky pro vás i váš tým, naleznete v tématu [lastní nastavení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="window-layouts"></a>Rozložení oken

Můžete definovat a uložit několik rozložení oken a mezi nimi přepínat. Můžete například definovat jedno rozložení pro kódování a jeden pro ladění. Pozice okna a chování uspořádat a uložit vlastní rozložení najdete v tématu [přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="external-tools"></a>Externí nástroje

Můžete přizpůsobit **nástroje** nabídky ke spuštění externích nástrojů. Další informace najdete v tématu [Správa externích nástrojů](../ide/managing-external-tools.md).

## <a name="see-also"></a>Viz také:

- [Nastavení prostředí](environment-settings.md)
- [Visual Studio IDE – přehled](../get-started/visual-studio-ide.md)
- [Rychlý start: První pohled na integrovaném vývojovém prostředí sady Visual Studio](../ide/quickstart-ide-orientation.md)
- [Přizpůsobení sady Visual Studio pro Mac integrovaného vývojového prostředí](/visualstudio/mac/customizing-the-ide)