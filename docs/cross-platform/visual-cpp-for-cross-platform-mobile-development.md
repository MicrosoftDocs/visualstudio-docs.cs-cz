---
title: Vývoj mobilních aplikací pro různé platformy C++ s využitím | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: bc4164ec405aed2941e807934ee8d66b7ae72504
ms.sourcegitcommit: ca3bb6db949f5e405f6ffe1afa5f430662c1173f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2019
ms.locfileid: "74098975"
---
# <a name="cross-platform-mobile-development-with-c"></a>Vývoj multiplatformních mobilních řešení v jazyce C++

Nativní C++ aplikace pro zařízení s iOS, Androidem a Windows můžete vytvářet pomocí nástrojů pro různé platformy, které jsou k dispozici v aplikaci Visual Studio. **Vývoj pro mobilní C++ zařízení v nástroji** je pracovní zatížení, které je dostupné v instalačním programu sady Visual Studio. Nainstaluje sady SDK a nástroje, které potřebujete pro vývoj sdílených knihoven a nativních aplikací pro různé platformy. Po nainstalování můžete použít C++ k vytvoření kódu, který běží na zařízeních s iOS a Androidem, na platformách Windows, Windows Store a Xbox.

Psaní kódu pro více platforem je často frustrující. Primární vývojové jazyky a nástroje pro iOS, Android a Windows se na všech platformách liší. Nicméně všechny platformy podporují psaní kódu v C++. Je to společný jmenovatel, který umožňuje opakované použití základního kódu napříč platformami. Nativní kód napsaný C++ v může být více výkonných i odolný proti zpětné analýze. Opětovné použití kódu může ušetřit čas i úsilí při vytváření aplikací pro více platforem.

Vývoj s C++ využitím pro vývoj mobilních aplikací pro různé platformy má několik výhod:

- **Snadná instalace** Instalační program sady Visual Studio získá a nainstaluje požadované nástroje a sady SDK třetích stran, které potřebujete k vytváření aplikací nebo knihoven pro Android a iOS. Konfigurace a nastavení jsou jednoduché a většinou automatické.

- **Výkonné a známé prostředí pro sestavování.** Vytvářejte řešení a projekty pro více platforem snadno pomocí šablon sady Visual Studio. Spravujte vlastnosti pro všechny projekty pomocí jednoho společného rozhraní. Upravte veškerý kód v editoru sady Visual Studio a využijte integrované technologie IntelliSense pro různé platformy pro dokončování kódu a zvýrazňování chyb.

- **Jednotné prostředí pro ladění.** Pomocí špičkových ladicích nástrojů v aplikaci Visual Studio můžete sledovat a krokovat C++ kód na všech platformách: zařízení a emulátory s Androidem, simulátory a zařízení s Windows a Windows Store a emulátory.

## <a name="get-the-tools"></a>Získat nástroje

