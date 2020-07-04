---
title: Odinstalace Visual Studio pro Mac
description: Pokyny k odinstalaci Visual Studio pro Mac a souvisejících nástrojů
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 4EB95F75-BC2E-4982-9564-2975805712D8
ms.topic: how-to
ms.openlocfilehash: f8452094f0059a1ffa4421d1ccd02ee244559c72
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950342"
---
# <a name="uninstalling-visual-studio-for-mac"></a>Odinstalace Visual Studio pro Mac

Existuje řada produktů Xamarin, které umožňují vývoj aplikací pro různé platformy, včetně samostatných aplikací, jako je Visual Studio pro Mac.

Tuto příručku můžete použít k odinstalování jednotlivých produktů, a to tak, že přejdete do příslušné části, nebo můžete použít skripty, které jsou uvedené v části [skript odinstalace](#uninstall-script) pro odinstalaci všeho.

## <a name="uninstall-script"></a>Odinstalace skriptu

Existují dva skripty, které lze použít k odinstalování Visual Studio pro Mac a všech komponent pro váš počítač:

- [Visual Studio a skript Xamarin](#visual-studio-for-mac-and-xamarin-script)
- [Skript .NET Core](#net-core-script)

Následující části obsahují informace o stahování a používání skriptů.

### <a name="visual-studio-for-mac-and-xamarin-script"></a>Visual Studio pro Mac a skript Xamarin

Součásti sady Visual Studio a Xamarin můžete odinstalovat v jednom z nich pomocí [skriptu pro odinstalaci](https://raw.githubusercontent.com/MicrosoftDocs/visualstudio-docs/master/mac/resources/uninstall-vsmac.sh).

Tento skript pro odinstalaci obsahuje většinu příkazů, které najdete v článku. Skript obsahuje tři hlavní opomenutí a není zahrnutý v důsledku možných vnějších závislostí. Pokud to chcete odebrat, přejděte do příslušné části níže a odstraňte je ručně:

- **[Odinstalace mono](#uninstall-mono-sdk-mdk)**
- **[Odinstalace Androidu AVD](#uninstall-android-avd)**
- **[Odinstalace Android SDK a Java SDK](#uninstall-android-sdk-and-java-sdk)**

Chcete-li spustit skript, proveďte následující kroky:

1. Klikněte pravým tlačítkem na skript a vyberte **Uložit jako** a uložte soubor na Macu.
2. Otevřete terminál a změňte pracovní adresář na místo, kde byl skript stažen:

    ```bash
    cd /location/of/file
    ```

3. Nastavte spustitelný soubor skriptu a spusťte ho pomocí **sudo**:

    ```bash
    chmod +x ./uninstall-vsmac.sh
    sudo ./uninstall-vsmac.sh
    ```

4. Nakonec odstraňte skript pro odinstalaci.

### <a name="net-core-script"></a>Skript .NET Core

Skript pro odinstalaci pro .NET Core se nachází v úložišti rozhraní příkazového [řádku dotnet](https://raw.githubusercontent.com/dotnet/cli/master/scripts/obtain/uninstall/dotnet-uninstall-pkgs.sh) .

Chcete-li spustit skript, proveďte následující kroky:

1. Klikněte pravým tlačítkem na skript a vyberte **Uložit jako** a uložte soubor na Macu.
2. Otevřete terminál a změňte pracovní adresář na místo, kde byl skript stažen:

    ```bash
    cd /location/of/file
    ```

3. Nastavte spustitelný soubor skriptu a spusťte ho pomocí **sudo**:

    ```bash
    chmod +x ./dotnet-uninstall-pkgs.sh
    sudo ./dotnet-uninstall-pkgs.sh
    ```

4. Nakonec odstraňte skript pro odinstalaci rozhraní .NET Core.

## <a name="uninstall-visual-studio-for-mac"></a>Odinstalace Visual Studio pro Mac

Prvním krokem při odinstalaci sady Visual Studio z počítače Mac je vyhledání sady **Visual Studio. app** v adresáři **/applikace** a jejich přetažení do **koše**. Případně klikněte pravým tlačítkem myši a vyberte možnost **přesunout do koše** , jak je znázorněno na následujícím obrázku:

![Přesunout aplikaci Visual Studio do koše](media/uninstall-image1.png)

Odstraněním tohoto balíčku aplikace odeberete Visual Studio pro Mac, i když můžou být v systému souborů ještě jiné soubory související s Xamarin.

Pokud chcete odebrat všechna trasování Visual Studio pro Mac, spusťte v terminálu následující příkazy:

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
```

Možná budete chtít odebrat i následující adresář, který obsahuje různé soubory a složky Xamarin. Nicméně než byste si měli být vědomi, že tento adresář obsahuje podpisové klíče pro Android. Další informace najdete v části věnované **[odinstalaci Android SDK a Java SDK](#uninstall-android-sdk-and-java-sdk)**:

```bash
rm -rf ~/Library/Developer/Xamarin
```

## <a name="uninstall-mono-sdk-mdk"></a>Odinstalovat sadu mono SDK (MDK)

Mono je open-source implementace .NET Framework Microsoftu a používá se pro všechny produkty Xamarin – Xamarin. iOS, Xamarin. Android a Xamarin. Mac, aby bylo možné vyvíjet tyto platformy v jazyce C#.

> [!WARNING]
> K dispozici jsou jiné aplikace mimo Visual Studio pro Mac, které používají mono, jako je třeba Unity.
> Před odinstalováním se ujistěte, že neexistují žádné další závislosti na mono.

Chcete-li odebrat rozhraní mono z počítače, spusťte v terminálu následující příkazy:

```bash
sudo rm -rf /Library/Frameworks/Mono.framework
sudo pkgutil --forget com.xamarin.mono-MDK.pkg
sudo rm -rf /etc/paths.d/mono-commands
```

## <a name="uninstall-xamarinandroid"></a>Odinstalace Xamarin. Android

Pro instalaci a používání nástroje Xamarin. Android, jako jsou Android SDK a Java SDK, se vyžaduje několik položek.

Pomocí následujících příkazů odeberte Xamarin. Android:

```bash
sudo rm -rf /Developer/MonoDroid
rm -rf ~/Library/MonoAndroid
sudo pkgutil --forget com.xamarin.android.pkg
sudo rm -rf /Library/Frameworks/Xamarin.Android.framework
```

### <a name="uninstall-android-sdk-and-java-sdk"></a>Odinstalace Android SDK a Java SDK

Android SDK se vyžaduje pro vývoj aplikací pro Android. Pokud chcete úplně odebrat všechny části Android SDK, najděte soubor na **~/Library/Developer/Xamarin/** a přesuňte ho do **koše**.

> [!WARNING]
> Měli byste si uvědomit, že podpisové klíče Androidu, které jsou vygenerovány Visual Studio pro Mac, jsou umístěny v `~/Library/Developer/Xamarin/Keystore` . Ujistěte se, že je budete patřičně zálohovali, nebo neodstraňujte tento adresář, pokud chcete uchovávat úložiště klíčů.

Java SDK (JDK) není nutné odinstalovat, protože už je předem zabalená jako součást Mac OS X/macOS.

### <a name="uninstall-android-avd"></a>Odinstalovat Android AVD

> [!WARNING]
> K dispozici jsou jiné aplikace mimo Visual Studio pro Mac, které také používají Android AVD a tyto další komponenty pro Android, jako je například Android Studio. odebrání tohoto adresáře může způsobit přerušení projektů v Android Studio.

Pokud chcete odebrat všechny AVDsy Androidu a další komponenty pro Android, použijte následující příkaz:

```bash
rm -rf ~/.android
```

Pokud chcete odebrat jenom Android AVDs, použijte následující příkaz:

```bash
rm -rf ~/.android/avd
```

## <a name="uninstall-xamarinios"></a>Odinstalace Xamarin. iOS

Xamarin. iOS umožňuje vývoj aplikací pro iOS pomocí C# nebo F # s Visual Studio pro Mac.

Pomocí následujících příkazů v terminálu odeberte všechny soubory Xamarin. iOS ze systému souborů:

```bash
rm -rf ~/Library/MonoTouch
sudo rm -rf /Library/Frameworks/Xamarin.iOS.framework
sudo rm -rf /Developer/MonoTouch
sudo pkgutil --forget com.xamarin.monotouch.pkg
sudo pkgutil --forget com.xamarin.xamarin-ios-build-host.pkg
sudo pkgutil --forget com.xamarin.xamarin.ios.pkg
```

## <a name="uninstall-xamarinmac"></a>Odinstalace Xamarin. Mac

Xamarin. Mac můžete z počítače odebrat pomocí následujících dvou příkazů k eradikaci produktu a licence z Mac:

```bash
sudo rm -rf /Library/Frameworks/Xamarin.Mac.framework
rm -rf ~/Library/Xamarin.Mac
```

## <a name="uninstall-workbooks-and-inspector"></a>Odinstalace sešitů a kontrol

Počínaje verzí 1.2.2 se dá z terminálu odinstalovat Xamarin Workbooks & inspektor.

```bash
sudo /Library/Frameworks/Xamarin.Interactive.framework/Versions/Current/uninstall
```

Pro starší verze je nutné ručně odebrat následující artefakty:

* Odstranit aplikaci sešitů na`"/Applications/Xamarin Workbooks.app"`
* Odstranit aplikaci Inspector na`"Applications/Xamarin Inspector.app"`
* Odstraňte doplňky: `"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Interactive"` a`"~/Library/Application Support/XamarinStudio-6.0/LocalInstall/Addins/Xamarin.Inspector"`
* Odstraňte inspektor a podpůrné soubory zde: `/Library/Frameworks/Xamarin.Interactive.framework` a`/Library/Frameworks/Xamarin.Inspector.framework`

## <a name="uninstall-the-xamarin-profiler"></a>Odinstalace Xamarin Profiler

```bash
sudo rm -rf "/Applications/Xamarin Profiler.app"
```

## <a name="uninstall-the-visual-studio-installer"></a>Odinstalace Instalační program pro Visual Studio

Pomocí následujících příkazů odeberte všechna trasování instalačního programu Xamarin Universal:

```bash
rm -rf ~/Library/Caches/XamarinInstaller/
rm -rf ~/Library/Caches/VisualStudioInstaller/
rm -rf ~/Library/Logs/XamarinInstaller/
rm -rf ~/Library/Logs/VisualStudioInstaller/
rm -rf ~/Library/Preferences/Xamarin/
rm -rf "~/Library/Preferences/Visual Studio/"
```

## <a name="see-also"></a>Viz také

- [Odinstalace sady Visual Studio (ve Windows)](/visualstudio/install/uninstall-visual-studio)