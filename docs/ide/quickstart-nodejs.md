---
title: 'Úvodní příručka: Vytvoření první aplikace Node.js pomocí Sady Visual Studio'
description: V tomto rychlém startu vytvoříte aplikaci Node.js v sadě Visual Studio.
ms.date: 06/27/2018
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f716421da3b9f888dbb7656c55db6814de88332b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235051"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Úvodní příručka: Vytvoření první aplikace Node.js pomocí Sady Visual Studio

V tomto 5-10 minut úvod do integrovaného vývojového prostředí Visual Studio (IDE), vytvoříte jednoduchou webovou aplikaci Node.js.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou visual studio a úlohu vývoje Node.js.

    ::: moniker range=">=vs-2019"
    Pokud jste visual studio 2019 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads)a nainstalujte ho zdarma.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste visual studio 2017 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)a nainstalujte ho zdarma.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...**, který otevře Instalační program sady Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úloha node.js v Instalačníslužbě VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ji nemáte nainstalovanou, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) pro nejlepší kompatibilitu s externími architekturami a knihovnami. Soubor Node.js je vytvořen pro 32bitové a 64bitové architektury. Nástroje Node.js v sadě Visual Studio, které jsou součástí úlohy Node.js, podporují obě verze. Je vyžadován pouze jeden a instalační program Node.js podporuje pouze jednu, která je nainstalována současně.
    
    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nerozpozná nainstalovaný za běhu, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný běh na stránce vlastností (po vytvoření projektu klepněte pravým tlačítkem myši na uzel projektu, zvolte **Vlastnosti**a nastavte **cestu Node.exe**). Můžete použít globální instalaci souboru Node.js nebo můžete určit cestu k místnímu interpretu v každém z projektů Node.js. 

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Node.js.

1. Pokud nemáte runtime Node.js již nainstalován, nainstalujte verzi LTS z webu [Node.js.](https://nodejs.org/en/download/)

    Další informace naleznete v požadavcích.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** otevřete vyhledávací pole, zadejte **Node.js**, pak zvolte **Vytvořit nový projekt webové aplikace Blank Node.js** (JavaScript). V zobrazeném dialogovém okně zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** rozbalte **JavaScript**a pak zvolte **Node.js**. V prostředním podokně zvolte **Prázdná uzlová webová aplikace**, pak zvolte **OK**.
    ::: moniker-end
    Pokud šablonu projektu **webové aplikace Blank Node.js** nevidíte, je nutné přidat **vývojové úlohy Node.js.** Podrobné pokyny naleznete v tématu [Požadavky](#prerequisites).

    Visual Studio vytvoří a nové řešení a otevře projekt. *server.js* se otevře v editoru v levém podokně.

## <a name="explore-the-ide"></a>Prozkoumejte ide

1. Podívejte se na **Průzkumníka řešení** v pravém podokně.

   ![Průzkumník řešení](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Projekt je zvýrazněný tučným písmem a má název, který jste zadali v dialogovém okně **Nový projekt**. Na disku je tento projekt reprezentován souborem *NJSProj* ve složce projektu.

   - Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako příslušný projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

   - Uzel npm zobrazuje všechny nainstalované balíčky npm. Po kliknutí pravým tlačítkem na uzel npm lze vyhledat a nainstalovat balíčky npm pomocí dialogového okna.

1. Chcete-li nainstalovat balíčky npm nebo příkazy Node.js z příkazového řádku, klepněte pravým tlačítkem myši na uzel projektu a **zvolte Otevřít příkazový řádek zde**.

   ![Příkazový řádek Node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. V souboru *server.js* v editoru `http.createServer` (v levém podokně) zvolte a stiskněte **klávesu F12** nebo zvolte **Přejít na definici** z nabídky Kontext (kliknutí pravým tlačítkem myši). Tento příkaz vás přenese `createServer` k definici funkce v *indexu index.d.ts*.

   ![Kontextová nabídka Přejít na definici](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Dostal zpět do *server.js*, pak dal kurzor na konci `res.end('Hello World\n');`řetězce v tomto řádku kódu, a upravit tak, aby to vypadalo takto:

    `res.end('Hello World\n' + res.connection.`

    V případě `connection.`psaní poskytuje technologie IntelliSense možnosti automatického dokončování položky kódu.

   ![Automatické dokončování technologie IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Zvolte **localPort**a `);` zadejte příkaz k dokončení příkazu tak, aby vypadal takto:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím **kláves Ctrl**+**F5** (nebo **Ladění > spustit bez ladění**) spusťte aplikaci. Aplikace se otevře v prohlížeči.

1. V okně prohlížeče se zobrazí "Hello World" plus místní číslo portu.

1. Zavřete webový prohlížeč.

Blahopřejeme k dokončení tohoto úvodního panelu, ve kterém jste začali s IDE sady Visual Studio a Node.js. Pokud byste se chtěli ponořit hlouběji do jeho možností, pokračujte kurzem v části **Kurzy** v obsahu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace do linuxové služby App Service](../javascript/publish-nodejs-app-azure.md)

- [Kurz pro Node.js a Express](../javascript/tutorial-nodejs.md)
- [Kurz pro Node.js a Reagovat](../javascript/tutorial-nodejs-with-react-and-jsx.md)