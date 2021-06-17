---
title: Aktualizace sady Visual Studio
titleSuffix: ''
description: Naučte se aktualizovat Visual Studio na nejnovější verzi, krok za krokem.
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
ms.openlocfilehash: 9244c9e234c56b058dbfe92a4ef6a10d8c9c702d
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113190"
---
# <a name="update-visual-studio-to-the-most-recent-release"></a>Aktualizace sady Visual Studio na nejnovější verzi

::: moniker range="vs-2017"

Doporučujeme, abyste aktualizovali na nejnovější [verzi](/visualstudio/releasenotes/vs2017-relnotes/) sady Visual Studio 2017, abyste vždycky získali nejnovější funkce, opravy a vylepšení.

A pokud si chcete vyzkoušet naši nejnovější verzi, zvažte místo toho stažení a instalaci sady [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) .

> [!IMPORTANT]
> Musíte se přihlásit pomocí účtu, který má oprávnění správce pro instalaci, aktualizaci nebo úpravu sady Visual Studio. Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v části [Update Visual Studio pro Mac](/visualstudio/mac/update).

## <a name="update-visual-studio-2017-version-156-or-later"></a>Aktualizace sady Visual Studio 2017 verze 15,6 nebo novější

Zjednodušili jsme možnosti instalace a aktualizace, které usnadňují použití přímo v rámci integrovaného vývojového prostředí (IDE). Tady je postup aktualizace z verze 15,6 a novější na novější verze sady Visual Studio.

### <a name="using-the-notifications-hub"></a>Použití centra oznámení

V případě aktualizace existuje odpovídající příznak oznámení v aplikaci Visual Studio.

1. Uložte svou práci.

1. Zvolte příznak oznámení a otevřete tak centrum **oznámení** a pak zvolte aktualizaci, kterou chcete nainstalovat.

   ![Aktualizace sady Visual Studio 2017 pomocí Centra oznámení](media/vs-install-notifications-hub-15dot6.png "Centrum oznámení v aplikaci Visual Studio 2017")

      > [!TIP]
      > Aktualizace pro edici sady Visual Studio 2017 je kumulativní, takže se vždy rozhodnete nainstalovat jednu s nejnovějším číslem verze.

1. Až se otevře dialogové okno **aktualizace** , vyberte **aktualizovat hned**.

    ![Aktualizace sady Visual Studio 2017 pomocí dialogového okna aktualizovat v centru oznámení](media/vs-update-now-from-notifications-hub.png "Dialogové okno aktualizace z centra oznámení v aplikaci Visual Studio")

     Pokud se otevře dialogové okno Access Control uživatele, vyberte **Ano**. V dalším kroku se může otevřít dialogové okno počkat a potom se Instalační program pro Visual Studio otevře, aby se aktualizace spustila.

     ![Nové prostředí Instalační program pro Visual Studio ve verzi 15,6](media/visual-studio-15dot6-installer.png "Nové prostředí Instalační program pro Visual Studio ve verzi 15,6")

     Vaše aktualizace bude pokračovat. Po dokončení se Visual Studio restartuje.

     > [!NOTE]
     > Při spuštění sady Visual Studio v režimu správce je po aktualizaci nutné ručně restartovat aplikaci Visual Studio.

### <a name="using-the-ide"></a>Používání prostředí IDE

Aktualizaci můžete vyhledat a pak ji nainstalovat z řádku nabídek v aplikaci Visual Studio.

1. Uložte svou práci.

1. Zvolit **nápovědu** > **pro kontrolu aktualizací**.

     ![Nová nabídka Help v aplikaci Visual Studio verze 15,6](media/vs-help-menu-check-for-updates.png "Nová nabídka Help v aplikaci Visual Studio verze 15,6")

1. Až se otevře dialogové okno **aktualizace** , vyberte **aktualizovat hned**.

   Aktualizace pokračuje, jak je popsáno v předchozí části, a poté se Visual Studio restartuje po úspěšném dokončení aktualizace.

   > [!NOTE]
   > Při spuštění sady Visual Studio v režimu správce je po aktualizaci nutné ručně restartovat aplikaci Visual Studio.

### <a name="using-the-visual-studio-installer"></a>Použití Instalační program pro Visual Studio

Stejně jako v dřívějších verzích sady Visual Studio můžete použít Instalační program pro Visual Studio k instalaci aktualizace.

