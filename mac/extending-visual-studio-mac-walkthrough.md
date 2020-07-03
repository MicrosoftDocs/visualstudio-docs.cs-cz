---
title: Rozšíření Visual Studio pro Macho návodu
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.topic: how-to
ms.openlocfilehash: 8b0f1213d500563e9fa6f3574c6b622e3214e03a
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939166"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Rozšíření Visual Studio pro Macho návodu

Toto téma vás provede vytvořením [jednoduchého balíčku rozšíření](https://github.com/mjh4/AddIns/tree/master/DateInserter). Balíček rozšíření vytvoří nový příkaz v nabídce úprav Visual Studio pro Mac, která umožňuje uživateli vložit aktuální datum a čas do otevřeného textového dokumentu.

Tento příklad používá tvůrce doplňku. Tvůrce doplňku vytvoří novou šablonu projektu a naplní ji požadovanými soubory pro náš vlastní balíček rozšíření.

1. Začněte spuštěním Visual Studio pro Mac, pokud už není otevřený:

   ![Snímek obrazovky Visual Studio pro Mac](media/extending-visual-studio-mac-addin3.png)

2. Nainstalujte _balíček rozšíření doplňku tvůrce doplňku_ pomocí Správce rozšíření. V nabídce sady Visual Studio vyberte možnost **rozšíření...**:

   ![Karta Správce doplňků](media/extending-visual-studio-mac-addin4.png)

3. Přejděte na kartu Galerie a zadejte `Addin Maker` do pravého horního panelu hledání. V kategorii vývoje doplňku vyberte možnost tvůrce doplňku a klikněte na <kbd>nainstalovat</kbd>. Pokud se nic neobjeví, zkuste znovu spustit aktualizaci a prohledat:

   ![Správce doplňků](media/extending-visual-studio-mac-addin5.png)

4. Teď, když je doplněk AddIn maker nainstalovaný, můžete začít sestavovat balíček rozšíření. Začněte vytvořením nového řešení.

5. V **dialogovém okně nové řešení**vyberte **další > různé > obecné > Xamarin Studio Template >** a na následující obrazovce zadejte nové řešení `DateInserter` :

   ![Vytváření nového řešení](media/extending-visual-studio-mac-addin7New.png)

6. V Visual Studio pro Mac se naplní nové řešení:

   ![Vyplněné řešení](media/extending-visual-studio-mac-addin8.png)

7. Odeberte kód šablony `Manifest.addin.xml` a nahraďte ji následujícím kódem:

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

8. Nyní je třeba nastavit soubory, které budou nakonec zpracovávat data a čas do textového editoru. Klikněte pravým tlačítkem myši na uzel projektu a přidejte nový soubor. Vyberte **obecné > prázdnou třídu** a pojmenujte nový soubor *InsertDateHandler*:

   ![Obslužná rutina data vložení](media/extending-visual-studio-mac-addin9.png)

9. Pojďme odebrat kód šablony z `InsertDateHandler.cs` a nahradit ho následujícím kódem:

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

   Tyto dvě zástupné metody rozšíříme později.

10. Klikněte pravým tlačítkem na projekt **DateInserter** a vyberte **Přidat > nový soubor**. Vyberte **obecné > prázdný výčet**a potom zadejte název nového souboru *DateInserterCommands*:

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Přidejte `InsertDate` příkaz jako nový výčet do `DateInserterCommands.cs` souboru:

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

12. V tomto okamžiku byste měli mít funkční balíček rozšíření. Můžete ho otestovat uložením práce a spuštěním aplikace. Rozhraní IDE spustí novou instanci Visual Studio pro Mac s nainstalovaným novým balíčkem rozšíření. Pokud přejdete do **nabídky upravit**, uvidíte, že Visual Studio pro Mac má novou možnost s názvem **Vložit datum**, jak je znázorněno na následujícím snímku obrazovky:

    ![Vložit datum – příkaz](media/extending-visual-studio-mac-addin11.png)

    Všimněte si, že výběr možnosti Vložit datum z nabídky nemá žádný účinek, protože aktuální implementace má pouze zástupné metody.

13. Rozhraní je pro balíček rozšíření zavedeno a je čas napsat kód, který splňuje datum vložení. Nejprve se ujistěte, že je **příkaz Vložit datum** povolen pouze v případě, že má uživatel otevřený textový soubor nahrazením `Update` metody v `InsertDateHandler.cs` následujícím kódu:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Aktualizujte metodu příkazu `Run` pro vložení data a času s následujícím kódem:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Nakonec spustíme náš balíček rozšíření, abychom ho otestovali. V nové instanci Visual Studio pro Mac vyberte **upravit > datum vložení**. Aktuální datum a čas jsou vloženy do našeho blikajícího kurzoru, jak je znázorněno na snímku obrazovky níže:

    ![Snímek obrazovky pro vložení data](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Viz také

- [Vytvoření prvního rozšíření (Visual Studio ve Windows)](/visualstudio/extensibility/extensibility-hello-world)