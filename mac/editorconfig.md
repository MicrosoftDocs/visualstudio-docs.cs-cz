---
title: EditorConfig
description: Pomocí souboru editorconfig umožňující konzistentní projektu kódování styly v sadě Visual Studio pro Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: d42103d17b64ee9b3fb2a0660017824490655808
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294016"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Vytváření a úpravy vlastního souboru EditorConfig

V sadě Visual Studio pro Mac, můžete přidat [EditorConfig](http://editorconfig.org/) soubor do projektu nebo řešení, které vynucují konzistentní kódování styly pro všechny uživatele, který funguje v základu kódu. Nastavení deklarované v souboru EditorConfig přednost před globální sady Visual Studio pro Mac nastavení textového editoru. Pomocí EditorConfig souborů v rámci projektu nebo základ kódu vám umožní nastavit vaši kódování styl, předvoleb a upozornění pro váš projekt. Protože soubor je součástí vašeho základu kódu, usnadňuje pro všechny uživatele na dodržují kódování údajů projektu, bez ohledu na to, které používají editoru kódu nebo prostředí IDE.

[EditorConfig](http://editorconfig.org/) souborů jsou podporovány v mnohé editory Integrovaná vývojová prostředí a kód, včetně sady Visual Studio 2017.

## <a name="supported-settings"></a>Podporovaná nastavení

Editor v sadě Visual Studio for Mac podporuje základní sadu [EditorConfig vlastnosti](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig podporuje také [konvence kódování](/visualstudio/ide/editorconfig-code-style-settings-reference) v jazyce C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Přidejte do projektu soubor EditorConfig

### <a name="adding-a-new-editorconfig-file"></a>Když přidáte nový soubor EditorConfig

1. Otevřete projekt v sadě Visual Studio pro Mac. Vyberte řešení nebo projekt uzel, který chcete přidat EditorConfig soubor. Přidání souboru do adresáře řešení .editorconfig nastavení platí pro všechny projekty v řešení.

2. Klikněte pravým tlačítkem na uzel a vyberte možnost **Přidat > Nový soubor** otevřít **nový soubor** dialogové okno:

    ![Položky nabídky obsahu](media/editorconfig-image0.png)

3. Zvolte **různé > prázdný textový soubor** a přiřaďte mu **název** `.editorconfig`. Stisknutím klávesy **nový** k vytvoření souboru a otevřít ji v editoru:

    ![Dialogové okno Nový soubor](media/editorconfig-image1.png)

    Přidání položky na úrovni řešení automaticky vytvoří a vnoří ho **položky řešení** složky:

    ![Položka řešení, které jsou zobrazeny v oblasti řešení](media/editorconfig-image1a.png)

4. Upravte soubor. Příklad:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Nastavení z `.editorconfig` souboru budou platit pro nový kód, který napíšete, ale existující kód může třeba naformátována být konzistentní s novým nastavením. Chcete-li použít nastavení z `.editorconfig` soubor existující zdrojový soubor, otevřete soubor a zvolte **Upravit > Formát > formát dokumentu** z řádku nabídek::

    ![Položka nabídky Formát dokumentu](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Přidání stávajícího souboru EditorConfig

Pokud pracujete s projektem nebo řešení, která již obsahuje `.editorconfig` souboru, nic, musíte udělat v aplikaci nastavení. Všechny nové řádky kódu se formátují podle nastavení EditorConfig.

Můžete chtít znovu použít existující `.editorconfig` souboru ve vašem projektu. Chcete-li přidat existující soubor, postupujte takto:

1. Klikněte pravým tlačítkem na složku, chcete ho přidat do a vyberte **Přidat > Přidat soubory**.

2. Přejděte do adresáře požadovaný soubor.

3. Soubory začínající `.` (například `.editorconfig`) jsou skryté soubory v systému macOS, takže stiskněte **Command + Shift +.** Chcete-li `.editorconfig` souborů viditelné.

4. Vyberte `.editorconfig` souboru a klikněte na tlačítko **otevřít**:

    ![přidáním nového okna souboru](media/editorconfig-image3b.png)

5. Jakmile se zobrazí se následující dialogové okno, vyberte **zkopírujte soubor do adresáře** možnost a vyberte **OK**:

    ![Přidejte soubor do složky dialogové okno Možnosti](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Odráží nastavení .editorconfig

Po přidání souboru EditorConfig do vašeho základu kódu, je automaticky formátován jakékoli nový kód přidaný podle zadaného nastavení. Existující kód neodráží automaticky nastavení není-li formátovat základu kódu.

Tak, aby odrážely nastavení z `.editorconfig` souboru, vyberte uzel řešení a zvolte **Upravit > Formát > formát dokumentu** z řádku nabídek:

![Formátovat dokument na řádku nabídek](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>Úpravy souboru EditorConfig

Zadejte nastavení, které jsou vysvětleny níže použijeme předchozí příklad pomocí souborů EditorConfig jednoduchý soubor rozložení:

```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Nastavení `root` k `true` označí tento soubor jako soubor nejvrchnější základu kódu a výše `.editorconfig` soubory v projektu jsou ignorovány, jak je vysvětleno v [přepsat nastavení EditorConfig](#override-editorconfig-settings) oddílu.

Každý oddíl je označen čtverec (**[] č.**) složené závorky a určuje informace o typech souborů, by se týkají následující vlastnosti.

V předchozím příkladu některá nastavení se použijí na všechny soubory v projektu a ostatní jsou přidány pouze pro soubory C#. Následujících snímcích obrazovky zobrazit před a po `.editorconfig` aplikovala nastavení:

**Před**:

![Před nastavení editorconfig](media/editorconfig-image4.png)

**Po**:

![Po použití nastavení editorconfig](media/editorconfig-image5.png)

Další informace o dostupných nastaveních EditorConfig, najdete v článku [nastavení konvence pro EditorConfig psaní kódu .NET](/visualstudio/ide/editorconfig-code-style-settings-reference) článku a [nepodporuje vlastnosti](http://editorconfig.org/#supported-properties) části na oficiální dokumentaci.

## <a name="override-editorconfig-settings"></a>Přepsat nastavení EditorConfig

Je možné mít víc než jeden `.editorconfig` souboru v každé řešení. Visual Studio pro Mac čtení `.editorconfig` soubory shora dolů v řešení, přidávání a přepsání nastavení jako jeho nepovede. To znamená, že v nastavení `.editorconfig` _nejbližší_ při úpravě souboru bude mít přednost. Nastavení pocházejí ze `.editorconfig` souborové složce (pokud existuje), pak bude `.editorconfig` v nadřazené složce (pokud existuje, který) atd. dokud nenajde `root=true`.

Pokud chcete zajistit, aby _žádné_ nastavení z jakékoli vyšší úrovně `.editorconfig` soubory aplikují i na této části základu kódu, přidejte `root=true` vlastnost k hornímu okraji nižší úrovně `.editorconfig` souboru:

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Viz také:

- [Vytvořit nastavení vlastního editoru pomocí řešení EditorConfig (Visual Studio na Windows)](/visualstudio/ide/create-portable-custom-editor-options)