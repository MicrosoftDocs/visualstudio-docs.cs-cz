---
title: Stránka Kompilovat, návrhář projektu (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9ffdfe4abbef5701cc060171ecbc379ae3a9215
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284314"
---
# <a name="compile-page-project-designer-visual-basic"></a>Stránka Kompilovat, návrhář projektu (Visual Basic)

K určení instrukcí kompilace použijte stránku **kompilovat** Návrháře projektu. Na této stránce můžete také zadat rozšířené možnosti kompilátoru a události před sestavením nebo po sestavení.

Chcete-li získat přístup ke stránce **kompilovat** , vyberte uzel projektu (nikoli uzel **řešení** ) v **Průzkumník řešení**. Pak zvolte **projekt**, **vlastnosti** na řádku nabídek. Když se zobrazí Návrhář projektu, klikněte na kartu **kompilovat** .

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfigurace a platforma

Následující nastavení umožňují vybrat konfiguraci a platformu pro zobrazení nebo úpravu.

> [!NOTE]
> V případě zjednodušených konfigurací sestavení Určuje projektový systém, zda má být vytvořena verze ladění nebo vydání. Proto se seznamy **konfigurací** a **platforem** nezobrazují.

**Konfigurace**

Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení jsou **ladění** (výchozí), **vydání**nebo **všechny konfigurace**. Další informace naleznete v tématu [Principy konfigurací sestavení](../../ide/understanding-build-configurations.md) a [Postupy: vytváření a úpravy konfigurací](../../ide/how-to-create-and-edit-configurations.md).

**Platforma**

Určuje, která nastavení platformy se mají zobrazit nebo upravit. Můžete zadat **Libovolný procesor** (výchozí), **x64**nebo **x86**.

## <a name="compiler-configuration-options"></a>Možnosti konfigurace kompilátoru

Následující nastavení umožňují nastavit možnosti konfigurace kompilátoru.

**Výstupní cesta sestavení**

Určuje umístění výstupních souborů pro tuto konfiguraci projektu. Do tohoto pole zadejte cestu k výstupu sestavení nebo klikněte na tlačítko **Procházet** a vyberte cestu. Všimněte si, že cesta je relativní; Pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug\ nebo bin\Release \\ .

V případě zjednodušených konfigurací sestavení Určuje projektový systém, zda má být vytvořena verze ladění nebo vydání. Příkaz **Build** z nabídky **ladění** (F5) vloží sestavení do umístění ladění bez ohledu na **výstupní cestu** , kterou zadáte. Příkaz **Build** v nabídce **sestavení** však vloží do umístění, které zadáte.

**Možnost Explicit**

Určuje, zda má být povolena implicitní deklarace proměnných. Pokud chcete vyžadovat explicitní deklaraci proměnných, vyberte **zapnuto** . To způsobí, že kompilátor ohlásí chyby, pokud proměnné nejsou deklarovány dříve, než budou použity. Vyberte **vypnuto** pro povolení implicitní deklarace proměnných.

Toto nastavení odpovídá možnosti kompilátoru [/OptionExplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) .

Pokud soubor zdrojového kódu obsahuje [příkaz Option Explicit](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), `On` `Off` hodnota nebo v příkazu přepíše **možnost explicitní** nastavení na **stránce kompilovat**.

Při vytváření nového projektu je **možnost explicitní** nastavení na **stránce kompilovat** nastavena na hodnotu **explicitní nastavení možnosti** v dialogovém okně **Možnosti** . Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení **Možnosti Explicit** ve výchozím nastavení **VB** je **zapnuté**.

**Možnost nastavení explicitní** na `Off` není obvykle dobrým zvykem. V jednom nebo více umístěních byste mohli nastavovat navýšení názvu proměnné, což způsobí, že při spuštění programu dojde k neočekávaným výsledkům.

**Možnost Strict**

Určuje, zda se má vynutila striktní Sémantika typu. Pokud je nastavená **možnost Strict** **, v následujících**podmínkách dojde k chybě při kompilaci:

- Implicitní zužující převody

- Pozdní vazba

- Implicitní zadání, které má za následek `Object` typ

K implicitnímu zužujícímu chybám konverze dojde, pokud je k dispozici implicitní převod datového typu, který představuje zužující převod. Další informace naleznete v tématu [Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [implicitní a explicitní převody](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)a [rozšiřování a zúžení převodů](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Objekt je pozdní vazbou, je-li přiřazen k vlastnosti nebo metodě proměnné, která je deklarována jako typ `Object` . Další informace najdete v tématu [příkaz Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement) a v [počáteční a pozdní vazbě](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

K chybám implicitního typu objektu dojde v případě, že příslušný typ nelze odvodit pro deklarovanou proměnnou, takže typ `Object` je odvozený. K tomu primárně dochází, když použijete `Dim` příkaz k deklaraci proměnné bez použití `As` klauzule a `Option Infer` je vypnuta. Další informace naleznete v tématu [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option include Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)a [Visual Basic Language Specification](/dotnet/visual-basic/reference/language-specification).

**Možnost Strict** nastavení odpovídá možnosti kompilátoru [/OptionStrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) .

Pokud soubor zdrojového kódu obsahuje [příkaz Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement), `On` `Off` hodnota nebo v příkazu přepisuje nastavení **Option Strict** na **stránce kompilovat**.

Při vytváření projektu je **možnost striktní** nastavení na **stránce kompilovat** nastavena na hodnotu **Option Strict** v dialogovém okně **Možnosti** . Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení **Možnosti Strict** ve **výchozích hodnotách VB** je **vypnuto**.

**Možnost striktní jednotlivá upozornění**

Oddíl **Konfigurace upozornění** **stránky kompilace** obsahuje nastavení, která odpovídají třem podmínkám, které způsobují chybu při kompilaci, pokud `Option Strict` je zapnutá. Tato nastavení jsou následující:

- **Implicitní převod**

- **Pozdní vazba; volání může v době běhu selhat.**

- **Implicitní typ; Předpokládá se objekt**

Pokud nastavíte **možnost Strict** na **zapnuto**, všechna tři tato nastavení konfigurace upozornění jsou nastavená na hodnotu **Chyba**. Pokud nastavíte **možnost Strict** na **vypnuto**, všechna tři nastavení budou nastavena na **hodnotu žádná**.

Každé nastavení konfigurace upozornění můžete jednotlivě změnit na **žádné**, **varování**nebo **Chyba**. Pokud jsou všechna tři nastavení konfigurace upozornění nastavena na hodnotu **Chyba**, `On` zobrazí se v `Option strict` poli. Pokud jsou všechny tři nastaveny na **možnost žádné**, `Off` zobrazí se v tomto poli. Pro jakoukoli jinou kombinaci těchto nastavení se zobrazí **(vlastní)** .

**Možnost Compare**

Určuje typ porovnání řetězce, který se má použít. Vyberte **binární soubor** , chcete-li kompilátoru dát pokyn k použití binárního porovnávání řetězců s rozlišováním velkých a malých písmen. Vyberte **text** , který bude používat porovnávání textových řetězců bez rozlišení malých a velkých písmen specifických pro národní prostředí.

Toto nastavení odpovídá možnosti kompilátoru [/OptionCompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) .

Pokud soubor zdrojového kódu obsahuje [příkaz Option Compare](/dotnet/visual-basic/language-reference/statements/option-compare-statement), `Binary` `Text` hodnota nebo v příkazu přepíše nastavení **Možnosti Compare** na **stránce kompilovat**.

Při vytváření projektu je **možnost porovnat** nastavení na **stránce kompilovat** nastavena na hodnotu nastavení **Možnosti Compare** v dialogovém okně **Možnosti** . Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení **Možnosti porovnat** ve výchozím nastavení **VB** je **binární**.

**Odvoditelné možnosti**

Určuje, zda má být v deklaracích proměnných povolen odvození místního typu. Výběrem **na** povolíte použití odvození místního typu. Pokud chcete blokovat odvození místního typu, vyberte **vypnuto** .

Toto nastavení odpovídá možnosti kompilátoru [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer) .

Pokud soubor zdrojového kódu obsahuje [příkaz Option](/dotnet/visual-basic/language-reference/statements/option-infer-statement), `On` `Off` přepíše hodnota nebo v příkazu **možnost odvoditelné** nastavení na **stránce kompilovat**.

Při vytváření projektu je **možnost odvodit** nastavení na **stránce kompilovat** nastavena na hodnotu nastavení **odvoditelné možnosti** v dialogovém okně **Možnosti** . Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klikněte v nabídce **nástroje** na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení **Možnosti odvozeno** ve **výchozím nastavení VB** je **zapnuto**.

**Cílový procesor**

Určuje procesor, na který má výstupní soubor cílit. Určete **x86** pro jakýkoli 32 procesor kompatibilní s procesorem Intel, **x64** pro libovolný 64 procesor kompatibilní s procesorem Intel, **ARM** pro libovolný procesor ARM nebo **libovolný** procesor, který určí, že libovolný procesor je přijatelný. **Libovolný procesor** je výchozí hodnotou pro nové projekty, protože umožňuje spuštění aplikace na největším počtu typů hardwaru.

Další informace najdete v tématu [/Platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**Preferovat 32 – bit**

Pokud je zaškrtnuto políčko **Prefer32-bit** , aplikace běží jako 32ová aplikace v 32 i v 64 bitových verzích systému Windows. V opačném případě bude aplikace spuštěna jako 32ová aplikace v 32 verzích systému Windows a jako aplikace 64 64 v systému Windows v 16bitovém verzích.

Spuštění jako 64 aplikace zdvojnásobí velikost ukazatele a může způsobit problémy s kompatibilitou s knihovnami, které jsou výhradně 32 bitů. Má smysl spustit aplikaci jako 64, pouze pokud je výrazně rychlejší nebo potřebuje více než 4 GB paměti.

Toto zaškrtávací políčko je k dispozici pouze v případě, že jsou splněné všechny následující podmínky:

- Na **stránce kompilovat**je cílový seznam **procesorů** nastavený na **Libovolný procesor**.

- Na **stránce aplikace**seznam **Typ aplikace** určuje, že projekt je aplikace.

- Na **stránce aplikace**se v seznamu **cílový rámec** určuje .NET Framework 4,5.

**Konfigurace upozornění**

V této tabulce jsou uvedeny podmínky sestavení a odpovídající úroveň oznámení pro **každý z nich**, **Upozornění**nebo **Chyba** .

Ve výchozím nastavení jsou všechna upozornění kompilátoru přidána do Seznam úkolů během kompilace. Vyberte **Zakázat všechna upozornění** , aby kompilátor vydával upozornění nebo chyby. Vyberte možnost **považovat všechna upozornění za chyby** , pokud chcete, aby kompilátor považoval upozornění jako chyby, které je nutné opravit.

**Zakázat všechna upozornění**

Určuje, jestli má kompilátor vystavovat oznámení uvedená v tabulce **podmínky a oznámení** popsané dříve v tomto dokumentu. Ve výchozím nastavení je toto políčko zaškrtnuto. Zaškrtněte toto políčko, pokud chcete kompilátoru dát pokyn, aby nemohly vystavovat upozornění nebo chyby.

Toto nastavení odpovídá možnosti kompilátoru [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) .

**Považovat všechna upozornění za chyby**

Určuje, jak považovat upozornění. Ve výchozím nastavení toto políčko není zaškrtnuté, takže všechna oznámení upozornění zůstanou nastavená na **varování**. Zaškrtnutím tohoto políčka změníte všechna upozornění na **chyby**.

Tato možnost je k dispozici pouze v případě, že je zaškrtnuto políčko **Zakázat všechna upozornění** .

**Generovat soubor dokumentace XML**

Určuje, zda se má generovat informace dokumentace. Ve výchozím nastavení je toto zaškrtávací políčko zaškrtnuto a dává kompilátoru pokyn, aby vygeneroval informace dokumentace a zahrnul je do souboru XML. Zrušením zaškrtnutí tohoto políčka dáte pokyn kompilátoru, aby nevytvořil dokumentaci.

Toto nastavení odpovídá možnosti kompilátoru [/doc](/dotnet/visual-basic/reference/command-line-compiler/doc) .

**Registrovat pro zprostředkovatele komunikace s objekty COM**

Určuje, jestli bude vaše spravovaná aplikace vystavovat objekt COM (obálka s podporou modelu COM), která umožňuje objektu COM interakci s aplikací.

Ve výchozím nastavení toto políčko není zaškrtnuto, což znamená, že aplikace nebude umožňovat zprostředkovatele komunikace s objekty COM. Zaškrtnutím tohoto políčka povolíte zprostředkovatele komunikace s objekty COM.

Tato možnost není k dispozici pro projekty aplikace nebo konzolové aplikace systému Windows.

**Události sestavení**

Klikněte na toto tlačítko pro přístup k dialogovému oknu **události sestavení** . Pomocí tohoto dialogového okna můžete zadat pokyny pro konfiguraci před sestavením a po sestavení pro projekt. Toto dialogové okno se vztahuje pouze na Visual Basic projekty. Další informace najdete v [dialogovém okně události sestavení (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

**Pokročilé možnosti kompilace**

Kliknutím na toto tlačítko otevřete dialogové okno **Nastavení AdvancedCompiler** . Dialogové okno **Nastavení AdvancedCompiler** slouží k určení rozšířených vlastností konfigurace sestavení projektu. Toto dialogové okno se vztahuje pouze na Visual Basic projekty. Další informace najdete v tématu [dialogové okno Upřesnit nastavení kompilátoru (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="see-also"></a>Viz také

- [Postupy: Určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Visual Basic Kompilátor příkazového řádku](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Postupy: Vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md)
