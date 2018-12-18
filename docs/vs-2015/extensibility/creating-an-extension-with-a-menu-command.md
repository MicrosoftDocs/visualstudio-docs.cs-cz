---
title: Vytváření rozšíření pomocí příkazu nabídky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb99149a7b617d8e48e036d9e706e5e1c0a6169b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779304"
---
# <a name="creating-an-extension-with-a-menu-command"></a>Vytváření rozšíření pomocí příkazu nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit rozšíření pomocí příkazu nabídky, který spustí Poznámkový blok.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Vytvoření příkazu nabídky  
  
1.  Vytvořte projekt VSIX s názvem **FirstMenuCommand**. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C# / rozšíření**.  
  
2.  Po otevření projektu přidat vlastní příkaz šablonu položky s názvem **FirstCommand**. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a vyberte **Add / nová položka**. V **přidat novou položku** dialogové okno, přejděte na **Visual C# / rozšíření** a vyberte **vlastního příkazu**. V **název** pole v dolní části okna, změňte název souboru příkazu **FirstCommand.cs**.  
  
3.  Sestavte projekt a spusťte ladění.  
  
     Experimentální instanci sady Visual Studio se zobrazí. Další informace o experimentální instanci najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
4.  V experimentální instanci aplikace, otevřete **nástrojů / rozšíření a aktualizace** okna. Měli byste vidět **FirstMenuCommand** rozšíření tady. (Pokud otevřete **rozšíření a aktualizace** v instanci pracovního sadě Visual Studio, neuvidíte **FirstMenuCommand**).  
  
     Teď přejděte **nástroje** nabídky v experimentální instanci aplikace. Měli byste vidět **vyvolat FirstCommand** příkazu. V tomto okamžiku je právě zobrazí okno se zprávou s textem "FirstCommandPackage uvnitř FirstMenuCommand.FirstCommand.MenuItemCallback()". Uvidíme, jak se ve skutečnosti spustí program Poznámkový blok z tohoto příkazu v další části.  
  
## <a name="changing-the-menu-command-handler"></a>Změna obslužná rutina příkazu nabídky  
 Teď můžeme aktualizovat obslužná rutina příkazu Spustit Poznámkový blok.  
  
1.  Zastavit ladění a vrátit se zpět k vaší instanci pracovní sady Visual Studio. Otevřete soubor FirstCommand.cs a přidejte následující příkaz using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Najdete soukromý konstruktor FirstCommand. Toto je kde příkazu se připojili ke službě příkazu a zadaná obslužná rutina příkazu. Změňte název obslužná rutina příkazu StartNotepad, následujícím způsobem:  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Odeberte metodu MenuItemCallback a přidejte StartNotepad metodu, která se právě spusťte program Poznámkový blok:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Nyní vyzkoušejte. Při spuštění ladění projektu a klikněte na tlačítko **nástroje / vyvolat FirstCommand**, byste měli vidět instance poznámkového bloku přijít.  
  
     Můžete použít instanci <xref:System.Diagnostics.Process> má třída spustit libovolný spustitelný soubor, nejen Poznámkový blok. Vyzkoušejte si to s calc.exe, např.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Čištění experimentální prostředí  
 Pokud vyvíjíte několik rozšíření nebo stačí zkoumání výsledků s různými verzemi kódu rozšíření, experimentální prostředí mohou přestat fungovat tak, jak by měl. V takovém případě byste měli spustit skript obnovení. Je volána **resetovat Visual Studio 2015 experimentální instanci**, a je dodáván jako součást sady Visual Studio SDK. Tento skript odebere všechny odkazy na vaše rozšíření v experimentální prostředí, abyste je mohli začít úplně od začátku.  
  
 Můžete získat tohoto skriptu v jednom ze dvou způsobů:  
  
1.  Z plochy, vyhledejte **resetovat Visual Studio 2015 experimentální instanci**.  
  
2.  Z příkazového řádku spusťte následující příkaz:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>Nasazení rozšíření  
 Teď, když máte rozšíření nástroje s požadovaným způsobem, je čas přemýšlení o sdílení s přáteli nebo kolegy. Je to jednoduché, za předpokladu, že mají nainstalovanou sadu Visual Studio 2015. Všechno, co musíte udělat, je odešlete soubor .vsix, který jste vytvořili. (Nezapomeňte vytvořit v režimu vydání.)  
  
 Soubor .vsix pro tuto příponu můžete najít v adresáři bin FirstMenuCommand. Konkrétně za předpokladu, že jste vytvořili konfiguraci vydané verze, bude ve:  
  
 **\<adresář kódu > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Pokud chcete nainstalovat rozšíření, přítele musí zavřít všechny otevřené instance sady Visual Studio, pak poklikejte na soubor .vsix, kterým se zobrazí **instalátor VSIX**. Soubory se zkopírují do **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** adresáře.  
  
 Při přítele sady Visual Studio zobrazí znovu, kterou najdete FirstMenuCommand rozšíření v **nástrojů / rozšíření a aktualizace**. Že se podíváte na **rozšíření a aktualizace** odinstalace nebo zakázání rozšíření, příliš.  
  
## <a name="next-steps"></a>Další kroky  
 Tento návod vám ukázal pouze malou část můžete dělat pomocí rozšíření sady Visual Studio. Tady je krátký seznam (poměrně snadno) je dobré, které vám pomůžou s rozšířeními sady Visual Studio:  
  
1. Můžete provést mnoho dalších věcí s jednoduchý příkaz:  
  
   1.  Přidat vlastní ikonu: [přidávání ikon k příkazům nabídky](../extensibility/adding-icons-to-menu-commands.md)  
  
   2.  Změna textu příkazu nabídky: [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md)  
  
   3.  Přidání místní nabídky k příkazu: [vazby klávesové zkratky a položkami nabídky](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2. Přidat různé druhy příkazy, nabídky a panely nástrojů: [rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)  
  
3. Přidat oken nástrojů a rozšíření integrovaných okna nástrojů sady Visual Studio: [rozšíření a přizpůsobení nástrojů Windows](../extensibility/extending-and-customizing-tool-windows.md)  
  
4. Přidání technologie IntelliSense, návrhy kódu a jiné funkce pro existující kód editory: [rozšíření pro Editor a služeb jazyka](../extensibility/extending-the-editor-and-language-services.md)  
  
5. Přidání stránky možnosti a vlastnosti a nastavení uživatele do rozšíření: [rozšíření vlastností a okno Vlastnosti](../extensibility/extending-properties-and-the-property-window.md) a [rozšíření uživatelská nastavení a možnosti](../extensibility/extending-user-settings-and-options.md)  
  
   Jiné druhy rozšíření vyžaduje trochu více práce, jako je vytvoření nového typu projektu ([rozšíření projektů](../extensibility/extending-projects.md)), vytvoření nového typu editoru ([vytváření vlastních editorů a návrhářů](../extensibility/creating-custom-editors-and-designers.md)), nebo implementace rozšíření v izolovaném prostředí: [izolované prostředí sady Visual Studio](../extensibility/visual-studio-isolated-shell.md)

