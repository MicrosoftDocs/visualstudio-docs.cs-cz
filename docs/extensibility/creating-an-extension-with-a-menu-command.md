---
title: Vytváření rozšíření pomocí příkazu nabídky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 539ab866056b97f7054dda1843870dcfdd4379d9
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248134"
---
# <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky
Tento návod ukazuje, jak vytvořit rozšíření pomocí příkazu nabídky, který spustí Poznámkový blok.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-menu-command"></a>Vytvoření příkazu nabídky  
  
1.  Vytvořte projekt VSIX s názvem **FirstMenuCommand**. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C#** > **rozšiřitelnost**.  
  
2.  Po otevření projektu přidat vlastní příkaz šablonu položky s názvem **FirstCommand**. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **přidat** > **nová položka**. V **přidat novou položku** dialogové okno, přejděte na **Visual C#** > **rozšiřitelnost** a vyberte **vlastního příkazu**. V **název** pole v dolní části okna, změňte název souboru příkazu *FirstCommand.cs*.  
  
3.  Sestavte projekt a spusťte ladění.  
  
     Experimentální instanci sady Visual Studio se zobrazí. Další informace o experimentální instanci najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
4.  V experimentální instanci aplikace, otevřete **nástroje** > **rozšíření a aktualizace** okna. Měli byste vidět **FirstMenuCommand** rozšíření tady. (Pokud otevřete **rozšíření a aktualizace** v instanci pracovního sadě Visual Studio, neuvidíte **FirstMenuCommand**).  
  
     Teď přejděte **nástroje** nabídky v experimentální instanci aplikace. Měli byste vidět **vyvolat FirstCommand** příkazu. V tomto okamžiku je právě zobrazí okno se zprávou, že **FirstCommandPackage uvnitř FirstMenuCommand.FirstCommand.MenuItemCallback()**. Uvidíme, jak se ve skutečnosti spustí program Poznámkový blok z tohoto příkazu v další části.  
  
## <a name="change-the-menu-command-handler"></a>Změnit obslužná rutina příkazu nabídky  
 Teď můžeme aktualizovat obslužná rutina příkazu Spustit Poznámkový blok.  
  
1.  Zastavit ladění a vrátit se zpět k vaší instanci pracovní sady Visual Studio. Otevřít *FirstCommand.cs* soubor a přidejte následující příkaz using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Najdete soukromý konstruktor FirstCommand. Toto je kde příkazu se připojili ke službě příkazu a zadaná obslužná rutina příkazu. Změňte název obslužná rutina příkazu StartNotepad, následujícím způsobem:  
  
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
  
3.  Odeberte `MenuItemCallback` metoda a přidejte `StartNotepad` metodu, která se právě spusťte program Poznámkový blok:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Nyní vyzkoušejte. Při spuštění ladění projektu a klikněte na tlačítko **nástroje** > **vyvolat FirstCommand**, byste měli vidět instance poznámkového bloku přijít.  
  
     Můžete použít instanci <xref:System.Diagnostics.Process> má třída spustit libovolný spustitelný soubor, nejen Poznámkový blok. Vyzkoušejte si to s `calc.exe`, např.  
  
## <a name="clean-up-the-experimental-environment"></a>Vyčistěte experimentální prostředí.  
 Pokud vyvíjíte několik rozšíření nebo stačí zkoumání výsledků s různými verzemi kódu rozšíření, experimentální prostředí mohou přestat fungovat tak, jak by měl. V takovém případě byste měli spustit skript obnovení. Je volána **resetovat Visual Studio 2015 experimentální instanci**, a je dodáván jako součást sady Visual Studio SDK. Tento skript odebere všechny odkazy na vaše rozšíření v experimentální prostředí, abyste je mohli začít úplně od začátku.  
  
 Můžete získat tohoto skriptu v jednom ze dvou způsobů:  
  
1.  Z plochy, vyhledejte **resetovat Visual Studio 2015 experimentální instanci**.  
  
2.  Z příkazového řádku spusťte následující příkaz:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploy-your-extension"></a>Nasazení vašeho rozšíření  
 Teď, když máte rozšíření nástroje s požadovaným způsobem, je čas přemýšlení o sdílení s přáteli nebo kolegy. Je to jednoduché, za předpokladu, že mají nainstalovanou sadu Visual Studio 2015. Vše, co musíte udělat poslal je *VSIX* souborů, které jste vytvořili. (Nezapomeňte vytvořit v režimu vydání.)  
  
 Můžete najít *VSIX* u tohoto rozšíření v soubor *FirstMenuCommand* adresáře bin. Konkrétně za předpokladu, že jste vytvořili konfiguraci vydané verze, bude ve:  
  
 *\<adresář kódu > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix*  
  
 K instalaci rozšíření, přítele musí zavřít všechny otevřené instance sady Visual Studio a pak dvakrát klikněte *VSIX* souboru, kterým se zobrazí **instalátor VSIX**. Soubory se zkopírují do *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions* adresáře.  
  
 Při přítele sady Visual Studio zobrazí znovu, kterou najdete FirstMenuCommand rozšíření v **nástroje** > **rozšíření a aktualizace**. Že se podíváte na **rozšíření a aktualizace** odinstalace nebo zakázání rozšíření, příliš.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod vám ukázal pouze malou část můžete dělat pomocí rozšíření sady Visual Studio. Tady je krátký seznam (poměrně snadno) je dobré, které vám pomůžou s rozšířeními sady Visual Studio:  
  
1. Můžete provést mnoho dalších věcí s jednoduchý příkaz:  
  
   1.  Přidáte vlastní ikonu: [Přidání ikon k příkazům nabídky](../extensibility/adding-icons-to-menu-commands.md)  
  
   2.  Změna textu příkazu nabídky: [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3.  Přidání místní nabídky k příkazu: [Vytvoření vazby klávesové zkratky a položkami nabídky](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Přidáte různé druhy příkazy, nabídky a panely nástrojů: [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)  
  
3. Přidat oken nástrojů a rozšíření integrovaných okna nástrojů sady Visual Studio: [Rozšířit a přizpůsobit panely nástrojů](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Přidáte do existující editory kódu technologie IntelliSense, kód návrhy a další funkce: [Rozšíření služby jazyk a editor](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Přidání stránky možnosti a vlastnosti a nastavení uživatele do rozšíření: [Rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md) a [rozšířit uživatelská nastavení a Ooptions](../extensibility/extending-user-settings-and-options.md)  
  
   Jiné druhy rozšíření vyžaduje trochu více práce, jako je vytvoření nového typu projektu ([rozšíření projektů](../extensibility/extending-projects.md)), vytvoření nového typu editoru ([vytvoření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)), nebo implementaci vašeho rozšíření izolovaného prostředí: [Prostředí sady Visual Studio izolovaný režim](../extensibility/visual-studio-isolated-shell.md)