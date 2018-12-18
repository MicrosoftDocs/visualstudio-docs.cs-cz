---
title: Vytvoření webové aplikace v ASP.NET CoreC#
description: Zjistěte, jak vytvořit jednoduchou webovou aplikaci Hello World v sadě Visual Studio s C# a ASP.NET Core, krok za krokem.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: mvc,seodec18
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: fb9dbc94d06bbb260884a2379e2427969fec1031
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159240"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Rychlý start: Vytvoření vaší první webové aplikace ASP.NET Core pomocí sady Visual Studio

V tomto úvodu 5 až 10 minut na tom, jak pomocí sady Visual Studio vytvoříte jednoduchou webovou aplikaci "Hello World" pomocí šablony projektu ASP.NET a programovací jazyk C#.

## <a name="before-you-begin"></a>Než začnete

### <a name="install-visual-studio"></a>Instalace sady Visual Studio

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stránku a nainstalovat zdarma.

### <a name="update-visual-studio"></a>Aktualizace sady Visual Studio

Pokud jste již nainstalovali aplikaci Visual Studio, ujistěte se, že používáte nejnovější verzi. Další informace o tom, jak aktualizovat vaši instalaci, najdete v článku [aktualizace Visual Studio 2017 na nejnovější verzi](../install/update-visual-studio.md) stránky.

### <a name="choose-your-theme-optional"></a>Zvolte motiv (volitelné)

Tento rychlý úvodní kurz obsahuje snímky obrazovky, použít tmavý motiv. Pokud nepoužíváte tmavý motiv, ale chtěli, najdete v článku [přizpůsobit IDE sady Visual Studio a Editor](quickstart-personalize-the-ide.md) stránku a zjistěte, jak.

## <a name="create-a-project"></a>Vytvoření projektu

Pokud chcete začít, vytvoříte projekt webové aplikace ASP.NET Core. Typ projektu obsahuje všechny soubory šablony k vytvoření webové aplikace, než jste přidali ještě nic!

1. Otevřete Visual Studio 2017.

1. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

1. V levém podokně **nový projekt** dialogového okna rozbalte **Visual C#** a klikněte na tlačítko **.NET Core**. V prostředním podokně vyberte **webové aplikace ASP.NET Core**. Pojmenujte svůj soubor `HelloWorld` a zvolte **OK**.

   ![Vytvořit nový projekt webové aplikace ASP.NET Core pro jazyk C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Pokud se nezobrazí **.NET Core** kategorii šablony projektu, zvolte **otevřít instalační program Visual Studio** odkaz v levém podokně. (V závislosti na nastavení zobrazení může být potřeba stránku posunout, aby ji.)
   >
   > ![Otevřít instalační program sady Visual Studio z dialogového okna Nový projekt](../ide/media/open-visual-studio-installer.png)
   >
   > Spustí se instalační program pro Visual Studio. Zvolte **vývoj pro ASP.NET a web** úlohy a klikněte na tlačítko **změnit**.
   >
   > ![Úlohy technologie ASP.NET v instalačním programu VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Může mít ukončit sadu Visual Studio, abyste mohli pokračovat v instalaci nové úlohy.)

1. V **nová webová aplikace ASP.NET Core** dialogu **ASP.NET Core 2.0** nebo novější z hlavní nabídky rozevíracího seznamu.

   > [!NOTE]
   > Pokud nevidíte **ASP.NET Core 2.0** nebo novější, ujistěte se, že používáte nejnovější verzi sady Visual Studio. Další informace o tom, jak aktualizovat vaši instalaci, najdete v článku [aktualizace Visual Studio 2017 na nejnovější verzi](../install/update-visual-studio.md) stránky.

1. Dále zvolte **webovou aplikaci**a klikněte na tlačítko **OK**.

   ![Dialogové okno nové webové aplikace ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

Brzy NATO Visual Studio otevře soubor projektu.

## <a name="create-the-app"></a>Vytvoření aplikace

1. V **Průzkumníka řešení**, rozbalte **stránky** složky a klikněte na tlačítko **About.cshtml**.

   ![Zvolte soubor About.cshtml z Průzkumníka řešení](../ide/media/csharp-aspnet-about-page-html-file.png)

   Tento soubor odpovídá na stránku s názvem **o** ve webové aplikaci.

   ![Na stránce o ve webové aplikaci](../ide/media/csharp-aspnet-about-page.png)

   V editoru HTML zobrazí kód pro oblasti "Další informace" **o** stránky.

   ![Kód HTML pro další informace o oblasti v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Změní celý text "Další informace" číst "**Hello World!**".

   ![Změnit výchozí kód HTML pro další informace o oblasti v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. V **Průzkumníka řešení**, rozbalte **About.cshtml**a klikněte na tlačítko **About.cshtml.cs**. (Tento soubor také odpovídá **o** stránka ve webové aplikaci.)

   ![Zvolte soubor About.cshtml z Průzkumníka řešení](../ide/media/csharp-aspnet-about-page-code-file.png)

   V editoru, zobrazí se vám C# kód, který obsahuje text "Popis aplikace" oblasti **o** stránky.

   ![Kód jazyka C# pro oblasti Popis aplikace v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Změní celý text zprávy "Popis aplikace" číst "**jaká je Moje zpráva?**".

   ![Změnit výchozí text zprávy pro oblasti Popis aplikace v editoru sady Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-app"></a>Spuštění aplikace

1. Stisknutím klávesy **Ctrl**+**F5** ke spuštění aplikace a otevřete ho ve webovém prohlížeči.

   > [!NOTE]
   > Pokud se zobrazí chybová zpráva s upozorněním, **nelze se připojit k webovému serveru služby IIS Express**, nebo chybovou zprávu s odkazem na server certifikát SSL, zavřete sadu Visual Studio. Dále otevřete Visual Studio s použitím **spustit jako správce** možnost v nabídce klikněte pravým tlačítkem nebo kontext. Spusťte aplikaci znovu.

1. V horní části webové stránky, zvolte **o**.

   ![Vyberte o z webové stránky](../ide/media/csharp-aspnet-home-page-about.png)

1. Zobrazení aktualizované text, který jste přidali do **o** stránky.

   ![Zobrazit aktualizované informace o stránce obsahující text, který jste přidali](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Zavřete webový prohlížeč.

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli ještě něco o jazyce C#, ASP.NET Core a Visual Studio IDE (integrované vývojové prostředí).

## <a name="next-steps"></a>Další kroky

Další informace najdete dál v následujícím kurzu:

> [!div class="nextstepaction"]
> [Začínáme s C# a technologie ASP.NET v sadě Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Viz také:

[Publikování webové aplikace do služby Azure App Service pomocí sady Visual Studio](../deployment/quickstart-deploy-to-azure.md)
