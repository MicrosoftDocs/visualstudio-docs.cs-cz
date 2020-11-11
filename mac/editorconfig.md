---
title: EditorConfig
description: Použití souboru editorconfig k povolení konzistentních stylů pro kódování projektů v Visual Studio pro Mac.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.topic: how-to
ms.openlocfilehash: c7269b4272fb8ed2c73dbe9f57e94da071dc623e
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493059"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Vytvoření a úprava vlastního souboru EditorConfig

V Visual Studio pro Mac můžete přidat soubor [EditorConfig](https://editorconfig.org/) do projektu nebo řešení, abyste vynutili konzistentní styly kódování pro všechny, které fungují v základu kódu. Nastavení deklarované v souboru EditorConfig mají přednost před nastaveními globální Visual Studio pro Mac textový editor. Použití souboru EditorConfig v rámci projektu nebo základu kódu vám umožní nastavit styl kódování, předvolby a upozornění pro váš projekt. Vzhledem k tomu, že soubor je součástí vašeho základu kódu, usnadňuje všem uživatelům dodržování postupů kódování projektu, bez ohledu na integrované vývojové prostředí (IDE) nebo Editor kódu, který používají.

Soubory [EditorConfig](https://editorconfig.org/) jsou podporovány v mnoha prostředích pro IDES a editory kódu, včetně sady Visual Studio.

## <a name="supported-settings"></a>Podporovaná nastavení

Editor v Visual Studio pro Mac podporuje základní sadu [vlastností EditorConfig](https://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig také podporuje [konvence kódování](/visualstudio/ide/editorconfig-code-style-settings-reference) v jazyce C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Přidat soubor EditorConfig do projektu

### <a name="adding-a-new-editorconfig-file"></a>Přidání nového souboru EditorConfig

1. Otevřete projekt v Visual Studio pro Mac. Vyberte buď řešení, nebo uzel projektu, do kterého chcete přidat soubor EditorConfig. Přidání souboru do adresáře řešení aplikuje nastavení. editorconfig na všechny projekty v řešení.

2. Klikněte pravým tlačítkem na uzel a výběrem **přidat > nový soubor** otevřete dialogové okno **nový soubor** :

    ![Položky nabídky obsahu](media/editorconfig-image0.png)

3. Vyberte možnost **různé > prázdný textový soubor** a **pojmenujte** ji `.editorconfig` . Stisknutím klávesy **New** vytvořte soubor a otevřete ho v editoru:

    ![Dialogové okno Nový soubor](media/editorconfig-image1.png)

    Přidání položky na úrovni řešení se automaticky vytvoří a zahnízda ve složce **položky řešení** :

    ![Položka řešení zobrazená v okně řešení](media/editorconfig-image1a.png)

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

4. Nastavení ze `.editorconfig` souboru bude platit pro jakýkoli nový kód, který píšete, ale existující kód může být nutné přeformátovat, aby byl konzistentní s novým nastavením. Chcete-li použít nastavení ze `.editorconfig` souboru do existujícího zdrojového souboru, otevřete soubor a v řádku nabídek vyberte možnost **upravit formát > > formátovat dokument** ::

    ![Formátovat položku nabídky dokumentu](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Přidání existujícího souboru EditorConfig

Pokud pracujete s projektem nebo řešením, které již `.editorconfig` soubor obsahuje, neexistuje žádná akce, kterou je třeba použít pro nastavení. Jakékoli nové řádky kódu jsou formátovány podle nastavení EditorConfig.

Je možné, že budete chtít znovu použít existující `.editorconfig` soubor v projektu. Chcete-li přidat existující soubor, postupujte následovně:

1. Klikněte pravým tlačítkem na složku, do které chcete přidat, a vyberte **přidat > přidat soubory**.

2. Přejděte do adresáře požadovaného souboru.

3. Soubory začínající `.` (například `.editorconfig` ) jsou skryté soubory v MacOS, takže stiskněte kombinaci kláves **Command + Shift +.** aby byl `.editorconfig` soubor viditelný.

4. Vyberte `.editorconfig` soubor a klikněte na **otevřít** :

    ![Přidání nového okna souboru](media/editorconfig-image3b.png)

5. Až se zobrazí následující dialogové okno, vyberte možnost **zkopírovat soubor do adresáře** a vyberte **OK** :

    ![Přidat soubor do složky možnosti dialogového okna](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>Reflektování nastavení. editorconfig

Po přidání souboru EditorConfig do základu kódu se nový přidaný kód automaticky zformátuje podle zadaného nastavení. Existující kód automaticky neodráží nastavení, pokud neformátujete základ kódu.

Chcete-li odrážet nastavení ze `.editorconfig` souboru, vyberte uzel řešení a v řádku nabídek zvolte **upravit formát > > formátovat dokument** :

![Formátování dokumentu z řádku nabídek](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>Úprava souboru EditorConfig

Soubory EditorConfig používají k určení nastavení, které je vysvětleno níže v předchozím příkladu, použití jednoduchého rozložení souborů:

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

Nastavení `root` pro `true` označení tohoto souboru jako souboru nejvyšší úrovně základu kódu a všech vyšších `.editorconfig` souborů v projektu jsou ignorovány, jak je vysvětleno v části [přepsání nastavení EditorConfig](#override-editorconfig-settings) .

Každý oddíl obsahuje hranaté závorky ( **[]** ) a určuje informace o typech souborů, ke kterým by měly být tyto vlastnosti.

V předchozím příkladu jsou některá nastavení použita pro všechny soubory v projektu a ostatní jsou přidány pouze do souborů C#. Snímky obrazovky uvedené níže se zobrazí před a po `.editorconfig` použití nastavení:

**Před** :

![Před použitím nastavení editorconfig](media/editorconfig-image4.png)

**Po** :

![Po použití nastavení editorconfig](media/editorconfig-image5.png)

Další informace o dostupných nastaveních EditorConfig naleznete v části [Nastavení konvence kódování .NET pro článek EditorConfig](/visualstudio/ide/editorconfig-code-style-settings-reference) a v části [podporované vlastnosti](https://editorconfig.org/#supported-properties) v oficiální dokumentaci.

## <a name="override-editorconfig-settings"></a>Přepsat nastavení EditorConfig

V každém řešení je možné mít více než jeden `.editorconfig` soubor. Visual Studio pro Mac čte `.editorconfig` soubory shora dolů v řešení a přidává a přepisuje nastavení při jejich přechodu. To znamená, že nastavení v `.editorconfig` _nejbližším_ souboru, který budete upravovat, bude mít přednost. Nastavení jsou pořízena ze `.editorconfig` souboru stejné složky (pokud existuje), potom `.editorconfig` v nadřazené složce (pokud existuje) atd. dokud to nenajde `root=true` .

Pokud chcete zajistit, aby se _no_ v `.editorconfig` této části základu kódu nepoužívala žádná nastavení ze všech souborů vyšší úrovně, přidejte `root=true` vlastnost na začátek souboru nižší úrovně `.editorconfig` :

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>Viz také

- [Vytvoření vlastního nastavení editoru pomocí EditorConfig (Visual Studio ve Windows)](/visualstudio/ide/create-portable-custom-editor-options)