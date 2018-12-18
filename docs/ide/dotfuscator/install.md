---
title: Instalace řešení Dotfuscator Community Edition (CE)
ms.date: 06/22/2017
ms.devlang: dotnet
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
keywords: Nástroj Dotfuscator, řešení Dotfuscator CE, PreEmptive, společnosti PreEmptive Solutions PreEmptive ochrany, ochranu, community edition, obfuskace, .NET, bezplatný, Visual Studio 2017, nainstalujte
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Zjistěte, jak nainstalovat bezplatný nástroj Dotfuscator Community Edition zahrnuty v sadě Visual Studio 2017.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: douge
ms.openlocfilehash: d513588a7d00e874b38306150f896157906e2733
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880361"
---
# <a name="install-dotfuscator-community-edition-ce"></a>Instalace řešení Dotfuscator Community Edition (CE)

Visual Studio 2017 zavádí nové prostředí pro instalaci low impact.
V důsledku toho není ve výchozím nastavení nainstalován nástroj Dotfuscator Community Edition (řešení Dotfuscator CE).
Je však snadné instalace řešení Dotfuscator CE i v případě, že už jste nainstalovali aplikaci Visual Studio.

> [!NOTE]
> Kromě verze řešení Dotfuscator CE dodávané s verzemi sady Visual Studio poskytuje společnosti PreEmptive Solutions aktualizované verze také pravidelně na svém webu.
> Pokud chcete stáhnout **nejnovější verzi** přímo, bez instalace ze sady Visual Studio **[kliknutím sem přejdete na stránku pro stažení nástroje Dotfuscator] [ download]**.

## <a name="within-visual-studio"></a>V sadě Visual Studio

Řešení Dotfuscator CE můžete nainstalovat z integrovaného vývojového prostředí sady Visual Studio:

1. V **Snadné spuštění** panelu hledání (Ctrl + Q), typ `dotfuscator`. <br/> <br/> ![Snadné spuštění](media/install_from_vs_12.png) <br/> <br/>
2. Výsledky na panelu Snadné spuštění uvedeno v části *nainstalovat* záhlaví, vyberte **PreEmptive ochranu – řešení Dotfuscator (jednotlivých komponent)**.
   * Pokud jste místo toho najdete v části *nabídky* záhlaví, **Dotfuscator nástroje - PreEmptive ochranu –**, pak řešení Dotfuscator CE je již nainstalována. Podrobnosti o použití najdete v části [stránku Začínáme úplné řešení Dotfuscator CE uživatelské příručce nástroje][get-started].
3. Visual Studio Installer, který se spustí okna, předem nakonfigurovaným programem instalace řešení Dotfuscator CE.
   * Může být nutné zadat přihlašovací údaje správce, abyste mohli pokračovat.
4. Ukončete všechny instance aplikace Visual Studio IDE. <br/> <br/> ![Klikněte na nainstalovat](media/install_from_vs_345.png) <br/> <br/>
5. V okně instalačního programu sady Visual Studio klikněte na tlačítko *nainstalovat*.

Po dokončení instalace můžete začít používat řešení Dotfuscator CE. Podrobnosti najdete v tématu [stránku Začínáme úplné řešení Dotfuscator CE uživatelské příručce nástroje][get-started].

## <a name="during-visual-studio-installation"></a>Během instalace sady Visual Studio

Pokud jste ještě nenainstalovali aplikaci Visual Studio 2017, můžete získat z instalačního programu [webu sady Visual Studio][2017-install].
Při spuštění, zobrazí se možnosti instalace pro vybranou edici sady Visual Studio.

![Možnosti instalace](media/install_ui.png)

Pak můžete nainstalovat nástroj Dotfuscator CE jednotlivých součástí sady Visual Studio 2017:

1. Vyberte **jednotlivé komponenty** kartu.
2. V části *kódu nástroje*, zkontrolujte *PreEmptive ochranu – řešení Dotfuscator* položky.<br/> <br/> ![Jednotlivé komponenty](media/install_individually_12.png) <br/> <br/>
3. *Souhrn* panelu zobrazí *PreEmptive ochranu – řešení Dotfuscator* pod *jednotlivé komponenty* oddílu. <br/> <br/> ![Souhrn](media/install_individually_3.png) <br/> <br/>
4. Konfigurovat další nastavení instalace podle požadavků vašeho prostředí.
5. Až budete připraveni k instalaci sady Visual Studio, klikněte na tlačítko *nainstalovat* tlačítko.

Po dokončení instalace můžete začít používat řešení Dotfuscator CE. Podrobnosti najdete v tématu [stránku Začínáme úplné řešení Dotfuscator CE uživatelské příručce nástroje][get-started].

## <a name="see-also"></a>Viz také:

[This topic in the full Dotfuscator CE User Guide]: https://www.preemptive.com/dotfuscator/ce/docs/help/

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]:  https://visualstudio.microsoft.com/downloads/#vs-2017
[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_install.html