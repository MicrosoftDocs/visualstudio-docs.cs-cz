---
title: Instalace sady Visual Studio pro Mac
description: Pokyny k instalaci sady Visual Studio pro Mac a další komponenty potřebné pro vývoj pro různé platformy.
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: e725234cadc301d5e0e369131efd53c1c69d6337
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53158954"
---
# <a name="set-up-and-install-visual-studio-for-mac"></a>Nastavte nahoru a instalace sady Visual Studio pro Mac

## <a name="requirements"></a>Požadavky

Pro počáteční vývoj nativních, jsou aplikací napříč platformami, když si stáhnout Visual Studio pro Mac existuje několik věcí, které musíte nainstalovat a nastavit v rámci přípravy.

Pro práci se systémem iOS v sadě Visual Studio potřebujete následující:

* počítač Mac s macOS Sierra 10.12 nebo vyšší
* Xcode 8.3 nebo vyšší. Nejnovější stabilní verze je obvykle vhodné.
* Apple ID. Pokud ještě nemáte Apple ID můžete vytvořit nový na https://appleid.apple.com. Je potřeba mít Apple ID, instalace a přihlášení do Xcode.

> [!TIP]
> 2019 Visual Studio pro Mac ve verzi preview je [nyní k dispozici](install-preview.md) pro testování.

## <a name="install"></a>Instalace

1. Stáhněte si Visual Studio for Mac z [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com/)

2. Po stažení instalačního programu balíčku, klikněte na tlačítko **VisualStudioForMacInstaller.dmg** souboru připojit instalační program a spusťte jej dvojitým kliknutím logo, jak je znázorněno v následujícím obrázku:

   ![Dialogové okno instalačního programu](media/installer-image1.png)

3. Můžete být vyzváni pomocí dialogového okna výstrah podobně jako na následujícím obrázku. V tomto případě klikněte na tlačítko **otevřít**:

   ![dialogového okna výstrah](media/installer-image2.png)

4. Instalační program zkontroluje váš systém ověření komponenty, které potřebujete k instalaci nebo aktualizaci:

   ![Vyhodnocení systému](media/installer-image3.png)

5. Zobrazí se vám pak pomocí dialogového okna výstrah s výzvou k potvrzení o ochraně osobních údajů a licenční podmínky. Stisknutím klávesy **pokračovat** tlačítko potvrďte podmínky:

   ![Dialogové okno licence](media/installer-image4.png)

6. Instalační program zobrazí seznam požadovaných součástí, které nebyly nalezeny a, které je potřeba stáhnout a nainstalovat. Vyberte produkty, které si chcete stáhnout tady:

   ![Vybrat položky](media/installer-image5.png)

   Pokud nechcete instalovat všechny platformy, vám pomohou rozhodnout, které platformy nainstalovat pomocí Průvodce níže:

   * **Aplikace pomocí Xamarinu**:
      - Xamarin.Forms – vyberte **Android** a **iOS** platformy.
      - iOS – vybrat **iOS** platformy (Všimněte si, že budete muset nainstalovat [ **Xcode**](https://developer.apple.com/xcode/)).
      - Android – vybrat **Android** platformy (Všimněte si, že musí také vybrat příslušné závislosti).
      - Vybrat pouze – Mac **macOS** platformy (Všimněte si, že budete muset nainstalovat [ **Xcode**](https://developer.apple.com/xcode/)).
      - Vyberte plně multiplatformní aplikace Xamarin – **Android**, **iOS**, a **macOS** platformy.
   * **Aplikace .NET core** – vyberte **.NET Core** platformy.
   * **Webové aplikace ASP.NET Core** – vyberte **.NET Core** platformy.
   * **Multiplatformní vývoj her Unity** – žádné další platformy je potřeba nainstalovat za Visual Studio pro Mac. Odkazovat [Průvodce nastavením Unity](setup-vsmac-tools-unity.md) pro další informace o instalaci rozšíření Unity.

   Tento instalační obrazovce zobrazí verzi a velikost jednotlivých součástí. Můžete kliknout jednotlivých komponent pro zobrazení seznamu závislostí pro danou součást (pro Android), najdete v další balíčky, které stáhne (pro .NET Core), nebo zobrazit další aplikace vyžaduje (pro iOS a macOS):

   ![Android Další závislosti](media/installer-image6.png)

7. Jakmile budete spokojeni se svým výběrem, vyberte **instalovat a aktualizovat** tlačítko pro spuštění procesu instalace.

8. Instalační program spustí stahování a instalace z vybraných položek:

   ![Spouští se instalace](media/installer-image7.png)

   ![Stahování Xamarin.Mac](media/installer-image8.png)

   ![Dokončuje se instalace](media/installer-image9.png)

9. Můžete být vyzváni ke zvýšení oprávnění potřebná pro jednotlivé součásti, které jsou vyžadovány k dokončení instalace. Zadejte pověření správce a pokračujte v procesu instalace:

   ![Zadejte oprávnění, abyste mohli pokračovat s instalačním programem](media/installer-image10.png)

10. Jakmile je instalace úspěšná, můžete začít vyvíjet aplikace ve Visual Studiu stisknutím klávesy **Start**:

    ![Otevřít Visual Studio](media/installer-image11.png)

> [!NOTE]
> Pokud jste zvolili neinstaluje platformu nebo nástroj při původní instalaci (zrušením výběru ho v kroku #6), musíte spustit [instalační program](https://visualstudio.microsoft.com/vs/) znovu Pokud budete chtít později přidat komponenty.

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>Instalace sady Visual Studio pro Mac za bránou firewall nebo proxy serverem

Instalace sady Visual Studio pro Mac za bránou firewall, některé koncové body musí být přístupné umožní se soubory ke stažení potřebné nástroje a aktualizací softwaru.

Konfigurace sítě pro povolení přístupu do následujících umístění:

* [Visual Studio koncových bodů](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>Další kroky

Instalace sady Visual Studio for Mac umožňuje začít psát kód pro vaše aplikace. Následující pokyny jsou k dispozici pro vás provedou další kroky vytváření a nasazování vašich projektů.

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [Zřizování zařízení](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning)(pro spuštění vaší aplikace na zařízení).

### <a name="android"></a>Android

1. [Pomocí Xamarin Android SDK Manager](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Emulátor sady Android SDK](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [Nastavení zařízení pro vývoj](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>Aplikace .NET core, ASP.NET Core webových aplikací, vývoj her pro Unity

Další úlohy, najdete [úlohy](workloads.md) stránky.

## <a name="see-also"></a>Viz také:

- [Instalace sady Visual Studio 2017 (ve Windows)](/visualstudio/install/install-visual-studio)
