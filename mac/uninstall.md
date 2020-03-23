---
title: Odinstalace Visual Studia pro Mac
description: Pokyny pro odinstalaci Sady Visual Studio pro Mac a souvisejících nástrojů.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.openlocfilehash: 348a6ad1bde58c17b2bbb1ef4868fcfa6835ef9f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "76892165"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Odinstalace Visual Studio pro Mac

Pomocí této příručky můžete odinstalovat jednotlivé součásti v sadě Visual Studio for Mac jednotlivě přechodem na příslušnou část nebo můžete odinstalovat vše pomocí skriptů uvedených v části [Odinstalovat skript.](#uninstall-script)

> [!NOTE]
> Tyto informace odeberou jenom Visual Studio 2019 nebo 2017 pro Mac z vašeho počítače. chcete-li odinstalovat kód sady Visual Studio, přečtěte [si tento problém](https://github.com/Microsoft/vscode/issues/52151) podrobnosti.

## <a name="uninstall-script"></a>Odinstalovat skript

Existují dva skripty, které lze použít k odinstalaci sady Visual Studio pro Mac a všechny součásti pro váš počítač:

- [Skript Visual Studio a Xamarin](#visual-studio-for-mac-and-xamarin-script)
- [Základní skript rozhraní .NET](#net-core-script)

Následující části obsahují informace o stahování a používání skriptů.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Visual Studio pro Mac a Xamarin skript

Součásti sady Visual Studio a Xamarin můžete odinstalovat najednou pomocí [odinstalačního skriptu](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Tento odinstalační skript obsahuje většinu příkazů, které najdete v článku. Existují tři hlavní opomenutí ze skriptu a nejsou zahrnuty z důvodu možných externích závislostí. Chcete-li toto odstranit, přejděte na příslušnou část níže a ručně je odeberte:

- **[Odinstalace mono](#uninstall-mono-sdk-mdk)**
- **[Odinstalace systému Android AVD](#uninstall-android-avd)**
- **[Odinstalace sady Android SDK a Java SDK](#uninstall-android-sdk-and-java-sdk)**

Chcete-li skript spustit, postupujte takto:

1. Klikněte pravým tlačítkem myši na skript a výběrem **možnosti Uložit jako** uložte soubor na Mac.
2. Otevřete terminál a změňte pracovní adresář na místo, kde byl skript stažen:

    ```bash
    cd /location/of/file
    ```

3. Make skript spustitelný a spustit jej s **sudo**:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Nakonec odstraňte odinstalační skript a odeberte Visual Studio pro Mac z doku (pokud tam je).

### <a name="net-core-script"></a>Základní skript rozhraní .NET

Odinstalační skript pro rozhraní .NET Core je umístěn v [repo dotnet cli](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh)

Chcete-li skript spustit, postupujte takto:

1. Klikněte pravým tlačítkem myši na skript a výběrem **možnosti Uložit jako** uložte soubor na Mac.
2. Otevřete terminál a změňte pracovní adresář na místo, kde byl skript stažen:

    ```bash
    cd /location/of/file
    ```

3. Make skript spustitelný a spustit jej s **sudo**:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Nakonec odstraňte odinstalační skript .NET Core.

## <a name="uninstall-visual-studio-for-mac"></a>Odinstalace Visual Studia pro Mac

Prvním krokem při odinstalaci Sady Visual Studio z Macu je vyhledání **souboru Visual Studio.app** v **adresáři /Applications** a přetažení do **koše**. Případně klikněte pravým tlačítkem myši a vyberte **Přesunout do koše,** jak je znázorněno na následujícím obrázku:

![Přesunutí aplikace Visual Studia do koše](media/uninstall-image1.png)

Odstraněním této sady aplikací odeberete Visual Studio pro Mac, i když v systému souborů mohou být další soubory související s Xamarinem.

Chcete-li odebrat všechny stopy visual studia pro Mac, spusťte v terminálu následující příkazy:

```bash
sudo rm -rf "/Applications/Visual Studio.app"
rm -rf ~/Library/Caches/VisualStudio
rm -rf ~/Library/Preferences/VisualStudio
rm -rf ~/Library/Preferences/Visual\ Studio
rm -rf ~/Library/Logs/VisualStudio
rm -rf ~/Library/VisualStudio
rm -rf ~/Library/Preferences/Xamarin/
rm -rf ~/Library/Application\ Support/VisualStudio
rm -rf ~/Library/Application\ Support/VisualStudio/7.0/LocalInstall/Addins/
rm -rf ~/Library/Application\ Support/VisualStudio/8.0/LocalInstall/Addins/
```

Můžete také odebrat následující adresář obsahující různé soubory a složky Xamarin. Než tak učiníte, měli byste si však být vědomi toho, že tento adresář obsahuje podpisové klíče Android. Další informace naleznete v části **[Odinstalace sady Android SDK a Java SDK](#uninstall-android-sdk-and-java-sdk)**:

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Odinstalovat mono sdk (MDK)

Mono je open source implementace rozhraní .NET Framework společnosti Microsoft a používá ji všechny produkty Xamarin – Xamarin.iOS, Xamarin.Android a Xamarin.Mac, které umožňují vývoj těchto platforem v systému C#.

> [!WARNING]
> Existují další aplikace mimo Visual Studio pro Mac, které také používají Mono, jako je například Unity.
> Ujistěte se, že neexistují žádné další závislosti na Mono před odinstalováním.

Chcete-li odebrat mono framework z počítače, spusťte v terminálu následující příkazy:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Odinstalovat Xamarin.Android

Existuje celá řada položek potřebných pro instalaci a použití Xamarin.Android, například Android SDK a Java SDK.

K odebrání Xamarinu použijte následující příkazy:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Odinstalace sady Android SDK a Java SDK

Android SDK je vyžadován pro vývoj aplikací pro Android. Chcete-li zcela odebrat všechny části sady Android SDK, vyhledejte soubor na **adrese ~/Library/Developer/Xamarin/** a přesuňte jej do **koše**.

> [!WARNING]
> Měli byste si být vědomi toho, že podpisové klíče `~/Library/Developer/Xamarin/Keystore`Android, které jsou generovány Visual Studio pro Mac jsou umístěny v . Ujistěte se, že zálohovat tyto vhodně, nebo se vyhnout odebrání tohoto adresáře, pokud chcete zachovat úložiště klíčů.

Java SDK (JDK) nemusí být odinstalován, protože je již předem zabalen jako součást Mac OS X / macOS.

### <a name="uninstall-android-avd"></a>Odinstalace systému Android AVD

> [!WARNING]
> Existují i jiné aplikace mimo Visual Studio pro Mac, které také používají Android AVD a tyto další součásti android, jako je například Android Studio.Odebrání tohoto adresáře může způsobit, že se projekty v Android Studiu přeruší.

Chcete-li odebrat všechny AVD android a další součásti Android, použijte následující příkaz:

```bash
rm -rf ~/.android
```

Chcete-li odebrat pouze zařízení Android AVD, použijte následující příkaz:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Odinstalace xamarin.iOS

Xamarin.iOS umožňuje vývoj aplikací iOS pomocí C# nebo F# s Visual Studio pro Mac.

Pomocí následujících příkazů v terminálu odeberte všechny soubory Xamarin.iOS ze systému souborů:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Odinstalace Xamarin.Macu

Xamarin.Mac lze z vašeho počítače odebrat pomocí následujících dvou příkazů k odstranění produktu a licence z vašeho Macu:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Odinstalace sešitů a inspektoru

Počínaje 1.2.2 lze sešity Xamarin & Inspector odinstalovat z terminálu spuštěním:

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

U starších verzí je třeba ručně odebrat následující artefakty:

* Odstranění aplikace Sešity na adrese`"/Applications/Xamarin Workbooks.app"`
* Odstranit aplikaci Inspektor na adrese`"Applications/Xamarin Inspector.app"`
* Odstraňte doplňky: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` a`"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Odstranit inspektora a podpůrné `/Library/Frameworks/Xamarin.Interactive.framework` soubory zde: a`/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Odinstalace profilovače Xamarin

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Odinstalace Instalačního programu sady Visual Studio

Pomocí následujících příkazů odeberte všechna stopy univerzálního instalačního programu Xamarin:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

* * * 





## <a name="uninstall-visual-studio-2019-for-mac-preview"></a>Odinstalace Visual Studia 2019 pro Mac Preview

Visual Studio 2019 pro Mac Preview bylo spuštěno jako samostatná verze preview, která vám umožní pokračovat ve spolupráci s instalací Visual Studia 2017 pro Mac vedle sebe.

Teď, když visual studio 2019 pro Mac bylo vydáno, můžete teď bezpečně odebrat aplikaci Visual Studio 2019 for Mac Preview.

Chcete-li odinstalovat sadu aplikací náhledu, vyberte ve složce **Aplikace** **možnost Visual Studio (Náhled)** a klikněte na **Přesunout do koše**, jak je znázorněno na následujícím obrázku:

![výběr možnosti "přesunout do koše" ve finderu](media/uninstall-remove-vspreview.png)

Soubor plist náhledu můžete také odebrat pomocí následujícího příkazu:

```bash
rm -rf ~/Library/Preferences/com.microsoft.visual-studio-preview.plist
```

## <a name="see-also"></a>Viz také

- [Odinstalace Sady Visual Studio (ve Windows)](/visualstudio/install/uninstall-visual-studio)