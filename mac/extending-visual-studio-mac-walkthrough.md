---
title: Rozšíření návodu k Visual Studiu pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: c5b3b759b32acfc86b4b584b3f3d52298c138a2c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983286"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Rozšíření návodu k Visual Studiu pro Mac

Toto téma vás provede [vytvořením jednoduchého balíčku rozšíření](https://github.com/mjh4/AddIns/tree/master/DateInserter). Balíček rozšíření vytvoří nový příkaz v nabídce Visual Studio for Mac's Edit, který uživateli umožní vložit aktuální datum a čas do otevřeného textového dokumentu.

Tento příklad používá Add-in Maker. Tvůrce doplňků vytvoří novou šablonu projektu a naplní ji požadovanými soubory pro náš vlastní balíček rozšíření.

1. Začněte spuštěním Visual Studia pro Mac, pokud ještě není otevřený:

   ![Snímek obrazovky Visual Studio for Mac](media/extending-visual-studio-mac-addin3.png)

2. Nainstalujte _balíček rozšíření Add-in Maker_ pomocí Správce rozšíření. V nabídce Visual Studio zvolte **Rozšíření...**:

   ![Karta Správce doplňku](media/extending-visual-studio-mac-addin4.png)

3. Přejděte na kartu `Addin Maker` Galerie a zadejte do vyhledávacího panelu vpravo nahoře. V kategorii Vývoj doplňků vyberte Addin Maker a klepněte na <kbd>tlačítko Instalovat</kbd>. Pokud se nic nezobrazí, stiskněte tlačítko Aktualizovat a znovu vyhledejte:

   ![Správce doplňků](media/extending-visual-studio-mac-addin5.png)

4. Teď, když je nainstalován Addin Maker, můžete začít vytvářet balíček rozšíření. Začněte vytvořením nového řešení.

5. V **dialogovém okně Nové řešení**zvolte **Jiné > různé > Obecné > šablona Xamarin Studio Addin > C#** a na následujícím názvu obrazovky nové řešení `DateInserter`:

   ![Vytvoření nového řešení](media/extending-visual-studio-mac-addin7New.png)

6. Visual Studio pro Mac naplní nové řešení:

   ![Nabytá řešení](media/extending-visual-studio-mac-addin8.png)

7. Odeberte kód `Manifest.addin.xml` šablony a nahraďte ho následujícím:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
      <ExtensionModel>
          <Extension path = "/MonoDevelop/Ide/Commands/Edit">
              <Command id = "DateInserter.DateInserterCommands.InsertDate"
                  _label = "Insert Date"
                  defaultHandler = "DateInserter.InsertDateHandler" />
          </Extension>

          <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
              <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
          </Extension>
      </ExtensionModel>
   ```

8. Nyní je třeba nastavit soubory, které budou nakonec zpracovávat vložení data a času do textového editoru. Klikněte pravým tlačítkem myši na uzel projektu a přidejte nový soubor. Vyberte **Obecné > Prázdná třída** a pojmenujte nový soubor *InsertDateHandler*:

   ![Vložit obslužnou rutinu data](media/extending-visual-studio-mac-addin9.png)

9. Odebereme kód `InsertDateHandler.cs` šablony a nahraďte ho následujícím kódem:

   ```cs
   using MonoDevelop.Components.Commands;
   using MonoDevelop.Ide;
   using MonoDevelop.Ide.Gui;
   using System;

   namespace DateInserter
   {
      class InsertDateHandler : CommandHandler
      {
          protected override void Run()
          {

          }

          protected override void Update(CommandInfo info)
          {

          }
      }
   }
   ```

   Tyto dva zástupné metody rozšíříme později.

10. Klikněte pravým tlačítkem myši na projekt **DateInserter** a vyberte **přidat > nový soubor**. Vyberte **Možnost Obecné > Prázdný výčet**a pojmenujte nový soubor *DateInserterCommands*:

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Přidejte `InsertDate` příkaz jako nový výčet `DateInserterCommands.cs` do souboru:

    ``` cs
    using System;

    namespace DateInserter
    {
      public enum DateInserterCommands
      {
          InsertDate,
      }
    }
    ```

12. V tomto okamžiku byste měli mít balíček pracovní rozšíření. Můžete to vyzkoušet uložením práce a spuštěním aplikace. IDE spustí novou instanci Visual Studio pro Mac s nainstalovaným novým balíčkem rozšíření. Pokud přejdete do **nabídky Úpravy**, uvidíte, že Visual Studio pro Mac má novou možnost s názvem **Vložit datum**, jak ukazuje snímek obrazovky níže:

    ![Příkaz Vložit datum](media/extending-visual-studio-mac-addin11.png)

    Všimněte si, že výběr Vložit datum z nabídky nemá žádný vliv, protože aktuální implementace má pouze zástupné metody.

13. Rámec je na místě pro balíček rozšíření a je čas napsat kód, který povýše vložení data. Nejprve se ujistěte, že **příkaz Vložit datum** je povolen pouze v `Update` případě, že má uživatel otevřený textový soubor nahrazením metody následujícím `InsertDateHandler.cs` kódem:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Aktualizujte `Run` metodu příkazu a vložte datum a čas pomocí následujícího kódu:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Nakonec spustíme náš rozšiřující balíček a otestujeme jej. V nové instanci Visual Studia for Mac vyberte **Upravit > Datum vložení**. Aktuální datum a čas je vložen na naší stříšce, jak je znázorněno na obrázku níže:

    ![Snímek obrazovky S datem vložení](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Viz také

- [Vytvoření prvního rozšíření (Visual Studio ve Windows)](/visualstudio/extensibility/extensibility-hello-world)