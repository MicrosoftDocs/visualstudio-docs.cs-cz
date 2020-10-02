---
title: Nastavení EditorConfig
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.openlocfilehash: 277e5cd03d4006ced0791356be73ca1fcbe5c217
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659248"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Vytvoření přenosného nastavení vlastního editoru pomocí řešení EditorConfig

Můžete přidat soubor EditorConfig do projektu nebo základ kódu k prosazování konzistentních stylů kódování pro všechny, které fungují v základu kódu. Nastavení EditorConfig mají přednost před globálním nastavením textového editoru sady Visual Studio. To znamená, že můžete každý základ kódu přizpůsobit tak, aby se používala nastavení textového editoru, která jsou specifická pro daný projekt. Vlastní předvolby osobního editoru můžete nastavit i v dialogovém okně **Možnosti** sady Visual Studio. Tato nastavení platí vždy, když pracujete v základu kódu bez souboru *. editorconfig* nebo když soubor *. editorconfig* nepřepíše konkrétní nastavení. Příkladem takové předvolby je odsazení &mdash; tabulátorů nebo mezer.

Nastavení EditorConfig jsou podporovaná mnoha editory kódu a prostředími IDEs, včetně sady Visual Studio. Je to přenosná komponenta, která se přenáší s vaším kódem a může vymáhat styly kódování i mimo sadu Visual Studio.

::: moniker range=">=vs-2019"

Když do projektu přidáte soubor EditorConfig v aplikaci Visual Studio, nové řádky kódu jsou formátovány podle nastavení EditorConfig. Formátování stávajícího kódu se nemění, Pokud nespustíte některý z následujících příkazů:

 - [Vyčištění kódu](../ide/code-styles-and-code-cleanup.md) (**CTRL** + **K**, **CTRL +** + **E**), který aplikuje nastavení prázdných mezer, jako je styl odsazení a vybraná nastavení stylu kódu, jako je například způsob řazení `using` direktiv.
 - **Upravit** > **Rozšířené možnosti** > **Formátovat dokument** (nebo **CTRL +** + **k**, **CTRL** + **D** ve výchozím profilu), který aplikuje jenom nastavení mezer, jako je styl odsazení.

 ::: moniker-end

::: moniker range="=vs-2017"

