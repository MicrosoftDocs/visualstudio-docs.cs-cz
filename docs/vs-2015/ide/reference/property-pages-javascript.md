---
title: Stránky vlastností, JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffb1298981481bde063de898dc81c02dad548888
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297834"
---
# <a name="property-pages-javascript"></a>Stránky vlastností, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Stránky vlastností**poskytují přístup k nastavení projektu. Můžete použít stránky, které se zobrazí na **stránkách vlastností** , chcete-li změnit vlastnosti projektu.

 Chcete-li získat přístup k vlastnostem projektu, vyberte uzel projektu v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Na **stránkách vlastností**se zobrazí následující stránky a možnosti.

## <a name="configuration-and-platform-page"></a>Stránka konfigurace a platforma
 Pomocí následujících možností vyberte konfiguraci a platformu, které chcete zobrazit nebo upravit.

 **Konfigurace** Určuje nastavení konfigurace, která se mají zobrazit nebo upravit. Nastavení jsou **ladění** (výchozí), **vydaná verze**, **všechny konfigurace**nebo uživatelsky definovaná konfigurace. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platforma** Určuje nastavení platformy, která se mají zobrazit nebo upravit. Nastavení jsou **všechny procesory** (výchozí pro [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace), **x64**, **ARM**, **x86**nebo uživatelsky definované platformy. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>Stránka Obecné
 Pomocí následujících možností nastavte obecné vlastnosti projektu.

> [!NOTE]
> Některé možnosti jsou k dispozici pouze v aplikacích pro Windows Store.

 **Výstupní cesta** Určuje umístění výstupních souborů pro konfiguraci projektu. Cesta je relativní; Pokud zadáte absolutní cestu, absolutní cesta je uložena v projektu. Výchozí cesta je bin\Debug.

 Použijete-li zjednodušené konfigurace sestavení, systém projektu určí, zda má být vytvořena verze ladění nebo vydání. Po kliknutí na položku **ladit**, **Spustit ladění** (nebo stiskněte klávesu F5) je sestavení vloženo do umístění ladění bez ohledu na **výstupní cestu** , kterou zadáte. Příkaz **Sestavit řešení** v nabídce **sestavení** však vloží do umístění, které zadáte. Chcete-li povolit pokročilé konfigurace sestavení, v řádku nabídek klikněte na položku **nástroje**, **Možnosti**. V dialogovém okně **Možnosti** rozbalte položku **projekty a řešení**, vyberte možnost **Obecné**a zrušte zaškrtnutí políčka **Zobrazit pokročilé konfigurace sestavení** . Tím získáte ruční kontrolu nad všemi konfiguračními hodnotami a zda je vytvořena verze ladění nebo vydání. Další informace naleznete v tématu [NIB: Obecné, projekty a řešení, dialogové okno Možnosti](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Výchozí jazyk** Určuje výchozí jazyk pro projekt. Možnost jazyka vybraná v části **hodiny, jazyk a oblast** v Ovládacích panelech určuje preferovaný jazyk uživatele. Zadáním výchozího jazyka pro projekt se ujistěte, že zadané výchozí jazykové prostředky budou použity, pokud preferovaný jazyk uživatele neodpovídá jazykovým prostředkům uvedeným v aplikaci.

## <a name="debug-page"></a>Ladit stránku
 Pomocí následujících možností nastavte vlastnosti pro chování ladění v projektu.

> [!NOTE]
> Některé možnosti jsou k dispozici pouze v aplikacích pro Windows Store.

 **Spuštění ladicího programu** Určuje výchozího hostitele pro ladicí program.

- Vyberte možnost **místní počítač** a spusťte tak aplikaci na hostitelském počítači sady Visual Studio. Další informace najdete v tématu [spuštění aplikací v místním počítači](https://go.microsoft.com/fwlink/?LinkId=234912).

- Vyberte **simulátor** pro spuštění aplikace v simulátoru. Další informace najdete v tématu [spuštění aplikací v simulátoru](https://go.microsoft.com/fwlink/?LinkId=234913).

- Vyberte možnost **vzdálený počítač** a spusťte aplikaci ve vzdáleném počítači. Další informace o vzdáleném ladění najdete v tématu [spuštění aplikací na vzdáleném počítači](https://go.microsoft.com/fwlink/?LinkId=234914).

  **Spustit aplikaci** Určuje, jestli se má aplikace spustit, když stisknete klávesu F5 nebo kliknete na **ladit**, **Spustit ladění**. Pokud chcete aplikaci spustit, vyberte **Ano** . v opačném případě vyberte možnost **ne**. Pokud vyberete **ne**, můžete aplikaci ladit i v případě, že ji chcete spustit pomocí jiné metody.

  **Typ ladicího programu** Určuje typy kódu pro ladění. Vyberte možnost **skript pouze** pro ladění kódu JavaScriptu. Možnost **spravovaná pouze** pro ladění kódu, který je spravován modulem CLR (Common Language Runtime). Vyberte možnost **nativní pouze** pro C++ ladění kódu. Vyberte možnost **nativní pomocí skriptu** pro C++ ladění a JavaScript. Vyberte **smíšený (spravovaný a nativní)** pro ladění spravovaného i C++ kódu.

  **Povolení zpětné smyčky místní sítě** Určuje, jestli je pro testování aplikací povolený přístup k adrese zpětné smyčky IP. Pokud je klientská aplikace na stejném počítači, na kterém běží serverová aplikace, vyberte **Ano** , pokud chcete použít adresu zpětné smyčky. v opačném případě vyberte možnost **ne**. Tato vlastnost je k dispozici pouze v případě, že je vlastnost **ladicí program na spuštění** nastavena na hodnotu **vzdálený počítač**.

  **Název počítače** Určuje název vzdáleného počítače pro hostování ladicího programu. Tato vlastnost je k dispozici pouze v případě, že je **pro spuštění ladicího programu** nastaven **vzdálený počítač**.

  **Vyžadovat ověření** Určuje, zda vzdálený počítač vyžaduje ověření. Tato vlastnost je k dispozici pouze v případě, že je **pro spuštění ladicího programu** nastaven **vzdálený počítač**.
