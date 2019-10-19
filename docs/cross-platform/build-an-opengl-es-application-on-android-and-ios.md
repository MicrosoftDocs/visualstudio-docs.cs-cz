---
title: Sestavení aplikace OpenGL ES v Androidu a iOS | Microsoft Docs
ms.custom: ''
ms.date: 10/09/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: a15902278e9a73488b315729a2db6e8fb5d53935
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588925"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Sestavení aplikace OpenGL ES v Androidu a iOS

Můžete vytvářet řešení a projekty sady Visual Studio pro aplikace pro iOS a aplikace pro Android, které sdílejí společný kód. Tento článek vás provede šablonou řešení, která vytvoří jednoduchou aplikaci pro iOS a nativní aplikaci aktivity pro Android. Aplikace mají C++ běžný kód, který používá OpenGL ES k zobrazení stejné animované rotující krychle na každé platformě. OpenGL ES (OpenGL pro vložené systémy nebo GLES) je 2D a 3D grafické rozhraní API, které se podporuje na mnoha mobilních zařízeních.

## <a name="requirements"></a>Požadavky

Než budete moct vytvořit aplikaci OpenGL ES pro iOS a Android, ujistěte se, že jste splnili všechny požadavky na systém. Pokud jste to ještě neudělali, nainstalujte si C++ vývoj pro mobilní zařízení pomocí úlohy v instalační program pro Visual Studio. Chcete-li získat šablony OpenGL ES a sestavit pro iOS, zahrňte volitelné C++ vývojové nástroje pro iOS. Pokud chcete sestavit Android, nainstalujte nástroje C++ pro vývoj pro Android a požadované nástroje třetích stran: Android NDK, Apache Ant a Google Android Emulator. Pro lepší výkon emulátoru na platformách Intel doporučujeme také nainstalovat Intel Hardware Accelerated Execution Manager (modul HAXM). Dále nakonfigurujte Intel modul HAXM a Android Emulator pro spuštění ve vašem systému. Další informace a podrobné pokyny najdete v tématu [instalace vývoje mobilních aplikací pro různé platformy C++pomocí ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md).

K sestavení a otestování aplikace pro iOS budete potřebovat počítač Mac, který je nastavený podle pokynů k instalaci. Další informace o tom, jak nastavit pro vývoj pro iOS, najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="create-a-new-opengles-application-project"></a>Vytvoření nového projektu aplikace OpenGL

V tomto kurzu nejprve vytvoříte nový projekt aplikace OpenGL ES. a potom v emulátoru Androidu Sestavte a spusťte výchozí aplikaci. V dalším kroku sestavíte aplikaci pro iOS a spustíte ji na zařízení s iOS.

::: moniker range="vs-2017"

1. V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** v části **šablony**zvolte možnost **Visual C++**  > pro **různé platformy**a pak zvolte šablonu **aplikace OpenGL (Android, iOS)** .

