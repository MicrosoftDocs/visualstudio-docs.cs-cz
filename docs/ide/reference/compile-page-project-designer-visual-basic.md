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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7a97068b70a76dfe343de5fa68db77d2ce9781
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111303"
---
# <a name="compile-page-project-designer-visual-basic"></a>Stránka Kompilovat, návrhář projektu (Visual Basic)

Pomocí stránky **Kompilace** návrháře projektu určete pokyny kompilace. Můžete také zadat rozšířené možnosti kompilátoru a události před sestavením nebo po sestavení na této stránce.

Chcete-li získat přístup ke stránce **Kompilace,** zvolte uzel projektu (nikoli uzel **řešení)** v **Průzkumníku řešení**. Pak na řádku nabídek zvolte **Projekt**, **Vlastnosti.** Po zobrazení Návrháře projektů klikněte na kartu **Kompilace.**

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="configuration-and-platform"></a>Konfigurace a platforma

Následující nastavení umožňují vybrat konfiguraci a platformu, kterou chcete zobrazit nebo upravit.

> [!NOTE]
> U zjednodušených konfigurací sestavení systém projektu určuje, zda má být konto kvytvoření ladicí nebo vydané verze. Proto nejsou **zobrazeny** konfigurace a **platformy** seznamy.

**Konfigurace**

Určuje, která nastavení konfigurace se mají zobrazit nebo upravit. Nastavení jsou **Ladění** (výchozí), **Vydání**nebo **Všechny konfigurace**. Další informace naleznete [v tématu Principy konfigurací sestavení](../../ide/understanding-build-configurations.md) a [postup: Vytvoření a úpravy konfigurací](../../ide/how-to-create-and-edit-configurations.md).

**Platforma**

Určuje, které nastavení platformy se má zobrazit nebo upravit. Můžete zadat **libovolný procesor** (výchozí), **x64**nebo **x86**.

## <a name="compiler-configuration-options"></a>Možnosti konfigurace kompilátoru

Následující nastavení umožňují nastavit možnosti konfigurace kompilátoru.

**Vytvořit výstupní cestu**

Určuje umístění výstupních souborů pro konfiguraci tohoto projektu. Do tohoto pole zadejte cestu výstupu sestavení nebo klepnutím na tlačítko **Procházet** vyberte cestu. Všimněte si, že cesta je relativní; pokud zadáte absolutní cestu, bude uložena jako relativní. Výchozí cesta je bin\Debug\ nebo\\bin\Release .

U zjednodušených konfigurací sestavení systém projektu určuje, zda má být konto kvytvoření ladicí nebo vydané verze. Příkaz **Sestavení** z nabídky **Ladění** (F5) vloží sestavení do umístění ladění bez ohledu na zadanou **výstupní cestu.** Příkaz **Sestavení** z nabídky **Sestavení** jej však umístí do zadaného umístění.

**Možnost explicitní**

Určuje, zda má být povolena implicitní deklarace proměnných. Chcete-li vyžadovat explicitní deklaraci proměnných, vyberte **možnost Zapnuto.** To způsobí, že kompilátor hlásit chyby, pokud proměnné nejsou deklarovány před jejich použitím. Chcete-li povolit implicitní deklaraci proměnných, vyberte **možnost Vypnuto.**

Toto nastavení odpovídá možnosti kompilátoru [/optionexplicit.](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)

Pokud soubor zdrojového kódu obsahuje explicitní `On` `Off` [příkaz option](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), hodnota nebo v příkazu přepíše nastavení **Explicitní možnost** na **stránce Kompilace**.

Když vytvoříte nový projekt, nastavení **Explicitní možnost** na **stránce Kompilace** je nastaveno na hodnotu nastavení **Explicitní volba** v dialogovém okně **Možnosti.** Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klepněte v nabídce **Nástroje** na **příkaz Možnosti**. V dialogovém okně **Možnosti** rozbalte **položku Projekty a řešení**a klepněte na tlačítko **Výchozí hodnoty VB**. Počáteční výchozí nastavení **explicitně možnosti** ve **výchozím nastavení VB** je **Zapnuto**.

