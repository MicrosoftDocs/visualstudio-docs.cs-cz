---
title: Visual C++ pro vývoj mobilních řešení napříč platformami | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5dfa353c1ae49e938c74e6d209cc2957dff2352d
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251634"
---
# <a name="visual-c-for-cross-platform-mobile-development"></a>Visual C++ pro vývoj mobilních řešení napříč platformami
Můžete vytvářet nativní aplikace C++ pro iOS, Android a Windows a sdílet společný kód v knihovnách vytvořené pro iOS, Android a Windows pomocí jazyka Visual C++ pro vývoj mobilních řešení napříč platformami. To je k dispozici v sadě Visual Studio 2015, který nainstaluje sady SDK a nástroje, které potřebujete pro vývoj pro různé platformy sdílených knihoven a nativních aplikací možnost. Po instalaci, můžete vytvořit kód, který běží na iOS a androidem a platformy kromě Windows, Windows Phone a Xbox Visual C++.  
  
 Psaní kódu pro různé platformy může být frustrující. Primární programovacích jazyků a nástrojů pro iOS, Android a Windows se liší na jednotlivých platformách. Ale všechny platformy podporují psaní kódu v jazyce C++. Toto je společným faktorem, který můžete použít k zajištění opakované použití jádra kódu napříč platformami. Nativní kód napsaný v jazyce C++ může být oba výkonnější a odolnější vůči zpětná analýza. Opakované využívání kódu ušetříte čas a námahu při vytváření aplikací pro různé platformy.  
  
 Vývoj pomocí jazyka Visual C++ pro vývoj mobilních řešení pro různé platformy má několik výhod:  
  
1.  **Snadná instalace.** Instalační program sady Visual Studio získá a nainstaluje potřebné nástroje třetích stran a sady SDK potřebujete k vývoji aplikací nebo knihovny pro Android a iOS. Konfigurace a nastavení je jednoduché a většinou automatické.  
  
2.  **Sestavení výkonných a dobře známého prostředí.** Projekty a sdílet řešení pro různé platformy můžete jednoduše vytvořte pomocí šablony sady Visual Studio. Spravujte vlastnosti pro všechny projekty pomocí jednoho rozhraní pro běžné. Upravit veškerý kód v editoru sady Visual Studio a využijte výhod integrovaných multiplatformní IntelliSense, dokončování kódu a zvýrazňování chyb.  
  
3.  **Jednotné možnosti ladění.** Sledování a procházejte kódem po krocích C++ na všech platformách, včetně zařízení s Androidem a emulátory, simulátory Iosu a zařízení a zařízení s Windows nebo Windows Phone a emulátory pomocí špičkové ladicí nástroje v sadě Visual Studio.  
  
## <a name="get-the-tools"></a>Získání nástrojů  
 Visual C++ pro vývoj mobilních řešení pro různé platformy je Instalovatelná možnost, která je součástí sady Visual Studio 2015. Požadavky a pokyny k instalaci najdete v tématu [instalaci Visual C++ pro vývoj mobilních řešení napříč platformami](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). K vytvoření kódu pro iOS, potřebujete také do počítače Mac a Apple iOS vývojářský účet. Další informace najdete v tématu [instalace a konfigurace nástroje potřebné k vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).  
  
## <a name="come-up-to-speed"></a>Zrychlit pochází  
 Pokud přecházíte z Androidu nebo iOS development, máme několik skvělých materiálů o tom, jak začít pracovat. Visual Studio je výrazová a výkonné vývojové prostředí. Zjistěte, jak ji používat, zkuste použít [Začínáme pro vývojáře pro Android](/previous-versions/windows/apps/dn275875\(v=win.10\)) nebo [Začínáme pro vývojáře v systému iOS](/previous-versions/windows/apps/jj657966\(v=win.10\)). Tato témata vás seznámí s Visual Studio a koncepty, že které budete potřebovat k vývoji aplikací pro různé platformy pro Windows a Windows Phone. Zápis první multiplatformní aplikace pro iOS a Android, najdete v článku [sestavení aplikace OpenGL ES na Androidu a iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).  
  
 Visual C++ pro vývoj Multiplatformních mobilních aplikací obsahuje několik šablon můžete začít pracovat na své aplikace:  
  
