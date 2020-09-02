---
title: Visual C++ for Cross-Platform Mobile Development | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e947800c82036b061b2f48303733690a95ec53bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62573063"
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Visual C++ for Cross-Platform Mobile Development
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí Visual C++ for Cross-Platform Mobile Development můžete vytvářet nativní aplikace C++ pro zařízení s iOS, Androidem a Windows a sdílet společný kód v knihovnách postavených pro iOS, Android a Windows. Tato možnost je k dispozici v aplikaci Visual Studio 2015 a instaluje sady SDK a nástroje, které potřebujete pro vývoj sdílených knihoven a nativních aplikací pro různé platformy. Po instalaci můžete použít Visual C++ a vytvořit kód, který běží na zařízeních s iOS a Androidem a na platformách, a to i na Windows, Windows Phone a Xbox.  
  
 Psaní kódu pro více platforem může být frustrující. Primární vývojové jazyky a nástroje pro iOS, Android a Windows se na všech platformách liší. Nicméně všechny platformy podporují psaní kódu v jazyce C++. Toto je společný jmenovatel, který můžete použít k povolení opakovaného použití základního kódu napříč platformami. Nativní kód napsaný v jazyce C++ může být více výkonných i odolný proti zpětné analýze. Opětovné použití kódu může ušetřit čas i úsilí při vytváření aplikací pro více platforem.  
  
 Vývoj pomocí Visual C++ for Cross-Platform Mobile Development má několik výhod:  
  
1. **Snadná instalace** Instalační program sady Visual Studio získá a nainstaluje požadované nástroje a sady SDK třetích stran, které potřebujete k vytváření aplikací nebo knihoven pro Android a iOS. Konfigurace a nastavení jsou jednoduché a většinou automatické.  
  
2. **Výkonné a známé prostředí pro sestavování.** Vytvářejte řešení a projekty pro více platforem snadno pomocí šablon sady Visual Studio. Spravujte vlastnosti pro všechny projekty pomocí jednoho společného rozhraní. Upravte veškerý kód v editoru sady Visual Studio a využijte integrované technologie IntelliSense pro různé platformy pro dokončování kódu a zvýrazňování chyb.  
  
3. **Jednotné prostředí pro ladění.** Pomocí špičkových ladicích nástrojů v aplikaci Visual Studio můžete sledovat a krokovat kód C++ na všech platformách, včetně zařízení s Androidem a emulátorů, simulátorů a zařízení s Androidem a zařízení s Windows nebo Windows Phone a emulátorů.  
  
