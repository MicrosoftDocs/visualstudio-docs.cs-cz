---
title: Stránky vlastností, JavaScript
ms.date: 06/21/2017
ms.technology: vs-javascript
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6883e556cd70adddd45fd442d338e10d1cafa1e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926200"
---
# <a name="property-pages-javascript"></a>Stránky vlastností, JavaScript

**Stránky vlastností** poskytují přístup k nastavení projektu. Ke změně vlastností projektu můžete použít stránky, které se zobrazují na **stránkách vlastností.**

Chcete-li získat přístup k vlastnostem projektu, vyberte uzel projektu v **Průzkumníku řešení**. V nabídce **Project** klepněte na **položku Vlastnosti**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Následující stránky a možnosti se zobrazí na **stránkách vlastností**.

## <a name="configuration-and-platform-page"></a>Stránka konfigurace a platformy

Následující možnosti slouží k výběru konfigurace a platformy, které chcete zobrazit nebo upravit.

 **Konfigurace**

Určuje nastavení konfigurace, která se mají zobrazit nebo upravit. Nastavení jsou **Ladění** (výchozí), **Vydání**, **Všechny konfigurace**nebo uživatelem definovaná konfigurace. Další informace naleznete v [tématu How to: Set debug and release configurations in Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Platforma**

Určuje nastavení platformy, které se má zobrazit nebo upravit. Nastavení jsou **Libovolný procesor** [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] (výchozí pro aplikace), **x64**, **ARM**, **x86**nebo uživatelem definovaná platforma. Další informace naleznete v [tématu How to: Set debug and release configurations in Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Obecná stránka

Následující možnosti slouží k nastavení obecných vlastností projektu.

> [!NOTE]
> Některé možnosti jsou k dispozici pouze v aplikacích UPW.

 **Výstupní cesta**

Určuje umístění výstupních souborů pro konfiguraci projektu. Cesta je relativní; Pokud zadáte absolutní cestu, absolutní cesta se uloží do projektu. Výchozí cesta je bin\Ladění.

Při použití zjednodušené konfigurace sestavení, systém projektu určuje, zda chcete vytvořit ladicí nebo vyvolanou verzi. Po klepnutí na **tlačítko Ladění** > **start ladění** (nebo stiskněte **klávesu F5**), sestavení je umístěn v umístění ladění bez ohledu na **výstupní cestu,** kterou zadáte. Příkaz **Sestavit řešení** v nabídce **Sestavení** jej však umístí do zadaného umístění. Chcete-li povolit pokročilé konfigurace sestavení, zvolte na řádku nabídek**možnost Možnosti** **nástrojů** > . V dialogovém okně **Možnosti** rozbalte **položku Projekty a řešení**, vyberte **obecné**a zrušte zaškrtnutí **políčka Zobrazit pokročilé konfigurace sestavení.** To vám dává ruční kontrolu nad všechny hodnoty konfigurace a zda je vytvořena ladicí nebo vyvolaná verze.

 **Výchozí jazyk**

Určuje výchozí jazyk projektu. Možnost jazyka vybraná v ovládacím **panelu Hodiny, Jazyk a Oblast** určuje preferovaný jazyk uživatele. Zadáním výchozího jazyka pro projekt se ujistěte, že zadané výchozí jazykové prostředky jsou použity, pokud upřednostňovaný jazyk uživatele neodpovídá jazykovým prostředkům poskytnutým v aplikaci.

## <a name="debug-page"></a>Ladicí stránka

Následující možnosti slouží k nastavení vlastností pro ladění chování v projektu.

> [!NOTE]
> Některé možnosti jsou k dispozici pouze v aplikacích UPW.

 **Ladicí program ke spuštění**

Určuje výchozího hostitele ladicího programu.

- Chcete-li spustit aplikaci v hostitelském počítači sady Visual Studio, vyberte **možnost Místní počítač.** Další informace naleznete v tématu [Spouštění aplikací v místním počítači](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

- Vyberte **Simulátor** pro spuštění aplikace v simulátoru. Další informace naleznete [v tématu Spouštění aplikací v simulátoru](../../debugger/run-windows-store-apps-in-the-simulator.md).

- Chcete-li spustit aplikaci ve vzdáleném počítači, vyberte **možnost Vzdálený počítač.** Další informace o vzdáleném ladění naleznete v tématu [Spouštění aplikací ve vzdáleném počítači](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

**Spustit aplikaci**

Určuje, zda má být aplikace spouštěna po stisknutí klávesy **F5** nebo při **klepnutí** > na tlačítko Ladění**spouštět ladění**. Chcete-li aplikaci spustit, vyberte **možnost Ano.** v opačném případě vyberte **možnost Ne**. Pokud vyberete **možnost Ne**, můžete aplikaci ladit, pokud k jeho spuštění použijete jinou metodu.

**Typ ladicího programu**

Určuje typy kódu, který má být ladit. Chcete-li ladit kód javascriptu, vyberte **možnost Pouze skript.** Chcete-li ladit kód, který je spravován běžným jazykem, vyberte **možnost Pouze spravované.** Chcete-li ladit kód jazyka C++, vyberte **možnost Pouze nativní.** Chcete-li ladit C++ a JavaScript, vyberte **nativní pomocí skriptu.** Vyberte **Smíšené (spravované a nativní)** pro ladění spravovaného i c++ kódu.

**Povolit zpětnou vazbu místní sítě**

Určuje, zda je pro testování aplikací povolen přístup k adrese zpětné smyčky IP. Výběrem **možnosti Ano** povolíte použití adresy zpětné smyčky, pokud je klientská aplikace ve stejném počítači, ve kterém je spuštěna serverová aplikace; v opačném případě vyberte **možnost Ne**. Tato vlastnost je k dispozici pouze v případě, že je vlastnost **Debugger to Launch** nastavena na **vzdálené počítače**.

**Název počítače**

Určuje název vzdáleného počítače, který má být hostitelem ladicího programu. Tato vlastnost je k dispozici pouze **v případě, že debugger ke spuštění** je nastavena na vzdálené **počítače**.

**Vyžadovat ověření**

Určuje, zda vzdálený počítač vyžaduje ověření. Tato vlastnost je k dispozici pouze **v případě, že debugger ke spuštění** je nastavena na vzdálené **počítače**.
