---
title: Instalace sady Visual Studio 2019 pro Mac
description: Pokyny k instalaci sady Visual Studio 2019 pro Mac a další součásti, které jsou potřeba pro vývoj pro různé platformy.
author: asb3993
ms.author: amburns
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 1ace600f9c4582e99c6fa324cb9dcc61593d3d97
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73716778"
---
# <a name="install-visual-studio-2019-for-mac"></a>Instalace sady Visual Studio 2019 pro Mac

K zahájení vývoje nativních aplikací .NET pro více platforem na macOS nainstalujte Visual Studio 2019 pro Mac podle následujících kroků.

 > [!div class="button"]
 > [Stáhnout Visual Studio pro Mac](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=navigation+cta&utm_content=download+vsmac2019)

## <a name="requirements"></a>Požadavky

- Počítač Mac s macOS vysokým 10,12 nebo novějším.

Pro sestavování aplikací Xamarin pro iOS nebo macOS budete také potřebovat:

- Xcode 10,0 nebo vyšší. Obvykle se doporučuje nejnovější stabilní verze.
- Apple ID. Pokud ještě nemáte Apple ID, můžete ho vytvořit na https://appleid.apple.com. Je potřeba, abyste měli Apple ID pro instalaci a přihlášení do Xcode.

## <a name="installation-instructions"></a>Pokyny k instalaci

1. Stáhněte instalační program ze [stránky pro stažení Visual Studio pro Mac](https://aka.ms/vsmac).
2. Po dokončení stahování kliknutím na **VisualStudioforMacInstaller. dmg** připojte instalační program a potom ho spusťte dvojitým kliknutím na logo šipky:

    [![kliknutím na velkou šipku spusťte instalaci.](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Je možné, že se zobrazí upozornění na aplikaci, která se stahuje z Internetu. Klikněte na **otevřít**.
4. Počkejte, než instalační program zkontroluje váš systém:

    [![instalační program zkontroluje nainstalované součásti systému.](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Zobrazí se výstraha s výzvou k potvrzení ochrany osobních údajů a licenčních podmínek. Použijte odkazy pro jejich čtení a pak stiskněte **pokračovat** , pokud souhlasíte:

    [![postupujte podle odkazů na soukromí a podmínky a potom pokračujte v případě, že souhlasíte](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Zobrazí se seznam dostupných úloh. Vyberte komponenty, které chcete použít:

    [![zvolit volitelné funkce úlohy, které chcete nainstalovat.](media/install-selection.png)](media/install-selection.png#lightbox)

   Pokud nechcete instalovat všechny platformy, použijte Průvodce níže, který vám pomůže určit, které platformy se mají nainstalovat:


|Typ aplikace  |Cílové  |Výběr  |Poznámky  |
|---------|---------|---------|---------|
|**Aplikace používající Xamarin**| Xamarin.Forms|Výběr platforem **Android** a **iOS** |Budete muset nainstalovat [ **Xcode**](https://developer.apple.com/xcode/) |
||jenom iOS|Vybrat platformu **iOS**|Budete muset nainstalovat [ **Xcode**](https://developer.apple.com/xcode/)|
||Jenom Android|Vybrat platformu pro **Android**|Všimněte si, že byste také měli vybrat relevantní závislosti.|
||Jenom Mac|Vybrat platformu **MacOS (kakao)**|Budete muset nainstalovat [ **Xcode**](https://developer.apple.com/xcode/)|
|**Aplikace .NET Core**|         |Vyberte platformu **.NET Core** .|         |
|**ASP.NET Core webové aplikace**|         |Vyberte platformu **.NET Core** .|         |
|**Azure Functions**|         |Vyberte platformu **.NET Core** .|         |
|**Vývoj her v Unity pro různé platformy**|         |Kromě Visual Studio pro Mac nemusíte instalovat žádné další platformy.| Další informace o instalaci rozšíření Unity najdete v [Průvodci nastavením Unity](/visualstudio/mac/setup-vsmac-tools-unity) .|


7. Po provedení výběru klikněte na tlačítko **nainstalovat** .
8. Instalační program zobrazí průběh stahování a instalace Visual Studio pro Mac a vybraných úloh. Budete vyzváni k zadání hesla pro udělení oprávnění nutných k instalaci.:

    [![zvolit volitelné funkce úlohy, které chcete nainstalovat.](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Po nainstalování Visual Studio pro Mac vás vyzve k přizpůsobení instalace přihlášením a výběrem vazeb klíčů, které chcete použít:

    [![přihlášení k prostředí IDE](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![vyberte, které klávesové zkratky byste chtěli použít.](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Pokud máte potíže se sítí při instalaci v podnikovém prostředí, Projděte si pokyny k [instalaci za bránou firewall nebo proxy serverem](/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) .

Přečtěte si další informace o změnách v [poznámkách k verzi](/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Pokud se rozhodnete, že během původní instalace nechcete instalovat platformu nebo nástroj (zrušíte jejich výběr v kroku #6), musíte instalační program spustit znovu, pokud chcete přidat komponenty později.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalace Visual Studio pro Mac za bránou firewall nebo proxy server

Aby bylo možné nainstalovat Visual Studio pro Mac za bránou firewall, je nutné, aby byly k dispozici určité koncové body, aby bylo možné stáhnout požadované nástroje a aktualizace softwaru.

Nakonfigurujte síť tak, aby povolovala přístup do následujících umístění:

- [Koncové body sady Visual Studio](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Další kroky

Instalace Visual Studio pro Mac umožňuje začít psát kód pro vaše aplikace. K dispozici jsou následující příručky, které vás provedou dalšími kroky při psaní a nasazování vašich projektů.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Zřizování zařízení](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(pro spuštění aplikace na zařízení).

### <a name="android"></a>Android

1. [Použití nástroje Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulátor sady Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Nastavení zařízení pro vývoj](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplikace .NET Core, ASP.NET Core Web Apps, vývoj her v Unity

Další úlohy najdete na stránce [úlohy](workloads.md) .

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Viz také:

- [Instalace sady Visual Studio (ve Windows)](/visualstudio/install/install-visual-studio)
