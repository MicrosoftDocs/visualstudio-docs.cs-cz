---
title: Stránky vlastností, JavaScript
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a35ee6d086153adc718a1616c0c8f0c8c606fbb7
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220027"
---
# <a name="property-pages-javascript"></a>Stránky vlastností, JavaScript
**Stránky vlastností** poskytuje přístup k nastavení projektu. Můžete použít stránky, které se zobrazují v **stránky vlastností** Chcete-li změnit vlastnosti projektu.

Pro přístup k vlastnostem projektu, vyberte uzel projektu v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Následující stránky a možnosti se zobrazí v **stránky vlastností**.

## <a name="configuration-and-platform-page"></a>Stránka Konfigurace a platforma
 Vybrat konfigurace a platformy, zobrazit nebo upravit pomocí následujících možností.

 **Konfigurace**

 Určuje nastavení konfigurace má být zobrazeno nebo upraveno. Nastavení musí být **ladění** (výchozí), **vydání**, **všechny konfigurace**, nebo konfigurace definovaná uživatelem. Další informace najdete v tématu [postupy: nastavení ladění a konfigurace v sadě Visual Studio verze](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Platforma**

 Určuje nastavení platformy má být zobrazeno nebo upraveno. Nastavení musí být **jakýkoli procesor** (výchozí pro [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikace), **x64**, **ARM**, **x86**, nebo platforma definovaná uživatelem. Další informace najdete v tématu [postupy: nastavení ladění a konfigurace v sadě Visual Studio verze](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Obecná stránka
 Pomocí následujících možností můžete nastavit obecné vlastnosti projektu.

> [!NOTE]
> Některé možnosti jsou dostupné jenom v aplikacích pro UPW.


 **Výstupní cesta**

 Určuje umístění výstupních souborů pro konfiguraci projektu. Cesta je relativní; Pokud zadáte absolutní cestu, absolutní cesta je uložena v projektu. Výchozí cesta je bin\Debug.

 Při použití zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. Po kliknutí na **ladění**, **spustit ladění** (nebo stiskněte klávesu F5) je sestavení umístěno do místa ladění bez ohledu **výstupní cesta** zadáte. Ale **sestavit řešení** příkaz **sestavení** nabídky se vloží do umístění, které zadáte. Chcete-li povolit pokročilé konfigurace sestavení, na panelu nabídek zvolte **nástroje**, **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**vyberte **Obecné**a poté zrušte zaškrtnutí **zobrazit pokročilé konfiguracesestavení**zaškrtávací políčko. To umožňuje ruční kontrolu všech hodnot konfigurace a určuje, zda je sestavena verze ladění nebo vydání.

 **Výchozí jazyk**

 Určuje výchozí jazyk pro projekt. Jazykové možnosti vybrané v **hodiny, jazyk a oblast** v Ovládacích panelech určuje upřednostňovaný jazyk uživatele. Zadáním výchozího jazyka pro projekt, ujistěte se, že zadané výchozí jazykové prostředky se používají Pokud preferovaný jazyk uživatele neodpovídá jazykovým prostředkům poskytovaným v aplikaci.

## <a name="debug-page"></a>Stránka ladit
 Pomocí následujících možností můžete nastavit vlastnosti pro ladění chování v projektu.

> [!NOTE]
> Některé možnosti jsou dostupné jenom v aplikacích pro UPW.


 **Spustit ladicí program**

 Určuje výchozího hostitele pro ladicí program.

-   Vyberte **místního počítače** a spusťte tak aplikaci v hostitelském počítači Visual Studio. Další informace najdete v tématu [spouštění aplikací v místním počítači](../../debugger/run-windows-store-apps-on-the-local-machine.md).

-   Vyberte **simulátor** a spusťte tak aplikaci v simulátoru. Další informace najdete v tématu [spouštění aplikací v simulátoru](../../debugger/run-windows-store-apps-in-the-simulator.md).

-   Vyberte **vzdálený počítač** a spusťte tak aplikaci ve vzdáleném počítači. Další informace o vzdáleném ladění naleznete v tématu [spouštění aplikací ve vzdáleném počítači](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

**Spuštění aplikace**

Určuje, jestli se má spustit při stisknutí klávesy F5 nebo kliknutím na aplikaci **ladění**, **spustit ladění**. Vyberte **Ano** pro spuštění aplikace; v opačném případě vyberte **ne**. Pokud vyberete **ne**, můžete stále ladit aplikaci, je-li použít jinou metodu jej spustit.

**Typ ladicího programu**

Určuje typy kódu k ladění. Vyberte **pouze pro skript** na ladění kódu JavaScript. Vyberte **pouze spravované** na ladění kódu, který je spravován modulem common language runtime. Vyberte **pouze nativní** na ladění kódu C++. Vyberte **nativní pomocí skriptu** pro ladění jazyka C++ a JavaScript. Vyberte **smíšený (spravovaný a nativní)** a spusťte tak ladění spravovaného kódu jazyka C++.

**Povolit zpětnou smyčku místní sítě**

Určuje, zda je povolen přístup na IP adresu zpětné smyčky pro testování aplikací. Vyberte **Ano** povolit použití adresu zpětné smyčky Pokud klientská aplikace je na stejném počítači, kde je serverová aplikace spuštěna; v opačném případě, že vyberte **ne**. Tato vlastnost je k dispozici pouze tehdy, pokud **spustit ladicí program** je nastavena na **vzdálený počítač**.

**Název počítače**

Určuje název vzdáleného počítače tak, že hostitelem ladicího programu. Tato vlastnost je k dispozici pouze tehdy, pokud **spustit ladicí program** je nastavena na **vzdálený počítač**.

**Vyžadovat ověření**

Určuje, zda vzdálený počítač vyžaduje ověřování. Tato vlastnost je k dispozici pouze tehdy, pokud **spustit ladicí program** je nastavena na **vzdálený počítač**.
