---
title: Vytvoření aplikace pro nativní činnost v Androidu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e554c7b97c2feac031510cfdd0894d29b4ba85eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151034"
---
# <a name="create-an-android-native-activity-app"></a>Vytvoření aplikace s NativeActivity pro Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když nainstalujete možnost Visual C++ for Cross-Platform Mobile Development, Visual Studio 2015 se dá použít k vytvoření plně funkčních aplikací pro nativní aktivity Androidu. Android Native Development Kit (NDK) je sada nástrojů, která umožňuje implementovat většinu aplikací pro Android pomocí čistě kódu C/C++. Některý kód Java JNI funguje jako Glue, aby mohl váš kód C/C++ pracovat s Androidem. Android NDK představil možnost vytvářet nativní aplikace aktivity s rozhraním Android API úrovně 9. Nativní kód aktivity je oblíbený pro vytváření her a aplikací s grafickými náročnou, které používají modul Unreal nebo OpenGL. Toto téma vás provede vytvořením jednoduché aplikace nativní aktivity, která používá OpenGL. Další témata najdete v rámci životního cyklu vývojářů při úpravách, sestavování, ladění a nasazování nativního kódu aktivity.  
  
 [Požadavků](#req)   
 [Vytvořit nový projekt nativní aktivity](#Create)   
 [Sestavování a spouštění výchozí aplikace aktivity nativní pro Android](#BuildHello)  
  
## <a name="requirements"></a><a name="req"></a> Požadavků  
 Než budete moct vytvořit aplikaci pro nativní aktivity Androidu, musíte se ujistit, že jste splnili všechny požadavky na systém a nainstalujete Visual C++ možností vývoje mobilních aplikací v aplikaci Visual Studio 2015. Další informace najdete v tématu [instalace Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Zajistěte, aby se v instalaci zahrnovaly potřebné nástroje a sady SDK třetích stran, a že je instalace Microsoft Visual Studio Emulator for Android.  
  
## <a name="create-a-new-native-activity-project"></a><a name="Create"></a> Vytvořit nový projekt nativní aktivity  
 V tomto kurzu nejprve vytvoříte nový projekt nativní aktivity pro Android a potom sestavíte a spustíte výchozí aplikaci v emulátoru sady Visual Studio pro Android.  
  
#### <a name="to-create-a-new-project"></a>Vytvoření nového projektu  
  
1. Otevřete sadu Visual Studio. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.  
  
2. V dialogovém okně **Nový projekt** , v části **šablony**zvolte možnost **Visual C++**, pro **různé platformy**a pak zvolte šablonu **aplikace nativního Inactivity (Android)** .  
  
3. Přiřaďte aplikaci název jako `MyAndroidApp` a pak zvolte **OK**.  
  
    ![Vytvoření projektu nativní aktivity](../cross-platform/media/cppmdd-newproject.PNG "CppMDD_NewProject")  
  
    Visual Studio vytvoří nové řešení a otevře Průzkumník řešení.  
  
    ![Nativní projekt aktivity v Průzkumník řešení](../cross-platform/media/cppmdd-rc-na-solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
   Nové řešení aplikace pro nativní činnost v Androidu zahrnuje dva projekty:  
  
- **MyAndroidApp. NativeActivity** obsahuje odkazy a připevnění kódu vaší aplikace, aby běžel jako nativní aktivita v Androidu. Implementace vstupních bodů ze spojovacího kódu je v Main. cpp. Předkompilované hlavičky jsou v souboru PCH. h. Tento projekt nativní aplikace aktivity je zkompilován do sdílené knihovny. soubor, který je vyzvednut projektem balení.  
  
- **MyAndroidApp. balení** vytvoří soubor. APK pro nasazení v zařízení nebo emulátoru Androidu. Obsahuje prostředky a AndroidManifest.xml soubor, ve kterém jste nastavili vlastnosti manifestu. Obsahuje také soubor build.xml, který řídí proces sestavení ANT. Ve výchozím nastavení je nastaven jako spouštěný projekt, aby jej bylo možné nasadit a spustit přímo ze sady Visual Studio.  
  
## <a name="build-and-run-the-default-android-native-activity-app"></a><a name="BuildHello"></a> Sestavování a spouštění výchozí aplikace aktivity nativní pro Android  
 Sestavte a spusťte aplikaci generovanou šablonou a ověřte instalaci a instalaci. Pro tento úvodní test spusťte aplikaci na jednom z profilů zařízení nainstalovaných emulátorem sady Visual Studio pro Android. Pokud dáváte přednost testování aplikace na jiném cíli, můžete načíst cílový emulátor nebo připojit zařízení k počítači.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>Sestavení a spuštění výchozí nativní aplikace aktivity  
  
1. Pokud ještě není vybraná, vyberte v rozevíracím seznamu **platformy řešení** možnost **x86** .  
  
     ![Výběr platformy řešení – rozevírací seznam x86](../cross-platform/media/cppmdd-rc-na-solution-x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     Pokud se seznam **platformy řešení** nezobrazuje, zvolte možnost **platformy řešení** v seznamu **Přidat nebo odebrat tlačítka** a pak zvolte svou platformu.  
  
2. Na panelu nabídek vyberte **sestavení**, **řešení sestavení**.  
  
     V okně výstup se zobrazí výstup procesu sestavení pro dva projekty v řešení.  
  
3. Jako cíl nasazení vyberte jeden z profilů Androidu pro emulátor (x86).  
  
     Pokud máte nainstalované další emulátory nebo zařízení s Androidem, můžete je vybrat v rozevíracím seznamu cíl nasazení.  
  
4. Stisknutím klávesy F5 spusťte ladění, nebo stisknutím klávesy Shift + F5 spusťte bez ladění.  
  
     V emulátoru sady Visual Studio pro Android bude vypadat výchozí aplikace.  
  
     ![Emulátor, ve kterém běží vaše aplikace](../cross-platform/media/cppmdd-emulator-running-app.PNG "CppMDD_Emulator_Running_App")  
  
     Visual Studio spustí emulátor, což trvá několik sekund, než se načte a nasadí váš kód. Po spuštění aplikace můžete nastavit zarážky a použít ladicí program ke krokování kódu, kontrole místních hodnot a sledování hodnot.  
  
5. Pro zastavení ladění stiskněte Shift + F5.  
  
     Emulátor je samostatný proces, který pokračuje v běhu. Kód můžete upravovat, kompilovat a nasazovat několikrát do stejného emulátoru.