## <a name="get-the-tools"></a>Získat nástroje  
 Visual C++ for Cross-Platform Mobile Development je instalovatelný způsob, který je součástí sady Visual Studio 2015. Požadavky a pokyny k instalaci najdete v tématu [Install Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Pro vytváření kódu pro iOS budete potřebovat taky počítač Mac a vývojářský účet pro Apple iOS. Další informace najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Až do rychlosti  
 Pokud přecházíte na vývoj pro Android nebo iOS, máme k dispozici nějaký skvělý materiál o tom, jak začít. Visual Studio je prostředí pro rychlé a podporující vývoj. Pokud se chcete dozvědět, jak ho používat, zkuste [začít pro vývojáře v Androidu](https://msdn.microsoft.com/library/windows/apps/dn275875.aspx) nebo [začít pro vývojáře v iOS](https://msdn.microsoft.com/library/windows/apps/xaml/jj657966.aspx). Tato témata vás seznámí s prostředím Visual Studio a koncepty, které budete potřebovat pro vývoj aplikací pro Windows a Windows Phone v různých platformách. Pokud chcete začít psát svoji první aplikaci pro více platforem pro iOS a Android, přečtěte si téma [Vytvoření aplikace OPENGL ES v Androidu a iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C++ for Cross-Platform Mobile Development obsahuje několik šablon, které vám pomůžou začít s aplikacemi:  
  
- Aplikace OpenGLes 2 (Android, iOS, Windows Universal)  
  
     Vytvoří řešení, které obsahuje sadu projektů pro sestavení nativní aplikace aktivity pro Android, aplikaci pro iOS a univerzální aplikaci pro Windows spolu se sdílenou knihovnou kódu C++. Tyto aplikace používají knihovny specifické pro platformu vytvořené pomocí společného kódu C++ OpenGL ES pro vykreslení stejné otáčející se datové krychle v každé aplikaci. Při instalaci sady Visual Studio, aby používala tuto šablonu, musíte zahrnout možnost nástroje pro vývoj univerzálních aplikací pro Windows.  
  
- Aplikace s nativní aktivitou (Android)  
  
     Vytvoří úplnou aplikaci OpenGL v C++ jako projekt nativní aktivity Androidu.  
  
- Aplikace OpenGLs (Android, iOS)  
  
     Vytvoří řešení se sadou projektů pro sestavení nativní aktivity aplikace pro Android i aplikace pro iOS. Tyto aplikace používají knihovny specifické pro platformu vytvořené pomocí společného kódu C++ OpenGL ES pro vykreslení stejné otáčející se datové krychle v každé aplikaci.  
  
- Sdílená knihovna (Android, iOS)  
  
     Vytvoří řešení s projekty pro vytvoření souboru dynamické knihovny (. so) Androidu a souboru statické knihovny pro iOS (. a) pomocí společného kódu C++ ve sdíleném projektu.  
  
- Základní aplikace (Android, ANT)  
  
     Vytvoří projekt aplikace pro Android "Hello, World", který používá pouze zdrojový kód Java a systém sestavení ANT.  
  
- Základní aplikace (Android, Gradle)  
  
     Vytvoří projekt aplikace pro Android "Hello, World", který používá pouze zdrojový kód Java a systém sestavení Gradle.  
  
- Základní knihovna (Android, ANT)  
  
     Vytvoří projekt knihovny Android "Hello, World", který používá pouze zdrojový kód Java a systém sestavení ANT.  
  
- Základní knihovna (Android, Gradle)  
  
     Vytvoří projekt knihovny Android "Hello, World", který používá pouze zdrojový kód Java a systém sestavení Gradle.  
  
- Dynamická sdílená knihovna (Android)  
  
     Vytvoří soubor dynamické knihovny Android (. so) pomocí kódu jazyka C++.  
  
- Aplikace OpenGLes 2 (iOS)  
  
     Vytvoří řešení se sadou projektů pro sestavení aplikace OpenGL ES 2 pro iOS. Aplikace používá knihovnu C++ OpenGL ES Code k vykreslení otáčející se datové krychle v aplikaci pro iOS. Tato aplikace může být dobrým výchozím bodem pro zobrazení způsobu importu knihoven C++ do vaší aplikace pro iOS.  
  
- Statická knihovna (Android)  
  
     Vytvoří projekt pro sestavení statické knihovny pro Android. Můžete propojit jenom jednu dynamickou knihovnu v aplikaci pro Android, ale můžete propojit libovolný počet statických knihoven.  
  
- Statická knihovna (iOS)  
  
     Vytvoří projekt pro sestavení statické knihovny pro iOS.  
  
- Projekt makefile (Android)  
  
     Vytvoří obálku projektu pro vlastní projekty se souborem Android makefile.  
  
## <a name="try-out-sample-code"></a>Vyzkoušet vzorový kód  
 Stáhněte si ukázky, které ukazují, jak vytvářet knihovny sdíleného kódu, které můžete použít v aplikacích pro Windows, Android a iOS a jak vytvářet kompletní nativní aktivity aplikací pro Android. Chcete-li začít, přečtěte si [Příklady vývoje mobilních aplikací pro různé platformy](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>V této části  
  
1. [Instalace komponenty Visual C++ for Cross-Platform Mobile Development](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2. [Instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3. [Vytvoření aplikace pro nativní činnost v Androidu](../cross-platform/create-an-android-native-activity-app.md)  
  
4. [Sestavení aplikace OpenGL ES v Androidu a iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5. [Příklady vývoje mobilních aplikací pro různé platformy](../cross-platform/cross-platform-mobile-development-examples.md)
