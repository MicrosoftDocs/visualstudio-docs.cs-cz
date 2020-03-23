---
title: Instalace Visual Studia 2017 pro Mac
description: Pokyny k instalaci Sady Visual Studio pro Mac a další chod komponent y potřebné pro vývoj napříč platformami.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.openlocfilehash: dfc9f7469f5954aaac56b5d45bb5ae722110dfcc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984908"
---
# <a name="install-visual-studio-2017-for-mac"></a>Instalace Visual Studia 2017 pro Mac

> [!NOTE]
> Visual Studio 2019 pro Mac je [teď k dispozici](installation.md?view=vsmac-2019). Starší verze Visual Studia for Mac najdete na [stránce stažení](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)sady Visual Studio .

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Přechod z Visual Studia 2019 pro Mac?

Pro nejlepší prostředí byste měli před přechodem na nižší verzi zajistit [odinstalaci](uninstall.md) Visual Studia 2019 pro Mac. Pokud máte problémy, které způsobují stažení, dejte nám vědět [nahlášením problému](report-a-problem.md).
 
## <a name="requirements"></a>Požadavky

Chcete-li začít vyvíjet nativní aplikace pro různé platformy při stahování Visual Studia pro Mac, je třeba nainstalovat a nastavit několik věcí při přípravě.

Pro práci s iOS v Sadě Visual Studio potřebujete následující části:

- Mac s macOS Sierra 10.12 nebo vyšším
- Xcode 9.3 nebo vyšší. Obvykle se doporučuje nejnovější stabilní verze.
- An Apple ID. Pokud už Apple ID nemáte, můžete si na https://appleid.apple.com. Pro instalaci a přihlášení ke Xcode je nutné mít Apple ID.

## <a name="install"></a>Instalace

1. Stažení Visual Studia pro Mac z [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)

2. Po stažení instalačního balíčku klikněte na soubor **VisualStudioForMacInstaller.dmg,** abyste nainstalovali instalační program a pak jej spusťte poklepáním na logo, jak ukazuje následující obrázek:

   ![Dialogové okno Instalační program](media/installer-image1.png)

3. Může se zobrazit výzva s výstražným dialogem podobným následujícímu obrázku. V takovém případě klepněte na tlačítko **Otevřít**:

   ![dialogové okno výstrahy](media/installer-image2.png)

4. Instalační program zkontroluje váš systém a ověří, které součásti je třeba nainstalovat nebo aktualizovat:

   ![Posouzení vašeho systému](media/installer-image3.png)

5. Poté se zobrazí dialogové okno s upozorněním, ve kterém budete s žádostí o potvrzení podmínek ochrany osobních údajů a licencí. Stisknutím tlačítka **Pokračovat** potvrďte podmínky:

   ![Dialogové okno Licence](media/installer-image4.png)

6. Instalační program zobrazí seznam požadovaných součástí, které chybí a které je třeba stáhnout a nainstalovat. Zde vyberte produkty, které chcete stáhnout zde:

   ![Vybrat položky](media/installer-image5.png)

   Pokud si nepřejete instalovat všechny platformy, použijte níže uvedenou příručku, která vám pomůže rozhodnout, které platformy nainstalovat:

   * **Aplikace používající Xamarin**:
      - Xamarin.Forms – Vyberte platformy **Android** a **iOS.**
      - Pouze iOS – Vyberte platformu **iOS** (Všimněte si, že budete muset nainstalovat [**Xcode**](https://developer.apple.com/xcode/)).
      - Pouze android – Vyberte platformu **Android** (Všimněte si, že byste měli také vybrat příslušné závislosti).
      - Pouze Mac – Vyberte platformu **macOS** (Všimněte si, že budete muset nainstalovat [**Xcode**](https://developer.apple.com/xcode/)).
      - Plně multiplatformní aplikace Xamarin – Vyberte platformy **Android**, **iOS**a **macOS.**
   * **.NET Core aplikace** – vyberte **platformu .NET Core.**
   * **ASP.NET základní webové aplikace** – vyberte **platformu .NET Core.**
   * **Vývoj her Unity napříč platformami** – kromě Visual Studia pro Mac není třeba instalovat žádné další platformy. Další informace o instalaci rozšíření Unity naleznete v [průvodci nastavením Unity.](/visualstudio/mac/setup-vsmac-tools-unity)

   Na této instalační obrazovce se zobrazí verze a velikost jednotlivých komponent. Kliknutím na jednotlivé komponenty můžete zobrazit seznam závislostí pro tuto komponentu (pro Android), zobrazit další balíčky, které stáhne (pro .NET Core), nebo zobrazit všechny další požadované aplikace (pro iOS a macOS):

   ![Android další závislosti](media/installer-image6.png)

7. Jakmile budete s výběrem spokojeni, spusťte proces instalace výběrem vyberte tlačítko **Instalovat a aktualizovat.**

8. Instalační program spustí proces stahování a instalace vybraných položek:

   ![Spuštění instalace](media/installer-image7.png)

   ![Stahování Xamarin.Mac](media/installer-image8.png)

   ![Dokončovací instalace](media/installer-image9.png)

9. Může být výzva ke zvýšení oprávnění nezbytných pro jednotlivé součásti, které jsou potřebné k dokončení instalace. Chcete-li pokračovat v procesu instalace, zadejte zde pověření správce:

   ![Zadání oprávnění pro pokračování v instalačním programu](media/installer-image10.png)

10. Po úspěšné instalaci můžete začít vyvíjet aplikace v sadě Visual Studio stisknutím **tlačítka Start**:

    ![Otevřete sadu Visual Studio.](media/installer-image11.png)

> [!NOTE]
> Pokud jste se rozhodli neinstalovat platformu nebo nástroj během původní instalace (zrušením výběru v kroku #6), je nutné [instalační program](https://visualstudio.microsoft.com/vs/) spustit znovu, pokud chcete součásti přidat později.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalace Visual Studia pro Mac za bránu firewall nebo proxy server

Chcete-li nainstalovat Visual Studio pro Mac za bránu firewall, musí být některé koncové body přístupné, aby bylo možné stahovat požadované nástroje a aktualizace softwaru.

Nakonfigurujte síť tak, aby umožňovala přístup k následujícím umístěním:

- [Koncové body Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

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

Další úlohy najdete na stránce [Úlohy.](/visualstudio/mac/workloads)

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Viz také

- [Instalace Visual Studia 2017 (ve Windows)](/visualstudio/install/install-visual-studio)