1. Uložte svou práci.

1. Spusťte instalační program. Instalační program pro Visual Studio může před pokračováním vyžadovat aktualizaci.

   > [!NOTE]
   > V počítači s Windows 10 můžete instalační program najít pod písmenem **v** jako **instalační program pro Visual Studio** nebo pod písmenem **M** jako **instalační program Microsoft Visual Studio**.

1. Na stránce **produkt** v instalačním programu vyhledejte verzi sady Visual Studio, kterou jste předtím nainstalovali.

1. Pokud je aktualizace k dispozici, zobrazí se tlačítko **aktualizovat** . (Může trvat několik sekund, než instalační program zjistí, zda je aktualizace k dispozici.)

   Kliknutím na tlačítko **aktualizovat** nainstalujte aktualizace.

     ![Aktualizace sady Visual Studio 2017 pomocí Instalační program pro Visual Studio](media/update-visual-studio.png "Aktualizace sady Visual Studio 2017 pomocí Instalační program pro Visual Studio")

## <a name="update-visual-studio-2017-version-155-or-earlier"></a>Aktualizace sady Visual Studio 2017 verze 15,5 nebo starší

Pokud používáte starší verzi, můžete použít aktualizaci ze sady Visual Studio 2017 verze 15,0 prostřednictvím verze 15,5.

### <a name="update-by-using-the-notifications-hub"></a>Aktualizace pomocí Centra oznámení

1. V případě aktualizací existuje odpovídající příznak oznámení v aplikaci Visual Studio.

   ![Aktualizovat příznak oznámení sady Visual Studio 2017](media/notification-flag.png "Příznak oznámení o aktualizacích v aplikaci Visual Studio")

   Kliknutím na příznak oznámení otevřete centrum **oznámení** .

   ![Aktualizace sady Visual Studio 2017 v centru oznámení](media/notifications-hub.png "Aktualizace sady Visual Studio 2017 v centru oznámení")

      > [!TIP]
      > Aktualizace pro edici sady Visual Studio 2017 je kumulativní, takže se vždy rozhodnete nainstalovat jednu s nejnovějším číslem verze.

1. Vyberte **k dispozici možnost aktualizace sady Visual Studio**, která otevře dialogové okno **rozšíření a aktualizace** .

   ![Zvolit aktualizaci sady Visual Studio](media/notifications-hub-select.png "Zvolit aktualizaci sady Visual Studio")

1. V dialogovém okně **rozšíření a aktualizace** klikněte na tlačítko **aktualizovat** .

   ![V dialogovém okně rozšíření a aktualizace vyberte aktualizovat.](media/notifications-extensions-and-updates.png "Dialogové okno rozšíření a aktualizace v aplikaci Visual Studio")

#### <a name="more-about-visual-studio-notifications"></a>Další informace o oznámeních sady Visual Studio

Visual Studio vás upozorní, když je k dispozici aktualizace pro vlastní aplikaci Visual Studio nebo pro jakékoli komponenty, a také když dojde k určitým událostem v prostředí sady Visual Studio.

* Pokud je příznak oznámení žlutý, je k dispozici aktualizace produktu Visual Studio, kterou si můžete nainstalovat.
* Pokud je příznak oznámení červený, dojde k problému s vaší licencí.
* Pokud je příznak oznámení černý, jsou k dispozici volitelné nebo informativní zprávy, které je potřeba zkontrolovat.

Zvolte příznak oznámení a otevřete tak centrum **oznámení** a pak zvolte oznámení, na kterých chcete pracovat. Případně můžete oznámení ignorovat nebo zavřít.

 ![Zobrazení volitelné nebo informativní zprávy v centru oznámení](media/notification-flag-optional.png "Příznak volitelného nebo informativního oznámení zprávy v aplikaci Visual Studio")

Pokud se rozhodnete ignorovat oznámení, Visual Studio ho přestane zobrazovat. Chcete-li obnovit seznam ignorovaných oznámení, klikněte na tlačítko **Nastavení** v centru oznámení.

   ![Kliknutím na tlačítko nastavení v centru oznámení zobrazíte možnosti oznámení.](media/vs-notifications-hub-settings-button.png "Kliknutím na tlačítko nastavení v centru oznámení zobrazíte možnosti oznámení.")

