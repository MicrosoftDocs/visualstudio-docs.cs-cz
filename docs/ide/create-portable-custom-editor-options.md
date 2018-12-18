---
title: EditorConfig nastavení
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.openlocfilehash: f2df8491ca3af165681a76c039d63c42c008f2f8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062923"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Vytvoření nastavení přenosné vlastního editoru pomocí řešení EditorConfig

V sadě Visual Studio 2017, můžete přidat [EditorConfig](http://editorconfig.org/) soubor do projektu nebo základ kódu k vynucení konzistentní kódování styly pro všechny uživatele, který funguje v základu kódu. EditorConfig nastavení přednost před globální sady Visual Studio text nastavení editoru. To znamená, že můžete každý základ kódu přizpůsobit tak, aby se používala nastavení textového editoru, která jsou specifická pro daný projekt. Stále můžete nastavit předvolby osobní editoru v sadě Visual Studio **možnosti** dialogové okno. Tato nastavení platí vždy, když pracujete v základu kódu bez *.editorconfig* souboru, nebo když *.editorconfig* souboru nepřepíše konkrétní nastavení. Příkladem takových předvoleb je styl odsazení&mdash;tabulátory nebo mezery.

EditorConfig nastavení podporuje řadu editory kódu a prostředími IDE, jako je Visual Studio. Je přenosný komponentu, která se přenáší pomocí kódu a můžete vynutit kódování styly i mimo sadu Visual Studio.

Když přidáte soubor EditorConfig do projektu v sadě Visual Studio, formátování existující kód není změnit, dokud se formátovat dokument (**upravit** > **Upřesnit**  >  **Formátovat dokument** nebo **Ctrl**+**K**, **Ctrl**+**D**ve výchozím profilu). Však žádné nové řádky kódu se formátují podle nastavení EditorConfig. EditorConfig nastavení, které chcete, můžete definovat **formátovat dokument** použít [ **formátování** stránka možností](reference/options-text-editor-csharp-formatting.md#format-document-settings).

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [EditorConfig v sadě Visual Studio pro Mac](/visualstudio/mac/editorconfig).

## <a name="coding-consistency"></a>Kódování konzistence

Nastavení v souborech EditorConfig umožňují udržovat konzistentní kódování – styly a nastavení v základu kódu, jako je například odsazení stylu, šířku karty, znaky konce řádku, kódování, a další, bez ohledu na editor a integrované vývojové prostředí používáte. Například při psaní kódu v jazyce C#, pokud vašeho základu kódu obsahuje konvenci preferovat, odsazení vždy skládá z pěti znaky mezery, dokumenty pomocí kódování UTF-8 a každý řádek vždy končí řetězcem znaků CR/LF, můžete nakonfigurovat *.editorconfig* soubor, který chcete.

Převody, které používáte na váš osobní projekty kódování mohou lišit od těch použít u týmových projektů. Například můžete dát přednost, pokud jste psaní kódu, se odsazení přidá znak tabulátoru. Váš tým ale dát přednost, že odsazení přidá čtyři znaky mezery namísto znak tabulátoru. EditorConfig soubory tento problém vyřešit tím, že povolíte konfiguraci pro každý scénář.

Vzhledem k tomu, že nastavení jsou obsaženy v souboru v základu kódu, jejich přenosu spolu s tohoto základu kódu. Za předpokladu, otevřete soubor kódu v editoru EditorConfig nedodržují předpisy, jsou implementovány nastavení textového editoru. Další informace o souborech EditorConfig, najdete v článku [EditorConfig.org](http://editorconfig.org/) webu.

> [!NOTE]
> Vytváření názvů, které jsou nastaveny v souboru EditorConfig nelze aktuálně používá v kanálu CI/CD, jak vytvořit chyby nebo upozornění. Všechny odchylky styl se zobrazí pouze v editoru sady Visual Studio a **seznam chyb**.

## <a name="supported-settings"></a>Podporovaná nastavení

Editor v sadě Visual Studio podporuje základní sadu [EditorConfig vlastnosti](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- Znaková sada
- Trim\_trailing_whitespace
- insert\_final_newline
- kořen

EditorConfig editor nastavení je podporované ve všech jazycích, Visual Studio podporované s výjimkou XML. Kromě toho podporuje EditorConfig [styl kódu](../ide/editorconfig-code-style-settings-reference.md) a [pojmenování](../ide/editorconfig-naming-conventions.md) konvence pro C# a Visual Basic.

## <a name="adding-and-removing-editorconfig-files"></a>Přidávání a odebírání souborů EditorConfig

Přidání EditorConfig soubor do projektu nebo základ kódu nelze převést existující styly nové značky. Například pokud máte odsazení v souboru, které jsou formátovány pomocí karty a přidání EditorConfig souboru, který odsazení pomocí mezer, znaků odsazení nebudou automaticky převedena na mezery. Však žádné nové řádky kódu se formátují podle EditorConfig souboru. Kromě toho pokud formátovat dokument (**upravit** > **Upřesnit** > **formátovat dokument** nebo **Ctrl** + **K**, **Ctrl**+**D**), použijí se nastavení v souboru EditorConfig do existujícího kódu.

Pokud soubor EditorConfig odeberte z projektu nebo základ kódu, musí zavřete a znovu otevřít soubory se vrátit do editoru globální nastavení pro nové řádky kódu.

### <a name="to-add-an-editorconfig-file-to-a-project-or-solution"></a>Chcete-li přidat soubor s příponou EditorConfig projektu nebo řešení

1. Otevřete projekt nebo řešení v sadě Visual Studio. Vyberte uzel projektu nebo řešení, podle toho, jestli vaše *.editorconfig* nastavení platit pro všechny projekty v řešení nebo jen jeden. Můžete také vybrat složku ve vašem projektu nebo řešení pro přidání *.editorconfig* do souboru.

1. Na panelu nabídek zvolte **projektu** > **přidat novou položku**, nebo stiskněte klávesu **Ctrl**+**Shift** + **A**.

   **Přidat novou položku** zobrazí se dialogové okno.

1. V kategoriích vlevo vyberte **Obecné**a klikněte na tlačítko **textový soubor** šablony. V **název** textové pole, zadejte `.editorconfig` a klikněte na tlačítko **přidat**.

   *.Editorconfig* souboru se zobrazí v Průzkumníku řešení a otevře v editoru.

   ![.editorconfig souboru v Průzkumníku řešení](media/editorconfig-in-solution-explorer.png)

1. Upravte soubor podle potřeby, například:

   ```EditorConfig
   root = true

   [*.{cs,vb}]
   indent_size = 4
   trim_trailing_whitespace = true

   [*.cs]
   csharp_new_line_before_open_brace = methods
   ```

### <a name="other-ways-to-add-an-editorconfig-file"></a>Další způsoby přidávání souboru EditorConfig

Existuje několik způsobů přidáte soubor EditorConfig do projektu:

- Nainstalujte [rozšíření služeb jazyka EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) snadněji přidat prázdnou *.editorconfig* soubor do projektu. Až nainstalujete toto rozšíření, jednoduše zvolte **přidat** > **.editorconfig File** z nabídky klikněte pravým tlačítkem nebo kontext uzel řešení, uzel projektu nebo v jakékoli složce  **Průzkumník řešení**. Toto rozšíření také zlepšuje prostředí pro úpravy *.editorconfig* souboru.

   ![Přidat .editorconfig soubor s příponou](media/editorconfig-extension-add.png)

- Vyzkoušejte si [IntelliCode rozšíření](/visualstudio/intellicode/intellicode-visual-studio). Tento experimentální rozšíření odvodí z něj styl kódu z existujícího kódu a pak vytvoří neprázdný *.editorconfig* soubor s předvolby stylu kódu již definována.

## <a name="override-editorconfig-settings"></a>Přepsat nastavení EditorConfig

Když přidáte *.editorconfig* soubor do složky ve vaší hierarchii soubor, jeho nastavení platí pro všechny příslušné soubory na této úrovni a nižší. EditorConfig nastavení pro konkrétní projekt, základ kódu nebo části základu kódu, můžete také přepsat tak, aby používala různých konvencí než ostatní části základu kódu. To může být užitečné, když zahrnout kód z někde jinde a nechcete měnit její konvence.

Chcete-li přepsat některá nebo všechna nastavení EditorConfig, přidejte *.editorconfig* souboru na úrovni hierarchie souborů chcete těchto přepsaného nastavení použít. Nové nastavení souborů EditorConfig použít na soubory na stejné úrovni a všech podadresářích.

![EditorConfig hierarchie](../ide/media/vside_editorconfig_hierarchy.png)

Pokud je zapotřebí přepsat některé, ale ne všechna nastavení, zadejte pouze tyto nastavení v *.editorconfig* souboru. Pouze vlastnosti, která explicitně zadáte v souboru nižší úrovně se přepíšou. Další nastavení z vyšší úrovně *.editorconfig* souborů i nadále. Pokud chcete zajistit, aby _žádné_ nastavení z _jakékoli_ vyšší úrovně *.editorconfig* soubory aplikují i na této části základu kódu, přidejte ```root=true``` vlastnost nižší úrovně *.editorconfig* souboru:

```EditorConfig
# top-most EditorConfig file
root = true
```

Čtení souborů EditorConfig shora dolů a posledního čtení nejbližší souborů EditorConfig. Vytváření z odpovídajících EditorConfig části se použijí v pořadí, ve kterém byly přečtěte si, tak vytváření názvů v blíže soubory přednost.

## <a name="editing-editorconfig-files"></a>Úprava souborů EditorConfig

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

```EditorConfig
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Teď, když stisknete **kartu** klíčů, získáte tabulátory místo mezer.

![Stisknutím klávesy TAB přidá znak Tab](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Řešení potíží s nastavení EditorConfig

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
- [Zásady vytváření názvů rozhraní .NET](../ide/editorconfig-naming-conventions.md)
- [Podpora EditorConfig pro služby jazyka](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](http://editorconfig.org/)
- [Funkce editoru kódu](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig (Visual Studio for Mac)](/visualstudio/mac/editorconfig)