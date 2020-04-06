---
title: Vytvoření rozšíření pomocí příkazu nabídky | Dokumenty společnosti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739556"
---
# <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky

Tento návod ukazuje, jak vytvořit rozšíření s příkazem nabídky, který spouští poznámkový blok.

## <a name="prerequisites"></a>Požadavky

Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Vytvoření příkazu nabídky

1. Vytvořte projekt VSIX s názvem **FirstMenuCommand**. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** vyhledáním "vsix".

2. Při otevření projektu přidejte vlastní šablonu položky příkazu s názvem **FirstCommand**. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu a vyberte **přidat** > **novou položku**. V dialogovém okně **Přidat novou položku** přejděte na položku**Rozšiřitelnost** **jazyka Visual C#** > a vyberte **vlastní příkaz**. V poli **Název** v dolní části okna změňte název příkazového souboru na *FirstCommand.cs*.

3. Sestavení projektu a začít ladění.

    Zobrazí se experimentální instance sady Visual Studio. Další informace o experimentální instanci naleznete [v tématu Experimentální instance](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. V experimentální instanci otevřete okno Rozšíření a aktualizace **nástrojů.** > **Extensions and Updates** Zde by se mělo zobrazit rozšíření **FirstMenuCommand.** (Pokud otevřete **rozšíření a aktualizace** v pracovní instanci sady Visual Studio, neuvidíte **FirstMenuCommand).**

::: moniker-end

::: moniker range=">=vs-2019"

4. V experimentální instanci otevřete okno **Správa** > **rozšíření.** Zde by se mělo zobrazit rozšíření **FirstMenuCommand.** (Pokud otevřete spravovat rozšíření v pracovní **instanci** sady Visual Studio, neuvidíte **FirstMenuCommand).**

::: moniker-end

Nyní přejděte do nabídky **Nástroje** v experimentální instanci. Měli byste vidět **příkaz Invoke FirstCommand.** V tomto okamžiku příkaz vyvolá okno se zprávou, které říká **FirstCommandPackage Inside FirstMenuCommand.FirstCommand.MenuItemCallback()**. Uvidíme, jak skutečně spustit Poznámkový blok z tohoto příkazu v další části.

## <a name="change-the-menu-command-handler"></a>Změna obslužné rutiny příkazů nabídky

Nyní aktualizujte obslužnou rutinu příkazu pro spuštění programu Poznámkový blok.

1. Přestaňte ladit a vraťte se do pracovní instance sady Visual Studio. Otevřete *soubor FirstCommand.cs* a přidejte následující příkaz using:

    ```csharp
    using System.Diagnostics;
    ```

2. Najděte soukromé FirstCommand konstruktoru. Toto je místo, kde je příkaz připojen ke službě příkazu a je zadána obslužná rutina příkazu. Změňte název obslužné rutiny příkazů na StartNotepad takto:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Odstraňte `MenuItemCallback` metodu `StartNotepad` a přidejte metodu, která se spustí poznámkový blok:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Teď to vyzkoušejte. Když začnete ladit projekt a klepnete na **tlačítko Nástroje** > **vyvolat FirstCommand**, měli byste vidět instanci poznámkového bloku přijít.

    Můžete použít instanci <xref:System.Diagnostics.Process> třídy ke spuštění libovolného spustitelného souboru, nikoli pouze poznámkového bloku. Zkuste to `calc.exe`s , například.

## <a name="clean-up-the-experimental-environment"></a>Vyčištění experimentálního prostředí

Pokud vyvíjíte více rozšíření nebo jen zkoumání výsledků s různými verzemi kódu rozšíření, experimentální prostředí může přestat fungovat tak, jak by měl. V takovém případě byste měli spustit resetovací skript. Nazývá se **Obnovit visual studio experimentální instance**a dodává se jako součást sady Visual Studio SDK. Tento skript odebere všechny odkazy na vaše rozšíření z experimentálního prostředí, takže můžete začít od začátku.

K tomuto skriptu se dostanete jedním ze dvou způsobů:

1. Na ploše **vyhledejte obnovení experimentální instance sady Visual Studio**.

2. Z příkazového řádku spusťte následující:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Nasazení rozšíření

Nyní, když máte rozšíření nástroje běží tak, jak chcete, je čas přemýšlet o sdílení se svými přáteli a kolegy. To je snadné, pokud mají nainstalovanou Visual Studio 2015. Jediné, co musíte udělat, je poslat jim *.vsix* soubor, který jste vytvořili. (Nezapomeňte jej sestavit v režimu vydání.)

Soubor *.vsix* pro tuto příponu naleznete v adresáři přihrádky *FirstMenuCommand.* Konkrétně za předpokladu, že jste vytvořili konfiguraci vydání, bude v:

*\<adresář kódu>\FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*

Chcete-li nainstalovat rozšíření, váš přítel musí zavřít všechny otevřené instance sady Visual Studio a potom poklepat na soubor *.vsix,* který vyvolá **Instalační program VSIX**. Soubory jsou zkopírovány do adresáře *%LocalAppData%\Microsoft\VisualStudio\<verze>\Extensions.*

Když váš přítel znovu vyvolá Visual Studio, najdou rozšíření FirstMenuCommand v **rozšíření nástroje** > **a aktualizace**. Mohou také přejít na **rozšíření a aktualizace** a odinstalovat nebo zakázat rozšíření.

## <a name="next-steps"></a>Další kroky

Tento návod se zobrazí pouze malou část, co můžete dělat s rozšířením sady Visual Studio. Tady je krátký seznam dalších (přiměřeně jednoduchých) věcí, které můžete dělat s rozšířeními sady Visual Studio:

1. Pomocí jednoduchého příkazu nabídky můžete dělat mnohem více věcí:

   1. Přidání vlastní ikony: [Přidání ikon do příkazů nabídky](../extensibility/adding-icons-to-menu-commands.md)

   2. Změna textu příkazu nabídky: [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Přidání klávesové zkratky nabídky k příkazu: [Vazba klávesových zkratek na položky nabídky](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Přidání různých druhů příkazů, nabídek a panelů nástrojů: [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)

3. Přidání oken nástrojů a rozšíření vestavěných oken nástrojů sady Visual Studio: [Rozšíření a přizpůsobení oken nástrojů](../extensibility/extending-and-customizing-tool-windows.md)

4. Přidání technologie IntelliSense, návrhů kódu a dalších funkcí do stávajících editorů kódu: [Rozšíření editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md)

5. Přidání stránek možností a vlastností a uživatelských nastavení do rozšíření: [Rozšíření vlastností a okna Vlastnosti](../extensibility/extending-properties-and-the-property-window.md) a [Rozšíření uživatelských nastavení a možností](../extensibility/extending-user-settings-and-options.md)

   Jiné druhy rozšíření vyžadují trochu více práce, jako je například vytvoření nového typu projektu ([Rozšířit projekty),](../extensibility/extending-projects.md)vytvoření nového typu editoru ([Vytvořit vlastní editory a návrháře](../extensibility/creating-custom-editors-and-designers.md)) nebo implementace rozšíření v izolovaném prostředí: [Izolované prostředí Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