### <a name="update-by-using-the-visual-studio-installer"></a>Aktualizace pomocí Instalační program pro Visual Studio

1. Spusťte instalační program. Než budete pokračovat, možná budete muset instalační program aktualizovat. Pokud se jedná o tento případ, budete vyzváni k tomu.

   > [!NOTE]
   > V počítači s Windows 10 můžete instalační program najít pod písmenem **v** jako **instalační program pro Visual Studio** nebo pod písmenem **M** jako **instalační program Microsoft Visual Studio**.

1. Na stránce **produkt** v instalačním programu vyhledejte verzi sady Visual Studio, která byla dříve nainstalována.

1. Pokud je aktualizace k dispozici, zobrazí se tlačítko **aktualizovat** . (Může trvat několik sekund, než instalační program zjistí, zda je aktualizace k dispozici.)

   Kliknutím na tlačítko **aktualizovat** nainstalujte aktualizace.

     ![Aktualizace sady Visual Studio 2017 pomocí Instalační program pro Visual Studio](media/update-visual-studio.png "Aktualizace sady Visual Studio pomocí Instalační program pro Visual Studio")

::: moniker-end

::: moniker range="vs-2019"

Doporučujeme, abyste aktualizovali na nejnovější [verzi](/visualstudio/releases/2019/release-notes/) sady Visual Studio 2019, abyste vždycky získali nejnovější funkce, opravy a vylepšení.

Pokud jste ještě nenainstalovali Visual Studio 2019, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) . Pokud aktuálně používáte jinou verzi sady Visual Studio, můžete buď [nainstalovat verze sady Visual Studio vedle](../install/install-visual-studio-versions-side-by-side.md)sebe, nebo [odinstalovat předchozí verze sady Visual Studio](../install/uninstall-visual-studio.md).

> [!IMPORTANT]
> Musíte se přihlásit pomocí účtu, který má oprávnění správce pro instalaci, aktualizaci nebo úpravu sady Visual Studio. Další informace naleznete v tématu [uživatelská oprávnění a aplikace Visual Studio](../ide/user-permissions-and-visual-studio.md).
>
> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v části [Update Visual Studio pro Mac](/visualstudio/mac/update).

Tady je postup aktualizace sady Visual &nbsp; Studio &nbsp; 2019.

## <a name="use-the-visual-studio-installer"></a>Použití Instalační program pro Visual Studio

1. Najděte **instalační program pro Visual Studio** v počítači.

   V nabídce Start systému Windows můžete vyhledat "instalační program".

   ![Instalační program pro Visual Studio](media/vs-2019/visual-studio-installer.png "Vyhledejte Instalační program pro Visual Studio")

   Než budete pokračovat, bude pravděpodobně nutné aktualizovat instalační program. Pokud ano, postupujte podle pokynů.

1. V instalačním programu vyhledejte edici sady Visual Studio, kterou jste nainstalovali.

   Například pokud jste dříve nainstalovali Visual &nbsp; Studio Community &nbsp; 2019 a pro něj existuje aktualizace, zobrazí se v instalačním programu zpráva **k dispozici aktualizace** .

     ![Vyberte edici sady Visual Studio 2019, kterou chcete aktualizovat.](media/vs-2019/vs-installer-update-visual-studio-community.png "Vyberte edici sady Visual Studio 2019, kterou chcete aktualizovat.")

1. Pro instalaci aktualizací vyberte **aktualizovat** .

    ![Kliknutím na tlačítko Aktualizovat nainstalujete aktualizace.](media/vs-2019/vs-installer-choose-update-visual-studio-community.png "Kliknutím na tlačítko Aktualizovat nainstalujete aktualizace.")

1. Po dokončení aktualizace se může zobrazit výzva k restartování počítače. Pokud ano, udělejte to a potom spusťte Visual Studio jako obvykle.

   Pokud se vám nezobrazí výzva k restartování počítače, klikněte na tlačítko **Spustit** a spusťte aplikaci Visual Studio z instalačního programu.

    ![Kliknutím na tlačítko Spustit spusťte aplikaci Visual Studio.](media/vs-2019/choose-launch-visual-studio-community.png "Kliknutím na tlačítko Spustit spusťte aplikaci Visual Studio.")

## <a name="use-the-ide"></a>Použití integrovaného vývojového prostředí

