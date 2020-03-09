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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408474"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Vytvoření nastavení přenosné vlastního editoru pomocí řešení EditorConfig

Můžete přidat soubor [EditorConfig](https://editorconfig.org/) do projektu nebo základ kódu k prosazování konzistentních stylů kódování pro všechny, které fungují v základu kódu. EditorConfig nastavení přednost před globální sady Visual Studio text nastavení editoru. To znamená, že můžete každý základ kódu přizpůsobit tak, aby se používala nastavení textového editoru, která jsou specifická pro daný projekt. Vlastní předvolby osobního editoru můžete nastavit i v dialogovém okně **Možnosti** sady Visual Studio. Tato nastavení platí vždy, když pracujete v základu kódu bez souboru *. editorconfig* nebo když soubor *. editorconfig* nepřepíše konkrétní nastavení. Příkladem takové preference je styl odsazení&mdash;tabulátory nebo mezery.

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

Můžete definovat, která nastavení EditorConfig má **formátovat dokument** použít na [stránce možnosti **formátování** ](reference/options-text-editor-csharp-formatting.md#format-document-settings).

::: moniker-end

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [EditorConfig v Visual Studio pro Mac](/visualstudio/mac/editorconfig).

## <a name="code-consistency"></a>Konzistence kódu

Nastavení v souborech EditorConfig umožňují udržovat konzistentní kódování – styly a nastavení v základu kódu, jako je například odsazení stylu, šířku karty, znaky konce řádku, kódování, a další, bez ohledu na editor a integrované vývojové prostředí používáte. Například při kódování v C#, pokud má základ kódu konvenci pro preferovat, že se vždy skládají jenom z pěti mezer, dokumenty používají kódování UTF-8 a každý řádek vždycky končí znakem CR/LF, můžete nakonfigurovat soubor *. editorconfig* tak, aby to provedl.

Převody, které používáte na váš osobní projekty kódování mohou lišit od těch použít u týmových projektů. Například můžete dát přednost, pokud jste psaní kódu, se odsazení přidá znak tabulátoru. Váš tým ale dát přednost, že odsazení přidá čtyři znaky mezery namísto znak tabulátoru. EditorConfig soubory tento problém vyřešit tím, že povolíte konfiguraci pro každý scénář.

Vzhledem k tomu, že nastavení jsou obsaženy v souboru v základu kódu, jejich přenosu spolu s tohoto základu kódu. Za předpokladu, otevřete soubor kódu v editoru EditorConfig nedodržují předpisy, jsou implementovány nastavení textového editoru. Další informace o souborech EditorConfig najdete na webu [EditorConfig.org](https://editorconfig.org/) .

> [!NOTE]
> Vytváření názvů, které jsou nastaveny v souboru EditorConfig nelze aktuálně používá v kanálu CI/CD, jak vytvořit chyby nebo upozornění. Jakékoli odchylky stylu se zobrazí pouze v editoru sady Visual Studio a **Seznam chyb**.

## <a name="supported-settings"></a>Podporovaná nastavení

Editor v sadě Visual Studio podporuje základní sadu [vlastností EditorConfig](https://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- ukončit\_of_line
- Znaková sada
- trailing_whitespace\_pro ořezávání
- Vložit\_final_newline
- kořen

EditorConfig editor nastavení je podporované ve všech jazycích, Visual Studio podporované s výjimkou XML. Kromě toho EditorConfig podporuje konvence [stylu kódu](../ide/editorconfig-code-style-settings-reference.md) , včetně [jazyků](../ide/editorconfig-language-conventions.md), [formátování](../ide/editorconfig-formatting-conventions.md)a konvencí [pojmenování](../ide/editorconfig-naming-conventions.md) pro C# a Visual Basic.

## <a name="add-and-remove-editorconfig-files"></a>Přidání a odebrání souborů EditorConfig

Když do projektu nebo základu kódu přidáte soubor EditorConfig, všechny nové řádky kódu, které zapíšete, jsou formátovány podle souboru EditorConfig. Přidání souboru EditorConfig však nepřevede existující styly na nové, dokud neformátujete dokument nebo nespustíte [Vyčištění kódu](../ide/code-styles-and-code-cleanup.md). Pokud jste například v souboru naformátovali znaky, které jsou naformátované pomocí karet, a přidáte soubor EditorConfig, který se odsadí s mezerami, znaky odsazení se nebudou automaticky převádět na mezery. Při formátování dokumentu (**úprava** > **Rozšířené** > **formátování dokumentu** nebo **CTRL**+**K**, **CTRL**+**D**) se nastavení prázdného místa v souboru EditorConfig použije na existující řádky kódu.

Pokud odeberete soubor EditorConfig z projektu nebo základu kódu a chcete, aby byly nové řádky kódu formátovány podle nastavení globálního editoru, je nutné zavřít a znovu otevřít všechny otevřené soubory kódu.

### <a name="add-an-editorconfig-file-to-a-project"></a>Přidat soubor EditorConfig do projektu

1. Otevřete projekt nebo řešení v sadě Visual Studio. Vyberte buď projekt nebo uzel řešení v závislosti na tom, zda má být nastavení *. editorconfig* použito pro všechny projekty v řešení nebo pouze jeden. Můžete také vybrat složku v projektu nebo řešení, do které chcete přidat soubor *. editorconfig* .

1. Z panelu nabídek zvolte možnost **projekt** > **Přidat novou položku**nebo stiskněte klávesovou **zkratku CTRL**+**SHIFT**+**A**.

   Otevře se dialogové okno **Přidat novou položku** .

1. Do vyhledávacího pole vyhledejte **editorconfig**.

   Ve výsledcích hledání se zobrazí dvě šablony položek **souboru editorconfig** .

   ![Šablony položek souborů EditorConfig v aplikaci Visual Studio](media/editorconfig-item-templates.png)

1. Vyberte šablonu **soubor editorconfig (výchozí)** a přidejte soubor editorconfig, který se předběžně vyplnil dvěma základními možnostmi editorconfig pro odsazení stylu a velikost. Případně můžete vybrat šablonu **soubor editorconfig (.NET)** a přidat soubor editorconfig, který byl předem vyplněný výchozím [stylem kódu .NET, formátováním a zásadami vytváření názvů](../ide/editorconfig-code-style-settings-reference.md).

   V Průzkumník řešení se zobrazí soubor *. editorconfig* a otevře se v editoru.

   ![soubor. editorconfig v Průzkumník řešení a editoru](media/editorconfig-dotnet.png)

1. Upravte soubor podle potřeby.

### <a name="other-ways-to-add-an-editorconfig-file"></a>Další způsoby přidávání souboru EditorConfig

Existuje několik způsobů přidáte soubor EditorConfig do projektu:

- [Funkce odvození kódu](/visualstudio/intellicode/code-style-inference) IntelliCode pro Visual Studio odvodí vaše styly kódu z existujícího kódu. Pak vytvoří neprázdný soubor EditorConfig s předem definovanými preferencemi stylu kódu.

- Od sady Visual Studio 2019 můžete [vygenerovat soubor EditorConfig na základě vašeho nastavení stylu kódu](/visualstudio/ide/code-styles-and-code-cleanup#code-styles-in-editorconfig-files) v **nástrojích** > **Možnosti**.

## <a name="file-hierarchy-and-precedence"></a>Hierarchie souborů a Priorita

Když přidáte soubor *. editorconfig* do složky ve vaší hierarchii souborů, bude jeho nastavení platit pro všechny příslušné soubory na této úrovni a níže. EditorConfig nastavení pro konkrétní projekt, základ kódu nebo části základu kódu, můžete také přepsat tak, aby používala různých konvencí než ostatní části základu kódu. To může být užitečné, když zahrnout kód z někde jinde a nechcete měnit její konvence.

Pokud chcete přepsat některá nebo všechna nastavení EditorConfig, přidejte soubor *. EditorConfig* na úrovni hierarchie souborů, který chcete použít pro přepsané nastavení. Nové nastavení souborů EditorConfig použít na soubory na stejné úrovni a všech podadresářích.

![EditorConfig hierarchie](../ide/media/vside_editorconfig_hierarchy.png)

Pokud chcete přepsat některá, ale ne všechna nastavení, určete pouze tato nastavení v souboru *. editorconfig* . Pouze vlastnosti, která explicitně zadáte v souboru nižší úrovně se přepíšou. Další nastavení ze souborů vyšších úrovní *. editorconfig* budou nadále platit. Pokud chcete zajistit, aby se v této části základu kódu nepoužívala _žádná_ nastavení ze _všech_ souborů *editorconfig* na vyšší úrovni, přidejte do souboru *. editorconfig* na nižší úrovni vlastnost ```root=true```:

```ini
# top-most EditorConfig file
root = true
```

Soubory EditorConfig jsou čteny shora dolů. Pokud existuje více vlastností se stejným názvem, má přednost vlastnost naposledy Nalezeno s tímto názvem.

## <a name="edit-editorconfig-files"></a>Upravit soubory EditorConfig

Visual Studio pomáhá upravovat soubory *. editorconfig* zadáním seznamů dokončení IntelliSense.

![Technologie IntelliSense v souboru .editorconfig](media/editorconfig-intellisense-no-extension.png)

Poté, co jste upravili soubor EditorConfig, musí znovu načíst soubory kódu pro nové nastavení projevilo.

Pokud upravíte spoustu souborů *. editorconfig* , můžete najít užitečné [rozšíření služby editorconfig Language](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) . Funkce tohoto rozšíření patří zvýrazňování syntaxe, Vylepšená technologie IntelliSense, ověřování a formátování kódu.

![Technologie IntelliSense s příponou EditorConfig Language Service](media/editorconfig-intellisense.png)

## <a name="example"></a>Příklad

Následující příklad ukazuje stav odsazení fragmentu C# kódu před a po přidání souboru *. editorconfig* do projektu. Nastavení **tabulátorů** v dialogovém okně **Možnosti** pro textový editor sady Visual Studio je nastaveno tak, aby při stisknutí klávesy **tabulátoru** vytvořilo znaky mezery.

![Karta nastavení textového editoru](../ide/media/vside_editorconfig_tabsetting.png)

Podle očekávání se po stisknutí klávesy **TAB** na dalším řádku Odsadí řádek přidáním čtyř dalších prázdných znaků.

![Kód před použitím EditorConfig](../ide/media/vside_editorconfig_before.png)

Přidejte do projektu nový soubor s názvem *. editorconfig* s následujícím obsahem. Nastavení `[*.cs]` znamená, že tato změna se vztahuje pouze C# na soubory kódu v projektu.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Když teď stisknete klávesu **TAB** , místo mezer se zobrazí znaky tabulátoru.

![Stisknutím klávesy TAB přidá znak Tab](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>Řešení potíží s nastavením EditorConfig

Pokud je soubor EditorConfig kdekoli v adresářové struktuře dosahovalo nebo přesahovalo umístění vašeho projektu, Visual Studio použije nastavení editoru v tomto souboru k editoru. V takovém případě může zobrazit následující zprávy ve stavovém řádku:

   **"Předvolby uživatele pro tento typ souboru se přepsaly konvencemi psaní kódu tohoto projektu."**

To znamená, že pokud se v souboru EditorConfig na projektu ve struktuře adresáře nebo nad ním **nachází > nastavení** **editoru > ** **textový editor** (například velikost odsazení a styl, velikost tabulátoru nebo konvence kódování), konvence v souboru EditorConfig přepíší nastavení v **možnostech**. Toto chování můžete řídit přepnutím možnosti **konvence psaní kódu projektu** v části **nástroje** > **Možnosti** > **textový editor**. Zrušíte zaškrtnutí možnosti vypne podporou pro EditorConfig pro sadu Visual Studio.

![Možnosti v nabídce nástroje - postupujte podle konvence psaní kódu projektu](media/coding_conventions_option.png)

Všechny soubory *. editorconfig* v nadřazených adresářích můžete najít tak, že otevřete příkazový řádek a spustíte následující příkaz z kořenového adresáře disku, který obsahuje váš projekt:

```Shell
dir .editorconfig /s
```

Rozsah konvencí EditorConfig můžete řídit nastavením vlastnosti ```root=true``` v souboru *. EditorConfig* v kořenovém adresáři úložiště nebo v adresáři, ve kterém se nachází váš projekt. Visual Studio hledá soubor s názvem *. editorconfig* v adresáři otevřeného souboru a v každém nadřazeném adresáři. Hledání skončí, když dosáhne kořenového FilePath, nebo pokud se najde soubor *. editorconfig* s ```root=true```.

## <a name="see-also"></a>Viz také

- [Konvence stylu kódu .NET](../ide/editorconfig-code-style-settings-reference.md)
- [Podpora EditorConfig pro službu jazyka](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [Funkce editoru kódu](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio pro Mac)](/visualstudio/mac/editorconfig)
