---
title: Rozšíření sady Visual Studio pro Mac návodu
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: cbf0d99bd87b31484b6c74e9a6d67ac88dc5ba99
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294302"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Rozšíření sady Visual Studio pro Mac návodu

Toto téma vás provede vytváření [jednoduché rozšíření balíčku](https://github.com/mjh4/AddIns/tree/master/DateInserter). Balíček rozšíření vytvoří nový příkaz v sadě Visual Studio pro Mac úpravy nabídky, které umožní uživateli vkládat do otevřete textový dokument aktuální datum a čas.

Tento příklad používá Tvůrce Add-in. Doplněk tvůrce vytvoří novou šablonu projektu a naplní ji požadovaných souborů pro balíček naše vlastní rozšíření.

1. Začněte tím, že spuštění sady Visual Studio pro Mac, pokud již není otevřen:

   ![Visual Studio for Mac – snímek obrazovky](media/extending-visual-studio-mac-addin3.png)

2. Nainstalujte _balíček rozšíření Maker Add-in_ pomocí Správce rozšíření. V nabídce sady Visual Studio zvolte **rozšíření...** :

   ![Karta Správce doplňků](media/extending-visual-studio-mac-addin4.png)

3. Přejděte na kartu galerie a typ `Addin Maker` do panelu hledání v pravé horní části. Vyberte doplněk Tvůrce kategorii vývoj Add-in a klikněte na <kbd>nainstalovat</kbd>. Pokud není nic se zobrazí, stiskněte tlačítko Aktualizovat a hledat znovu:

   ![Správce doplňků](media/extending-visual-studio-mac-addin5.png)

4. Teď, když je nainstalován doplněk tvůrce, můžete začít vytvářet balíček rozšíření. Začněte vytvořením nového řešení.

5. Z **dialogového okna nové řešení**, zvolte **jiných > Různé > Obecné > Xamarin Studio doplněk > C#** šablony a na následující obrazovce zadejte název nové řešení `DateInserter`:

   ![Vytvoření nového řešení](media/extending-visual-studio-mac-addin7New.png)

6. Visual Studio pro Mac se vyplní nové řešení:

   ![Mají údaj vyplněný řešení](media/extending-visual-studio-mac-addin8.png)

7. Odebrat kód šablony v `Manifest.addin.xml` a nahraďte následujícím kódem:

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

8. Teď budete muset nastavit soubory, které se nakonec postará vkládání data a času v textovém editoru. Klikněte pravým tlačítkem na uzel projektu a přidejte nový soubor. Vyberte **Obecné > prázdná třída** a pojmenujte nový soubor *InsertDateHandler*:

   ![Vložit datum obslužné rutiny](media/extending-visual-studio-mac-addin9.png)

9. Odebereme kód šablony z `InsertDateHandler.cs` a nahraďte ho následujícím kódem:

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

   Později budete rozšiřováním tyto dvě metody zástupný symbol.

10. Klikněte pravým tlačítkem na **DateInserter** projektu a vyberte **Přidat > Nový soubor**. Vyberte **Obecné > prázdný výčet**a potom zadejte název nového souboru *DateInserterCommands*:

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Přidat `InsertDate` příkaz jako nový výčet v `DateInserterCommands.cs` souboru:

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

12. V tomto okamžiku byste měli mít funkční rozšíření balíčku. Otestovat tak uložení práce a spuštění aplikace. Rozhraní IDE spustí novou instanci sady Visual Studio for Mac pomocí nového balíčku rozšíření nainstalované. Pokud přejdete **nabídky Upravit**, uvidíte, že Visual Studio for Mac obsahuje nový parametr s názvem **vložit datum**, jak je znázorněno v následujícím snímku obrazovky:

    ![Vložit datum příkaz](media/extending-visual-studio-mac-addin11.png)

    Všimněte si, že v nabídce vyberete vložit datum nemá žádný účinek, jako má aktuální implementace jenom metody zástupný symbol.

13. Rozhraní je na místě pro balíček rozšíření, a je čas na psaní kódu, která je základem vkládání datum. Nejprve, ujistěte se, že **příkazu Insert datum** je povolená pouze, když uživatel textu otevřete soubor tak, že nahradíte `Update` metoda ve `InsertDateHandler.cs` následujícím kódem:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Aktualizace příkazu `Run` metoda vložit datum a čas s následujícím kódem:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Můžeme spustit a konečně, náš balíček rozšíření a otestovat ho. V nové instanci sady Visual Studio pro Mac, vyberte **Upravit > Vložit datum**. Aktuální datum a čas bude vložena na naše stříška, jak je znázorněno v následujícím snímku obrazovky:

    ![Vložit datum – snímek obrazovky](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Viz také:

- [Vytvořit své první rozšíření (Visual Studio na Windows)](/visualstudio/extensibility/extensibility-hello-world)