Když do projektu přidáte soubor EditorConfig v aplikaci Visual Studio, nové řádky kódu jsou formátovány podle nastavení EditorConfig. Formátování stávajícího kódu se nemění, pokud dokument neformátujete (**upravíte**  >  **Rozšířený**  >  **Formát dokumentu** nebo **CTRL** + **K**, **CTRL** + **D** ve výchozím profilu). Formátování dokumentu má vliv pouze na prázdné nastavení, jako je styl odsazení, pokud jste nenakonfigurovali formát dokumentu k [provedení dalšího vyčištění kódu](../ide/code-styles-and-code-cleanup.md#apply-code-styles).

 ::: moniker-end

::: moniker range="vs-2017"

Můžete definovat, která nastavení EditorConfig má **formátovat dokument** použít na [stránce možnosti **formátování** ](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [EditorConfig v Visual Studio pro Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Konzistence kódu

Nastavení v souborech EditorConfig umožňují zachovat konzistentní styly a nastavení kódování v základu kódu, jako je styl odsazení, Šířka tabulátoru, konec znaků řádku, kódování a další, bez ohledu na Editor nebo rozhraní IDE, které používáte. Například při psaní kódu v jazyce C# má vaše základová konvence přednost před tím, že se vždy skládají jenom z pěti znaků mezery, dokumenty používají kódování UTF-8 a každý řádek vždycky končí znakem CR/LF, můžete nakonfigurovat soubor *. editorconfig* tak, aby to provedl.

Konvence kódování, které použijete v osobních projektech, se můžou lišit od těch, které se používají v projektech týmu. Můžete například chtít, aby při kódování a odsazení přidal znak tabulátoru. Váš tým však může preferovat, že odsazení přičítá místo znaku tabulátoru znaky mezer. Soubory EditorConfig tento problém řeší tím, že vám umožní mít konfiguraci pro každý scénář.

Vzhledem k tomu, že nastavení jsou obsažena v souboru v základu kódu, cestují spolu s tímto základem kódu. Pokud otevřete soubor kódu v editoru kompatibilním s EditorConfig, nastavení textového editoru jsou implementovaná. Další informace o souborech EditorConfig najdete na webu [EditorConfig.org](https://editorconfig.org/) .

> [!NOTE]
> Konvence nastavené v souboru EditorConfig se momentálně nedají vykonat v kanálu CI/CD jako chyby sestavení nebo upozornění. Jakékoli odchylky stylu se zobrazí pouze v editoru sady Visual Studio a **Seznam chyb**.

## <a name="supported-settings"></a>Podporovaná nastavení

Editor v sadě Visual Studio podporuje základní sadu [vlastností EditorConfig](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- ukončit \_ of_line
- charset
- trailing_whitespace střihu \_
- vložit \_ final_newline
- kořen

Nastavení editoru EditorConfig jsou podporovaná ve všech jazycích podporovaných v aplikaci Visual Studio s výjimkou XML. Kromě toho EditorConfig podporuje konvence [stylu kódu](/dotnet/fundamentals/code-analysis/code-style-rule-options) , včetně [jazyků](/dotnet/fundamentals/code-analysis/style-rules/language-rules), [formátování](/dotnet/fundamentals/code-analysis/style-rules/formatting-rules)a konvencí [pojmenování](/dotnet/fundamentals/code-analysis/style-rules/naming-rules) pro C# a Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Přidání a odebrání souborů EditorConfig

Když do projektu nebo základu kódu přidáte soubor EditorConfig, všechny nové řádky kódu, které zapíšete, jsou formátovány podle souboru EditorConfig. Přidání souboru EditorConfig však nepřevede existující styly na nové, dokud neformátujete dokument nebo nespustíte [Vyčištění kódu](../ide/code-styles-and-code-cleanup.md). Pokud jste například v souboru naformátovali znaky, které jsou naformátované pomocí karet, a přidáte soubor EditorConfig, který se odsadí s mezerami, znaky odsazení se nebudou automaticky převádět na mezery. Při formátování dokumentu (**Úprava**  >  **rozšířeného**  >  **formátu dokumentu** nebo **CTRL** + **K**, **CTRL** + **D**) se nastavení prázdného místa v souboru EditorConfig použije na existující řádky kódu.

Pokud odeberete soubor EditorConfig z projektu nebo základu kódu a chcete, aby byly nové řádky kódu formátovány podle nastavení globálního editoru, je nutné zavřít a znovu otevřít všechny otevřené soubory kódu.

### <a name="add-an-editorconfig-file-to-a-project"></a>Přidat soubor EditorConfig do projektu

1. Otevřete projekt nebo řešení v aplikaci Visual Studio. Vyberte buď projekt nebo uzel řešení v závislosti na tom, zda má být nastavení *. editorconfig* použito pro všechny projekty v řešení nebo pouze jeden. Můžete také vybrat složku v projektu nebo řešení, do které chcete přidat soubor *. editorconfig* .

1. Z panelu nabídek zvolte **projekt**  >  **Přidat novou položku**nebo stiskněte klávesy **CTRL** + **SHIFT** + **A**.

   Otevře se dialogové okno **Přidat novou položku** .

1. Do vyhledávacího pole vyhledejte **editorconfig**.

   Ve výsledcích hledání se zobrazí dvě šablony položek **souboru editorconfig** .

   ![Šablony položek souborů EditorConfig v aplikaci Visual Studio](media/editorconfig-item-templates.png)

1. Vyberte šablonu **soubor editorconfig (výchozí)** a přidejte soubor editorconfig, který se předběžně vyplnil dvěma základními možnostmi editorconfig pro odsazení stylu a velikost. Případně můžete vybrat šablonu **soubor editorconfig (.NET)** a přidat soubor editorconfig, který byl předem vyplněný výchozím [stylem kódu .NET, formátováním a zásadami vytváření názvů](/dotnet/fundamentals/code-analysis/code-style-rule-options).

   V Průzkumník řešení se zobrazí soubor *. editorconfig* a otevře se v editoru.

   ![soubor. editorconfig v Průzkumník řešení a editoru](media/editorconfig-dotnet.png)

1. Upravte soubor podle potřeby.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Další způsoby, jak přidat soubor EditorConfig

Existuje několik dalších způsobů, jak můžete přidat soubor EditorConfig do projektu:

- [Funkce odvození kódu](/visualstudio/intellicode/code-style-inference) IntelliCode pro Visual Studio odvodí vaše styly kódu z existujícího kódu. Pak vytvoří neprázdný soubor EditorConfig s předem definovanými preferencemi stylu kódu.

- Od sady Visual Studio 2019 můžete [vygenerovat soubor EditorConfig v závislosti na nastavení stylu kódu](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files) v **Tools**  >  **možnostech**nástrojů.

## <a name="file-hierarchy-and-precedence"></a>Hierarchie souborů a Priorita

Když přidáte soubor *. editorconfig* do složky ve vaší hierarchii souborů, bude jeho nastavení platit pro všechny příslušné soubory na této úrovni a níže. Můžete také přepsat nastavení EditorConfig pro konkrétní projekt, základ kódu nebo část základu kódu, aby používaly různé konvence než jiné části základu kódu. To může být užitečné, když zařadíte kód z někde jinde a nechcete měnit jeho konvence.

Pokud chcete přepsat některá nebo všechna nastavení EditorConfig, přidejte soubor *. EditorConfig* na úrovni hierarchie souborů, který chcete použít pro přepsané nastavení. Nové nastavení souboru EditorConfig se týká souborů na stejné úrovni a všech podadresářích.

![Hierarchie EditorConfig](../ide/media/vside_editorconfig_hierarchy.png)

Pokud chcete přepsat některá, ale ne všechna nastavení, určete pouze tato nastavení v souboru *. editorconfig* . Přepsány jsou pouze vlastnosti, které jsou explicitně uvedeny v souboru nižší úrovně. Další nastavení ze souborů vyšších úrovní *. editorconfig* budou nadále platit. Pokud chcete zajistit, aby se v této části základu kódu nepoužívala _žádná_ nastavení ze _všech_ souborů *editorconfig* na vyšší úrovni, přidejte ```root=true``` vlastnost do souboru *. editorconfig* na nižší úrovni:

```ini
# top-most EditorConfig file
root = true
```

Soubory EditorConfig jsou čteny shora dolů. Pokud existuje více vlastností se stejným názvem, má přednost vlastnost naposledy Nalezeno s tímto názvem.

## <a name="edit-editorconfig-files"></a>Upravit soubory EditorConfig

Visual Studio pomáhá upravovat soubory *. editorconfig* zadáním seznamů dokončení IntelliSense.

![IntelliSense v souboru. editorconfig](media/editorconfig-intellisense-no-extension.png)

Po úpravě souboru EditorConfig je nutné znovu načíst soubory kódu, aby se nové nastavení projevilo.

Pokud upravíte spoustu souborů *. editorconfig* , můžete najít užitečné [rozšíření služby editorconfig Language](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) . Některé funkce tohoto rozšíření zahrnují zvýrazňování syntaxe, vylepšenou technologii IntelliSense, ověřování a formátování kódu.

![IntelliSense s rozšířením jazykové služby EditorConfig](media/editorconfig-intellisense.png)

## <a name="example"></a>Příklad

Následující příklad ukazuje stav odsazení fragmentu kódu v jazyce C# před a po přidání souboru *. editorconfig* do projektu. Nastavení **tabulátorů** v dialogovém okně **Možnosti** pro textový editor sady Visual Studio je nastaveno tak, aby při stisknutí klávesy **tabulátoru** vytvořilo znaky mezery.

![Nastavení karty textový editor](../ide/media/vside_editorconfig_tabsetting.png)

Podle očekávání se po stisknutí klávesy **TAB** na dalším řádku Odsadí řádek přidáním čtyř dalších prázdných znaků.

![Kód před použitím EditorConfig](../ide/media/vside_editorconfig_before.png)

Přidejte do projektu nový soubor s názvem *. editorconfig* s následujícím obsahem. `[*.cs]`Nastavení znamená, že tato změna se vztahuje pouze na soubory kódu jazyka C# v projektu.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Když teď stisknete klávesu **TAB** , místo mezer se zobrazí znaky tabulátoru.

![Klávesa TAB přidá znak tabulátoru](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Řešení potíží s nastavením EditorConfig

Pokud je soubor EditorConfig kdekoli ve struktuře adresáře na umístění projektu nebo nad jeho umístěním, Visual Studio použije nastavení editoru v tomto souboru do editoru. V takovém případě se může na stavovém řádku zobrazit tato zpráva:

   **"Předvolby uživatele pro tento typ souboru se přepsaly konvencemi psaní kódu tohoto projektu."**

To znamená, že pokud se **v**  >  **Options**  >  souboru EditorConfig v projektu ve struktuře adresáře nebo nad projektem v rámci struktury v adresáři nachází všechna**nastavení editoru** (například velikost odsazení a styl, velikost tabulátoru nebo konvence kódování), nahradí konvence v souboru EditorConfig nastavení v **možnostech**. Toto chování můžete řídit přepnutím možnosti **konvence psaní kódu projektu** v části **nástroje**  >  **Options**  >  **textový editor**. Zrušením zaškrtnutí možnosti vypnete podporu EditorConfig pro Visual Studio.

![Možnosti nástrojů – Sledujte konvence psaní kódu projektu](media/coding_conventions_option.png)

Všechny soubory *. editorconfig* v nadřazených adresářích můžete najít tak, že otevřete příkazový řádek a spustíte následující příkaz z kořenového adresáře disku, který obsahuje váš projekt:

```Shell
dir .editorconfig /s
```

Rozsah konvencí EditorConfig můžete řídit nastavením ```root=true``` vlastnosti v souboru *. EditorConfig* v kořenovém adresáři úložiště nebo v adresáři, ve kterém se nachází váš projekt. Visual Studio hledá soubor s názvem *. editorconfig* v adresáři otevřeného souboru a v každém nadřazeném adresáři. Hledání skončí, když dosáhne kořenového FilePath, nebo pokud se najde soubor *. editorconfig* , který se nachází ```root=true``` .

## <a name="see-also"></a>Viz také

- [Konvence stylu kódu .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Podpora EditorConfig pro službu jazyka](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Funkce editoru kódu](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio pro Mac)](/visualstudio/mac/editorconfig)
