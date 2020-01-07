---
title: EditorConfig nastavení
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3aee4945b4a3b41a7f6ec532268c2c19f549d0a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589783"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Vytvoření nastavení přenosné vlastního editoru pomocí řešení EditorConfig

Můžete přidat soubor [EditorConfig](https://editorconfig.org/) do projektu nebo základ kódu k prosazování konzistentních stylů kódování pro všechny, které fungují v základu kódu. EditorConfig nastavení přednost před globální sady Visual Studio text nastavení editoru. To znamená, že můžete každý základ kódu přizpůsobit tak, aby se používala nastavení textového editoru, která jsou specifická pro daný projekt. Stále můžete nastavit předvolby osobní editoru v sadě Visual Studio **možnosti** dialogové okno. Tato nastavení platí vždy, když pracujete v základu kódu bez *.editorconfig* souboru, nebo když *.editorconfig* souboru nepřepíše konkrétní nastavení. Příkladem takových předvoleb je styl odsazení&mdash;tabulátory nebo mezery.

EditorConfig nastavení podporuje řadu editory kódu a prostředími IDE, jako je Visual Studio. Je přenosný komponentu, která se přenáší pomocí kódu a můžete vynutit kódování styly i mimo sadu Visual Studio.

::: moniker range=">=vs-2019"

Když do projektu přidáte soubor EditorConfig v aplikaci Visual Studio, nové řádky kódu jsou formátovány podle nastavení EditorConfig. Formátování stávajícího kódu se nemění, Pokud nespustíte některý z následujících příkazů:

 - [Vyčištění kódu](../ide/code-styles-and-code-cleanup.md) (**CTRL**+**K**, **CTRL**+**E**), které aplikuje nastavení mezer, jako je styl odsazení a vybraná nastavení stylu kódu, jako je například způsob řazení `using` direktiv.
 - **Upravit** **Formát dokumentu** > **upřesnit** > (nebo **CTRL**+**K**, **CTRL**+**D** ve výchozím profilu), který aplikuje jenom nastavení mezer, například styl odsazení.

 ::: moniker-end

::: moniker range="=vs-2017"

Když do projektu přidáte soubor EditorConfig v aplikaci Visual Studio, nové řádky kódu jsou formátovány podle nastavení EditorConfig. Formátování existujícího kódu se nezměnilo, pokud jej neprovedete (**upravíte** > **Rozšířený** > **formátování dokumentu** nebo **CTRL**+**K**, **CTRL**+**D** ve výchozím profilu). Formátování dokumentu má vliv pouze na prázdné nastavení, jako je styl odsazení, pokud jste nenakonfigurovali formát dokumentu k [provedení dalšího vyčištění kódu](../ide/code-styles-and-code-cleanup.md#apply-code-styles).

 ::: moniker-end

::: moniker range="vs-2017"

EditorConfig nastavení, které chcete, můžete definovat **formátovat dokument** použít [ **formátování** stránka možností](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [EditorConfig v sadě Visual Studio pro Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Konzistence kódu

Nastavení v souborech EditorConfig umožňují udržovat konzistentní kódování – styly a nastavení v základu kódu, jako je například odsazení stylu, šířku karty, znaky konce řádku, kódování, a další, bez ohledu na editor a integrované vývojové prostředí používáte. Například při psaní kódu v jazyce C#, pokud vašeho základu kódu obsahuje konvenci preferovat, odsazení vždy skládá z pěti znaky mezery, dokumenty pomocí kódování UTF-8 a každý řádek vždy končí řetězcem znaků CR/LF, můžete nakonfigurovat *.editorconfig* soubor, který chcete.

Převody, které používáte na váš osobní projekty kódování mohou lišit od těch použít u týmových projektů. Například můžete dát přednost, pokud jste psaní kódu, se odsazení přidá znak tabulátoru. Váš tým ale dát přednost, že odsazení přidá čtyři znaky mezery namísto znak tabulátoru. EditorConfig soubory tento problém vyřešit tím, že povolíte konfiguraci pro každý scénář.

Vzhledem k tomu, že nastavení jsou obsaženy v souboru v základu kódu, jejich přenosu spolu s tohoto základu kódu. Za předpokladu, otevřete soubor kódu v editoru EditorConfig nedodržují předpisy, jsou implementovány nastavení textového editoru. Další informace o souborech EditorConfig, najdete v článku [EditorConfig.org](https://editorconfig.org/) webu.

> [!NOTE]
> Vytváření názvů, které jsou nastaveny v souboru EditorConfig nelze aktuálně používá v kanálu CI/CD, jak vytvořit chyby nebo upozornění. Všechny odchylky styl se zobrazí pouze v editoru sady Visual Studio a **seznam chyb**.

## <a name="supported-settings"></a>Podporovaná nastavení

Editor v sadě Visual Studio podporuje základní sadu [EditorConfig vlastnosti](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- Znaková sada
- Trim\_trailing_whitespace
- insert\_final_newline
- kořen

EditorConfig editor nastavení je podporované ve všech jazycích, Visual Studio podporované s výjimkou XML. Kromě toho EditorConfig podporuje konvence [stylu kódu](../ide/editorconfig-code-style-settings-reference.md) , včetně [jazyků](../ide/editorconfig-language-conventions.md), [formátování](../ide/editorconfig-formatting-conventions.md)a konvencí [pojmenování](../ide/editorconfig-naming-conventions.md) pro C# a Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Přidání a odebrání souborů EditorConfig

Když do projektu nebo základu kódu přidáte soubor EditorConfig, všechny nové řádky kódu, které zapíšete, jsou formátovány podle souboru EditorConfig. Přidání souboru EditorConfig však nepřevede existující styly na nové, dokud neformátujete dokument nebo nespustíte [Vyčištění kódu](../ide/code-styles-and-code-cleanup.md). Pokud jste například v souboru naformátovali znaky, které jsou naformátované pomocí karet, a přidáte soubor EditorConfig, který se odsadí s mezerami, znaky odsazení se nebudou automaticky převádět na mezery. Při formátování dokumentu (**úprava** > **Rozšířené** > **formátování dokumentu** nebo **CTRL**+**K**, **CTRL**+**D**) se nastavení prázdného místa v souboru EditorConfig použije na existující řádky kódu.

Pokud odeberete soubor EditorConfig z projektu nebo základu kódu a chcete, aby byly nové řádky kódu formátovány podle nastavení globálního editoru, je nutné zavřít a znovu otevřít všechny otevřené soubory kódu.

### <a name="add-an-editorconfig-file-to-a-project"></a>Přidat soubor EditorConfig do projektu

1. Otevřete projekt nebo řešení v sadě Visual Studio. Vyberte uzel projektu nebo řešení, podle toho, jestli vaše *.editorconfig* nastavení platit pro všechny projekty v řešení nebo jen jeden. Můžete také vybrat složku ve vašem projektu nebo řešení pro přidání *.editorconfig* do souboru.

1. Na panelu nabídek zvolte **projektu** > **přidat novou položku**, nebo stiskněte klávesu **Ctrl**+**Shift** + **A**.

   **Přidat novou položku** zobrazí se dialogové okno.

1. Do vyhledávacího pole vyhledejte **editorconfig**.

   Ve výsledcích hledání se zobrazí dvě šablony položek **souboru editorconfig** .

   ![Šablony položek souborů EditorConfig v aplikaci Visual Studio](media/editorconfig-item-templates.png)

1. Vyberte šablonu **soubor editorconfig (výchozí)** a přidejte soubor editorconfig, který se předběžně vyplnil dvěma základními možnostmi editorconfig pro odsazení stylu a velikost. Případně můžete vybrat šablonu **soubor editorconfig (.NET)** a přidat soubor editorconfig, který byl předem vyplněný výchozím [stylem kódu .NET, formátováním a zásadami vytváření názvů](../ide/editorconfig-code-style-settings-reference.md).

   *.Editorconfig* souboru se zobrazí v Průzkumníku řešení a otevře v editoru.

   ![soubor. editorconfig v Průzkumník řešení a editoru](media/editorconfig-dotnet.png)

1. Upravte soubor podle potřeby.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Další způsoby přidávání souboru EditorConfig

Existuje několik způsobů přidáte soubor EditorConfig do projektu:

- [Funkce odvození kódu](/visualstudio/intellicode/code-style-inference) IntelliCode pro Visual Studio odvodí vaše styly kódu z existujícího kódu. Pak vytvoří neprázdný soubor EditorConfig s předem definovanými preferencemi stylu kódu.

- Od sady Visual Studio 2019 můžete [vygenerovat soubor EditorConfig na základě vašeho nastavení stylu kódu](/visualstudio/ide/code-styles-and-code-cleanup#code-styles-in-editorconfig-files) v **nástrojích** > **Možnosti**.

## <a name="file-hierarchy-and-precedence"></a>Hierarchie souborů a Priorita

Když přidáte *.editorconfig* soubor do složky ve vaší hierarchii soubor, jeho nastavení platí pro všechny příslušné soubory na této úrovni a nižší. EditorConfig nastavení pro konkrétní projekt, základ kódu nebo části základu kódu, můžete také přepsat tak, aby používala různých konvencí než ostatní části základu kódu. To může být užitečné, když zahrnout kód z někde jinde a nechcete měnit její konvence.

Chcete-li přepsat některá nebo všechna nastavení EditorConfig, přidejte *.editorconfig* souboru na úrovni hierarchie souborů chcete těchto přepsaného nastavení použít. Nové nastavení souborů EditorConfig použít na soubory na stejné úrovni a všech podadresářích.

![EditorConfig hierarchie](../ide/media/vside_editorconfig_hierarchy.png)

Pokud je zapotřebí přepsat některé, ale ne všechna nastavení, zadejte pouze tyto nastavení v *.editorconfig* souboru. Pouze vlastnosti, která explicitně zadáte v souboru nižší úrovně se přepíšou. Další nastavení z vyšší úrovně *.editorconfig* souborů i nadále. Pokud chcete zajistit, aby _žádné_ nastavení z _jakékoli_ vyšší úrovně *.editorconfig* soubory aplikují i na této části základu kódu, přidejte ```root=true``` vlastnost nižší úrovně *.editorconfig* souboru:

```ini
# top-most EditorConfig file
root = true
```

Soubory EditorConfig jsou čteny shora dolů. Pokud existuje více vlastností se stejným názvem, má přednost vlastnost naposledy Nalezeno s tímto názvem.

## <a name="edit-editorconfig-files"></a>Upravit soubory EditorConfig

Visual Studio umožňuje upravit *.editorconfig* soubory poskytnutím seznamech doplňování technologie IntelliSense.

![Technologie IntelliSense v souboru .editorconfig](media/editorconfig-intellisense-no-extension.png)

Poté, co jste upravili soubor EditorConfig, musí znovu načíst soubory kódu pro nové nastavení projevilo.

Pokud upravíte mnoho *.editorconfig* soubory, můžete zjistit [rozšíření služeb jazyka EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) užitečné. Funkce tohoto rozšíření patří zvýrazňování syntaxe, Vylepšená technologie IntelliSense, ověřování a formátování kódu.

![Technologie IntelliSense s příponou EditorConfig Language Service](media/editorconfig-intellisense.png)

## <a name="example"></a>Příklad

Následující příklad ukazuje stav odsadit fragment kódu jazyka C#, před a po přidání *.editorconfig* soubor do projektu. **Karty** nastavení **možnosti** dialogové okno pro textový editor sady Visual Studio je nastavena na vytvoření znaky po stisknutí klávesy **kartu** klíč.

![Karta nastavení textového editoru](../ide/media/vside_editorconfig_tabsetting.png)

Podle očekávání, stiskněte **kartu** klíč na další řádek odsadí řádek tak, že přidáte čtyři další prázdné znaky.

![Kód před použitím EditorConfig](../ide/media/vside_editorconfig_before.png)

Přidat nový soubor s názvem *.editorconfig* do projektu s použitím následujícího obsahu. `[*.cs]` Nastavení znamená, že tato změna platí pouze pro kód soubory jazyka C# v projektu.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Teď, když stisknete **kartu** klíčů, získáte tabulátory místo mezer.

![Stisknutím klávesy TAB přidá znak Tab](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Řešení potíží s nastavením EditorConfig

Pokud je soubor EditorConfig kdekoli v adresářové struktuře dosahovalo nebo přesahovalo umístění vašeho projektu, Visual Studio použije nastavení editoru v tomto souboru k editoru. V takovém případě může zobrazit následující zprávy ve stavovém řádku:

   **"Předvolby uživatele pro tento typ souboru jsou přepsány konvence psaní kódu tohoto projektu."**

To znamená, že pokud libovolný editor nastavení v **nástroje** > **možnosti** > **textový Editor** (například velikost odsazení a styl, velikost nebo psaní kódu konvence) jsou uvedeny v souboru EditorConfig dosahovalo nebo přesahovalo projektu do struktury adresářů, konvence v souboru EditorConfig potlačit nastavení ve **možnosti**. Toto chování můžete ovládat přepnutím **konvence psaní kódu projektu použijte** možnost **nástroje** > **možnosti**  >  **Textový Editor**. Zrušíte zaškrtnutí možnosti vypne podporou pro EditorConfig pro sadu Visual Studio.

![Možnosti v nabídce nástroje - postupujte podle konvence psaní kódu projektu](media/coding_conventions_option.png)

Můžete najít všechny *.editorconfig* soubory v nadřazené adresáře tak, že otevřete příkazový řádek a spuštěním následujícího příkazu z kořenového adresáře disku, který obsahuje projekt:

```Shell
dir .editorconfig /s
```

Obor vaše EditorConfig konvence můžete řídit nastavením ```root=true``` vlastnost *.editorconfig* souboru v kořenovém adresáři úložiště nebo do adresáře, který se nachází váš projekt. Visual Studio vyhledá soubor s názvem *.editorconfig* v adresáři otevřený soubor a v každé nadřazené adresáře. Hledání končí dosáhne filepath kořenové nebo pokud *.editorconfig* soubor s ```root=true``` nenajde.

## <a name="see-also"></a>Viz také:

- [Konvence stylu kódu .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Podpora EditorConfig pro služby jazyka](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Funkce editoru kódu](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio for Mac)](/visualstudio/mac/editorconfig)
