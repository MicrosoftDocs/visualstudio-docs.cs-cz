---
title: Protokoly kontejnerů Docker, proměnné prostředí a přístup k systému souborů
description: Popisuje, jak vylepšit schopnost ladit a diagnostikovat aplikace založené na kontejnerech v aplikaci Visual Studio pomocí okna nástroje, které vám umožní zjistit, co se v kontejnerech hostujících vaší aplikaci nachází.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: c870378cf277a6008f17ec42d960e07e18a53e86
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283122"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Jak zobrazit a diagnostikovat kontejnery a obrázky v aplikaci Visual Studio

Můžete zobrazit, co se chystá v kontejnerech, které hostují vaši aplikaci pomocí okna **kontejnery** . Pokud jste použili k používání příkazového řádku ke spuštění příkazů Docker k zobrazení a diagnostice toho, co se v kontejnerech chystá, toto okno poskytuje pohodlnější způsob, jak monitorovat kontejnery bez nutnosti opustit prostředí Visual Studio IDE.

## <a name="prerequisites"></a>Požadované součásti

- [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual studio 2019 verze 16,4 Preview 2](https://visualstudio.microsoft.com/downloads) nebo novější nebo pokud používáte starší verzi sady Visual Studio 2019, nainstalujte [rozšíření okna kontejnery](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Zobrazit informace o kontejnerech

Okno **kontejnery** se automaticky otevře při spuštění kontejnerového projektu .NET. Chcete-li zobrazit kontejnery v aplikaci Visual Studio kdykoli, použijte **kombinaci kláves CTRL** + **Q** k aktivaci vyhledávacího pole aplikace Visual Studio a zadejte `Containers` a vyberte první položku. Můžete také otevřít okno **kontejnery** z hlavní nabídky. Použijte cestu nabídky k **zobrazení**  >  **jiných**  >  **kontejnerů**Windows.  

![Snímek obrazovky s kartou prostředí v okně kontejnery](media/view-and-diagnose-containers/container-window.png)

Na levé straně se zobrazí seznam kontejnerů na místním počítači. Kontejnery spojené s vaším řešením jsou uvedené v části **kontejnery řešení**. Napravo se zobrazí podokno s kartami pro **prostředí**, **porty**, **protokoly**a **soubory**.

> [!TIP]
> V aplikaci Visual Studio můžete snadno přizpůsobit, kde je ukotveno okno nástrojů **kontejnery** . Viz [přizpůsobení rozložení oken v aplikaci Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Ve výchozím nastavení je okno **kontejnery** ukotveno v okně **kukátka** při spuštění ladicího programu.

## <a name="view-environment-variables"></a>Zobrazit proměnné prostředí

Karta **prostředí** zobrazuje proměnné prostředí v kontejneru. Pro kontejner vaší aplikace můžete tyto proměnné nastavit mnoha způsoby, například v souboru Dockerfile, v souboru. env nebo pomocí možnosti-e při spuštění kontejneru pomocí příkazu Docker.

![Snímek obrazovky s kartou prostředí v okně kontejnery](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Jakékoli změny proměnných prostředí se neprojeví v reálném čase. Proměnné prostředí na této kartě jsou také proměnné prostředí systému v kontejneru a neodrážejí proměnné uživatelského prostředí, které jsou místní pro aplikaci.

## <a name="view-port-mappings"></a>Zobrazit mapování portů

Na kartě **porty** můžete kontrolovat mapování portů, které jsou platné pro váš kontejner.

![Snímek obrazovky s kartou porty v okně kontejnery](media/view-and-diagnose-containers/containers-ports.png)

Dobře známé porty jsou propojené, takže pokud je na portu dostupný obsah, můžete kliknutím na odkaz otevřít prohlížeč.

## <a name="view-logs"></a>Zobrazení protokolů

Na kartě **protokoly** se zobrazují výsledky `docker logs` příkazu. Ve výchozím nastavení karta zobrazuje streamy stdout a stderr na kontejneru, ale můžete nakonfigurovat výstup. Podrobnosti najdete v tématu [protokolování Docker](https://docs.docker.com/config/containers/logging/).  Ve výchozím nastavení zaproudí protokoly na kartě **protokoly** , ale můžete ji zakázat kliknutím na tlačítko **zastavit** na kartě.

![Snímek obrazovky s kartou Logs v okně kontejnery](media/view-and-diagnose-containers/containers-logs.png)

Chcete-li vymazat protokoly, použijte tlačítko **Vymazat** na kartě **protokoly** .  Chcete-li získat všechny protokoly, použijte tlačítko **aktualizovat** .

> [!NOTE]
> Visual Studio automaticky přesměruje stdout a stderr do okna **výstup** , když spouštíte bez ladění pomocí kontejnerů Windows, takže kontejnery Windows spuštěné ze sady Visual Studio pomocí **klávesy CTRL** + **F5** nebudou na této kartě zobrazovat protokoly. místo toho použijte okno **výstup** .

## <a name="view-the-filesystem"></a>Zobrazit systém souborů

Na kartě **soubory** můžete zobrazit systém souborů kontejneru, včetně složky aplikace, která obsahuje váš projekt.

![Snímek obrazovky s kartou soubory v okně kontejnery](media/view-and-diagnose-containers/container-filesystem.png)

Chcete-li otevřít soubory v aplikaci Visual Studio, vyhledejte soubor a dvakrát na něj klikněte nebo klikněte pravým tlačítkem a vyberte možnost **otevřít**. Visual Studio otevře soubory v režimu jen pro čtení.

![Snímek obrazovky otevřeného souboru pro zobrazení v aplikaci Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Pomocí karty **soubory** můžete zobrazit protokoly aplikací, jako jsou protokoly IIS, konfigurační soubory a další soubory obsahu v systému souborů kontejneru.

## <a name="start-stop-and-remove-containers"></a>Spustit, zastavit a odebrat kontejnery

Ve výchozím nastavení okno **kontejnery** zobrazuje všechny kontejnery v počítači, který je nástrojem Docker. Pomocí tlačítek na panelu nástrojů můžete spustit, zastavit nebo odebrat (odstranit) kontejner, který již nechcete.  Tento seznam se dynamicky aktualizuje při vytváření nebo odebírání kontejnerů.

## <a name="open-a-terminal-window-in-a-running-container"></a>Otevření okna terminálu ve spuštěném kontejneru

Okno terminálu (příkazový řádek nebo interaktivní prostředí) můžete otevřít v kontejneru pomocí tlačítka **otevřít okno terminálu** v okně **kontejneru** .

![Snímek obrazovky okna otevření terminálu v okně kontejnery](media/view-and-diagnose-containers/containers-open-terminal-window.png)

V případě kontejnerů Windows se spustí příkazový řádek systému Windows. V případě kontejnerů Linux se otevře okno pomocí prostředí bash.

![Snímek obrazovky okna bash](media/view-and-diagnose-containers/container-bash-window.png)

V normálním případě se okno terminálu otevře mimo aplikaci Visual Studio jako samostatné okno. Pokud chcete, aby prostředí příkazového řádku bylo integrované do integrovaného vývojového prostředí (IDE) sady Visual Studio jako okno nástroje ukotvit, můžete nainstalovat [/Swagger/docs/v1./Swagger/docs/v1. Terminal](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Připojit ladicí program k procesu

Ladicí program lze připojit k procesu, který je spuštěn v kontejneru pomocí tlačítka **připojit k procesu** na panelu nástrojů okna kontejneru. Když použijete toto tlačítko, zobrazí se dialogové okno **připojit k procesu** a zobrazí dostupné procesy, které jsou spuštěny v kontejneru.  

![Snímek obrazovky dialogového okna připojit k procesu](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Ke spravovaným procesům se můžete připojit v kontejneru. Chcete-li vyhledat proces v jiném kontejneru, použijte tlačítko **Najít** a v dialogovém okně **Vybrat kontejner Docker** vyberte jiný kontejner.

## <a name="viewing-images"></a>Zobrazení obrázků

Obrázky na místním počítači můžete zobrazit také pomocí karty **bitové kopie** v okně **kontejnery** . Obrázky načtené z externích úložišť jsou seskupené dohromady v zobrazení TreeView. Vyberte obrázek pro zkontrolování podrobností obrázku.

Chcete-li odebrat obrázek, klikněte pravým tlačítkem myši na obrázek v ovládacím prvku TreeView a zvolte možnost **Odebrat**, nebo obrázek vyberte a použijte tlačítko **Odebrat** na panelu nástrojů.

## <a name="next-steps"></a>Další kroky

Další informace o nástrojích kontejnerů, které jsou dostupné v aplikaci Visual Studio, najdete v tématu [Přehled nástrojů kontejnerů](overview.md).

## <a name="see-also"></a>Viz také

[Vývoj kontejnerů v aplikaci Visual Studio](/visualstudio/containers)

[Tržiště rozšíření pro Visual Studio](https://marketplace.visualstudio.com/)