Vývoj pro mobilní C++ zařízení s je instalovatelným zatížením, které se dodává se sadou Visual Studio. Požadavky a pokyny k instalaci najdete v tématu [instalace vývoje mobilních aplikací pro různé C++platformy pomocí ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Pro vytváření kódu pro iOS budete potřebovat taky počítač Mac a vývojářský účet pro Apple iOS. Další informace najdete v tématu [instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="come-up-to-speed"></a>Až do rychlosti

Pokud přecházíte na vývoj pro Android nebo iOS, máme k dispozici nějaký skvělý materiál o tom, jak začít. Visual Studio je prostředí pro rychlé a podporující vývoj. Pokud se chcete dozvědět, jak ho používat, zkuste začít [pro vývojáře v Androidu](/previous-versions/windows/apps/dn275875\(v=win.10\)) nebo začít [pro vývojáře v iOS](/previous-versions/windows/apps/jj657966\(v=win.10\)). Tyto články vás seznámí se systémem Visual Studio a koncepty, které budete potřebovat pro vývoj aplikací pro různé platformy pro Windows a Windows Store. Pokud chcete začít psát svoji první aplikaci pro více platforem pro iOS a Android, přečtěte si téma [Vytvoření aplikace OPENGL ES v Androidu a iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).

Vývoj mobilních aplikací pomocí C++ úlohy zahrnuje několik šablon, které vám pomůžou začít s aplikacemi:

- Aplikace s nativní aktivitou (Android)

  Vytvoří kompletní C++ aplikaci OpenGL jako projekt nativní aktivity Androidu.

- Aplikace OpenGLs (Android, iOS)

  Vytvoří řešení se sadou projektů pro sestavení nativní aktivity aplikace pro Android i aplikace pro iOS. Tyto aplikace používají knihovny specifické pro platformu vytvořené pomocí běžných C++ kódů OpenGL ES k vykreslování stejné otáčející se datové krychle v každé aplikaci.

- Sdílená knihovna (Android, iOS)

  Vytvoří řešení s projekty pro vytvoření souboru dynamické knihovny (. so) Androidu a souboru statické knihovny pro iOS (. a) pomocí společného C++ kódu ve sdíleném projektu.

- Základní aplikace (Android, ANT)

  Vytvoří projekt aplikace pro Android "Hello, World", který používá pouze zdrojový kód Java a systém sestavení ANT.

- Základní aplikace (Android, Gradle)

  Vytvoří projekt aplikace pro Android "Hello, World", který používá pouze zdrojový kód Java a systém sestavení Gradle.

- Základní knihovna (Android, ANT)

  Vytvoří projekt knihovny Android "Hello, World", který používá pouze zdrojový kód Java a systém sestavení ANT.

- Základní knihovna (Android, Gradle)

  Vytvoří projekt knihovny Android "Hello, World", který používá pouze zdrojový kód Java a systém sestavení Gradle.

- Dynamická sdílená knihovna (Android)

  Vytvoří soubor dynamické knihovny Android (. so) pomocí C++ kódu.

- Aplikace OpenGLes 2 (iOS)

  Vytvoří řešení se sadou projektů pro sestavení aplikace OpenGL ES 2 pro iOS. Aplikace používá knihovnu kódu C++ OpenGL ES k vykreslování otáčející se datové krychle v aplikaci pro iOS. Tato aplikace může být dobrým výchozím bodem pro zobrazení způsobu importu C++ knihoven do vaší aplikace pro iOS.

- Statická knihovna (Android)

  Vytvoří projekt pro sestavení statické knihovny pro Android. Můžete propojit jenom jednu dynamickou knihovnu v aplikaci pro Android, ale můžete propojit libovolný počet statických knihoven.

- Statická knihovna (iOS)

  Vytvoří projekt pro sestavení statické knihovny pro iOS.

- Projekt makefile (Android)

  Vytvoří obálku projektu pro vlastní projekty se souborem Android makefile.

## <a name="try-out-sample-code"></a>Vyzkoušet vzorový kód

Stáhněte si ukázky, které ukazují, jak vytvářet knihovny sdíleného kódu, které můžete použít v aplikacích pro Windows, Android a iOS. A podívejte se na příklady vytvoření kompletních aplikací nativních aktivit pro Android. Chcete-li začít, přečtěte si [Příklady vývoje mobilních aplikací pro různé platformy](../cross-platform/cross-platform-mobile-development-examples.md).

## <a name="see-also"></a>Viz také:

[Instalace vývoje mobilních aplikací pro různé platformy C++ pomocí](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md) \
[Instalace a konfigurace nástrojů pro sestavení pomocí iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md) \
[Vytvoření aplikace nativní aktivity pro Android](../cross-platform/create-an-android-native-activity-app.md) \
[Sestavení aplikace OPENGL ES v Androidu a iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md) \
[Příklady vývoje mobilních aplikací pro různé platformy](../cross-platform/cross-platform-mobile-development-examples.md)
