---
title: Instalace sady Visual Studio 2017 pro Mac
description: Pokyny k instalaci Visual Studio pro Mac a dalších součástí potřebných pro vývoj pro různé platformy.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: decbdc244a7947b715b8ba5b27bda5aaf50d2266
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950608"
---
# <a name="install-visual-studio-2017-for-mac"></a>Instalace sady Visual Studio 2017 pro Mac

> [!NOTE]
> Visual Studio 2019 pro Mac je [teď k dispozici](installation.md?view=vsmac-2019). Starší verze Visual Studio pro Mac najdete na [stránce soubory ke stažení](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)pro Visual Studio.

## <a name="downgrading-from-visual-studio-2019-for-mac"></a>Downgrading ze sady Visual Studio 2019 for Mac?

Pro dosažení co nejlepších výsledků byste měli před přechodem do downgradu zajistit [odinstalaci](uninstall.md) sady Visual Studio 2019 for Mac. Pokud máte problémy, které by vám způsobily stažení, nezapomeňte nám sdělit [problém](report-a-problem.md).
 
## <a name="requirements"></a>Požadavky

Pokud chcete začít s vývojem nativních aplikací pro různé platformy při stažení Visual Studio pro Mac existuje několik věcí, které je potřeba nainstalovat a nastavit v přípravě.

Pro práci se systémem iOS v aplikaci Visual Studio potřebujete následující části:

- Počítač Mac s macOS vysokým 10,13 nebo novějším.
- Xcode 9,3 nebo vyšší. Obvykle se doporučuje nejnovější stabilní verze.
- Apple ID. Pokud ještě nemáte Apple ID, můžete ho vytvořit v https://appleid.apple.com . Je potřeba, abyste měli Apple ID pro instalaci a přihlášení do Xcode.

## <a name="install"></a>Instalace

1. Stažení Visual Studio pro Mac z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202017%20for%20Mac)

2. Po stažení balíčku instalačního programu kliknutím na soubor **VisualStudioForMacInstaller. dmg** připojte instalační program a spusťte ho dvojitým kliknutím na logo, jak je znázorněno na následujícím obrázku:

   ![Dialog instalačního programu](media/installer-image1.png)

3. Může se zobrazit dialogové okno s výstrahou, podobně jako na následujícím obrázku. V takovém případě klikněte na **otevřít**:

   ![Dialogové okno výstrahy](media/installer-image2.png)

4. Instalační služba zkontroluje váš systém a ověří, které součásti je třeba nainstalovat nebo aktualizovat:

   ![Vyhodnocení vašeho systému](media/installer-image3.png)

5. Zobrazí se dialogové okno výstrahy s výzvou k potvrzení ochrany osobních údajů a licenčních podmínek. Kliknutím na tlačítko **pokračovat** potvrďte tyto výrazy:

   ![Dialog License](media/installer-image4.png)

6. Instalační program zobrazí seznam požadovaných součástí, které chybí a které je potřeba stáhnout a nainstalovat. Vyberte produkty, které si přejete stáhnout:

   ![Vybrat položky](media/installer-image5.png)

   Pokud nechcete instalovat všechny platformy, použijte Průvodce níže, který vám pomůže určit, které platformy se mají nainstalovat:

   * **Aplikace používající Xamarin**:
      - Xamarin. Forms – výběr platforem **Android** a **iOS** .
      - jenom iOS – vyberte platformu **iOS** (Všimněte si, že budete muset nainstalovat [**Xcode**](https://developer.apple.com/xcode/)).
      - Jenom Android – vyberte platformu **Android** (Všimněte si, že byste také měli vybrat relevantní závislosti).
      - Jenom Mac – vyberte platformu **MacOS** (Všimněte si, že budete muset nainstalovat [**Xcode**](https://developer.apple.com/xcode/)).
      - Aplikace Xamarin pro více platforem – vyberte platformy **Android**, **iOS**a **MacOS** .
   * **Aplikace .NET Core** – vyberte platformu **.NET Core** .
   * **ASP.NET Core webové aplikace** – vyberte platformu **.NET Core** .
   * **Vývoj her v Unity pro různé platformy** – nemusíte instalovat žádné další platformy nad rámec Visual Studio pro Mac. Další informace o instalaci rozšíření Unity najdete v [Průvodci nastavením Unity](/visualstudio/mac/setup-vsmac-tools-unity) .

   Tato instalační obrazovka zobrazuje verzi a velikost jednotlivých komponent. Můžete kliknout na jednotlivé komponenty a zobrazit tak seznam závislostí pro tuto součást (pro Android), zobrazit další balíčky, které stahuje (pro .NET Core), nebo zobrazit další požadované aplikace (pro iOS a macOS):

   ![Další závislosti pro Android](media/installer-image6.png)

7. Až budete s výběrem spokojeni, kliknutím na tlačítko **instalovat a aktualizovat** spusťte proces instalace.

8. Instalační program spustí proces stažení a instalace vybraných položek:

   ![Spouští se instalace](media/installer-image7.png)

   ![Stahuje se Xamarin. Mac.](media/installer-image8.png)

   ![Dokončuje se instalace.](media/installer-image9.png)

9. Může se zobrazit výzva k zvýšení oprávnění potřebných pro jednotlivé komponenty, které jsou potřebné k dokončení instalace. Sem zadejte přihlašovací údaje správce, aby bylo možné pokračovat v procesu instalace:

   ![Zadejte oprávnění pro pokračování v instalačním programu](media/installer-image10.png)

10. Po úspěšném dokončení instalace můžete začít vyvíjet aplikace v aplikaci Visual Studio stisknutím klávesy **Start**:

    ![Otevřete sadu Visual Studio.](media/installer-image11.png)

> [!NOTE]
> Pokud jste se rozhodli neinstalovat platformu nebo nástroj během původní instalace (tím, že je zrušíte výběr v kroku #6), musíte [instalační program](https://visualstudio.microsoft.com/vs/) spustit znovu, pokud chcete přidat komponenty později.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalace Visual Studio pro Mac za bránou firewall nebo proxy server

Aby bylo možné nainstalovat Visual Studio pro Mac za bránou firewall, je nutné, aby byly k dispozici určité koncové body, aby bylo možné stáhnout požadované nástroje a aktualizace softwaru.

Nakonfigurujte síť tak, aby povolovala přístup do následujících umístění:

- [Koncové body sady Visual Studio](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Další kroky

Instalace Visual Studio pro Mac umožňuje začít psát kód pro vaše aplikace. K dispozici jsou následující příručky, které vás provedou dalšími kroky při psaní a nasazování vašich projektů.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Zřizování zařízení](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(pro spuštění aplikace na zařízení).

### <a name="android"></a>Telefon

1. [Použití nástroje Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulátor sady Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Nastavení zařízení pro vývoj](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplikace .NET Core, ASP.NET Core Web Apps, vývoj her v Unity

Další úlohy najdete na stránce [úlohy](/visualstudio/mac/workloads) .

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Acquisition/player]

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio 2017 (v systému Windows)](/visualstudio/install/install-visual-studio)
