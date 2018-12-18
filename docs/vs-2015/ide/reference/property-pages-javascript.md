---
title: Stránky vlastností, JavaScript | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 586ad4352dfdf88aef87d4f9c815a776f85a6a82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904190"
---
# <a name="property-pages-javascript"></a>Stránky vlastností, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Stránky vlastností**poskytuje přístup k nastavení projektu. Můžete použít stránky, které se zobrazují v **stránky vlastností** Chcete-li změnit vlastnosti projektu.  
  
 Pro přístup k vlastnostem projektu, vyberte uzel projektu v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
 Následující stránky a možnosti se zobrazí v **stránky vlastností**.  
  
## <a name="configuration-and-platform-page"></a>Stránka Konfigurace a platforma  
 Vybrat konfigurace a platformy, zobrazit nebo upravit pomocí následujících možností.  
  
 **Konfigurace**  
 Určuje nastavení konfigurace má být zobrazeno nebo upraveno. Nastavení musí být **ladění** (výchozí), **vydání**, **všechny konfigurace**, nebo konfigurace definovaná uživatelem. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Platforma**  
 Určuje nastavení platformy má být zobrazeno nebo upraveno. Nastavení musí být **jakýkoli procesor** (výchozí pro [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] aplikace), **x64**, **ARM**, **x86**, nebo platforma definovaná uživatelem. Další informace najdete v tématu [konfigurace ladění a verzí projektu](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="general-page"></a>Obecná stránka  
 Pomocí následujících možností můžete nastavit obecné vlastnosti projektu.  
  
> [!NOTE]
>  Některé možnosti jsou dostupné jenom v aplikacích Windows Store.  
  
 **Výstupní cesta**  
 Určuje umístění výstupních souborů pro konfiguraci projektu. Cesta je relativní; Pokud zadáte absolutní cestu, absolutní cesta je uložena v projektu. Výchozí cesta je bin\Debug.  
  
 Při použití zjednodušených konfigurací sestavení systém projektu určuje, jestli se má sestavení ladění nebo vydání verze. Po kliknutí na **ladění**, **spustit ladění** (nebo stiskněte klávesu F5) je sestavení umístěno do místa ladění bez ohledu **výstupní cesta** zadáte. Ale **sestavit řešení** příkaz **sestavení** nabídky se vloží do umístění, které zadáte. Chcete-li povolit pokročilé konfigurace sestavení, na panelu nabídek zvolte **nástroje**, **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**vyberte **Obecné**a poté zrušte zaškrtnutí **zobrazit pokročilé konfiguracesestavení**zaškrtávací políčko. To umožňuje ruční kontrolu všech hodnot konfigurace a určuje, zda je sestavena verze ladění nebo vydání. Další informace najdete v tématu [NIB: Obecné, projekty a řešení, dialogové okno Možnosti](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
 **Výchozí jazyk**  
 Určuje výchozí jazyk pro projekt. Jazykové možnosti vybrané v **hodiny, jazyk a oblast** v Ovládacích panelech určuje upřednostňovaný jazyk uživatele. Zadáním výchozího jazyka pro projekt, ujistěte se, že zadané výchozí jazykové prostředky se používají Pokud preferovaný jazyk uživatele neodpovídá jazykovým prostředkům poskytovaným v aplikaci.  
  
## <a name="debug-page"></a>Stránka ladit  
 Pomocí následujících možností můžete nastavit vlastnosti pro ladění chování v projektu.  
  
> [!NOTE]
>  Některé možnosti jsou dostupné jenom v aplikacích Windows Store.  
  
 **Spustit ladicí program**  
 Určuje výchozího hostitele pro ladicí program.  
  
- Vyberte **místního počítače** a spusťte tak aplikaci v hostitelském počítači Visual Studio. Další informace najdete v tématu [spouštění aplikací v místním počítači](http://go.microsoft.com/fwlink/?LinkId=234912).  
  
- Vyberte **simulátor** a spusťte tak aplikaci v simulátoru. Další informace najdete v tématu [spouštění aplikací v simulátoru](http://go.microsoft.com/fwlink/?LinkId=234913).  
  
- Vyberte **vzdálený počítač** a spusťte tak aplikaci ve vzdáleném počítači. Další informace o vzdáleném ladění naleznete v tématu [spouštění aplikací ve vzdáleném počítači](http://go.microsoft.com/fwlink/?LinkId=234914).  
  
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



