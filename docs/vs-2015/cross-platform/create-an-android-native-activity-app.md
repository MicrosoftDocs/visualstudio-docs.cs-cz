---
title: Vytvoření nové aplikace Android Native Activity | Dokumentace Microsoftu
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
ms.assetid: 884014b1-5208-45ec-b0da-ad0070d2c24d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f6bc8d96c6207889f07ec6bf1257be3d620855fc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731427"
---
# <a name="create-an-android-native-activity-app"></a>Vytvoření aplikace s NativeActivity pro Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Při instalaci Visual C++ pro vývoj mobilních řešení napříč platformami možnost Visual Studio 2015 je možné vytvořit plně funkční aplikace Android Native Activity. Android Kit pro nativní vývoj (NDK) je sada nástrojů, která umožňuje provádět většinu aplikace pro Android pomocí čistého kódu C/C++. Nějaký kód Java JNI funguje jako spojovacího kódu C/C++ pracovat s Androidem umožňuje. Sada Android NDK zavedena možnost vytvářet aplikace Native Activity s Android API úrovně 9. Nativní kód aktivity se používá pro vytvoření hry a grafické náročné aplikace, které používají OpenGL nebo Unreal Engine. Toto téma vás provede vytvořením jednoduché aplikace s Nativeactivity, který využívá OpenGL. Další témata projdete developer životní cyklus úpravy, sestavování, ladění a nasazování Nativeactivity kódu.  
  
 [Požadavky](#req)   
 [Vytvoření nového projektu s Nativeactivity](#Create)   
 [Sestavte a spusťte výchozí aplikace Android Native Activity](#BuildHello)  
  
##  <a name="req"></a> Požadavky  
 Před vytvořením aplikace Android Native Activity, ujistěte se, jste splněny všechny požadavky na systém a instalaci možnost vývoj mobilní zařízení v jazyce Visual C++ v sadě Visual Studio 2015. Další informace najdete v tématu [instalaci Visual C++ pro vývoj mobilních řešení napříč platformami](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Ujistěte se, potřebné nástroje třetích stran a sady SDK jsou zahrnuty v instalaci a zda je nainstalována aplikace Microsoft Visual Studio Emulator for Android.  
  
##  <a name="Create"></a> Vytvoření nového projektu s Nativeactivity  
 V tomto kurzu budete nejdřív vytvořte nový projekt Android Native Activity a začnete vytvářet a spusťte výchozí aplikaci v emulátoru Visual Studia pro Android.  
  
#### <a name="to-create-a-new-project"></a>Chcete-li vytvořit nový projekt  
  
1. Otevřít Visual Studio. V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2. V **nový projekt** dialogovém okně **šablony**, zvolte **Visual C++**, **různé platformy**a klikněte na tlačítko  **Aplikace s Nativeactivity (Android)** šablony.  
  
3. Dejte aplikaci s názvem jako `MyAndroidApp`a klikněte na tlačítko **OK**.  
  
    ![Vytvoření projektu Nativeactivity](../cross-platform/media/cppmdd-newproject.PNG "CppMDD_NewProject")  
  
    Visual Studio vytvoří nové řešení a otevře se Průzkumník řešení.  
  
    ![Aktivity projektu v Průzkumníku řešení](../cross-platform/media/cppmdd-rc-na-solutionexp.PNG "CPPMDD_RC_NA_SolutionExp")  
  
   Nové řešení aplikace Android Native Activity obsahuje dva projekty:  
  
-   **MyAndroidApp.NativeActivity** obsahuje odkazy na a spojovacího kódu pro svoji aplikaci spouštět jako nativní aktivita v Androidu. Implementace vstupních bodů ze spojovacího kódu jsou v main.cpp. Soubor pch.h jsou předkompilované hlavičky. Tento projekt aplikace Nativeactivity je zkompilován do sdílené knihovny soubor .so, který převezme balícího projektu.  
  
-   **MyAndroidApp.Packaging** vytvoří soubor .apk pro nasazení na emulátoru nebo zařízení s Androidem. Tato položka obsahuje prostředky a souboru AndroidManifest.xml, kde nastavíte vlastnosti manifestu. Obsahuje také Build.XML – soubor, který řídí proces sestavení Ant. Ho jako spouštěný projekt ve výchozím nastavení, takže je možné nasadit a spustit přímo ze sady Visual Studio.  
  
##  <a name="BuildHello"></a> Sestavte a spusťte výchozí aplikace Android Native Activity  
 Sestavíte a spustíte aplikaci vygenerovaná šablona k ověření instalace a nastavení. Pro tento počáteční test spusťte aplikaci na jeden z profilů zařízení nainstaloval Visual Studio Emulator for Android. Pokud chcete testovat svou aplikaci na jiný cíl, můžete načíst cíl emulátor nebo připojte zařízení k počítači.  
  
#### <a name="to-build-and-run-the-default-native-activity-app"></a>Chcete sestavovat a spouštět aplikace s Nativeactivity výchozí  
  
1.  Pokud ještě není vybraná, zvolte **x86** z **platformy řešení** rozevíracího seznamu.  
  
     ![Výběru v rozevíracího seznamu x86 platformy řešení](../cross-platform/media/cppmdd-rc-na-solution-x86.png "CPPMDD_RC_NA_Solution_x86")  
  
     Pokud **platformy řešení** seznamu nezobrazuje, vyberte **platformy řešení** z **přidat nebo odebrat tlačítka** seznamu a pak zvolte vaši platformu.  
  
2.  V panelu nabídky zvolte **sestavení**, **sestavit řešení**.  
  
     V okně výstupu zobrazí výstup z procesu sestavení pro tyto dva projekty v řešení.  
  
3.  Vyberte jednu z emulátoru VS telefon s Androidem (x86) profily jako cíl nasazení.  
  
     Pokud jste nainstalovali jiné emulátory nebo připojené zařízení s Androidem, můžete je v rozevíracím seznamu cíl nasazení.  
  
4.  Stisknutím klávesy F5 spusťte ladění nebo Shift + F5 spustit bez ladění.  
  
     Tady je výchozí aplikace vypadá v sadě Visual Studio emulator for Android.  
  
     ![V emulátoru vaše aplikace běžela](../cross-platform/media/cppmdd-emulator-running-app.PNG "CppMDD_Emulator_Running_App")  
  
     Visual Studio spustí se emulátor, který trvá několik sekund na zatížení a nasaďte svůj kód. Po zahájení vaší aplikace můžete nastavit zarážky a ladicího programu můžete krokovat kód, prozkoumat místní hodnoty a podívejte se na hodnoty.  
  
5.  Stiskněte Shift + F5, můžete zastavit ladění.  
  
     Emulátor je samostatný proces, který zůstane spuštěný. Můžete upravit, zkompilujte a nasaďte svůj kód do stejné emulátor více než jednou.

