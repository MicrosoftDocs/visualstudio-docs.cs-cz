---
title: Vytvoření aplikace pro nativní činnost v Androidu | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 2b8fbc8d651536c35ee2dae985876f38336c9061
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588901"
---
# <a name="create-an-android-native-activity-app"></a>Vytvoření aplikace s NativeActivity pro Android

Když instalujete **mobilní vývoj C++**  pro různé platformy s využitím úlohy, Visual Studio se dá použít k vytvoření plně funkčních aplikací pro nativní aktivity Androidu. Android Native Development Kit (NDK) je sada nástrojů, která umožňuje implementovat většinu aplikací pro Android pomocí čistě C/C++ Code. Některý kód Java JNI funguje jako Glue, aby mohl vášC++ kód jazyka C pracovat s Androidem. Android NDK představil možnost vytvářet nativní aplikace aktivity s rozhraním Android API úrovně 9. Nativní kód aktivity je oblíbený pro vytváření her a aplikací s grafickými náročnou, které používají modul Unreal nebo OpenGL. Toto téma vás provede vytvořením jednoduché aplikace nativní aktivity, která používá OpenGL. Další témata najdete v rámci životního cyklu vývojářů při úpravách, sestavování, ladění a nasazování nativního kódu aktivity.

## <a name="requirements"></a>Požadavky

Než budete moct vytvořit aplikaci s nativní aktivitou pro Android, musíte se ujistit, že jste splnili všechny požadavky na systém a nainstalovali **mobilní C++ vývoj s** využitím úlohy v aplikaci Visual Studio. Další informace najdete v tématu [instalace vývoje mobilních aplikací pro různé platformy C++pomocí ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Ujistěte se, že jsou v instalaci zahrnuté nástroje a sady SDK a že je nainstalovaný emulátor Androidu.

## <a name="create-a-new-native-activity-project"></a>Vytvořit nový projekt nativní aktivity

V tomto kurzu nejprve vytvoříte nový projekt nativní aktivity pro Android a potom sestavíte a spustíte výchozí aplikaci v emulátoru Androidu.

::: moniker range="vs-2017"

1. V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** , v části **šablony**zvolte možnost **Visual C++**  > pro **různé platformy**a pak zvolte šablonu **aplikace nativního prostředí (Android)** .

1. Dejte aplikaci název jako *MyAndroidApp*a pak zvolte **OK**.

   ![Vytvoření projektu nativní aktivity](../cross-platform/media/cppmdd_newproject.PNG "CppMDD_NewProject")

   Visual Studio vytvoří nové řešení a otevře Průzkumník řešení.

   ![Nativní projekt aktivity v Průzkumník řešení](../cross-platform/media/cppmdd_rc_na_solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")

::: moniker-end

::: moniker range=">=vs-2019"

1. V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **vytvořit nový projekt** vyberte šablonu **aplikace (Android) pro nativní aktivity** a pak zvolte možnost **Další**.

1. V dialogovém okně **Konfigurovat nový projekt** zadejte název jako *MyAndroidApp* do pole **název projektu**a klikněte na tlačítko **vytvořit**.

   Visual Studio vytvoří nové řešení a otevře Průzkumník řešení.

::: moniker-end

Nové řešení aplikace pro nativní činnost v Androidu zahrnuje dva projekty:

- `MyAndroidApp.NativeActivity` obsahuje odkazy a připevnění kódu vaší aplikace, aby běžela jako nativní aktivita v Androidu. Implementace vstupních bodů ze spojovacího kódu je v *Main. cpp*. Předkompilované hlavičky jsou v souboru *PCH. h*. Tento projekt nativní aplikace aktivity je zkompilován do sdílené knihovny *.* soubor, který je vyzvednut projektem balení.

- `MyAndroidApp.Packaging` vytvoří soubor *. apk* pro nasazení na zařízení nebo emulátoru Androidu. Obsahuje soubor Resources a *souboru AndroidManifest. XML* , ve kterém jste nastavili vlastnosti manifestu. Obsahuje také soubor *Build. XML* , který řídí proces sestavení ANT. Ve výchozím nastavení je nastaven jako spouštěný projekt, aby jej bylo možné nasadit a spustit přímo ze sady Visual Studio.

## <a name="build-and-run-the-default-android-native-activity-app"></a>Sestavování a spouštění výchozí aplikace aktivity nativní pro Android

Sestavte a spusťte aplikaci generovanou šablonou a ověřte instalaci a instalaci. Pro tento úvodní test spusťte aplikaci na jednom z profilů zařízení nainstalovaných emulátorem Androidu. Pokud dáváte přednost testování aplikace na jiném cíli, můžete načíst cílový emulátor nebo připojit zařízení k počítači.

## <a name="to-build-and-run-the-default-native-activity-app"></a>Sestavení a spuštění výchozí nativní aplikace aktivity

1. Pokud ještě není vybraná, vyberte v rozevíracím seznamu **platformy řešení** možnost **x86** .

     ![Výběr platformy řešení – rozevírací seznam x86](../cross-platform/media/cppmdd_rc_na_solution_x86.png "CPPMDD_RC_NA_Solution_x86")

     Pokud se seznam **platformy řešení** nezobrazuje, zvolte možnost **platformy řešení** v seznamu **Přidat nebo odebrat tlačítka** a pak zvolte svou platformu.

1. Na panelu nabídek vyberte **sestavení** **řešení**sestavení  > .

     V okně výstup se zobrazí výstup procesu sestavení pro dva projekty v řešení.

1. Jako cíl nasazení vyberte jeden z profilů emulátoru Android.

     Pokud máte nainstalované další emulátory nebo zařízení s Androidem, můžete je vybrat v rozevíracím seznamu cíl nasazení.

1. Stisknutím klávesy **F5** spusťte ladění, nebo stisknutím **klávesy SHIFT** +**F5** spusťte bez ladění.

   V emulátoru Androidu vypadá výchozí aplikace jako.

   ![Emulátor, ve kterém běží vaše aplikace](../cross-platform/media/cppmdd_emulator_running_app.PNG "CppMDD_Emulator_Running_App")

   Visual Studio spustí emulátor, což trvá několik sekund, než se načte a nasadí váš kód. Po spuštění aplikace můžete nastavit zarážky a použít ladicí program ke krokování kódu, kontrole místních hodnot a sledování hodnot.

1. Stisknutím klávesy **Shift** +**F5** zastavíte ladění.

   Emulátor je samostatný proces, který pokračuje v běhu. Kód můžete upravovat, kompilovat a nasazovat několikrát do stejného emulátoru.
