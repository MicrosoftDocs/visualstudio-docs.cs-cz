---
title: Instalace Visual Studia 2019 pro Mac
description: Pokyny k instalaci Visual Studia 2019 pro Mac a dalších součástí potřebných pro vývoj napříč platformami.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: 45f9756607cbb638d1f69f77bdf8cd2ee30953c5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75851940"
---
# <a name="install-visual-studio-2019-for-mac"></a>Instalace Visual Studia 2019 pro Mac

Pokud chcete začít vyvíjet nativní aplikace .NET napříč platformami v macOS, nainstalujte Visual Studio 2019 for Mac podle následujících kroků.

 > [!div class="button"]
 > [Stažení Visual Studia pro Mac](https://visualstudio.microsoft.com/vs/mac/)

## <a name="requirements"></a>Požadavky

- Mac s macOS High Sierra 10.12 nebo vyšším.

Chcete-li vytvářet aplikace Xamarin pro iOS nebo macOS, budete také potřebovat:

- Xcode 10.0 nebo vyšší. Obvykle se doporučuje nejnovější stabilní verze.
- An Apple ID. Pokud už Apple ID nemáte, můžete si na https://appleid.apple.com. Pro instalaci a přihlášení ke Xcode je nutné mít Apple ID.

## <a name="installation-instructions"></a>Pokyny k instalaci

1. Stáhněte si instalační program ze [stránky pro stažení visual studia pro Mac](https://visualstudio.microsoft.com/vs/mac/).
2. Po dokončení stahování klikněte na **VisualStudioforMacInstaller.dmg** připojit instalační program, pak jej spustit poklepáním na logo šipky:

    [![Kliknutím na velkou šipku zahájíte instalaci.](media/install-installer-sml.png)](media/install-installer.png#lightbox)

3. Může se vám naskytnout upozornění týkající se aplikace stažené z Internetu. Klikněte na **Otevřít**.
4. Počkejte, než instalátor zkontroluje váš systém:

    [![Instalační program zkontroluje, zda systém nenainstalované součásti](media/install-checking-sml.png)](media/install-checking.png#lightbox)

5. Zobrazí se upozornění s žádostí o potvrzení ochrany osobních údajů a licenčních podmínek. Postupujte podle odkazů a přečtěte si je a stiskněte **tlačítko Pokračovat,** pokud souhlasíte:

    [![Sledujte odkazy na ochranu osobních údajů a podmínky a pokračujte, pokud souhlasíte](media/install-privacy.png)](media/install-privacy.png#lightbox)

6. Zobrazí se seznam dostupných úloh. Vyberte součásti, které chcete použít:

    [![Zvolte, které volitelné funkce pracovního vytížení chcete nainstalovat](media/install-selection.png)](media/install-selection.png#lightbox)

   Pokud si nepřejete instalovat všechny platformy, použijte níže uvedenou příručku, která vám pomůže rozhodnout, které platformy nainstalovat:


|Typ aplikace  |Cíl  |Výběr  |Poznámky  |
|---------|---------|---------|---------|
|**Aplikace používající Xamarin**| Xamarin.Forms|Výběr platforem **Android** a **iOS** |Budete muset nainstalovat [ **Xcode**](https://developer.apple.com/xcode/) |
||Jenom iOS|Výběr **platformy iOS**|Budete muset nainstalovat [ **Xcode**](https://developer.apple.com/xcode/)|
||Pouze pro Android|Vybrat platformu **Android**|Všimněte si, že byste měli také vybrat příslušné závislosti|
||Pouze Mac|Vyberte platformu **macOS (Kakao)**|Budete muset nainstalovat [ **Xcode**](https://developer.apple.com/xcode/)|
|**Základní aplikace .NET**|         |Vyberte **platformu .NET Core.**|         |
|**Webové aplikace ASP.NET Core**|         |Vyberte **platformu .NET Core.**|         |
|**Azure Functions**|         |Vyberte **platformu .NET Core.**|         |
|**Vývoj her Unity napříč platformami**|         |Kromě Visual Studia pro Mac není třeba instalovat žádné další platformy.| Další informace o instalaci rozšíření Unity naleznete v [průvodci nastavením Unity.](/visualstudio/mac/setup-vsmac-tools-unity)|


7. Po výběru stiskněte tlačítko **Instalovat.**
8. Instalační program zobrazí průběh stahování a instalace Visual Studia pro Mac a vybraných úloh. Budete vyzváni k zadání hesla, abyste udělili oprávnění potřebná k instalaci.:

    [![Zvolte, které volitelné funkce pracovního vytížení chcete nainstalovat](media/installation-progress.png)](media/installation-progress.png#lightbox)

9. Po instalaci vás Visual Studio for Mac vyzve k přizpůsobení instalace přihlášením a výběrem klíčových vazeb, které chcete použít:

    [![Přihlášení k ide](media/ide-tour-2019-start-signin.png)](media/ide-tour-2019-start-signin.png#lightbox)

    [![Zvolte, které klávesové zkratky chcete použít](media/ide-tour-2019-keyboard-shortcut.png)](media/ide-tour-2019-keyboard-shortcut.png#lightbox)

Pokud máte při instalaci v podnikovém prostředí potíže se sítí, přečtěte si [instalaci za bránou firewall nebo](/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server) pokyny pro proxy server.

Další informace o změnách v [poznámkách k verzi](/visualstudio/releasenotes/vs2019-mac-relnotes).

> [!NOTE]
> Pokud jste se během původní instalace rozhodli neinstalovat platformu nebo nástroj (zrušením výběru v kroku #6), je nutné instalační program spustit znovu, pokud chcete součásti přidat později.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalace Visual Studia pro Mac za bránu firewall nebo proxy server

Chcete-li nainstalovat Visual Studio pro Mac za bránu firewall, musí být některé koncové body přístupné, aby bylo možné stahovat požadované nástroje a aktualizace softwaru.

Nakonfigurujte síť tak, aby umožňovala přístup k následujícím umístěním:

- [Koncové body Visual Studio](/visualstudio/mac/install-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Další kroky

Instalace Visual Studia pro Mac umožňuje začít psát kód pro vaše aplikace. Následující příručky jsou k dispozici vás provede další kroky psaní a nasazování projektů.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Zřizování zařízení](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(Chcete-li spustit aplikaci na zařízení).

### <a name="android"></a>Android

1. [Použití Správce sdk pro Systém Xamarin Android](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulátor sady Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Nastavení zařízení pro vývoj](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core aplikace, ASP.NET základní webové aplikace, Unity vývoj her

Další úlohy najdete na stránce [Úlohy.](workloads.md)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio (ve Windows)](/visualstudio/install/install-visual-studio)
