---
title: Nastavení EditorConfig
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3aee4945b4a3b41a7f6ec532268c2c19f549d0a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301956"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Vytvoření přenosného nastavení vlastního editoru pomocí řešení EditorConfig

Soubor [EditorConfig](https://editorconfig.org/) můžete přidat do projektu nebo codebase vynutit konzistentní styly kódování pro všechny, kteří pracují v codebase. Nastavení EditorConfig má přednost před globálním nastavením textového editoru sady Visual Studio. To znamená, že můžete každý základ kódu přizpůsobit tak, aby se používala nastavení textového editoru, která jsou specifická pro daný projekt. V dialogovém okně **Možnosti** sady Visual Studio můžete stále nastavit vlastní předvolby osobního editoru. Tato nastavení platí vždy, když pracujete v základu kódu bez souboru *.editorconfig* nebo když soubor *.editorconfig* nepřepíše určité nastavení. Příkladem takové předvolby jsou&mdash;odsazení karet stylu nebo mezer.

Nastavení EditorConfig jsou podporovány mnoha editory kódu a IDE, včetně Visual Studio. Je to přenosná součást, která cestuje s vaším kódem a může vynutit styly kódování i mimo Visual Studio.

::: moniker range=">=vs-2019"

Když přidáte soubor EditorConfig do projektu v sadě Visual Studio, nové řádky kódu jsou formátovány podle nastavení EditorConfig. Formátování existujícího kódu se nezmění, pokud nespustíte jeden z následujících příkazů:

 - [Vyčištění kódu](../ide/code-styles-and-code-cleanup.md) (**Ctrl**+**K**, **Ctrl**+**E**), který použije všechna nastavení prázdného místa, například `using` styl odsazení, a vybraná nastavení stylu kódu, například jak seřadit direktivy.
 - **Upravit** > dokument **s rozšířeným** > **formátem** (nebo **Ctrl**+**K**, **Ctrl**+**D** ve výchozím profilu), který použije pouze nastavení prázdného místa, například styl odsazení.

 ::: moniker-end

::: moniker range="=vs-2017"

Když přidáte soubor EditorConfig do projektu v sadě Visual Studio, nové řádky kódu jsou formátovány podle nastavení EditorConfig. Formátování existujícího kódu se nezmění, pokud nespustíte dokument (**Upravit** > **dokument v rozšířeném** > **formátu** nebo **Ctrl**+**K**, **Ctrl**+**D** ve výchozím profilu). Formátování dokumentu ovlivní pouze nastavení prázdného místa, například styl odsazení, pokud jste nenakonfigurovali formátování dokumentu tak, aby [prováděl další vyčištění kódu](../ide/code-styles-and-code-cleanup.md#apply-code-styles).

 ::: moniker-end

::: moniker range="vs-2017"

Můžete definovat, která nastavení EditorConfig mají **formátovat dokument** použít na [stránce Možnosti **formátování** ](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu EditorConfig ve Visual Studiu for Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Konzistence kódu

Nastavení v souborech EditorConfig umožňují udržovat konzistentní styly kódování a nastavení v základu kódu, jako je styl odsazení, šířka karty, znaky konce řádku, kódování a další, bez ohledu na editor nebo rozhraní IDE, které používáte. Například při kódování v C#, pokud váš základ kódu má konvence přednost, že odsazení vždy skládá z pěti znaků mezer, dokumenty používají kódování UTF-8 a každý řádek vždy končí CR/LF, můžete nakonfigurovat soubor *.editorconfig* k tomu.

Konvence kódování, které používáte ve svých osobních projektech, se mohou lišit od těch, které se používají v projektech vašeho týmu. Můžete například dát přednost tomu, že při kódování přidá odsazení znak tabulátoru. Váš tým však může dát přednost tomu, aby odsazení přidalo čtyři znaky mezery namísto znaku karty. EditorConfig soubory vyřešit tento problém tím, že umožňuje mít konfiguraci pro každý scénář.

Vzhledem k tomu, že nastavení jsou obsaženy v souboru v základu kódu, cestují spolu s tímto základem kódu. Pokud otevřete soubor kódu v editoru kompatibilním s editorem EditorConfig, budou implementována nastavení textového editoru. Další informace o souborech EditorConfig naleznete na [webu EditorConfig.org.](https://editorconfig.org/)

> [!NOTE]
> Konvence, které jsou nastaveny v souboru EditorConfig nelze aktuálně vynutit v kanálu CI/CD jako chyby sestavení nebo upozornění. Všechny odchylky stylu se zobrazí pouze v editoru sady Visual Studio a **seznamu chyb**.

## <a name="supported-settings"></a>Podporovaná nastavení

Editor v sadě Visual Studio podporuje základní sadu [vlastností EditorConfig](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- konec\_of_line
- Charset
- trailing_whitespace\_oříznutí
- vložit\_final_newline
- kořen

Nastavení editoru EditorConfig jsou podporována ve všech jazycích podporovaných visual studio s výjimkou JAZYKA XML. Kromě toho EditorConfig podporuje konvence [stylu kódu,](../ide/editorconfig-code-style-settings-reference.md) včetně [jazyka](../ide/editorconfig-language-conventions.md), [formátování](../ide/editorconfig-formatting-conventions.md)a [konvence pojmenování](../ide/editorconfig-naming-conventions.md) pro C# a Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Přidání a odebrání souborů EditorConfig

Přidáte-li soubor EditorConfig do projektu nebo základu kódu, všechny nové řádky kódu, které napíšete, budou formátovány podle souboru EditorConfig. Přidání souboru EditorConfig však nepřevede existující styly na nové, dokud dokument nenaformátujete nebo nespustíte [vyčištění kódu](../ide/code-styles-and-code-cleanup.md). Pokud máte například v souboru odsazení, které jsou formátovány kartami, a přidáte soubor EditorConfig, který odsaze ní mezerami, znaky odsazení se automaticky nepřevedou na mezery. Při formátování dokumentu **(Upravit** > **dokument v rozšířeném** > **formátu** nebo **Ctrl**+**K**, **Ctrl**+**D)** se nastavení prázdného místa v souboru EditorConfig použije na existující řádky kódu.

Pokud odeberete soubor EditorConfig z projektu nebo základu kódu a chcete, aby byly nové řádky kódu formátovány podle globálního nastavení editoru, je nutné zavřít a znovu otevřít všechny otevřené soubory kódu.

### <a name="add-an-editorconfig-file-to-a-project"></a>Přidání souboru EditorConfig do projektu

1. Otevřete projekt nebo řešení v sadě Visual Studio. Vyberte uzel projektu nebo řešení v závislosti na tom, zda má nastavení *.editorconfig* použít pro všechny projekty v řešení nebo pouze jeden. Můžete také vybrat složku v projektu nebo řešení a přidat do ní soubor *.editorconfig.*

1. Na řádku nabídek zvolte Přidat**novou položku** **v Projectu** > nebo stiskněte **Ctrl**+**Shift**+**A**.

   Otevře se dialogové okno **Přidat novou položku.**

1. Ve vyhledávacím poli vyhledejte **editorconfig**.

   Ve výsledcích hledání jsou zobrazeny dvě šablony položek **editorconfig File.**

   ![Šablony položek souboru EditorConfig v sadě Visual Studio](media/editorconfig-item-templates.png)

1. Vyberte šablonu **editorconfig File (default),** chcete-li přidat předem vyplněný soubor EditorConfig se dvěma základními volbami EditorConfig pro styl a velikost odsazení. Nebo vyberte šablonu **editorconfig File (.NET),** chcete-li přidat soubor EditorConfig předem vyplněný výchozím [stylem kódu .NET, formátováním a konvencemi pojmenování](../ide/editorconfig-code-style-settings-reference.md).

   Soubor *.editorconfig* se zobrazí v Průzkumníku řešení a otevře se v editoru.

   ![Soubor .editorconfig v Průzkumníku řešení a v editoru](media/editorconfig-dotnet.png)

1. Upravte soubor podle potřeby.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Další způsoby přidání souboru EditorConfig

Existuje několik dalších způsobů, jak můžete do projektu přidat soubor EditorConfig:

- [Funkce odvození kódu](/visualstudio/intellicode/code-style-inference) IntelliCode pro Visual Studio odvodí styly kódu z existujícího kódu. Potom vytvoří neprázdný soubor EditorConfig s předvolbami stylu kódu, které jsou již definovány.

- Počínaje Visual Studio 2019, můžete [vygenerovat Soubor EditorConfig na základě nastavení stylu kódu](/visualstudio/ide/code-styles-and-code-cleanup#code-styles-in-editorconfig-files) v**možnosti** **nástroje** > .

## <a name="file-hierarchy-and-precedence"></a>Hierarchie souborů a priorita

Přidáte-li soubor *.editorconfig* do složky v hierarchii souborů, jeho nastavení se vztahuje na všechny příslušné soubory na této úrovni a níže. Můžete také přepsat EditorConfig nastavení pro konkrétní projekt, základ kódu nebo část základu kódu, tak, aby používá jiné konvence než jiné části codebase. To může být užitečné, když začleníte kód odjinud a nechcete změnit jeho konvence.

Chcete-li přepsat některá nebo všechna nastavení EditorConfig, přidejte soubor *.editorconfig* na úrovni hierarchie souborů, kterou chcete použít. Nové nastavení souboru EditorConfig platí pro soubory na stejné úrovni a všechny podadresáře.

![Hierarchie EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Pokud chcete přepsat některá, ale ne všechna nastavení, zadejte pouze tato nastavení v souboru *.editorconfig.* Přepsány jsou pouze vlastnosti, které explicitně uvádíte v souboru nižší úrovně. Další nastavení ze souborů *.editorconfig* vyšší úrovně nadále platí. Pokud chcete zajistit, aby v této části základu kódu _nebyla_ použita žádná nastavení _z_ žádných souborů *.editorconfig* vyšší úrovně, přidejte ```root=true``` vlastnost do souboru *editorconfig* nižší úrovně:

```ini
# top-most EditorConfig file
root = true
```

EditorConfig soubory jsou čteny shora dolů. Pokud existuje více vlastností se stejným názvem, má přednost naposledy nalezená vlastnost s tímto názvem.

## <a name="edit-editorconfig-files"></a>Upravit soubory EditorConfig

Visual Studio pomáhá upravovat *soubory .editorconfig* tím, že poskytuje seznamy dokončení Technologie IntelliSense.

![Technologie IntelliSense v souboru .editorconfig](media/editorconfig-intellisense-no-extension.png)

Po úpravě souboru EditorConfig je nutné znovu načíst soubory kódu, aby se nové nastavení projevilo.

Pokud upravíte mnoho souborů *.editorconfig,* může být [užitečné rozšíření EditorConfig Language Service.](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) Některé funkce tohoto rozšíření zahrnují zvýraznění syntaxe, vylepšené technologie IntelliSense, ověřování a formátování kódu.

![Technologie IntelliSense s rozšířením Language Service EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Příklad

Následující příklad ukazuje stav odsazení fragmentu kódu Jazyka C# před a po přidání souboru *.editorconfig* do projektu. Nastavení **Tabulátory** v dialogovém okně **Možnosti** pro textový editor sady Visual Studio je nastaveno tak, aby při stisknutí klávesy **Tabulátor** vytvářely mezery.

![Nastavení karty Textový editor](../ide/media/vside_editorconfig_tabsetting.png)

Podle očekávání stisknutím klávesy **Tab** na dalším řádku odsazete řádek přidáním čtyř dalších prázdné znaky.

![Kód před použitím EditorConfig](../ide/media/vside_editorconfig_before.png)

Přidejte do projektu nový soubor s názvem *.editorconfig* s následujícím obsahem. Nastavení `[*.cs]` znamená, že tato změna platí pouze pro soubory kódu Jazyka C# v projektu.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Když teď stisknete klávesu **Tab,** získáte místo mezer znaky tabulátoru.

![Klávesa Tab přidá znak tabulátoru](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Poradce při potížích s nastavením EditorConfig

Pokud je soubor EditorConfig kdekoli v adresářové struktuře v umístění projektu nebo nad ním, visual studio použije nastavení editoru v tomto souboru na editor. V takovém případě se může na stavovém řádku zobrazit následující zpráva:

   **"Uživatelské předvolby pro tento typ souboru jsou přepsány konvencemi kódování tohoto projektu."**

To znamená, že pokud jsou v souboru EditorConfig v adresářové struktuře nebo nad ním zadány nastavení editoru v**Options** > **textovém editoru** Možnosti **(například** > Velikost a styl odsazení, velikost tabulátoru nebo konvence kódování), konvence v souboru EditorConfig přepíší nastavení v **možnostech**. Toto chování můžete řídit přepnutím **možnosti Sledovat konvence kódování projektu** v**textovém editoru****možnosti** >  **nástroje** > . Zrušením zaškrtnutí možnosti vypnete podporu EditorConfig pro Visual Studio.

![Možnosti nástrojů – postupujte podle konvencí kódování projektů](media/coding_conventions_option.png)

Všechny soubory *.editorconfig* najdete v nadřazených adresářích otevřením příkazového řádku a spuštěním následujícího příkazu z kořenového adresáře disku, který obsahuje váš projekt:

```Shell
dir .editorconfig /s
```

Rozsah konvencí EditorConfig můžete řídit ```root=true``` nastavením vlastnosti v souboru *.editorconfig* v kořenovém adresáři úložiště nebo v adresáři, ve kterém je projekt umístěn. Visual Studio hledá soubor s názvem *.editorconfig* v adresáři otevřeného souboru a v každém nadřazeném adresáři. Hledání končí, jakmile dosáhne kořenové cesty souboru nebo pokud ```root=true``` je nalezen soubor *.editorconfig.*

## <a name="see-also"></a>Viz také

- [Konvence stylu kódu .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Podpora EditorConfig pro jazykovou službu](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Funkce editoru kódu](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio pro Mac)](/visualstudio/mac/editorconfig)
