---
title: Sestavení aplikace OpenGL ES v Androidu a iOS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b9f5db4ccd70136b711f5bd221244418cf843485
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151130"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Vytvoření aplikace OpenGL ES na Androidu a iOS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když nainstalujete možnost Visual C++ for Cross-Platform Mobile Development, můžete vytvářet řešení a projekty sady Visual Studio pro aplikace pro iOS a aplikace pro Android, které sdílejí společný kód. Toto téma vás provede šablonou řešení, která vytvoří jednoduchou aplikaci pro iOS a nativní aplikaci aktivity pro Android. Aplikace mají společný kód C++, který používá OpenGL ES k zobrazení stejné animované rotující krychle na každé platformě. OpenGL ES (OpenGL pro vložené systémy nebo GLES) je 2D a 3D grafické rozhraní API, které se podporuje na mnoha mobilních zařízeních.  
  
 [Požadavků](#req)   
 [Vytvoření nového projektu aplikace OpenGL](#Create)   
 [Sestavení a spuštění aplikace pro Android](#BuildAndroid)   
 [Sestavení a spuštění aplikace pro iOS](#BuildIOS)   
 [Přizpůsobení aplikací](#Customize)  
  
## <a name="requirements"></a><a name="req"></a> Požadavků  
 Než budete moct vytvořit aplikaci OpenGL ES pro iOS a Android, musíte se ujistit, že jste splnili všechny požadavky na systém. V aplikaci Visual Studio 2015 je nutné nainstalovat možnost Visual C++ for Cross-Platform Mobile Development. Ujistěte se, že jsou v instalaci zahrnuté nástroje a sady SDK a že je nainstalovaný emulátor sady Visual Studio pro Android. Další informace a podrobné pokyny najdete v tématu [instalace Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). K sestavení a otestování aplikace pro iOS budete potřebovat počítač Mac, který je nastavený podle pokynů k instalaci. Další informace o tom, jak nastavit pro vývoj pro iOS, najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md) .  
  
## <a name="create-a-new-opengles-application-project"></a><a name="Create"></a> Vytvoření nového projektu aplikace OpenGL  
 V tomto kurzu nejprve vytvoříte nový projekt aplikace OpenGL ES a potom sestavíte a spustíte výchozí aplikaci v emulátoru sady Visual Studio pro Android. V dalším kroku sestavíte aplikaci pro iOS a spustíte aplikaci v simulátoru iOS.  
  
#### <a name="to-create-a-new-project"></a>Vytvoření nového projektu  
  
1. Otevřete sadu Visual Studio. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.  
  
2. V dialogovém okně **Nový projekt** v části **šablony**zvolte možnost **Visual C++**, pro **různé platformy**a pak zvolte šablonu **aplikace OpenGL (Android, iOS)** .  
  
3. Přiřaďte aplikaci název jako `MyOpenGLESApp` a pak zvolte **OK**.  
  
    ![Nový projekt aplikace OpenGL](../cross-platform/media/cppmdd-opengles-newproj.PNG "CPPMDD_OpenGLES_NewProj")  
  
    Visual Studio vytvoří nové řešení a otevře Průzkumník řešení.  
  
    ![MyOpenGLESApp v Průzkumník řešení](../cross-platform/media/cppmdd-opengles-solexpl.PNG "CPPMDD_OpenGLES_SolExpl")  
  
   Nové řešení aplikace OpenGL ES zahrnuje tři projekty knihovny a dva aplikační projekty. Složka knihovny obsahuje projekt sdíleného kódu a dva projekty specifické pro platformu, které odkazují na sdílený kód:  
  
- **MyOpenGLESApp. Android. NativeActivity** obsahuje odkazy a připevnění kódu, který implementuje vaši aplikaci jako nativní aktivitu v Androidu. Implementace vstupních bodů z kódu připevňování je v Main. cpp, který obsahuje společný sdílený kód v MyOpenGLESApp. Shared. Předkompilované hlavičky jsou v souboru PCH. h. Tento projekt nativní aplikace aktivity se zkompiluje do sdíleného souboru knihovny (. so), který si vybral projekt MyOpenGLESApp. Android. balení.  
  
- **MyOpenGLESApp. iOS. StaticLibrary** vytvoří soubor statické knihovny pro iOS (. a), který obsahuje sdílený kód v MyOpenGLESApp. Shared. Je propojena s aplikací vytvořenou projektem MyOpenGLESApp. iOS. Application.  
  
- **MyOpenGLESApp. Shared** obsahuje sdílený kód, který funguje na různých platformách. Používá makra preprocesoru pro podmíněnou kompilaci kódu specifického pro platformu. Sdílený kód je vyzvednut odkazem na projekt v MyOpenGLESApp. Android. NativeActivity a MyOpenGLESApp. iOS. StaticLibrary.  
  
  Řešení obsahuje dva projekty pro sestavování aplikací pro platformy Android a iOS:  
  
- **MyOpenGLESApp. Android. balení** vytvoří soubor. APK pro nasazení na zařízení nebo emulátoru Androidu. Obsahuje prostředky a AndroidManifest.xml soubor, ve kterém jste nastavili vlastnosti manifestu. Obsahuje také soubor build.xml, který řídí proces sestavení ANT. Ve výchozím nastavení je nastaven jako spouštěný projekt, aby jej bylo možné nasadit a spustit přímo ze sady Visual Studio.  
  
- **MyOpenGLESApp. iOS. Application** obsahuje kód prostředky a cíl-C připevnit k vytvoření aplikace pro iOS, která odkazuje na kód statické knihovny C++ v MyOpenGLESApp. iOS. StaticLibrary. Tento projekt vytvoří balíček sestavení, který se přenese do vašeho počítače Mac pomocí sady Visual Studio a vzdáleného agenta. Při sestavování tohoto projektu Visual Studio pošle soubory a příkazy k sestavení a nasazení vaší aplikace na Macu.  
  
## <a name="build-and-run-the-android-app"></a><a name="BuildAndroid"></a> Sestavení a spuštění aplikace pro Android  
 Řešení vytvořené šablonou nastaví aplikaci pro Android jako výchozí projekt.  Tuto aplikaci můžete sestavit a spustit, abyste ověřili instalaci a instalaci. Pro počáteční test spusťte aplikaci na jednom z profilů zařízení nainstalovanou emulátorem sady Visual Studio pro Android. Pokud dáváte přednost testování aplikace na jiném cíli, můžete načíst cílový emulátor nebo připojit zařízení k počítači.  
  
#### <a name="to-build-and-run-the-android-native-activity-app"></a>Sestavení a spuštění aplikace nativní aktivity v Androidu  
  
1. Pokud ještě není vybraná, vyberte v rozevíracím seznamu **platformy řešení** možnost **x86** .  
  
    ![Nastavení platformy řešení na x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    Pro cílení na Android Emulator pro Windows použijte x86. Pokud cílíte na zařízení, vyberte platformu řešení na základě procesoru zařízení. Pokud se seznam **platformy řešení** nezobrazuje, zvolte možnost **platformy řešení** v seznamu **Přidat nebo odebrat tlačítka** a zvolte svou platformu.  
  
2. V **Průzkumník řešení**otevřete místní nabídku pro projekt MyOpenGLESApp. Android. balení a pak zvolte možnost **sestavit**.  
  
    ![Sestavit projekt pro balení pro Android](../cross-platform/media/cppmdd-opengles-andbuild.png "CPPMDD_OpenGLES_AndBuild")  
  
    V okně výstup se zobrazí výstup procesu sestavení pro sdílenou knihovnu Androidu a aplikaci pro Android.  
  
    ![Výstup sestavení pro projekty pro Android](../cross-platform/media/cppmdd-opengles-andoutput.png "CPPMDD_OpenGLES_AndOutput")  
  
3. Jako cíl nasazení vyberte jeden z profilů Androidu pro emulátor (x86).  
  
    ![Zvolit cíl nasazení](../cross-platform/media/cppmdd-opengles-pickemulator.png "CPPMDD_OpenGLES_PickEmulator")  
  
    Pokud máte nainstalované další emulátory nebo zařízení s Androidem, můžete je vybrat v rozevíracím seznamu cíl nasazení. Aby bylo možné aplikaci spustit, musí být sestavená platforma řešení shodná s platformou cílového zařízení.  
  
4. Stisknutím klávesy F5 spusťte ladění, nebo stisknutím klávesy Shift + F5 spusťte bez ladění.  
  
    Visual Studio spustí emulátor, což trvá několik sekund, než se načte a nasadí váš kód. Tady je postup, jak se aplikace zobrazí v emulátoru sady Visual Studio pro Android.  
  
    ![Aplikace spuštěná v Android Emulator](../cross-platform/media/cppmdd-opengles-andemulator.png "CPPMDD_OpenGLES_AndEmulator")  
  
    Po spuštění aplikace můžete nastavit zarážky a použít ladicí program ke krokování kódu, kontrole místních hodnot a sledování hodnot.  
  
5. Pro zastavení ladění stiskněte Shift + F5.  
  
    Emulátor je samostatný proces, který pokračuje v běhu. Kód můžete upravovat, kompilovat a nasazovat několikrát do stejného emulátoru. Vaše aplikace se zobrazí v kolekci aplikací na emulátoru a je možné ji spustit přímo.  
  
   Vygenerovaná projekty aplikace a knihovny pro nativní prostředí Android vloží sdílený kód C++ do dynamické knihovny, která obsahuje kód "připevnit" pro rozhraní s platformou Androidu. To znamená, že většina kódu aplikace je v knihovně, a pokyny k manifestu, prostředkům a sestavení jsou v projektu balení. Sdílený kód je volán z Main. cpp v projektu NativeActivity. Další informace o tom, jak programovat nativní aktivitu Androidu, najdete na stránce věnované [konceptům](https://developer.android.com/ndk/guides/concepts.html) pro vývojáře pro Android NDK.  
  
   Sada Visual Studio sestavuje projekty nativních aktivit Androidu pomocí NDK pro Android, který jako sadu nástrojů platformy používá Clang. Visual Studio mapuje vlastnosti v projektu NativeActivity na přepínače příkazového řádku a možnosti, které se používají ke kompilaci, propojení a ladění na cílové platformě. Pro podrobnosti otevřete dialogové okno **stránky vlastností** pro projekt MyOpenGLESApp. Android. NativeActivity. Další informace o přepínačích příkazového řádku naleznete v [příručce uživatele kompilátoru Clang](http://clang.llvm.org/docs/UsersManual.html).  
  
## <a name="build-and-run-the-ios-app"></a><a name="BuildIOS"></a> Sestavení a spuštění aplikace pro iOS  
 Projekt aplikace pro iOS se vytvoří a upraví v aplikaci Visual Studio, ale z důvodu licenčních omezení musí být sestavený a nasazený z Mac. Visual Studio komunikuje se vzdáleným agentem spuštěným na Macu pro přenos souborů projektu a provádění příkazů sestavení, nasazení a ladění. Před vytvořením aplikace pro iOS musíte nastavit a nakonfigurovat počítač Mac a sadu Visual Studio, abyste mohli komunikovat. Podrobné pokyny najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Jakmile je vzdálený agent spuštěný a Visual Studio se spáruje s vaším počítačem Mac, můžete sestavit a spustit aplikaci pro iOS a ověřit instalaci a instalaci.  
  
#### <a name="to-build-and-run-the-ios-app"></a>Sestavení a spuštění aplikace pro iOS  
  
1. Ověřte, zda je na počítači Mac spuštěn vzdálený agent a zda je aplikace Visual Studio spárována se vzdáleným agentem. Vzdálený agent spustíte tak, že otevřete okno aplikace Terminal a zadáte `vcremote` . Další informace najdete v tématu [Konfigurace vzdáleného agenta v aplikaci Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).  
  
    ![Okno terminálu Mac se systémem vcremote](../cross-platform/media/cppmdd-common-vcremote.png "CPPMDD_common_vcremote")  
  
2. Pokud ještě není vybraná, vyberte v rozevíracím seznamu **platformy řešení** možnost **x86** .  
  
    ![Nastavení platformy řešení na x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "CPPMDD_OpenGLES_SolutionPlat")  
  
    K zaměření simulátoru iOS použijte x86. Pokud cílíte na zařízení s iOS, vyberte platformu řešení na základě procesoru zařízení (obvykle procesor ARM). Pokud se seznam **platformy řešení** nezobrazuje, zvolte možnost **platformy řešení** v seznamu **Přidat nebo odebrat tlačítka** a zvolte svou platformu.  
  
3. V Průzkumník řešení otevřete místní nabídku pro projekt MyOpenGLESApp. iOS. Application a vyberte možnost **sestavit**.  
  
    ![Sestavit projekt aplikace pro iOS](../cross-platform/media/cppmdd-opengles-iosbuild.png "CPPMDD_OpenGLES_iOSBuild")  
  
    V okně výstup se zobrazí výstup procesu sestavení pro statickou knihovnu iOS a aplikaci pro iOS. Na Macu se v okně terminálu, na kterém běží vzdálený agent, zobrazuje příkaz a aktivitu přenosu souborů.  
  
    Na počítači Mac se může zobrazit výzva k přijetí žádosti o podepsání kódu. Pokračujte výběrem možnosti pokračovat.  
  
4. Kliknutím na **simulátor iOS** na panelu nástrojů spustíte aplikaci v simulátoru iOS na vašem počítači Mac. Spuštění simulátoru může chvíli trvat. Možná budete muset vyvolat simulátor do popředí na Macu, abyste viděli jeho výstup.  
  
    ![Aplikace běžící na simulátoru iOS](../cross-platform/media/cppmdd-opengles-iossimulator.png "CPPMDD_OpenGLES_iOSSimulator")  
  
    Po spuštění vaší aplikace můžete nastavit zarážky a použít ladicí program sady Visual Studio k prohlédnutí místních hodnot, viz zásobník volání a sledovat hodnoty.  
  
    ![Ladicí program na zarážce v aplikaci iOS](../cross-platform/media/cppmdd-opengles-iosdebug.png "CPPMDD_OpenGLES_iOSDebug")  
  
5. Pro zastavení ladění stiskněte Shift + F5.  
  
    Simulátor iOS je samostatný proces, který je dál spouštěný na Macu. Kód můžete upravovat, kompilovat a nasazovat několikrát do stejné instance simulátoru iOS. Kód můžete spustit také přímo v simulátoru po jeho nasazení.  
  
   Vygenerovaná projekty aplikace a knihovny pro iOS vloží kód jazyka C++ do statické knihovny, která implementuje pouze sdílený kód. Většina kódu aplikace je v projektu aplikace. Volání do kódu sdílené knihovny v tomto projektu šablony jsou vytvořena v souboru GameViewController. m. Sada Visual Studio při sestavování aplikace pro iOS používá sadu nástrojů Xcode Platform, která vyžaduje komunikaci se vzdáleným klientem, který běží na Macu.  
  
   Visual Studio přenáší soubory projektu a pošle příkazy do vzdáleného klienta k sestavení aplikace pomocí Xcode. Vzdálený klient odesílá informace o stavu sestavení zpět do sady Visual Studio. Po úspěšném vytvoření aplikace můžete pomocí sady Visual Studio odeslat příkazy ke spuštění a ladění aplikace. Ladicí program v aplikaci Visual Studio řídí aplikaci spuštěnou v simulátoru iOS spuštěnou na počítači Mac nebo připojeném zařízení s iOS. Visual Studio mapuje vlastnosti v projektu StaticLibrary na přepínače příkazového řádku a možnosti, které se používají k sestavení, propojení a ladění na cílové platformě iOS. Pro podrobnosti o možnosti příkazového řádku kompilátoru otevřete dialogové okno **stránky vlastností** pro projekt MyOpenGLESApp. iOS. StaticLibrary.  
  
## <a name="customize-your-apps"></a><a name="Customize"></a> Přizpůsobení aplikací  
 Můžete upravit sdílený kód jazyka C++ a přidat nebo změnit běžné funkce. Je nutné změnit volání na sdílený kód v projektech MyOpenGLESApp. Android. NativeActivity a MyOpenGLESApp. iOS. Application, aby odpovídaly. Makra preprocesoru můžete použít k určení sekcí specifických pro platformu v rámci společného kódu. Makro preprocesoru `__ANDROID__` je předdefinované při sestavování pro Android. Makro preprocesoru `__APPLE__` je předdefinované při sestavení pro iOS.  
  
 Chcete-li zobrazit technologii IntelliSense pro konkrétní platformu projektu, vyberte projekt v rozevíracím seznamu přepínačů kontextu v navigačním panelu v horní části okna editoru.  
  
 ![Rozevírací seznam přepínačů kontextu projektu v editoru](../cross-platform/media/cppmdd-opengles-contextswitcher.png "CPPMDD_OpenGLES_ContextSwitcher")  
  
 Problémy IntelliSense v aktuálním projektu jsou označeny červenou vlnovkou. Problémy v jiných projektech jsou označeny fialovou vlnovkou. Ve výchozím nastavení Visual Studio nepodporuje barevné zabarvení kódu ani technologii IntelliSense pro soubory Java nebo objektivní-C. Nicméně stále můžete upravovat zdrojové soubory a měnit prostředky, abyste mohli nastavit název, ikonu a další podrobnosti implementace aplikace.