Aktualizaci můžete vyhledat a pak ji nainstalovat pomocí řádku nabídek nebo vyhledávacího pole v aplikaci Visual Studio 2019.

### <a name="open-visual-studio"></a>Otevřete sadu Visual Studio.

1. V nabídce **Start** systému Windows vyberte možnost **Visual Studio 2019**.

    ![Otevřete Visual Studio 2019](media/vs-2019/vs-installer-visual-studio-2019.png "Otevřete Visual Studio 2019 z Windows.")

1. V části **Začínáme** vyberte libovolnou možnost a otevřete integrované vývojové prostředí (IDE).

    ![Otevřete Instalační program pro Visual Studio](media/vs2019-choose-option-from-get-started.png "Otevřete Instalační program pro Visual Studio")

    Otevře se Visual Studio. V integrovaném vývojovém prostředí se zobrazí zpráva **aktualizace sady Visual Studio 2019** .

    ![Zpráva o aktualizaci sady Visual Studio 2019 v integrovaném vývojovém prostředí](media/vs-2019/update-visual-studio-ide-message.png "Zpráva o aktualizaci sady Visual Studio 2019 v integrovaném vývojovém prostředí")

1. Ve zprávě **aktualizace sady Visual Studio 2019** vyberte možnost **Zobrazit podrobnosti**.

   ![Vyberte tlačítko Zobrazit podrobnosti ve zprávě aktualizace IDE sady Visual Studio 2019](media/vs-2019/update-visual-studio-ide-view-details.png "Klikněte na tlačítko Zobrazit podrobnosti ve zprávě aktualizace sady Visual Studio 2019.")

1. V dialogovém okně **stažená aktualizace a připraveno k instalaci** vyberte **aktualizovat**.

     ![V dialogovém okně aktualizace staženého a připraveno k instalaci klikněte na tlačítko Aktualizovat.](media/vs-2019/update-ready-install-visual-studio-community-from-ide.png "V dialogovém okně aktualizace staženého a připraveno k instalaci klikněte na tlačítko Aktualizovat.")

   Visual Studio aktualizuje, zavírá a znovu otevírá.

### <a name="in-visual-studio"></a>V nástroji Visual Studio

1. V řádku nabídek zvolte možnost **help** a pak možnost **Vyhledat aktualizace**.

     ![V nabídce nápovědu vyberte možnost vyhledat aktualizace.](media/vs-2019/vs-ide-check-updates-help-menu.png "V nabídce nápovědu vyberte možnost vyhledat aktualizace.")

    > [!NOTE]
    > Můžete také použít vyhledávací pole v integrovaném vývojovém prostředí (IDE) a vyhledat aktualizace. Stiskněte **kombinaci kláves CTRL** + **Q**, zadejte "Vyhledat aktualizace" a pak zvolte výsledek hledání, který odpovídá.

1. V dialogovém okně **aktualizace k dispozici** vyberte **aktualizovat**.

     ![Klikněte na tlačítko Aktualizovat v dialogovém okně aktualizace k dispozici.](media/vs-2019/update-visual-studio-community-from-ide.png "Klikněte na tlačítko Aktualizovat v dialogovém okně aktualizace k dispozici.")

   Visual Studio aktualizuje, zavírá a znovu otevírá.

## <a name="use-the-notifications-hub"></a>Použití centra oznámení

1. V aplikaci Visual Studio uložte svou práci.

1. Kliknutím na ikonu oznámení v pravém dolním rohu integrovaného vývojového prostředí sady Visual Studio otevřete centrum **oznámení** .

   ![Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio](media/vs-2019/notification-bar.png "Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio")

1. V **centru oznámení** zvolte aktualizaci, kterou chcete nainstalovat, a pak zvolte **Zobrazit podrobnosti**.

     ![Centrum oznámení v aplikaci Visual Studio 2019](media/vs-2019/notification-hub-update.png "Centrum oznámení v aplikaci Visual Studio 2019")

      > [!TIP]
      > Aktualizace pro edici sady Visual Studio 2019 je kumulativní, takže se vždy rozhodnete nainstalovat jednu s nejnovějším číslem verze.

1. V dialogovém okně **aktualizace k dispozici** vyberte **aktualizovat**.

   Visual Studio aktualizuje, zavírá a znovu otevírá.

## <a name="customize-update-settings"></a>Přizpůsobení nastavení aktualizace

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