1. Dejte aplikaci název jako *MyOpenGLESApp*a pak zvolte **OK**.

   ![Nový projekt aplikace OpenGL](../cross-platform/media/cppmdd_opengles_newproj.PNG "CPPMDD_OpenGLES_NewProj")

   Visual Studio vytvoří nové řešení a otevře Průzkumník řešení.

   ![MyOpenGLESApp v Průzkumník řešení](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

::: moniker-end

::: moniker range=">=vs-2019"

1. V aplikaci Visual Studio vyberte **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **vytvořit nový projekt** vyberte šablonu **aplikace OpenGL (Android, iOS)** a pak klikněte na tlačítko **Další**.

1. V dialogovém okně **Konfigurovat nový projekt** zadejte název jako *MyOpenGLESApp* do pole **název projektu**a klikněte na tlačítko **vytvořit**.

   Visual Studio vytvoří nové řešení a otevře Průzkumník řešení.

   ![MyOpenGLESApp v Průzkumník řešení](../cross-platform/media/cppmdd_opengles_solexpl.PNG "CPPMDD_OpenGLES_SolExpl")

::: moniker-end

Nové řešení aplikace OpenGL ES zahrnuje tři projekty knihovny a dva aplikační projekty. Složka knihovny obsahuje projekt sdíleného kódu a dva projekty specifické pro platformu, které odkazují na sdílený kód:

- `MyOpenGLESApp.Android.NativeActivity` obsahuje odkazy a připevnění kódu, který implementuje vaši aplikaci jako nativní aktivitu v Androidu. Vstupní body z kódu připevňování jsou implementovány v *Main. cpp*, který obsahuje společný sdílený kód v `MyOpenGLESApp.Shared`. Předkompilované hlavičky jsou v souboru *PCH. h*. Tento projekt nativní aplikace aktivity je zkompilován do sdíleného souboru knihovny ( *. so*), který je převzatý `MyOpenGLESApp.Android.Packaging` projektem.

- `MyOpenGLESApp.iOS.StaticLibrary` vytvoří soubor statické knihovny ( *. a*) iOS, který obsahuje sdílený kód v `MyOpenGLESApp.Shared`. Je propojena s aplikací vytvořenou `MyOpenGLESApp.iOS.Application` projektem.

- `MyOpenGLESApp.Shared` obsahuje sdílený kód, který funguje na různých platformách. Používá makra preprocesoru pro podmíněnou kompilaci kódu specifického pro platformu. Sdílený kód je vyzvednut odkazem na projekt v `MyOpenGLESApp.Android.NativeActivity` i `MyOpenGLESApp.iOS.StaticLibrary`.

Řešení obsahuje dva projekty pro sestavování aplikací pro platformy Android a iOS:

- `MyOpenGLESApp.Android.Packaging` vytvoří soubor *. apk* pro nasazení na zařízení nebo emulátoru Androidu. Tento soubor obsahuje soubor Resources a souboru AndroidManifest. XML, ve kterém jste nastavili vlastnosti manifestu. Obsahuje také soubor *Build. XML* , který řídí proces sestavení ANT. Ve výchozím nastavení je nastaven jako spouštěný projekt, aby jej bylo možné nasadit a spustit přímo ze sady Visual Studio.

- `MyOpenGLESApp.iOS.Application` obsahuje kód prostředky a cíl-C připevnit k vytvoření aplikace pro iOS, která odkazuje na C++ kód statické knihovny v `MyOpenGLESApp.iOS.StaticLibrary`. Tento projekt vytvoří balíček sestavení, který se přenese do vašeho počítače Mac pomocí sady Visual Studio a vzdáleného agenta. Při sestavování tohoto projektu Visual Studio pošle soubory a příkazy k sestavení a nasazení vaší aplikace na Macu.

## <a name="build-and-run-the-android-app"></a>Sestavení a spuštění aplikace pro Android

Řešení vytvořené šablonou nastaví aplikaci pro Android jako výchozí projekt.  Tuto aplikaci můžete sestavit a spustit, abyste ověřili instalaci a instalaci. Pro počáteční test spusťte aplikaci na jednom z profilů zařízení nainstalovaných emulátorem pro Android. Pokud dáváte přednost testování aplikace na jiném cíli, můžete načíst cílový emulátor nebo připojit zařízení k počítači.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Sestavení a spuštění aplikace nativní aktivity v Androidu

1. Pokud ještě není vybraná, vyberte v rozevíracím seznamu **platformy řešení** možnost **x86** .

   ![Nastavení platformy řešení na x86](../cross-platform/media/cppmdd_opengles_solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")

   K zacílení emulátoru použijte platformu x86. Chcete-li cílit na zařízení, vyberte platformu řešení na základě procesoru zařízení. Pokud se seznam **platformy řešení** nezobrazuje, zvolte možnost **platformy řešení** v seznamu **Přidat nebo odebrat tlačítka** a zvolte svou platformu.

1. V **Průzkumník řešení**otevřete místní nabídku pro `MyOpenGLESApp.Android.Packaging` projekt a pak zvolte možnost **sestavit**.

   ![Sestavit projekt pro balení pro Android](../cross-platform/media/cppmdd_opengles_andbuild.png "CPPMDD_OpenGLES_AndBuild")

   V okně výstup se zobrazí výstup procesu sestavení pro sdílenou knihovnu Androidu a aplikaci pro Android.

   ![Výstup sestavení pro projekty pro Android](../cross-platform/media/cppmdd_opengles_andoutput.png "CPPMDD_OpenGLES_AndOutput")

1. Jako cíl nasazení vyberte jeden ze emulovaných profilů zařízení s Androidem.

   ![Zvolit cíl nasazení](../cross-platform/media/cppmdd_opengles_pickemulator.png "CPPMDD_OpenGLES_PickEmulator")

   Pokud máte nainstalované další emulátory nebo zařízení s Androidem, můžete je vybrat v rozevíracím seznamu cíl nasazení. Aby bylo možné aplikaci spustit, musí být sestavená platforma řešení shodná s platformou cílového zařízení.

1. Stisknutím klávesy **F5** spusťte ladění, nebo stisknutím **klávesy SHIFT** +**F5** spusťte bez ladění.

   Visual Studio spustí emulátor, což trvá několik sekund, než se načte a nasadí váš kód. Tady je postup, jak se aplikace zobrazí v emulátoru:

   ![Aplikace spuštěná v Android Emulator](../cross-platform/media/cppmdd_opengles_andemulator.png "CPPMDD_OpenGLES_AndEmulator")

   Po spuštění aplikace můžete nastavit zarážky a použít ladicí program ke krokování kódu, kontrole místních hodnot a sledování hodnot.

1. Stisknutím klávesy **Shift** +**F5** zastavíte ladění.

   Emulátor je samostatný proces, který pokračuje v běhu. Kód můžete upravovat, kompilovat a nasazovat několikrát do stejného emulátoru. Vaše aplikace se zobrazí v kolekci aplikací na emulátoru a je možné ji spustit přímo.

   Vygenerovaná projekty aplikace a knihovny pro nativní prostředí Android vloží C++ sdílený kód do dynamické knihovny, která obsahuje kód "připevnit" rozhraní s platformou Androidu. Většina kódu aplikace je v knihovně, a pokyny k manifestu, prostředkům a sestavení jsou v projektu balení. Sdílený kód je volán z Main. cpp v projektu NativeActivity. Další informace o tom, jak programovat nativní aktivitu Androidu, najdete na stránce věnované [konceptům](https://developer.android.com/ndk/guides/concepts.html) pro vývojáře pro Android NDK.

   Sada Visual Studio sestavuje projekty nativních aktivit Androidu pomocí NDK pro Android, který jako sadu nástrojů platformy používá Clang. Visual Studio mapuje vlastnosti v projektu NativeActivity na možnosti, které se používají ke kompilaci, propojení a ladění na cílové platformě. Pro podrobnosti otevřete dialogové okno **stránky vlastností** pro projekt MyOpenGLESApp. Android. NativeActivity. Další informace o přepínačích příkazového řádku naleznete v [příručce uživatele kompilátoru Clang](http://clang.llvm.org/docs/UsersManual.html).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Sestavení a spuštění aplikace pro iOS na zařízení s iOS

Projekt aplikace pro iOS se vytvoří a upraví v aplikaci Visual Studio, ale z důvodu licenčních omezení musí být sestavený a nasazený z Mac. Visual Studio komunikuje se vzdáleným agentem spuštěným na Macu pro přenos souborů projektu a provádění příkazů sestavení, nasazení a ladění. Nastavte a nakonfigurujte si Mac a Visual Studio, aby komunikovaly před tím, než budete moct sestavit aplikaci pro iOS. Podrobné pokyny najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Po spuštění vzdáleného agenta na Macu a spárování se sadou Visual Studio můžete sestavit a spustit aplikaci pro iOS, abyste ověřili instalaci a instalaci.

Pokud chcete nasadit aplikaci pro iOS do zařízení se systémem iOS, musíte taky nastavit automatické přihlašování na Xcode na Macu. Automatické podepisování automaticky spravuje podepisování aplikací a vytváří zřizovací profil pro podepsání sestavení aplikace.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Nastavení automatického podepisování v Xcode

1. Pokud jste to ještě neudělali, nainstalujte [Xcode](https://developer.apple.com/xcode/) na Mac.

1. Otevřete aplikaci Xcode na Macu.

1. Vytvoří nový projekt Xcode **aplikace s jedním zobrazením** . Vyplňte požadovaná pole během vytváření projektu. Hodnoty mohou být libovolné, protože projekt se používá pouze k vytvoření zřizovacího profilu, který je použit později k podepsání sestavení aplikace.

1. Přidejte své Apple ID, které je zaregistrované v účtu [Apple Developer program](https://developer.apple.com/programs/) , do Xcode. Vaše Apple ID se používá jako podpisová identita k podepisování aplikací. Chcete-li přidat podpisovou identitu v Xcode, otevřete nabídku **Xcode** a vyberte možnost **Předvolby**. Vyberte **účty** a kliknutím na tlačítko Přidat (+) přidejte svoje Apple ID. Podrobné pokyny najdete v tématu [Přidání vašeho účtu Apple ID](https://help.apple.com/xcode/mac/current/#/devaf282080a).

1. V nastavení "Obecné" projektu Xcode změňte hodnotu **identifikátoru sady prostředků** na `com.<NameOfVSProject>`, kde `<NameOfVSProject>` je stejný název jako projekt řešení sady Visual Studio, který jste vytvořili. Pokud jste například vytvořili projekt s názvem `MyOpenGLESApp` v sadě Visual Studio, nastavte **identifikátor sady prostředků** na `com.MyOpenGLESApp`.

   ![Identifikátor Xcode sady prostředků](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "CPPMDD_OpenGLES_iOSXcodeId")

1. Pokud chcete povolit automatické podepisování, zaškrtněte. Automaticky spravovat podepisování * *.

   ![Automatické podepisování Xcode](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "CPPMDD_OpenGLES_iOSXcodeSign")

1. Vyberte název týmu Apple ID, které jste přidali jako vývojový **tým**.

   ![Xcode tým](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "CPPMDD_OpenGLES_iOSXcodeTeam")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>Sestavení a spuštění aplikace pro iOS na zařízení s iOS

1. Spusťte na Macu vzdálený agent a ověřte, že je Visual Studio spárováno se vzdáleným agentem. Vzdálený agent spustíte tak, že otevřete okno terminálu aplikace a zadáte `vcremote`. Další informace najdete v tématu [Konfigurace vzdáleného agenta v aplikaci Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Okno terminálu Mac se systémem vcremote](../cross-platform/media/cppmdd_common_vcremote.png "CPPMDD_common_vcremote")

1. Připojte zařízení s iOS k počítači Mac. Když zařízení připojíte poprvé k počítači, zobrazí se výstraha, jestli počítač pro přístup k vašemu zařízení důvěřujete. Povolte zařízení, aby důvěřovalo počítači Mac.

1. V aplikaci Visual Studio, pokud ještě není vybraná, vyberte platformu řešení z rozevíracího seznamu **platformy řešení** v závislosti na procesoru zařízení. V tomto příkladu je to **ARM64** procesor.

   ![Nastavení platformy řešení na ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "CPPMDD_OpenGLES_SolutionPlatARM64")

1. V Průzkumník řešení otevřete místní nabídku pro projekt MyOpenGLESApp. iOS. Application a kliknutím na **Uvolnit projekt** uvolněte projekt.

1. Znovu otevřete místní nabídku pro projekt MyOpenGLESApp. iOS. Application a vyberte **upravit projekt. pbxproj** a upravte soubor projektu. V souboru `project.pbxproj` vyhledejte atribut `buildSettings` a přidejte `DEVELOPMENT_TEAM` pomocí ID Apple Team. Níže uvedený snímek obrazovky ukazuje příklad hodnoty `123456ABC` pro ID týmu Apple. Hodnotu ID Apple Team můžete najít z Xcode. Přejděte na **nastavení sestavení** a najeďte myší na název vývojového týmu, abyste zobrazili popis. Popisek zobrazuje vaše ID týmu.

   ![Nastavit vývojový tým](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "CPPMDD_OpenGLES_iOSDevelopmentTeam")

1. Zavřete soubor `project.pbxproj` a pak otevřete místní nabídku pro nenačtený projekt MyOpenGLESApp. iOS. Application a zvolte možnost **znovu načíst projekt** a znovu načíst projekt.

1. Nyní Sestavte projekt MyOpenGLESApp. iOS. Application tak, že otevřete místní nabídku pro projekt a zvolíte možnost **sestavit**.

   ![Sestavit projekt aplikace pro iOS](../cross-platform/media/cppmdd_opengles_iosbuild.png "CPPMDD_OpenGLES_iOSBuild")

   V okně výstup se zobrazí výstup procesu sestavení pro statickou knihovnu iOS a aplikaci pro iOS. Na Macu se v okně terminálu, na kterém běží vzdálený agent, zobrazuje příkaz a aktivitu přenosu souborů.

   Na počítači Mac se může zobrazit výzva, abyste povolili kodesign pro přístup k řetězci klíčů. Pokračujte **výběrem možnosti** pokračovat.

1. Vyberte zařízení s iOS na panelu nástrojů a spusťte aplikaci na svém zařízení připojeném k počítači Mac. Pokud se aplikace nespustí, ověřte, že zařízení uděluje oprávnění k tomu, aby se vaše nasazená aplikace spustila na zařízení. Toto oprávnění můžete nastavit tak, že v zařízení nasadíte na **nastavení**  > **Obecné**  > **správu zařízení** . Vyberte svůj účet aplikace pro vývojáře, důvěřovat účtu a ověřte aplikaci. Zkuste znovu spustit aplikaci ze sady Visual Studio.

   ![aplikace pro iOS na zařízení s iOS](../cross-platform/media/cppmdd-opengles-iosdevice.png "CPPMDD_OpenGLES_iOSDevice")

   Po spuštění vaší aplikace můžete nastavit zarážky a použít ladicí program sady Visual Studio k prohlédnutí místních hodnot, viz zásobník volání a sledovat hodnoty.

   ![Ladicí program na zarážce v aplikaci iOS](../cross-platform/media/cppmdd_opengles_iosdebug.png "CPPMDD_OpenGLES_iOSDebug")

1. Stisknutím klávesy **Shift** +**F5** zastavíte ladění.

   Vygenerovaná projekty aplikace a knihovny pro iOS vloží C++ kód do statické knihovny, která implementuje pouze sdílený kód. Většina kódu aplikace je v projektu `Application`. Volání do kódu sdílené knihovny v tomto projektu šablony jsou vytvořena v souboru *GameViewController. m* . Sada Visual Studio při sestavování aplikace pro iOS používá sadu nástrojů Xcode Platform, která vyžaduje komunikaci se vzdáleným klientem, který běží na Macu.

   Visual Studio přenáší soubory projektu a pošle příkazy do vzdáleného klienta k sestavení aplikace pomocí Xcode. Vzdálený klient odesílá informace o stavu sestavení zpět do sady Visual Studio. Po úspěšném vytvoření aplikace můžete pomocí sady Visual Studio odeslat příkazy ke spuštění a ladění aplikace. Ladicí program v aplikaci Visual Studio řídí aplikaci spuštěnou na zařízení s iOS připojenou k vašemu počítači Mac. Visual Studio mapuje vlastnosti v projektu StaticLibrary na možnosti, které se používají ke kompilaci, propojení a ladění na cílové platformě iOS. Pro podrobnosti o možnosti příkazového řádku kompilátoru otevřete dialogové okno **stránky vlastností** pro projekt MyOpenGLESApp. iOS. StaticLibrary.

## <a name="customize-your-apps"></a>Přizpůsobení aplikací

Můžete upravit sdílený C++ kód a přidat nebo změnit běžné funkce. Je nutné změnit volání na sdílený kód v `MyOpenGLESApp.Android.NativeActivity` a `MyOpenGLESApp.iOS.Application` projektů, aby odpovídaly. Makra preprocesoru můžete použít k určení sekcí specifických pro platformu v rámci společného kódu. @No__t_0 makra preprocesoru je předdefinovaná při sestavování pro Android. @No__t_0 makra preprocesoru je předdefinovaná při sestavování pro iOS.

Chcete-li zobrazit technologii IntelliSense pro konkrétní platformu projektu, vyberte projekt v rozevíracím seznamu přepínačů kontextu v navigačním panelu v horní části okna editoru.

![Rozevírací seznam přepínačů kontextu projektu v editoru](../cross-platform/media/cppmdd_opengles_contextswitcher.png)

Problémy IntelliSense v kódu, které jsou používány aktuálním projektem, jsou označeny červenou vlnovkou. Problémy v jiných projektech jsou označeny fialovou vlnovkou. Visual Studio nepodporuje barevné zabarvení kódu nebo IntelliSense pro soubory v jazyce Java nebo objektivní-C. Nicméně stále můžete upravovat zdrojové soubory a měnit prostředky, abyste mohli nastavit název, ikonu a další podrobnosti implementace aplikace.
