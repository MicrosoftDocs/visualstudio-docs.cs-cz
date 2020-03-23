---
title: Protokoly kontejnerů Dockeru, proměnné prostředí a přístup k souborovým systémům
description: Popisuje, jak zlepšit možnost ladit a diagnostikovat aplikace založené na kontejnerech v sadě Visual Studio pomocí okna nástroje, abyste zjistili, co se děje uvnitř kontejnerů, které hostují vaši aplikaci.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 01/20/2020
ms.technology: vs-azure
monikerRange: vs-2019
ms.openlocfilehash: b4670c003c06f8d16979589a4dce5abf33d5e27d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027297"
---
# <a name="how-to-view-and-diagnose-containers-and-images-in-visual-studio"></a>Jak zobrazit a diagnostikovat kontejnery a obrázky v sadě Visual Studio

Můžete zobrazit, co se děje uvnitř kontejnerů, které hostují vaši aplikaci pomocí okna **Kontejnery.** Pokud jste zvyklí pomocí příkazového řádku ke spuštění příkazů Dockeru k zobrazení a diagnostice, co se děje s kontejnery, toto okno poskytuje pohodlnější způsob, jak sledovat kontejnery bez opuštění ide Visual Studio.

## <a name="prerequisites"></a>Požadavky

- [Desktop Dockeru](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
- [Visual Studio 2019 verze 16.4 Náhled 2](https://visualstudio.microsoft.com/downloads) nebo novější, nebo pokud používáte starší verzi Visual Studia 2019, nainstalujte [rozšíření okna Kontejnery](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vs-containers-tools-extensions).

## <a name="view-information-about-your-containers"></a>Zobrazení informací o kontejnerech

Okno **Kontejnery** se otevře automaticky při spuštění kontejnerizovaného projektu .NET. Chcete-li kontejnery v sadě Visual Studio kdykoli zobrazit, aktivujte vyhledávací `Containers` pole sady Visual Studio **pomocí klávesCtrl**+**Q** a zadejte a zvolte první položku. Okno **Kontejnery** můžete také otevřít z hlavní nabídky. Použijte cestu nabídky **Zobrazit** > jiné**kontejnery systému****Windows** > .  

![Snímek obrazovky s kartou Prostředí v okně Kontejnery](media/view-and-diagnose-containers/container-window.png)

Na levé straně se zobrazí seznam kontejnerů v místním počítači. Kontejnery přidružené k vašemu řešení jsou uvedeny v části **Kontejnery řešení**. Vpravo se zobrazí podokno s kartami **pro prostředí**, **porty**, **protokoly**a **soubory**.

> [!TIP]
> Můžete snadno přizpůsobit, kde **kontejnery** nástroj okno je ukotven v sadě Visual Studio. Viz [Přizpůsobení rozložení oken v sadě Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md). Ve výchozím nastavení je okno **Kontejnery** ukotveno s oknem **Kukátko,** když je ladicí program spuštěn.

## <a name="view-environment-variables"></a>Zobrazit proměnné prostředí

Karta **Prostředí** zobrazuje proměnné prostředí v kontejneru. Pro kontejner vaší aplikace můžete nastavit tyto proměnné mnoha způsoby, například v Dockerfile, v souboru .env nebo pomocí možnosti -e při spuštění kontejneru pomocí příkazu Docker.

![Snímek obrazovky s kartou Prostředí v okně Kontejnery](media/view-and-diagnose-containers/containers-environment-vars.png)

> [!NOTE]
> Změny proměnných prostředí se neprojeví v reálném čase. Proměnné prostředí na této kartě jsou také proměnné systémového prostředí v kontejneru a neodrážejí proměnné uživatelského prostředí místní aplikace.

## <a name="view-port-mappings"></a>Zobrazit mapování portů

Na kartě **Porty** můžete zkontrolovat mapování portů, která jsou v platnosti pro váš kontejner.

![Snímek obrazovky s kartou Porty v okně Kontejnery](media/view-and-diagnose-containers/containers-ports.png)

Známé porty jsou propojeny, takže pokud je na portu k dispozici obsah, můžete kliknutím na odkaz otevřít prohlížeč.

## <a name="view-logs"></a>Zobrazení protokolů

Karta **Protokoly** zobrazuje výsledky `docker logs` příkazu. Ve výchozím nastavení karta zobrazuje stdout a stderr datové proudy v kontejneru, ale můžete nakonfigurovat výstup. Podrobnosti naleznete v [tématu Docker protokolování](https://docs.docker.com/config/containers/logging/).  Ve výchozím nastavení karta **Protokoly** streamuje protokoly, ale můžete je zakázat výběrem tlačítka **Stop** na kartě.

![Snímek obrazovky s kartou Protokoly v okně Kontejnery](media/view-and-diagnose-containers/containers-logs.png)

Chcete-li vymazat protokoly, použijte tlačítko **Vymazat** na kartě **Protokoly.**  Chcete-li získat všechny protokoly, použijte tlačítko **Aktualizovat.**

> [!NOTE]
> Visual Studio automaticky přesměruje stdout a stderr do okna **Výstup** při spuštění bez ladění s kontejnery systému Windows, takže kontejnery systému Windows spuštěné z visual studia pomocí **ctrl**+**f5** nezobrazí protokoly na této kartě; místo toho použijte okno **Výstup.**

## <a name="view-the-filesystem"></a>Zobrazit souborový systém

Na kartě **Soubory** můžete zobrazit souborový systém kontejneru, včetně složky aplikace, která obsahuje váš projekt.

![Snímek obrazovky s kartou Soubory v okně Kontejnery](media/view-and-diagnose-containers/container-filesystem.png)

Chcete-li otevřít soubory v sadě Visual Studio, vyhledejte soubor a poklepejte na něj nebo klepněte pravým tlačítkem myši a zvolte **Otevřít**. Visual Studio otevírá soubory v režimu jen pro čtení.

![Snímek obrazovky se souborem otevřeným pro zobrazení v Sadě Visual Studio](media/view-and-diagnose-containers/container-file-open.png)

Pomocí karty **Soubory** můžete zobrazit protokoly aplikací, jako jsou protokoly služby IIS, konfigurační soubory a další soubory obsahu v souborovém systému kontejneru.

## <a name="start-stop-and-remove-containers"></a>Spuštění, zastavení a odebrání kontejnerů

Ve výchozím nastavení **kontejnery** okno zobrazuje všechny kontejnery na počítači, který spravuje Docker. Pomocí tlačítek panelu nástrojů můžete spustit, zastavit nebo odebrat (odstranit) kontejner, který již nechcete.  Tento seznam je dynamicky aktualizován při vytváření nebo odebírání kontejnerů.

## <a name="open-a-terminal-window-in-a-running-container"></a>Otevření okna terminálu v běžícím kontejneru

Okno terminálu (příkazový řádek nebo interaktivní prostředí) můžete otevřít v kontejneru pomocí tlačítka **Otevřít okno terminálu** v okně **Kontejner.**

![Snímek obrazovky s otevřeným oknem terminálu v okně Kontejnery](media/view-and-diagnose-containers/containers-open-terminal-window.png)

V kontejnerech systému Windows se otevře příkazový řádek systému Windows. Pro linuxové kontejnery otevře okno pomocí bash shellu.

![Snímek obrazovky okna bash](media/view-and-diagnose-containers/container-bash-window.png)

Za normálních okolností se okno terminálu otevře mimo Visual Studio jako samostatné okno. Pokud chcete, aby prostředí příkazového řádku bylo integrováno do prostředí IDE sady Visual Studio jako dokovatelného okna nástrojů, můžete nainstalovat [terminál Whack Whack](https://marketplace.visualstudio.com/items?itemName=DanielGriffen.WhackWhackTerminal).

## <a name="attach-the-debugger-to-a-process"></a>Připojení ladicího programu k procesu

Ladicí program můžete připojit k procesu, který je spuštěn v kontejneru pomocí tlačítka **Připojit k procesu** na panelu nástrojů okna kontejnery. Při použití tohoto tlačítka se zobrazí dialogové okno **Připojit k procesu** a zobrazí dostupné procesy, které jsou spuštěny v kontejneru.  

![Snímek obrazovky s dialogovým oknem Připojit k procesu](media/view-and-diagnose-containers/containers-attach-to-process.jpg)

Můžete připojit ke spravovaným procesům v kontejneru. Chcete-li vyhledat proces v jiném kontejneru, použijte tlačítko **Najít** a vyberte jiný kontejner v dialogovém okně **Vybrat kontejner Dockeru.**

## <a name="viewing-images"></a>Prohlížení obrázků

Obrázky v místním počítači můžete také zobrazit pomocí karty **Obrázky** v okně **Kontejnery.** Obrázky vytažené z externích úložišť jsou seskupeny do stromového zobrazení. Vyberte obrázek a zkontrolujte podrobnosti obrazu.

Chcete-li obrázek odebrat, klepněte pravým tlačítkem myši na obrázek v zobrazení stromu a zvolte **Odebrat**nebo vyberte obrázek a použijte tlačítko **Odebrat** na panelu nástrojů.

## <a name="next-steps"></a>Další kroky

Další informace o nástrojích kontejnerů dostupných v sadě Visual Studio najdete v přehledu [nástrojů kontejnerů](overview.md).

## <a name="see-also"></a>Viz také

[Vývoj kontejnerů v sadě Visual Studio](/visualstudio/containers)

[Tržiště rozšíření pro Visual Studio](https://marketplace.visualstudio.com/)
