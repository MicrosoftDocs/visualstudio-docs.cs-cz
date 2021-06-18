---
title: Aktualizace sady Visual Studio
titleSuffix: ''
description: Zjistěte, jak Visual Studio nejnovější verzi, krok za krokem.
ms.date: 04/06/2021
ms.custom: acquisition
ms.topic: how-to
ms.prod: visual-studio-windows
ms.technology: vs-installation
helpviewer_keywords:
- update [Visual Studio]
- change [Visual Studio]
f1_keywords:
- VS.ToolsOptionsPages.Environment.ProductUpdates
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b541568da45c9bd8dda7258534193371e7e9f04b
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306836"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aktualizace Visual Studio na nejnovější verzi

::: moniker range="vs-2017"

Doporučujeme vám aktualizovat na [](/visualstudio/releasenotes/vs2017-relnotes/) nejnovější verzi Visual Studio 2017, abyste vždy získali nejnovější funkce, opravy a vylepšení.

A pokud si chcete vyzkoušet naši nejnovější verzi, zvažte místo toho stažení a instalaci [Visual Studio 2019.](https://visualstudio.microsoft.com/downloads)

> [!IMPORTANT]
> Musíte se přihlásit pomocí účtu, který má oprávnění správce k instalaci, aktualizaci nebo úpravě Visual Studio. Další informace najdete v tématu [Uživatelská oprávnění a Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Toto téma se týká Visual Studio ve Windows. Další Visual Studio pro Mac v tématu [Aktualizace Visual Studio pro Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Aktualizace Visual Studio 2017 verze 15.6 nebo novější

Zjednodušili jsme prostředí instalace a aktualizací, aby bylo snazší ho používat přímo z integrovaného vývojového prostředí. Tady je postup aktualizace z verze 15.6 a novější na novější verze Visual Studio.

### <a name="using-the-notifications-hub"></a>Použití centra Oznámení

Pokud dojde k aktualizaci, v souboru se zobrazí odpovídající příznak Visual Studio.

1. Uložte svou práci.

1. Výběrem příznaku oznámení otevřete **centrum** Oznámení a pak zvolte aktualizaci, kterou chcete nainstalovat.

   ![Aktualizace Visual Studio 2017 pomocí centra oznámení](media/vs-install-notifications-hub-15dot6.png "Centrum oznámení v aplikaci Visual Studio 2017")

      > [!TIP]
      > Aktualizace edice nástroje Visual Studio 2017 je kumulativní, proto se vždy rozhodnete nainstalovat aktualizaci s nejnovějším číslem verze.

1. Po otevření **dialogového** okna Aktualizovat zvolte **Aktualizovat.**

    ![Aktualizace Visual Studio 2017 pomocí dialogového okna Aktualizace z centra Oznámení](media/vs-update-now-from-notifications-hub.png "Dialogové okno aktualizace z centra oznámení v aplikaci Visual Studio")

     Pokud se otevře Access Control uživatelského účtu, zvolte **Ano.** V dalším kroku se může na chvíli otevřít dialogové okno Počkejte prosím a potom se Instalační program pro Visual Studio otevře dialogové okno pro spuštění aktualizace.

     ![Nové prostředí Instalační program pro Visual Studio ve verzi 15.6](media/visual-studio-15dot6-installer.png "Nové prostředí Instalační program pro Visual Studio ve verzi 15,6")

     Vaše aktualizace pokračuje. Po dokončení se pak Visual Studio počítače.

     > [!NOTE]
     > Když spustíte Visual Studio v režimu správce, musíte ho Visual Studio po aktualizaci ručně restartovat.

### <a name="using-the-ide"></a>Používání prostředí IDE

Aktualizaci můžete zkontrolovat a pak ji nainstalovat z řádku nabídek v Visual Studio.

1. Uložte svou práci.

1. Zvolte **Help** > **Check for Updates (Kontrola nápovědy pro aktualizace).**

     ![Nová nabídka Nápověda v Visual Studio verze 15.6](media/vs-help-menu-check-for-updates.png "Nová nabídka Help v aplikaci Visual Studio verze 15,6")

1. Po otevření **dialogového** okna Aktualizovat zvolte **Aktualizovat.**

   Aktualizace pokračuje, jak je popsáno v předchozí části, a Visual Studio po úspěšném dokončení aktualizace znovu spustí.

   > [!NOTE]
   > Když spustíte Visual Studio v režimu správce, musíte ho Visual Studio po aktualizaci ručně restartovat.

### <a name="using-the-visual-studio-installer"></a>Použití Instalační program pro Visual Studio

Stejně jako v dřívějších Visual Studio můžete k instalaci aktualizace Instalační program pro Visual Studio použít nástroj .

1. Uložte svou práci.

1. Otevřete instalační program. Než Instalační program pro Visual Studio pokračovat, může aktualizace vyžadovat aktualizace.

   > [!NOTE]
   > Na počítači se systémem Windows 10 najdete instalační program pod písmenem **V** jako **Instalační program pro Visual Studio** nebo pod písmenem **M** jako instalační program **Microsoft Visual Studio.**

1. Na stránce **Produkt** v instalačním programu vyhledejte edici aplikace, Visual Studio jste nainstalovali dříve.

1. Pokud je k dispozici aktualizace, zobrazí se **tlačítko** Aktualizovat. (Může trvat několik sekund, než instalační program zjistí, jestli je aktualizace dostupná.)

   Pokud chcete **aktualizace** nainstalovat, zvolte tlačítko Aktualizovat.

     ![Aktualizace Visual Studio 2017 pomocí Instalační program pro Visual Studio](media/update-visual-studio.png "Aktualizace sady Visual Studio 2017 pomocí Instalační program pro Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aktualizace Visual Studio 2017 verze 15.5 nebo starší

Pokud používáte starší verzi, tady je postup použití aktualizace z verze Visual Studio 2017 verze 15.0 až 15.5.

### <a name="update-by-using-the-notifications-hub"></a>Aktualizace pomocí centra oznámení

1. Pokud jsou k dispozici aktualizace, existuje odpovídající příznak oznámení v Visual Studio.

   ![Příznak Visual Studio update Visual Studio 2017](media/notification-flag.png "Příznak oznámení o aktualizacích v aplikaci Visual Studio")

   Výběrem příznaku oznámení otevřete **centrum** Oznámení.

   ![Visual Studio 2017 v centru oznámení](media/notifications-hub.png "Aktualizace sady Visual Studio 2017 v centru oznámení")

      > [!TIP]
      > Aktualizace edice nástroje Visual Studio 2017 je kumulativní, proto se vždy rozhodnete nainstalovat aktualizaci s nejnovějším číslem verze.

1. Zvolte **možnost Visual Studio aktualizovat.** Otevře se dialogové **okno Rozšíření** a aktualizace.

   ![Zvolte Visual Studio Aktualizovat.](media/notifications-hub-select.png "Zvolit aktualizaci sady Visual Studio")

1. V **dialogovém okně Rozšíření** a aktualizace zvolte **tlačítko** Aktualizovat.

   ![V dialogovém okně Rozšíření a aktualizace zvolte Aktualizovat.](media/notifications-extensions-and-updates.png "Dialogové okno rozšíření a aktualizace v aplikaci Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Další informace o Visual Studio oznámení

Visual Studio vás upozorní, když je aktualizace dostupná pro Visual Studio nebo pro všechny komponenty a také v případě, že dojde k určitým událostem v Visual Studio prostředí.

* Pokud je příznak oznámení žlutý, je k dispozici Visual Studio aktualizace produktu, kterou můžete nainstalovat.
* Pokud je příznak oznámení červený, dojde k problému s vaší licencí.
* Pokud je příznak oznámení černý, existují volitelné nebo informační zprávy, které se mají zkontrolovat.

Výběrem příznaku oznámení otevřete centrum **Oznámení** a pak zvolte oznámení, se kterou chcete jednat. Nebo zvolte, že chcete oznámení ignorovat nebo zavřít.

 ![Zobrazení volitelné nebo informační zprávy v centru oznámení](media/notification-flag-optional.png "Příznak volitelného nebo informativního oznámení zprávy v aplikaci Visual Studio")

Pokud se rozhodnete oznámení ignorovat, Visual Studio přestane zobrazovat. Pokud chcete resetovat seznam ignorováných oznámení, zvolte tlačítko Nastavení **v** centru Oznámení.

   ![Výběrem tlačítka Nastavení v centru Oznámení zobrazíte možnosti oznámení.](media/vs-notifications-hub-settings-button.png "Kliknutím na tlačítko nastavení v centru oznámení zobrazíte možnosti oznámení.")

### <a name="update-by-using-the-visual-studio-installer"></a>Aktualizace pomocí Instalační program pro Visual Studio

1. Otevřete instalační program. Než budete pokračovat, možná budete muset instalační program aktualizovat. V takovém případě se zobrazí výzva k tomu.

   > [!NOTE]
   > Na počítači se systémem Windows 10 najdete instalační program pod písmenem **V** jako **Instalační program pro Visual Studio** nebo pod písmenem **M** jako instalační program **Microsoft Visual Studio.**

1. Na stránce **Produkt** v instalačním programu vyhledejte edici aplikace, Visual Studio nainstalovaná dříve.

1. Pokud je k dispozici aktualizace, zobrazí se **tlačítko** Aktualizovat. (Může trvat několik sekund, než instalační program zjistí, jestli je aktualizace dostupná.)

   Pokud chcete **aktualizace** nainstalovat, zvolte tlačítko Aktualizovat.

     ![Aktualizace Visual Studio 2017 pomocí Instalační program pro Visual Studio](media/update-visual-studio.png "Aktualizace sady Visual Studio pomocí Instalační program pro Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

Doporučujeme vám aktualizovat na [](/visualstudio/releases/2019/release-notes/) nejnovější verzi Visual Studio, abyste vždy získali nejnovější funkce, opravy a vylepšení.

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma. Pokud aktuálně používáte jinou verzi nástroje Visual Studio, můžete buď nainstalovat Visual Studio verze vedle [sebe,](../install/install-visual-studio-versions-side-by-side.md)nebo odinstalovat předchozí verze nástroje [Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Musíte se přihlásit pomocí účtu, který má oprávnění správce k instalaci, aktualizaci nebo úpravě Visual Studio. Další informace najdete v tématu [Uživatelská oprávnění a Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Toto téma se týká Visual Studio ve Windows. Další Visual Studio pro Mac v tématu [Aktualizace Visual Studio pro Mac](/visualstudio/mac/update).

Tady je postup aktualizace sady Visual &nbsp; Studio &nbsp; 2019.

## <a name="use-the-visual-studio-installer"></a>Použití Instalační program pro Visual Studio

1. Vyhledejte **Instalační program pro Visual Studio** v počítači.

   V části nabídka Start Windows můžete vyhledat instalační program.

   ![Instalační program pro Visual Studio](media/vs-2019/visual-studio-installer.png "Vyhledejte Instalační program pro Visual Studio")

   Než budete pokračovat, možná budete muset instalační program aktualizovat. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici Visual Studio, kterou jste nainstalovali.

   Pokud jste například nainstalovali Visual &nbsp; Studio Community &nbsp; 2019 a  existuje pro něj aktualizace, zobrazí se v instalačním programu zpráva o dostupné aktualizaci.

     ![Vyberte edici Visual Studio 2019, kterou chcete aktualizovat.](media/vs-2019/vs-installer-update-visual-studio-community.png "Vyberte edici sady Visual Studio 2019, kterou chcete aktualizovat.")

1. Zvolte **Aktualizovat** a nainstalujte aktualizace.

    ![Výběrem tlačítka Aktualizovat nainstalujte aktualizace.](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Kliknutím na tlačítko Aktualizovat nainstalujete aktualizace.")

1. Po dokončení aktualizace můžete být vyzváni k restartování počítače. Pokud ano, proveďte to a pak Visual Studio jako obvykle.

   Pokud nejste vyzváni k restartování počítače, zvolte Spustit, aby se Visual Studio z instalačního programu. 

    ![Výběrem tlačítka Spustit spusťte Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Kliknutím na tlačítko Spustit spusťte aplikaci Visual Studio.")

## <a name="use-the-ide"></a>Použití integrovaného vývojového prostředí (IDE)

Aktualizaci můžete vyhledat a pak ji nainstalovat pomocí řádku nabídek nebo vyhledávacího pole v Visual Studio 2019.

### <a name="open-visual-studio"></a>Otevřete sadu Visual Studio.

1. V nabídce **Start** ve Windows zvolte **Visual Studio 2019.**

    ![Open Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Otevřete Visual Studio 2019 z Windows.")

1. V **části Začínáme** zvolte libovolnou možnost pro otevření integrovaného vývojového prostředí.

    ![Otevřete Instalační program pro Visual Studio](media/vs2019-choose-option-from-get-started.png "Otevřete Instalační program pro Visual Studio")

    Otevře se Visual Studio. V integrovaném vývojovém **prostředí se Visual Studio zpráva o aktualizaci 2019.**

    ![Zpráva o aktualizaci Visual Studio 2019 v integrovaném vývojovém prostředí](media/vs-2019/update-visual-studio-ide-message.png "Zpráva o aktualizaci sady Visual Studio 2019 v integrovaném vývojovém prostředí")

1. Ve zprávě **Visual Studio 2019** zvolte **Zobrazit podrobnosti**.

   ![Zvolte tlačítko Zobrazit podrobnosti ve zprávě o aktualizaci integrovaného vývojového Visual Studio 2019.](media/vs-2019/update-visual-studio-ide-view-details.png "Klikněte na tlačítko Zobrazit podrobnosti ve zprávě aktualizace sady Visual Studio 2019.")

1. V dialogovém **okně Stažená aktualizace a připravená k** instalaci zvolte **Aktualizovat.**

     ![V dialogovém okně Stažené aktualizace a připraveno k instalaci zvolte tlačítko Aktualizovat.](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "V dialogovém okně aktualizace staženého a připraveno k instalaci klikněte na tlačítko Aktualizovat.")

   Visual Studio aktualizací, zavře se a pak se znovu otevře.

### <a name="in-visual-studio"></a>V nástroji Visual Studio

1. V řádku nabídek zvolte **Nápověda** a pak **zvolte Vyhledat aktualizace.**

     ![V nabídce Nápověda zvolte Vyhledat aktualizace.](media/vs-2019/vs-ide-check-updates-help-menu.png "V nabídce nápovědu vyberte možnost vyhledat aktualizace.")

    > [!NOTE]
    > Aktualizace můžete vyhledat také pomocí vyhledávacího pole v integrovaném vývojovém prostředí. Stiskněte **Ctrl** + **Q,** zadejte "vyhledat aktualizace" a pak zvolte výsledek hledání, který odpovídá.

1. V dialogovém **okně Aktualizovat** k dispozici zvolte **Aktualizovat.**

     ![Zvolte tlačítko Aktualizovat v dialogovém okně Aktualizovat k dispozici.](media/vs-2019/update-visual-studio-community-from-ide.png "Klikněte na tlačítko Aktualizovat v dialogovém okně aktualizace k dispozici.")

   Visual Studio aktualizací, zavře se a pak se znovu otevře.

## <a name="use-the-notifications-hub"></a>Použití centra Oznámení

1. V Visual Studio uložte svou práci.

1. Výběrem ikony oznámení v pravém dolním rohu integrovaného vývojového Visual Studio ideu otevřete **centrum** Oznámení.

   ![Ikona oznámení v integrovaném vývojovém Visual Studio ideu](media/vs-2019/notification-bar.png "Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio")

1. V **centru Oznámení zvolte** aktualizaci, kterou chcete nainstalovat, a pak zvolte **Zobrazit podrobnosti**.

     ![Centrum oznámení v Visual Studio 2019](media/vs-2019/notification-hub-update.png "Centrum oznámení v aplikaci Visual Studio 2019")

      > [!TIP]
      > Aktualizace edice nástroje Visual Studio 2019 je kumulativní, proto vždy zvolte instalaci verze s nejnovějším číslem verze.

1. V dialogovém **okně Aktualizovat** k dispozici zvolte **Aktualizovat.**

   Visual Studio aktualizací, zavře se a pak se znovu otevře.

## <a name="customize-update-settings"></a>Přizpůsobení nastavení aktualizací

Nastavení aktualizace můžete v nástroji Visual Studio několika různými způsoby, například změnou režimu instalace a výběrem automatického stahování.

Můžete si vybrat ze dvou režimů instalace:

* **Instalace při stahování**
* **Stáhnout vše a pak nainstalovat**

Můžete také zvolit nastavení **Automaticky stahovat aktualizace,** které umožňuje stahování aktualizací v době nečinnosti počítače.

Jak na to:

1. Na řádku nabídek zvolte **Nástroje** > **Možnosti**.

2. Rozbalte **prostředí** a pak zvolte **Aktualizace produktů**.

    ![Nastavení aktualizací v Visual Studio](media/vs-2019/update-settings-options.png)

3. Zvolte režim instalace a možnosti automatického stahování, které chcete pro Visual Studio aktualizace.

::: moniker-end

::: moniker range=">=vs-2022"

Doporučujeme vám aktualizovat na [](/visualstudio/releases/2022/release-notes/) nejnovější verzi Visual Studio, abyste vždy získali nejnovější funkce, opravy a vylepšení.

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma. Pokud aktuálně používáte jinou verzi nástroje Visual Studio, můžete buď nainstalovat Visual Studio verze vedle [sebe,](../install/install-visual-studio-versions-side-by-side.md)nebo odinstalovat předchozí verze nástroje [Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Musíte se přihlásit pomocí účtu, který má oprávnění správce k instalaci, aktualizaci nebo úpravě Visual Studio. Další informace najdete v tématu [Uživatelská oprávnění a Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Toto téma se týká Visual Studio ve Windows. Další Visual Studio pro Mac v tématu [Aktualizace Visual Studio pro Mac](/visualstudio/mac/update).

Tady je postup aktualizace sady Visual &nbsp; Studio &nbsp; 2022.

## <a name="use-the-visual-studio-installer"></a>Použití Instalační program pro Visual Studio

1. Vyhledejte **Instalační program pro Visual Studio** v počítači.

   V části nabídka Start Windows můžete vyhledat instalační program.

   ![Instalační program pro Visual Studio](media/vs-2019/visual-studio-installer.png "Vyhledejte Instalační program pro Visual Studio")

   Než budete pokračovat, možná budete muset instalační program aktualizovat. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici Visual Studio, kterou jste nainstalovali.

   Pokud jste například nainstalovali Visual &nbsp; Studio Community &nbsp; 2022  a existuje pro něj aktualizace, zobrazí se v instalačním programu zpráva Aktualizovat k dispozici.

     ![Vyberte edici Visual Studio 2019, kterou chcete aktualizovat.](media/vs-2019/vs-installer-update-visual-studio-community.png "Vyberte edici sady Visual Studio 2019, kterou chcete aktualizovat.")

1. Zvolte **Aktualizovat** a nainstalujte aktualizace.

    ![Výběrem tlačítka Aktualizovat nainstalujte aktualizace.](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Kliknutím na tlačítko Aktualizovat nainstalujete aktualizace.")

1. Po dokončení aktualizace můžete být vyzváni k restartování počítače. Pokud ano, proveďte to a pak Visual Studio jako obvykle.

   Pokud nejste vyzváni k restartování počítače, zvolte Spustit, aby se Visual Studio z instalačního programu. 

    ![Výběrem tlačítka Spustit spusťte Visual Studio](media/vs-2019/choose-launch-visual-studio-community.png "Kliknutím na tlačítko Spustit spusťte aplikaci Visual Studio.")

## <a name="use-the-ide"></a>Použití integrovaného vývojového prostředí (IDE)

Aktualizaci můžete vyhledat a pak ji nainstalovat pomocí řádku nabídek nebo vyhledávacího pole v Visual Studio 2022.

### <a name="open-visual-studio"></a>Otevřete sadu Visual Studio.

1. V nabídce **Start systému** Windows zvolte Visual Studio **2022.**

    ![Open Visual Studio 2022](media/vs-2019/vs-installer-visual-studio-2019.png "Otevřete Visual Studio 2019 z Windows.")

1. V **části Začínáme** zvolte libovolnou možnost pro otevření integrovaného vývojového prostředí.

    ![Otevřete Instalační program pro Visual Studio](media/vs2019-choose-option-from-get-started.png "Otevřete Instalační program pro Visual Studio")

    Otevře se Visual Studio. V integrovaném vývojovém prostředí se Visual Studio zpráva o aktualizaci **2022.**

    ![Zpráva o aktualizaci Visual Studio 2019 v integrovaném vývojovém prostředí](media/vs-2019/update-visual-studio-ide-message.png "Zpráva o aktualizaci sady Visual Studio 2019 v integrovaném vývojovém prostředí")

1. Ve zprávě **Visual Studio 2022 zvolte** **Zobrazit podrobnosti**.

   ![Zvolte tlačítko Zobrazit podrobnosti ve zprávě o aktualizaci integrovaného vývojového Visual Studio 2019.](media/vs-2019/update-visual-studio-ide-view-details.png "Klikněte na tlačítko Zobrazit podrobnosti ve zprávě aktualizace sady Visual Studio 2019.")

1. V dialogovém **okně Stažená aktualizace a připravená k** instalaci zvolte **Aktualizovat.**

     ![V dialogovém okně Stažené aktualizace a připraveno k instalaci zvolte tlačítko Aktualizovat.](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "V dialogovém okně aktualizace staženého a připraveno k instalaci klikněte na tlačítko Aktualizovat.")

   Visual Studio aktualizací, zavře se a pak se znovu otevře.

### <a name="in-visual-studio"></a>V nástroji Visual Studio

1. V řádku nabídek zvolte **Nápověda** a pak **zvolte Vyhledat aktualizace.**

     ![V nabídce Nápověda zvolte Vyhledat aktualizace.](media/vs-2019/vs-ide-check-updates-help-menu.png "V nabídce nápovědu vyberte možnost vyhledat aktualizace.")

    > [!NOTE]
    > Aktualizace můžete vyhledat také pomocí vyhledávacího pole v integrovaném vývojovém prostředí. Stiskněte **Ctrl** + **Q,** zadejte "vyhledat aktualizace" a pak zvolte výsledek hledání, který odpovídá.

1. V dialogovém **okně Aktualizovat** k dispozici zvolte **Aktualizovat.**

     ![Zvolte tlačítko Aktualizovat v dialogovém okně Aktualizovat k dispozici.](media/vs-2019/update-visual-studio-community-from-ide.png "Klikněte na tlačítko Aktualizovat v dialogovém okně aktualizace k dispozici.")

   Visual Studio aktualizací, zavře se a pak se znovu otevře.

## <a name="use-the-notifications-hub"></a>Použití centra Oznámení

1. V Visual Studio uložte svou práci.

1. Výběrem ikony oznámení v pravém dolním rohu integrovaného vývojového Visual Studio ideu otevřete **centrum** Oznámení.

   ![Ikona oznámení v integrovaném vývojovém Visual Studio ideu](media/vs-2019/notification-bar.png "Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio")

1. V **centru Oznámení zvolte** aktualizaci, kterou chcete nainstalovat, a pak zvolte **Zobrazit podrobnosti**.

     ![Centrum oznámení v Visual Studio 2019](media/vs-2019/notification-hub-update.png "Centrum oznámení v aplikaci Visual Studio 2019")

      > [!TIP]
      > Aktualizace edice nástroje Visual Studio 2022 je kumulativní, proto vždy zvolte instalaci verze s nejnovějším číslem verze.

1. V dialogovém **okně Aktualizovat** k dispozici zvolte **Aktualizovat.**

   Visual Studio aktualizací, zavře se a pak se znovu otevře.

## <a name="customize-update-settings"></a>Přizpůsobení nastavení aktualizací

Nastavení aktualizací v aplikaci Visual Studio můžete přizpůsobit několika různými způsoby, například změnou režimu instalace a výběrem možnosti automatické stahování.

Existují dva způsoby instalace, ze kterých si můžete vybrat:

* **Instalovat během stahování**
* **Stáhnout vše a pak nainstalovat**

Můžete také zvolit nastavení **automaticky stahovat aktualizace** , které umožňuje stažení aktualizací v době nečinnosti počítače.

Jak na to:

1. Na panelu nabídek vyberte  > **Možnosti** nástroje.

2. Rozbalte položku **prostředí** a pak zvolte možnost **aktualizace produktu**.

    ![Aktualizuje nastavení v aplikaci Visual Studio.](media/vs-2019/update-settings-options.png)

3. Vyberte režim instalace a možnosti automatického stažení, které chcete pro aktualizace sady Visual Studio.
::: moniker-end

## <a name="administrator-updates"></a>Aktualizace správců

Pokud jste součástí organizace, která soustřeďuje správu instalací softwaru, může váš podnikový správce způsobit, že se Visual Studio aktualizuje na vašem počítači. Další informace o tom, jak řídit nebo konfigurovat typy aktualizací, které může počítač přijmout, najdete v tématu [použití Configuration Manager k nasazení aktualizací sady Visual Studio](../install/applying-administrator-updates.md#using-configuration-manager-to-deploy-visual-studio-updates).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Souběžná instalace různých verzí sady Visual Studio](install-visual-studio-versions-side-by-side.md)
* [Aktualizace síťové instalace sady Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Příručka pro Visual Studio Enterprise](visual-studio-enterprise-guide.md)
* [Aktualizace sady Visual Studio v servisním směrném plánu](update-servicing-baseline.md)
* [Řízení aktualizací pro nasazení sady Visual Studio založené na síti](controlling-updates-to-visual-studio-deployments.md)
* [Úpravy sady Visual Studio](modify-visual-studio.md)
* [Odinstalace sady Visual Studio](uninstall-visual-studio.md)