Nastavení **možnosti explicitní** `Off` na obecně není osvědčeným postupem. V jednom nebo více umístěních může být chybně zadán název proměnné, což by při spuštění programu mohlo způsobit neočekávané výsledky.

**Možnost striktní**

Určuje, zda má být vynucena smámantika přísného typu. Pokud je **možnost Strict** **zapnutá**, následující podmínky způsobují chybu v době kompilace:

- Implicitní zužující převody

- Pozdní vazba

- Implicitní psaní, které `Object` má za následek typ

Implicitní zužující se chyby převodu dojít, pokud je implicitní převod datového typu, který je zužující převod. Další informace naleznete [v tématu Příkaz striktní možnosti](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [implicitní a explicitní převody](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)a [rozšiřující a zužující převody](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).

Objekt je pozdě vázán, pokud je přiřazen k vlastnosti nebo metodě `Object`proměnné, která je deklarována jako typ . Další informace naleznete [v tématu Možnost strict prohlášení](/dotnet/visual-basic/language-reference/statements/option-strict-statement) a včasné a pozdní [vazby](/dotnet/visual-basic/programming-guide/language-features/early-late-binding).

K implicitním chybám typu objektu dochází, když pro deklarovanou proměnnou nelze odvodit příslušný typ, takže `Object` je odvozen typ. K tomu dochází především při `Dim` použití příkazu deklarovat proměnnou bez použití `As` klauzule a `Option Infer` je vypnuto. Další informace naleznete [v tématu Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), Option [Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)a Visual Basic Language [Specification](/dotnet/visual-basic/reference/language-specification).

Nastavení **Option Strict** odpovídá možnosti kompilátoru [/optionstrict.](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)

Pokud soubor zdrojového kódu obsahuje příkaz `On` `Off` [Striktní možnosti](/dotnet/visual-basic/language-reference/statements/option-strict-statement), hodnota nebo v příkazu přepíše nastavení **Striktní možnostna** **stránce Kompilace**.

Při vytváření projektu je nastavení **Přísné možnosti** na **stránce Kompilace** nastaveno na hodnotu nastavení **Striktní možnosti** v dialogovém okně **Možnosti.** Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klepněte v nabídce **Nástroje** na **příkaz Možnosti**. V dialogovém okně **Možnosti** rozbalte **položku Projekty a řešení**a klepněte na tlačítko **Výchozí hodnoty VB**. Počáteční výchozí nastavení **Option Strict** v Výchozí **vB** je **vypnuto**.

**Možnost Strict Individuální varování**

**Včásti Konfigurace upozornění** na **stránce Kompilace** obsahuje nastavení, která odpovídají třem `Option Strict` podmínkám, které způsobují chybu v době kompilace, když je zapnuto. Níže jsou uvedeny následující nastavení:

- **Implicitní převod**

- **Pozdní vazba; volání může selhat v době běhu**

- **Implicitní typ; předpokládá se objekt**

Pokud nastavíte **možnost Striktní** na **Zapnuto**, všechna tři tato nastavení konfigurace upozornění jsou **nastavena**na možnost Chyba . Pokud nastavíte **možnost Strict** to **Off**, všechna tři nastavení jsou **nastavena**na žádné .

Každé nastavení konfigurace upozornění můžete jednotlivě změnit na **žádné**, **Upozornění**nebo **Chyba**. Pokud jsou všechna tři nastavení konfigurace `On` upozornění `Option strict` **nastavena**na možnost Chyba , zobrazí se v poli. Pokud jsou všechny **None**tři `Off` nastaveny na žádný , zobrazí se v tomto poli. Pro jakoukoli jinou kombinaci těchto nastavení se zobrazí **(vlastní).**

**Porovnání možností**

Určuje typ porovnání řetězců, které má být používáno. Vyberte **binární** pokyn kompilátoru použít binární, malá a velká písmena porovnání řetězců. Vyberte **Text,** chcete-li použít porovnání textových řetězců specifických pro národní prostředí a malá a velká písmena.

Toto nastavení odpovídá možnosti kompilátoru [/optioncompare.](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)

Pokud soubor zdrojového kódu obsahuje příkaz `Binary` `Text` Pro [porovnání možností](/dotnet/visual-basic/language-reference/statements/option-compare-statement), hodnota nebo v příkazu přepíše nastavení **Porovnání možností** na **stránce Kompilace**.

Při vytváření projektu je nastavení **Porovnání možností** na **stránce Kompilace** nastaveno na hodnotu nastavení **Porovnání voleb** v dialogovém okně **Možnosti.** Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klepněte v nabídce **Nástroje** na **příkaz Možnosti**. V dialogovém okně **Možnosti** rozbalte **položku Projekty a řešení**a klepněte na tlačítko **Výchozí hodnoty VB**. Počáteční výchozí nastavení **porovnání možností** ve výchozím nastavení **VB** je **Binární**.

**Odvodit možnost**

Určuje, zda má být v deklaracích proměnných povolen odvození místního typu. Výběrem **možnosti Zapnuto** povolíte použití odvození místního typu. Chcete-li blokovat odvození místního typu, vyberte **možnost Vypnuto.**

Toto nastavení odpovídá možnosti kompilátoru [/optioninfer.](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)

Pokud soubor zdrojového kódu obsahuje příkaz `On` Option `Off` [Infer ,](/dotnet/visual-basic/language-reference/statements/option-infer-statement)hodnota nebo v příkazu přepíše nastavení **Option Infer** na **stránce Kompilace**.

Když vytváříte projekt, nastavení **Option Infer** na **stránce Kompilace** je nastaveno na hodnotu nastavení **Option Odvod v** dialogovém okně **Volby.** Chcete-li zobrazit nebo změnit nastavení v tomto dialogovém okně, klepněte v nabídce **Nástroje** na **příkaz Možnosti**. V dialogovém okně **Možnosti** rozbalte **položku Projekty a řešení**a klepněte na tlačítko **Výchozí hodnoty VB**. Počáteční výchozí nastavení **Option Infer** v **Výchozí hodnoty VB** je **Zapnuto**.

**Cílový procesor**

Určuje procesor, na který má výstupní soubor cílit. Zadejte **x86** pro libovolný 32bitový procesor kompatibilní s procesorem Intel, **x64** pro libovolný 64bitový procesor kompatibilní s procesorem Intel, **ARM** pro libovolný procesor ARM nebo **libovolný procesor,** který určí, že jakýkoli procesor je přijatelný. **Libovolný procesor** je výchozí hodnota pro nové projekty, protože umožňuje aplikaci spustit na největší počet typů hardwaru.

Další informace naleznete v tématu [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).

**Preferujte 32bitové**

Pokud je zaškrtnuté políčko **Prefer32bit,** aplikace se spustí jako 32bitová aplikace v 32bitových i 64bitových verzích systému Windows. V opačném případě je aplikace spuštěna jako 32bitová aplikace v 32bitových verzích systému Windows a jako 64bitová aplikace v 64bitových verzích systému Windows.

Spuštění jako 64bitová aplikace zdvojnásobuje velikost ukazatele a může způsobit problémy s kompatibilitou s knihovnami, které jsou výhradně 32bitové. Má smysl spustit aplikaci jako 64bitovou pouze v případě, že běží výrazně rychleji nebo potřebuje více než 4 GB paměti.

Toto zaškrtávací políčko je k dispozici pouze v případě, že jsou splněny všechny následující podmínky:

- Na **stránce Kompilace**je seznam **Cílový procesor** nastaven na **libovolný procesor**.

- Na **stránce Aplikace**určuje seznam **Typ aplikace,** že projekt je aplikace.

- Na **stránce aplikace**určuje seznam **Cílová architektura** rozhraní .NET Framework 4.5.

**Konfigurace upozornění**

V této tabulce jsou uvedeny podmínky sestavení a odpovídající úroveň oznámení **žádné**, **upozornění**nebo **chyba** pro každou z nich.

Ve výchozím nastavení jsou všechna upozornění kompilátoru přidána do seznamu úloh během kompilace. Vyberte **Zakázat všechna upozornění,** chcete-li kompilátoru dát pokyn, aby nevydával upozornění nebo chyby. Pokud chcete, aby kompilátor považoval upozornění za chyby, které musí být opraveny, vyberte **považovat všechna upozornění za chyby.**

**Zakázat všechna upozornění**

Určuje, zda má být kompilátoru povoleno vydávání oznámení, jak je uvedeno v tabulce **Podmínka a oznámení** popsané výše v tomto dokumentu. Ve výchozím nastavení je toto políčko zaškrtnuto. Zaškrtnutím tohoto políčka dáte kompilátoru pokyn, aby nevydával upozornění nebo chyby.

Toto nastavení odpovídá možnosti kompilátoru [/nowarn.](/dotnet/visual-basic/reference/command-line-compiler/nowarn)

**Považovat všechna upozornění za chyby**

Určuje způsob zacházení s upozorněními. Ve výchozím nastavení je toto políčko zaškrtnuto, takže všechna upozornění zůstanou nastavena na **možnost Upozornění**. Zaškrtnutím tohoto políčka změníte všechna upozornění na **Chyba**.

Tato možnost je k dispozici pouze v případě, že není zaškrtnuto **možnostI Zakázat všechna upozornění.**

**Generovat soubor dokumentace XML**

Určuje, zda má být generovány informace o dokumentaci. Ve výchozím nastavení je toto políčko zaškrtnuto a kompilátoru dává pokyn ke generování informací o dokumentaci a jejich zahrnutí do souboru XML. Zrušte zaškrtnutí tohoto políčka, chcete-li kompilátoru dát pokyn, aby nevytvářel dokumentaci.

Toto nastavení odpovídá možnosti kompilátoru [/doc.](/dotnet/visual-basic/reference/command-line-compiler/doc)

**Zaregistrovat se pro interop COM**

Určuje, zda spravovaná aplikace zpřístupní objekt COM (obálku s volatelnou com), který umožňuje objektu COM pracovat s aplikací.

Ve výchozím nastavení je toto políčko zaškrtnuto, což určuje, že aplikace nepovolí interop com. Zaškrtnutím tohoto políčka povolíte interop com.

Tato možnost není k dispozici pro projekty aplikací nebo konzolových aplikací systému Windows.

**Události sestavení**

Klepnutím na toto tlačítko získáte přístup k dialogovému oknu **Události sestavení.** Toto dialogové okno slouží k určení pokynů pro konfiguraci před sestavením a po sestavení pro projekt. Toto dialogové okno platí pouze pro projekty jazyka Visual Basic. Další informace naleznete v [tématu Sestavení dialogového okna události (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md).

**Rozšířené možnosti kompilace**

Klepnutím na toto tlačítko získáte přístup k dialogovému oknu **Upřesnit nastavení kompilátoru.** Dialogové okno **Upřesnit nastavení kompilátoru** slouží k určení rozšířených vlastností konfigurace sestavení projektu. Toto dialogové okno platí pouze pro projekty jazyka Visual Basic. Další informace naleznete v [dialogovém okně Upřesnit nastavení kompilátoru (Visual Basic).](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)

## <a name="see-also"></a>Viz také

- [Postupy: Určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilátor příkazového řádku jazyka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Postupy: Vytvoření a úprava konfigurací](../../ide/how-to-create-and-edit-configurations.md)