-   Aplikace OpenGLES 2 (Android, iOS, Windows Universal)  
  
     Vytvoří řešení, které obsahuje sadu projektů k sestavení aplikace Nativeactivity pro Android, aplikace pro iOS a Universal Windows app, společně s sdílené knihovny kódu C++. Tyto aplikace pomocí knihovny pro konkrétní platformu vytvořené pomocí společný kód C++ OpenGL ES k vykreslení na stejnou datovou krychli pokryjte v každé aplikaci. Při instalaci sady Visual Studio pro tuto šablonu použít, je nutné zahrnout možnost Universal Windows nástroje pro vývoj aplikací.  
  
-   Aplikace s Nativeactivity (Android)  
  
     Vytvoří kompletní aplikace C++ OpenGL jako projekt aplikace Android Native Activity.  
  
-   Aplikace OpenGLES (Android, iOS)  
  
     Vytvoří řešení sadu projektů k sestavení aplikace Nativeactivity pro Android a aplikace pro iOS. Tyto aplikace pomocí knihovny pro konkrétní platformu vytvořené pomocí společný kód C++ OpenGL ES k vykreslení na stejnou datovou krychli pokryjte v každé aplikaci.  
  
-   Sdílená knihovna (Android, iOS)  
  
     Vytvoří řešení s projekty k vytvoření souboru s Androidem dynamická knihovna (.so) a soubor statická knihovna (.a) pro iOS pomocí společný kód C++ ve sdíleném projektu.  
  
-   Základní aplikace (Android, Ant)  
  
     Vytvoří aplikaci pro Android "Hello, World" projekt aplikace, který používá jenom pro zdrojový kód v Javě a Ant sestavovací systém.  
  
-   Základní aplikace (Android, Gradle)  
  
     Vytvoří aplikaci pro Android "Hello, World" projekt aplikace, který používá jenom pro zdrojový kód v Javě a Gradle sestavovací systém.  
  
-   Základní knihovna (Android, Ant)  
  
     Vytvoří aplikaci pro Android "Hello, World" projekt knihovny, který používá jenom pro zdrojový kód v Javě a Ant sestavovací systém.  
  
-   Základní knihovna (Android, Gradle)  
  
     Vytvoří aplikaci pro Android "Hello, World" projekt knihovny, který používá jenom pro zdrojový kód v Javě a Gradle sestavovací systém.  
  
-   Dynamická sdílená knihovna (Android)  
  
     Vytvoří soubor s Androidem dynamická knihovna (.so) s využitím kódu jazyka C++.  
  
-   Aplikace OpenGLES 2 (iOS)  
  
     Vytvoří sadu projektů k sestavení aplikace pro iOS OpenGL ES 2 řešení. Aplikace používá knihovny kódu C++ OpenGL ES k nakreslení pokryjte datovou krychli v aplikaci pro iOS. Tato aplikace může být dobrým výchozím bodem pro import knihoven C++ do aplikace pro iOS zobrazuje.  
  
-   Statická knihovna (Android)  
  
     Vytvoří projekt pro vytvoření statické knihovny pro Android. Můžete pouze jeden dynamické knihovny v aplikaci pro Android, ale můžete propojit libovolný počet statických knihoven.  
  
-   Statická knihovna (iOS)  
  
     Vytvoří projekt pro vytvoření statické knihovny pro iOS.  
  
-   Projekt makefile (Android)  
  
     Vytvoří obálku projektů pro projekty souborů pravidel s Androidem.  
  
## <a name="try-out-sample-code"></a>Vyzkoušejte si ukázkový kód  
 Stáhněte si ukázky, které ukazují, jak vytvořit knihovny sdíleného kódu, které používáte ve Windows, Android a aplikací pro iOS a jak vytvářet kompletní aplikace Nativeactivity pro Android. Abyste mohli začít, najdete v článku [příklady vývoj mobilních řešení napříč platformami](../cross-platform/cross-platform-mobile-development-examples.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
1.  [Instalovat Visual C++ pro vývoj mobilních řešení napříč platformami](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)  
  
2.  [Instalace a konfigurace nástroje potřebné k vytváření pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)  
  
3.  [Vytvoření nové aplikace Android nativeactivity](../cross-platform/create-an-android-native-activity-app.md)  
  
4.  [Vytvoření aplikace OpenGL ES na Androidu a iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)  
  
5.  [Příklady vývoj mobilních řešení napříč platformami](../cross-platform/cross-platform-mobile-development-examples.md)