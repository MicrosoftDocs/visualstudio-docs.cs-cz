---
title: Stránka Kompilovat, Návrhář projektu (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 65
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db830e04388b7465c941e2fdf069b49f98951a1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660829"
---
# <a name="compile-page-project-designer-visual-basic"></a>Stránka Kompilovat, návrhář projektu (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

K určení instrukcí kompilace použijte stránku **kompilovat** Návrháře projektu. Na této stránce můžete také zadat rozšířené možnosti kompilátoru a události před sestavením nebo po sestavení.

 Chcete-li získat přístup ke stránce **kompilovat** , vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **projekt**, **vlastnosti** na řádku nabídek. Když se zobrazí Návrhář projektu, klikněte na kartu **kompilovat** .

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="configuration-and-platform"></a>Konfigurace a platforma
 Následující nastavení umožňují vybrat konfiguraci a platformu pro zobrazení nebo úpravu.

> [!NOTE]
> V případě zjednodušených konfigurací sestavení Určuje projektový systém, zda má být vytvořena verze ladění nebo vydání. Proto se seznamy **konfigurací** a **platforem** nezobrazují. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Konfigurace** Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení jsou **ladění** (výchozí), **vydání**nebo **všechny konfigurace**. Další informace naleznete v tématech [ladění a vydání konfigurace projektu](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) a [Postupy: vytváření a úpravy konfigurací](../../ide/how-to-create-and-edit-configurations.md).

 **Platforma** Určuje, která nastavení platformy se mají zobrazit nebo upravit. Můžete zadat **Libovolný procesor** (výchozí), **x64**nebo **x86**. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="compiler-configuration-options"></a>Možnosti konfigurace kompilátoru
 Následující nastavení umožňují nastavit možnosti konfigurace kompilátoru.

 **Výstupní cesta sestavení** Určuje umístění výstupních souborů pro tuto konfiguraci projektu. Do tohoto pole zadejte cestu k výstupu sestavení nebo klikněte na tlačítko **Procházet** a vyberte cestu. Všimněte si, že cesta je relativní; Pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug\ nebo bin\Release \\. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 V případě zjednodušených konfigurací sestavení Určuje projektový systém, zda má být vytvořena verze ladění nebo vydání. Příkaz **Build** z nabídky **ladění** (F5) vloží sestavení do umístění ladění bez ohledu na **výstupní cestu** , kterou zadáte. Příkaz **Build** v nabídce **sestavení** však vloží do umístění, které zadáte. Další informace naleznete v tématu [Konfigurace projektů ladění a vydávání](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Možnost Explicit** Určuje, zda má být povolena implicitní deklarace proměnných. Pokud chcete vyžadovat explicitní deklaraci proměnných, vyberte **zapnuto** . To způsobí, že kompilátor ohlásí chyby, pokud proměnné nejsou deklarovány dříve, než budou použity. Vyberte **vypnuto** pro povolení implicitní deklarace proměnných.

 Toto nastavení odpovídá možnosti kompilátoru [/OptionExplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) .

 Pokud soubor zdrojového kódu obsahuje [příkaz Option Explicit](https://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc), hodnota `On` nebo `Off` v příkazu přepíše **možnost explicitní** nastavení na **stránce kompilovat**.

 Při vytváření nového projektu je **možnost explicitní** nastavení na **stránce kompilovat** nastavena na hodnotu **explicitní nastavení možnosti** v dialogovém okně **Možnosti** . Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení **Možnosti Explicit** ve výchozím nastavení **VB** je **zapnuté**.

 **Možnost nastavení explicitní** na `Off` není většinou dobrým zvykem. V jednom nebo více umístěních byste mohli nastavovat navýšení názvu proměnné, což způsobí, že při spuštění programu dojde k neočekávaným výsledkům.

 **Možnost Strict** Určuje, zda se má vynutila striktní Sémantika typu. Pokud je nastavená **možnost Strict** **, v následujících**podmínkách dojde k chybě při kompilaci:

- Implicitní zužující převody

- Pozdní vazba

- Implicitní zadání, které má za následek `Object` typ

  K implicitnímu zužujícímu chybám konverze dojde, pokud je k dispozici implicitní převod datového typu, který představuje zužující převod. Další informace naleznete v tématu [Option Strict](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [implicitní a explicitní převody](https://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66)a [rozšiřování a zúžení převodů](https://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd).

  Objekt je pozdní vazbou, je-li přiřazen k vlastnosti nebo metodě proměnné, která je deklarována jako typu `Object`. Další informace najdete v tématu [příkaz Option Strict](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5) a v [počáteční a pozdní vazbě](https://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724).

  K chybám implicitního typu objektu dojde v případě, že příslušný typ nelze odvodit pro deklarovanou proměnnou, takže typ `Object` je odvozený. K tomu primárně dochází, když použijete příkaz `Dim` k deklaraci proměnné bez použití klauzule `As` a `Option Infer` je vypnutá. Další informace naleznete v tématu [Option Strict Statement](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), [Option include Statement](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)a [Visual Basic Language Specification](https://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df).

  **Možnost Strict** nastavení odpovídá možnosti kompilátoru [/OptionStrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) .

  Pokud soubor zdrojového kódu obsahuje [příkaz Option Strict](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5), hodnota `On` nebo `Off` v příkazu přepisuje nastavení **Option Strict** na **stránce kompilovat**.

  Při vytváření projektu je **možnost striktní** nastavení na **stránce kompilovat** nastavena na hodnotu **Option Strict** v dialogovém okně **Možnosti** . Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení **Možnosti Strict** ve **výchozích hodnotách VB** je **vypnuto**.

  **Možnost striktní jednotlivá upozornění** Oddíl **Konfigurace upozornění** **stránky kompilace** obsahuje nastavení, která odpovídají třem podmínkám, které způsobují chybu při kompilaci, pokud je `Option Strict` zapnutá. Tato nastavení jsou následující:

- **Implicitní převod**

- **Pozdní vazba; volání může v době běhu selhat.**

- **Implicitní typ; Předpokládá se objekt**

  Pokud nastavíte **možnost Strict** na **zapnuto**, všechna tři tato nastavení konfigurace upozornění jsou nastavená na hodnotu **Chyba**. Pokud nastavíte **možnost Strict** na **vypnuto**, všechna tři nastavení budou nastavena na **hodnotu žádná**.

  Každé nastavení konfigurace upozornění můžete jednotlivě změnit na **žádné**, **varování**nebo **Chyba**. Pokud jsou všechna tři nastavení konfigurace upozornění nastavená na hodnotu **Chyba**, `On` se zobrazí v poli `Option strict`. Pokud jsou všechny tři nastaveny na **hodnotu None**, `Off` se zobrazí v tomto poli. Pro jakoukoli jinou kombinaci těchto nastavení se zobrazí **(vlastní)** .

  **Možnost Compare** Určuje typ porovnání řetězce, který se má použít. Vyberte **binární soubor** , chcete-li kompilátoru dát pokyn k použití binárního porovnávání řetězců s rozlišováním velkých a malých písmen. Vyberte **text** , který bude používat porovnávání textových řetězců bez rozlišení malých a velkých písmen specifických pro národní prostředí.

  Toto nastavení odpovídá možnosti kompilátoru [/OptionCompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) .

  Pokud soubor zdrojového kódu obsahuje [příkaz Option Compare](https://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e), hodnota `Binary` nebo `Text` v příkazu přepíše nastavení **Možnosti Compare** na **stránce kompilovat**.

  Při vytváření projektu je **možnost porovnat** nastavení na **stránce kompilovat** nastavena na hodnotu nastavení **Možnosti Compare** v dialogovém okně **Možnosti** . Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení **Možnosti porovnat** ve výchozím nastavení **VB** je **binární**.

  **Odvoditelné možnosti** Určuje, zda má být v deklaracích proměnných povolen odvození místního typu. Výběrem **na** povolíte použití odvození místního typu. Pokud chcete blokovat odvození místního typu, vyberte **vypnuto** .

  Toto nastavení odpovídá možnosti kompilátoru [/optioninfer](https://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed) .

  Pokud soubor zdrojového kódu obsahuje [příkaz Option-include](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652), hodnota `On` nebo `Off` v příkazu přepíše nastavení **odvoditelné z možnosti** na **stránce kompilovat**.

  Při vytváření projektu je **možnost odvodit** nastavení na **stránce kompilovat** nastavena na hodnotu nastavení **odvoditelné možnosti** v dialogovém okně **Možnosti** . Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení **Možnosti odvozeno** ve **výchozím nastavení VB** je **zapnuto**.

  **Cílový procesor** Určuje procesor, na který má výstupní soubor cílit. Určete **x86** pro jakýkoli 32 procesor kompatibilní s procesorem Intel, **x64** pro libovolný 64 procesor kompatibilní s procesorem Intel, **ARM** pro libovolný procesor ARM nebo **libovolný** procesor, který určí, že libovolný procesor je přijatelný. **Libovolný procesor** je výchozí hodnotou pro nové projekty, protože umožňuje spuštění aplikace na největším počtu typů hardwaru.

  Další informace najdete v tématu [/Platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1).

  **Preferovat 32 – bit** Pokud je zaškrtnuto políčko **Prefer32-bit** , aplikace běží jako 32ová aplikace v 32 i v 64 bitových verzích systému Windows. V opačném případě bude aplikace spuštěna jako 32ová aplikace v 32 verzích systému Windows a jako aplikace 64 64 v systému Windows v 16bitovém verzích.

  Spuštění jako 64 aplikace zdvojnásobí velikost ukazatele a může způsobit problémy s kompatibilitou s knihovnami, které jsou výhradně 32 bitů. Má smysl spustit aplikaci jako 64, pouze pokud je výrazně rychlejší nebo potřebuje více než 4 GB paměti.

  Toto zaškrtávací políčko je k dispozici pouze v případě, že jsou splněné všechny následující podmínky:

- Na **stránce kompilovat**je cílový seznam **procesorů** nastavený na **Libovolný procesor**.

- Na **stránce aplikace**seznam **Typ aplikace** určuje, že projekt je aplikace.

- Na **stránce aplikace**se v seznamu **cílový rámec** určuje .NET Framework 4,5.

  **Konfigurace upozornění** V této tabulce jsou uvedeny podmínky sestavení a odpovídající úroveň oznámení pro **každý z nich**, **Upozornění**nebo **Chyba** .

  Ve výchozím nastavení jsou všechna upozornění kompilátoru přidána do Seznam úkolů během kompilace. Vyberte **Zakázat všechna upozornění** , aby kompilátor vydával upozornění nebo chyby. Vyberte možnost **považovat všechna upozornění za chyby** , pokud chcete, aby kompilátor považoval upozornění jako chyby, které je nutné opravit.

  **Zakázat všechna upozornění** Určuje, jestli má kompilátor vystavovat oznámení uvedená v tabulce **podmínky a oznámení** popsané dříve v tomto dokumentu. Ve výchozím nastavení je toto zaškrtávací políčko zrušeno. Zaškrtněte toto políčko, pokud chcete kompilátoru dát pokyn, aby nemohly vystavovat upozornění nebo chyby.

  Toto nastavení odpovídá možnosti kompilátoru [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) .

  **Považovat všechna upozornění za chyby** Určuje, jak považovat upozornění. Ve výchozím nastavení toto políčko není zaškrtnuté, takže všechna oznámení upozornění zůstanou nastavená na **varování**. Zaškrtnutím tohoto políčka změníte všechna upozornění na **chyby**.

  Tato možnost je k dispozici pouze v případě, že je zaškrtnuto políčko **Zakázat všechna upozornění** .

  **Generovat soubor dokumentace XML** Určuje, zda se má generovat informace dokumentace. Ve výchozím nastavení je toto zaškrtávací políčko zaškrtnuto a dává kompilátoru pokyn, aby vygeneroval informace dokumentace a zahrnul je do souboru XML. Zrušením zaškrtnutí tohoto políčka dáte pokyn kompilátoru, aby nevytvořil dokumentaci.

  Toto nastavení odpovídá možnosti kompilátoru [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65) .

  **Registrovat pro zprostředkovatele komunikace s objekty COM** Určuje, jestli bude vaše spravovaná aplikace vystavovat objekt COM (obálka s podporou modelu COM), která umožňuje objektu COM interakci s aplikací.

  Ve výchozím nastavení toto políčko není zaškrtnuto, což znamená, že aplikace nebude umožňovat zprostředkovatele komunikace s objekty COM. Zaškrtnutím tohoto políčka povolíte zprostředkovatele komunikace s objekty COM.

  Tato možnost není k dispozici pro projekty aplikace nebo konzolové aplikace systému Windows.

  **Události sestavení** Klikněte na toto tlačítko pro přístup k dialogovému oknu **události sestavení** . Pomocí tohoto dialogového okna můžete zadat pokyny pro konfiguraci před sestavením a po sestavení pro projekt. Toto dialogové okno se vztahuje pouze na Visual Basic projekty. Další informace najdete v [dialogovém okně události sestavení (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

  **Pokročilé možnosti kompilace** Kliknutím na toto tlačítko otevřete dialogové okno **Nastavení AdvancedCompiler** . Dialogové okno **Nastavení AdvancedCompiler** slouží k určení rozšířených vlastností konfigurace sestavení projektu. Toto dialogové okno se vztahuje pouze na Visual Basic projekty. Další informace najdete v tématu [dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Viz také
 [Ladění a vydávání konfigurací projektů](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) [Správa vlastností kompilace](https://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c) [Postupy: určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [Visual Basic kompilátoru příkazového řádku](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c) [Postupy: vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md)
