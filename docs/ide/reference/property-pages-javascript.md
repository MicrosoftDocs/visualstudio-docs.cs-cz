---
title: Stránky vlastností, JavaScript
description: Přečtěte si, jak stránky vlastností poskytují přístup k nastavení projektu a jak použít stránky, které se zobrazí na stránkách vlastností pro změnu vlastností projektu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: cf6c984715f5cd35f08bb75526346b68c11dbeb9
ms.sourcegitcommit: a7944c325bedd8efbb244452741864089a02f5db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2020
ms.locfileid: "91947801"
---
# <a name="property-pages-javascript"></a>Stránky vlastností, JavaScript

**Stránky vlastností** poskytují přístup k nastavení projektu. Můžete použít stránky, které se zobrazí na **stránkách vlastností** , chcete-li změnit vlastnosti projektu.

Chcete-li získat přístup k vlastnostem projektu, vyberte uzel projektu v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Na **stránkách vlastností**se zobrazí následující stránky a možnosti.

## <a name="configuration-and-platform-page"></a>Stránka konfigurace a platforma

Pomocí následujících možností vyberte konfiguraci a platformu, které chcete zobrazit nebo upravit.

 **Konfigurace**

Určuje nastavení konfigurace, která se mají zobrazit nebo upravit. Nastavení jsou **ladění** (výchozí), **vydaná verze**, **všechny konfigurace**nebo uživatelsky definovaná konfigurace. Další informace naleznete v tématu [How to: set Debug and Release Configurations in Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Platforma**

Určuje nastavení platformy, která se mají zobrazit nebo upravit. Nastavení jsou **všechny procesory** (výchozí pro [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] aplikace), **x64**, **ARM**, **x86**nebo uživatelsky definované platformy. Další informace naleznete v tématu [How to: set Debug and Release Configurations in Visual Studio](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Stránka Obecné

Pomocí následujících možností nastavte obecné vlastnosti projektu.

> [!NOTE]
> Některé možnosti jsou dostupné jenom v aplikacích pro UWP.

 **Výstupní cesta**

Určuje umístění výstupních souborů pro konfiguraci projektu. Cesta je relativní; Pokud zadáte absolutní cestu, absolutní cesta je uložena v projektu. Výchozí cesta je bin\Debug.

Použijete-li zjednodušené konfigurace sestavení, systém projektu určí, zda má být vytvořena verze ladění nebo vydání. Po kliknutí na **ladění**  >  **Spustit ladění** (nebo stisknutím klávesy **F5**) je sestavení vloženo do umístění ladění bez ohledu na **výstupní cestu** , kterou zadáte. Příkaz **Sestavit řešení** v nabídce **sestavení** však vloží do umístění, které zadáte. Chcete-li povolit pokročilé konfigurace sestavení, na panelu nabídek vyberte možnost **nástroje**  >  **Možnosti**. V dialogovém okně **Možnosti** rozbalte položku **projekty a řešení**, vyberte možnost **Obecné**a zrušte zaškrtnutí políčka **Zobrazit pokročilé konfigurace sestavení** . Tím získáte ruční kontrolu nad všemi konfiguračními hodnotami a zda je vytvořena verze ladění nebo vydání.

 **Výchozí jazyk**

Určuje výchozí jazyk pro projekt. Možnost jazyka vybraná v části **hodiny, jazyk a oblast** v Ovládacích panelech určuje preferovaný jazyk uživatele. Zadáním výchozího jazyka pro projekt se ujistěte, že zadané výchozí jazykové prostředky budou použity, pokud preferovaný jazyk uživatele neodpovídá jazykovým prostředkům uvedeným v aplikaci.

## <a name="debug-page"></a>Ladit stránku

Pomocí následujících možností nastavte vlastnosti pro chování ladění v projektu.

> [!NOTE]
> Některé možnosti jsou dostupné jenom v aplikacích pro UWP.

 **Spuštění ladicího programu**

Určuje výchozího hostitele pro ladicí program.

- Vyberte možnost **místní počítač** a spusťte tak aplikaci na hostitelském počítači sady Visual Studio. Další informace najdete v tématu [spuštění aplikací v místním počítači](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

- Vyberte **simulátor** pro spuštění aplikace v simulátoru. Další informace najdete v tématu [spuštění aplikací v simulátoru](../../debugger/run-windows-store-apps-in-the-simulator.md).

- Vyberte možnost **vzdálený počítač** a spusťte aplikaci ve vzdáleném počítači. Další informace o vzdáleném ladění najdete v tématu [spuštění aplikací na vzdáleném počítači](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

**Spustit aplikaci**

Určuje, jestli se má aplikace spustit, když stisknete klávesu **F5** nebo kliknete na **ladění**  >  **Spustit ladění**. Pokud chcete aplikaci spustit, vyberte **Ano** . v opačném případě vyberte možnost **ne**. Pokud vyberete **ne**, můžete aplikaci ladit i v případě, že ji chcete spustit pomocí jiné metody.

**Typ ladicího programu**

Určuje typy kódu pro ladění. Vyberte možnost **skript pouze** pro ladění kódu JavaScriptu. Možnost **spravovaná pouze** pro ladění kódu, který je spravován modulem CLR (Common Language Runtime). Vyberte možnost **nativní pouze** pro ladění kódu C++. Vyberte možnost **nativní pomocí skriptu** pro ladění C++ a JavaScript. Vyberte **smíšený (spravovaný a nativní)** pro ladění spravovaného i C++ kódu.

**Povolení zpětné smyčky místní sítě**

Určuje, jestli je pro testování aplikací povolený přístup k adrese zpětné smyčky IP. Pokud je klientská aplikace na stejném počítači, na kterém běží serverová aplikace, vyberte **Ano** , pokud chcete použít adresu zpětné smyčky. v opačném případě vyberte možnost **ne**. Tato vlastnost je k dispozici pouze v případě, že je vlastnost **ladicí program na spuštění** nastavena na hodnotu **vzdálený počítač**.

**Název počítače**

Určuje název vzdáleného počítače pro hostování ladicího programu. Tato vlastnost je k dispozici pouze v případě, že je **pro spuštění ladicího programu** nastaven **vzdálený počítač**.

**Vyžadovat ověření**

Určuje, zda vzdálený počítač vyžaduje ověření. Tato vlastnost je k dispozici pouze v případě, že je **pro spuštění ladicího programu** nastaven **vzdálený počítač**.
