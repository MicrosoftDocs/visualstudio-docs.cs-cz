---
title: Vytvoření aplikace OpenGL ES na Androidu a iOS | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4978c8196553dba5566ec63fbfcd133d06b6dd6f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733409"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Vytvoření aplikace OpenGL ES na Androidu a iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Když instalujete Visual C++ pro vývoj mobilních řešení napříč platformami možnost, můžete vytvořit řešení sady Visual Studio a projekty aplikací pro iOS a aplikace pro Android, které sdílejí společný kód. Toto téma vás provede šablonu řešení, která vytvoří jednoduchý iOS aplikace i aplikace Android Native Activity. Aplikace mají kódu jazyka C++ společné, které využívá OpenGL ES zobrazíte stejné animovaný otáčení datové krychle na každé platformě. OpenGL ES (OpenGL pro vložené systémy nebo GLES) je 2D a 3D grafice rozhraní API, která je podporována v mnoha mobilních zařízení.  
  
 [Požadavky](#req)   
 [Vytvoření nového projektu aplikace OpenGLES](#Create)   
 [Sestavte a spusťte aplikaci pro Android](#BuildAndroid)   
 [Sestavte a spusťte aplikaci pro iOS](#BuildIOS)   
 [Přizpůsobení aplikací](#Customize)  
  
##  <a name="req"></a> Požadavky  
 Před vytvořením aplikace OpenGL ES pro iOS a Android, musí se ujistěte, že jste splnili všechny požadavky na systém. Visual C++ pro vývoj mobilních řešení napříč platformami možnost je nutné nainstalovat v sadě Visual Studio 2015. Ujistěte se, že požadované nástroje třetích stran a sady SDK jsou zahrnuty v instalaci a nainstalované Visual Studio Emulator for Android. Další informace a podrobné pokyny najdete v tématu [instalaci Visual C++ pro vývoj mobilních řešení napříč platformami](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Pokud chcete sestavovat a testovat aplikace pro iOS, budete potřebovat počítač Mac počítačů, nastavení podle pokynů k instalaci. Další informace o tom, jak nastavit pro vývoj pro iOS najdete v tématu [instalace a konfigurace nástrojů pro vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
##  <a name="Create"></a> Vytvoření nového projektu aplikace OpenGLES  
 V tomto kurzu nejprve vytvořte nový projekt aplikace OpenGL ES a následně vytvořit a spustit výchozí aplikaci v emulátoru Visual Studia pro Android. Dále vytvořte aplikaci pro iOS a spusťte aplikaci v simulátoru iOS.  
  
#### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1. Otevřít Visual Studio. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2. V **nový projekt** dialogovém okně **šablony**, zvolte **Visual C++**, **různé platformy**a klikněte na tlačítko  **Aplikace OpenGLES (Android, iOS)** šablony.  
  
3. Dejte aplikaci s názvem jako `MyOpenGLESApp`a klikněte na tlačítko **OK**.  
  
    ![Nový projekt aplikace OpenGLES](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
    Visual Studio vytvoří nové řešení a otevře se Průzkumník řešení.  
  
    ![V Průzkumníku řešení MyOpenGLESApp](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
   Nové řešení aplikace OpenGL ES obsahuje tři projekty knihovny a dva projekty aplikací. Složka knihovny obsahuje dva projekty specifické pro platformu, které odkazují na sdílený kód a projekt sdíleného kódu:  
  
- **MyOpenGLESApp.Android.NativeActivity** obsahuje odkazy na a spojovací kód, který implementuje vaši aplikaci jako nativní aktivita v Androidu. Implementace vstupních bodů ze spojovacího kódu jsou v main.cpp, která zahrnuje společný kód sdílený v MyOpenGLESApp.Shared. Soubor pch.h jsou předkompilované hlavičky. Tento projekt aplikace Nativeactivity je kompilován do souboru sdílená knihovna (.so), který převezme MyOpenGLESApp.Android.Packaging projektu.  
  
- **MyOpenGLESApp.iOS.StaticLibrary** vytvoří statická knihovna (.a) soubor pro iOS, která obsahuje sdílený kód v MyOpenGLESApp.Shared. Aplikace vytvořené projektem, MyOpenGLESApp.iOS.Application je propojen.  
  
- **MyOpenGLESApp.Shared** obsahuje sdílený kód, který funguje napříč platformami. Makra preprocesoru se používá pro podmíněnou kompilaci kódu specifické pro platformu. Sdílený kód převezme odkaz na projekt v MyOpenGLESApp.Android.NativeActivity a MyOpenGLESApp.iOS.StaticLibrary.  
  
  Řešení obsahuje dva projekty k sestavení aplikací pro platformy Android a iOS:  
  
- **MyOpenGLESApp.Android.Packaging** vytvoří soubor .apk pro nasazení na emulátoru nebo zařízení s Androidem. Tato položka obsahuje prostředky a souboru AndroidManifest.xml, kde nastavíte vlastnosti manifestu. Obsahuje také Build.XML – soubor, který řídí proces sestavení Ant. Ho jako spouštěný projekt ve výchozím nastavení, takže je možné nasadit a spustit přímo ze sady Visual Studio.  
  
- **MyOpenGLESApp.iOS.Application** obsahuje prostředky a Objective-C spojovací kód k vytvoření aplikace pro iOS, která odkazuje na statickou knihovnu kódu C++ v MyOpenGLESApp.iOS.StaticLibrary. Tento projekt vytvoří balíček sestavení, který bude převeden na počítači Mac pomocí sady Visual Studio a vzdáleného agenta. Při sestavování tohoto projektu sady Visual Studio odešle soubory a příkazy k vytvoření a nasazení vaší aplikace na počítači Mac.  
  
##  <a name="BuildAndroid"></a> Sestavte a spusťte aplikaci pro Android  
 Řešení vytvořených šablonou nastaví jako výchozí projekt aplikace pro Android.  Můžete sestavit a spustit tuto aplikaci k ověření instalace a nastavení. Pro počáteční testování spusťte aplikaci na jeden z profilů zařízení nainstaloval Visual Studio Emulator for Android. Pokud chcete testovat svou aplikaci na jiný cíl, můžete načíst cíl emulátor nebo připojte zařízení k počítači.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Sestavení a spuštění aplikace Android Native Activity  
  
1. Pokud ještě není vybraná, zvolte **x86** z **platformy řešení** rozevíracího seznamu.  
  
    ![Nastavte platformu řešení na x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Použijte x86 k cílení na Android emulátor pro Windows. Pokud se zaměřujete na zařízení, zvolte platformu řešení založené na procesoru zařízení. Pokud **platformy řešení** seznamu se nezobrazí, zvolte **platformy řešení** z **přidat nebo odebrat tlačítka** seznamu a pak zvolte vaši platformu.  
  
2. V **Průzkumníka řešení**, otevřete místní nabídku pro projekt MyOpenGLESApp.Android.Packaging a klikněte na tlačítko **sestavení**.  
  
    ![Vytvoření balíčků pro Android projektu](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
    V okně výstupu zobrazí výstup z procesu sestavení pro Android sdílené knihovny a aplikace pro Android.  
  
    ![Výstup sestavení pro projekty pro Android](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3. Vyberte jednu z emulátoru VS telefon s Androidem (x86) profily jako cíl nasazení.  
  
    ![Zvolte cíl nasazení](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
    Pokud jste nainstalovali jiné emulátory nebo připojené zařízení s Androidem, můžete je v rozevíracím seznamu cíl nasazení. Spusťte aplikaci, musí odpovídat sestavené platforma řešení platformě cílového zařízení.  
  
4. Stisknutím klávesy F5 spusťte ladění nebo Shift + F5 spustit bez ladění.  
  
    Visual Studio spustí se emulátor, který trvá několik sekund se má načíst a nasaďte svůj kód. Zde je, jak se aplikace objeví v emulátoru Visual Studia pro Android.  
  
    ![Aplikace spuštěné v emulátoru Androidu](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
    Po zahájení vaší aplikace můžete nastavit zarážky a ladicího programu můžete krokovat kód, prozkoumat místní hodnoty a podívejte se na hodnoty.  
  
5. Stiskněte Shift + F5, můžete zastavit ladění.  
  
    Emulátor je samostatný proces, který zůstane spuštěný. Můžete upravit, zkompilujte a nasaďte svůj kód do stejné emulátor více než jednou. Vaše aplikace se zobrazí v kolekci aplikaci v emulátoru a ji můžete spustit z něj přímo.  
  
   Vygenerovaný Android Nativeactivity aplikace a knihovny projektů vložit jazyka C++ sdíleného kódu ve dynamická knihovna, která obsahuje kód "spojovací" rozhraní s platformy Android. To znamená, že většinu kódu aplikace je v knihovně, a manifest, prostředky a pokyny pro sestavení jsou do balícího projektu. Sdílený kód je volána z main.cpp v projektu NativeActivity. Další informace o tom, jak aplikace Nativeactivity pro Android, najdete v části Android NDK pro vývojáře [koncepty](https://developer.android.com/ndk/guides/concepts.html) stránky.  
  
   Sada Visual Studio sestavuje projekty Nativeactivity pro Android pomocí Android NDK, který používá jako sada nástrojů platformy Clang. Visual Studio mapuje vlastností v projektu NativeActivity přepínače příkazového řádku a možnosti, které se používají ke kompilaci, propojení a ladění na cílovou platformu. Podrobnosti, otevřete **stránky vlastností** dialogové okno pro MyOpenGLESApp.Android.NativeActivity projektu. Další informace o parametrech příkazového řádku, najdete v článku [Clang kompilátoru uživatelské příručce](http://clang.llvm.org/docs/UsersManual.html).  
  
##  <a name="BuildIOS"></a> Sestavte a spusťte aplikaci pro iOS  
 Projekt aplikace pro iOS je vytvořena a upravovat v sadě Visual Studio, ale z důvodu licenčních omezení, musí být vytvořené a nasazené z macu. Komunikuje se službou Vzdálená agenta spuštěného na počítači Mac k přenosu souborů projektu a spuštění sestavení, nasazení a ladění příkazů sady Visual Studio. Musíte nastavit a nakonfigurovat Mac a Visual Studio ke komunikaci před sestavením aplikace pro iOS. Podrobné pokyny najdete v tématu [instalace a konfigurace nástrojů pro vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Jakmile se vzdálený agent běží a sady Visual Studio je spárovaná s počítači Mac, můžete sestavte a spusťte aplikaci pro iOS k ověření instalace a nastavení.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Sestavte a spusťte aplikaci pro iOS  
  
1. Ověřte, že vzdálený agent běží na počítači Mac a sadou Visual Studio je spárováno s vzdáleného agenta. Spuštění vzdáleného agenta, otevřete okno aplikaci terminál a zadejte `vcremote`. Další informace najdete v tématu [konfigurace vzdáleného agenta v sadě Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
    ![Okno terminálu na Macu vcremote](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2. Pokud ještě není vybraná, zvolte **x86** z **platformy řešení** rozevíracího seznamu.  
  
    ![Nastavte platformu řešení na x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Použijte x86 k cílení na simulátoru iOS. Pokud se zaměřujete na zařízení s Iosem, zvolte platformu řešení založené na procesoru zařízení (obvykle s procesorem ARM). Pokud **platformy řešení** seznamu se nezobrazí, zvolte **platformy řešení** z **přidat nebo odebrat tlačítka** seznamu a pak zvolte vaši platformu.  
  
3. V Průzkumníku řešení otevřete místní nabídku pro projekt MyOpenGLESApp.iOS.Application a zvolte **sestavení**.  
  
    ![Vytvoření projektu aplikace iOS](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
    V okně výstupu zobrazí výstup z procesu sestavení pro statické knihovny iOS a aplikace pro iOS. Na počítači Mac, běží vzdálený agent zobrazí v okně terminálu na příkazu a přenos souborů aktivity.  
  
    Na počítači Mac může zobrazit výzva na přijmout žádost o podepsání kódu. Zvolte povolit, pokračujte.  
  
4. Zvolte **simulátoru iOS** na panelu nástrojů a spusťte tak aplikaci v simulátoru iOS na vašem počítači Mac. To může chvíli trvat, spustit simulátor. Bude pravděpodobně nutné simulátoru přenést do popředí na počítači Mac zobrazíte jeho výstup.  
  
    ![Aplikace běžící na simulátoru iOS](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
    Po zahájení vaší aplikace můžete nastavit zarážky a pomocí ladicího programu sady Visual Studio zkoumat místních hodnot, Zobrazit zásobník volání a podívejte se na hodnoty.  
  
    ![Ladicí program na zarážce v aplikaci pro iOS](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5. Stiskněte Shift + F5, můžete zastavit ladění.  
  
    IOS Simulator je samostatný proces, který se bude spouštět na vašem počítači Mac. Můžete upravit, zkompilujte a nasaďte svůj kód více než jednou na stejnou instanci simulátoru iOS. Svůj kód můžete také spustit přímo v simulátoru po jeho nasazení.  
  
   Vygenerovaný iOS aplikace a knihovny projektů vložte kód jazyka C++ ve statické knihovně, která implementuje pouze sdílený kód. Většinu kódu aplikace je v projektu aplikace. Volání do sdílené knihovny kódu v této šabloně projektu se provádí v souboru GameViewController.m. Pokud chcete vytvořit aplikaci pro iOS, použije sada Visual Studio sadu nástrojů platformy Xcode, který vyžaduje komunikaci se vzdáleným klientem, který běží na macu  
  
   Visual Studio přenese soubory projektu a odesílá příkazy ke vzdálenému klientovi k sestavení aplikace pomocí Xcode. Vzdálený klient zasílá sestavení informace o stavu zpět do sady Visual Studio. Když aplikace vytvořila úspěšně, můžete odesílat příkazy ke spuštění a ladění aplikace Visual Studio. V ladicím programu sady Visual Studio určuje spuštěné ve spuštění simulátoru iOS na počítači Mac nebo na zařízení s iOS připojené aplikace. Visual Studio mapuje vlastností v projektu StaticLibrary přepínače příkazového řádku a možnosti, které se používají k vytváření, propojení a ladění na cílovou platformu iOS. Podrobnosti o kompilátoru příkazového řádku, otevřete **stránky vlastností** dialogové okno pro MyOpenGLESApp.iOS.StaticLibrary projektu.  
  
##  <a name="Customize"></a> Přizpůsobení aplikací  
 Můžete upravit sdíleným kódem C++ pro přidání nebo změnu běžné funkce. Je nutné změnit volání sdílený kód v projektech MyOpenGLESApp.Android.NativeActivity a MyOpenGLESApp.iOS.Application tak, aby odpovídaly. Makra preprocesoru můžete určit oddíly pro konkrétní platformu v společný kód. Makro preprocesoru `__ANDROID__` je předdefinovaná při sestavení pro Android. Makro preprocesoru `__APPLE__` je předdefinovaná při sestavení pro iOS.  
  
 Zobrazit informace IntelliSense pro konkrétní projekt platformu, vyberte projekt v rozevírací nabídce přepínání kontextu na navigačním panelu v horní části okna editoru.  
  
 ![Projekt přepínání kontextu rozevírací seznam v editoru](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 Technologie IntelliSense problémy v aktuálním projektu jsou označené červenou vlnovkou. Problémy v jiných projektech jsou označené fialovou vlnovkou. Ve výchozím nastavení Visual Studio nepodporuje kód zabarvení ani IntelliSense pro soubory v jazyce Java nebo Objective-C. Můžete však stále upravovat zdrojové soubory a změnit prostředky, které chcete nastavit název vaší aplikace, ikona a další podrobnosti implementace.

