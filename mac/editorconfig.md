---
title: EditorConfig
description: Použití souboru editorconfig k povolení konzistentních stylů kódování projektů v Sadě Visual Studio pro Mac.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 6f6241c114d636cc8cb01cf5c4bf9ba2b5106701
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "73716886"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Vytvoření a úprava vlastního souboru EditorConfig

V Sadě Visual Studio pro Mac můžete do projektu nebo řešení přidat soubor [EditorConfig,](https://editorconfig.org/) který vynucuje konzistentní styly kódování pro všechny uživatele, kteří pracují v základu kódu. Nastavení deklarovaná v souboru EditorConfig mají přednost před globálním nastavením textového editoru sady Visual Studio for Mac. Použití souboru EditorConfig v rámci projektu nebo codebase umožňuje nastavit styl kódování, předvolby a upozornění pro váš projekt. Vzhledem k tomu, že soubor je součástí základu kódu, usnadňuje všem uživatelům dodržovat postupy kódování projektu, bez ohledu na rozhraní IDE nebo editor kódu, které používají.

[EditorConfig](https://editorconfig.org/) soubory jsou podporovány na mnoha IDE a editory kódu, včetně Visual Studio.

## <a name="supported-settings"></a>Podporovaná nastavení

Editor v Sadě Visual Studio pro Mac podporuje základní sadu [vlastností EditorConfig](https://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig také podporuje [kódování konvence](/visualstudio/ide/editorconfig-code-style-settings-reference) v C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Přidání souboru EditorConfig do projektu

### <a name="adding-a-new-editorconfig-file"></a>Přidání nového souboru EditorConfig

1. Otevřete projekt ve Visual Studiu pro Mac. Vyberte buď uzel řešení nebo uzel projektu, do kterého chcete přidat soubor EditorConfig. Přidání souboru do adresáře řešení použije nastavení .editorconfig na všechny projekty v řešení.

2. Klikněte pravým tlačítkem myši na uzel a výběrem **možnosti Přidat > nový soubor** otevřete dialogové okno Nový **soubor:**

    ![Položky nabídky Obsahu](media/editorconfig-image0.png)

3. Zvolte **Různé > Prázdný textový soubor** a pojmenujte jej . **Name** `.editorconfig` Stisknutím **klávesy Nový** soubor vytvořte a otevřete jej v editoru:

    ![Dialogové okno Nový soubor](media/editorconfig-image1.png)

    Přidání položky na úrovni řešení se automaticky vytvoří a vnoří do složky **Položky řešení:**

    ![Položka řešení zobrazená v panelu řešení](media/editorconfig-image1a.png)

4. Upravte soubor. Například:

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

4. Nastavení ze `.editorconfig` souboru se bude vztahovat na všechny nové kód, který píšete, ale existující kód může být nutné přeformátovat, aby byl konzistentní s novým nastavením. Chcete-li použít `.editorconfig` nastavení ze souboru na existující zdrojový soubor, otevřete soubor a z panelu nabídek zvolte **Upravit > formát > formát dokumentu::**

    ![Formát položky nabídky Dokument](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Přidání existujícího souboru EditorConfig

Pokud pracujete s projektem nebo řešením, `.editorconfig` které již obsahuje soubor, není nic, co musíte udělat pro použití nastavení. Všechny nové řádky kódu jsou formátovány podle nastavení EditorConfig.

Můžete chtít znovu použít `.editorconfig` existující soubor v projektu. Chcete-li přidat existující soubor, postupujte takto:

1. Klikněte pravým tlačítkem myši na složku, do které ji chcete přidat, a vyberte **přidat > přidat soubory**.

2. Přejděte do adresáře požadovaného souboru.

3. Soubory začínající `.` na `.editorconfig`(například) jsou skryté soubory v systému macOS, takže stiskněte **command + Shift + .** aby byl `.editorconfig` soubor viditelný.

4. Vyberte `.editorconfig` soubor a klepněte na **Otevřít**:

    ![přidání nového okna souboru](media/editorconfig-image3b.png)

5. Až se zobrazí následující dialogové okno, vyberte možnost **Kopírovat soubor do adresáře** a vyberte **OK**:

    ![Přidání možností dialogového okna Přidat soubor do složky](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Zrcadlení nastavení .editorconfig

Jakmile přidáte soubor EditorConfig do základu kódu, každý nový přidaný kód se automaticky naformátuje podle zadaného nastavení. Existující kód automaticky neodráží nastavení, pokud nenaformátujete základ kódu.

Chcete-li zrcadlit `.editorconfig` nastavení ze souboru, vyberte uzel řešení a z řádku nabídek zvolte **Upravit > formát > formát dokumentu:**

![Formátování dokumentu z řádku nabídek](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>Úprava souboru EditorConfig

EditorConfig soubory používají jednoduché rozložení souborů k určení nastavení, což je vysvětleno níže pomocí předchozího příkladu:

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

Nastavení `root` `true` příznaků tohoto souboru jako nejvyššísoubor základu kódu `.editorconfig` a všechny vyšší soubory v projektu jsou ignorovány, jak je vysvětleno v části [Přepsat EditorConfig Nastavení.](#override-editorconfig-settings)

Každý oddíl je označen čtvercovými závorkami (**[ ]**) a určuje informace o typech souborů, ke kterým by se měly následující vlastnosti vztahuje.

Ve výše uvedeném příkladu jsou některá nastavení použita pro všechny soubory v projektu a jiná jsou přidána pouze do souborů Jazyka C#. Níže uvedené snímky obrazovky ukazují `.editorconfig` před a po použití nastavení:

**Před**:

![Před použitím nastavení editorconfig](media/editorconfig-image4.png)

**Po**:

![po použití nastavení editorconfig](media/editorconfig-image5.png)

Další informace o dostupných nastaveních EditorConfig naleznete v nastavení konvence kódování .NET pro článek [EditorConfig](/visualstudio/ide/editorconfig-code-style-settings-reference) a v části [Podporované vlastnosti](https://editorconfig.org/#supported-properties) v oficiální dokumentaci.

## <a name="override-editorconfig-settings"></a>Přepsat nastavení konfigurace editoru

Je možné mít více než `.editorconfig` jeden soubor v každém řešení. Visual Studio pro `.editorconfig` Mac čte soubory shora dolů v řešení, přidávání a přepsání nastavení, jak to jde. To znamená, že `.editorconfig` nastavení v _nejbližším_ souboru, který upravujete, bude mít přednost. Nastavení jsou převzaty ze souboru `.editorconfig` stejné složky `.editorconfig` (pokud existuje), pak v nadřazené složce (pokud existuje), atd. dokud nenajde `root=true`.

Pokud chcete zajistit, aby se na `.editorconfig` tuto část základu kódu _nepoužila žádná_ nastavení ze souborů vyšší úrovně, přidejte `root=true` vlastnost do horní části souboru nižší úrovně: `.editorconfig`

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Viz také

- [Vytvoření vlastního nastavení editoru pomocí EditorConfig (Visual Studio v systému Windows)](/visualstudio/ide/create-portable-custom-editor-options)