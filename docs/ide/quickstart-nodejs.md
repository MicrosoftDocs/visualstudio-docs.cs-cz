---
title: 'Rychlý Start: použití sady Visual Studio k vytvoření první aplikace Node. js'
description: V tomto rychlém startu vytvoříte aplikaci Node. js v aplikaci Visual Studio.
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
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235051"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Rychlý Start: použití sady Visual Studio k vytvoření první aplikace Node. js

V této 5-10 minut Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou webovou aplikaci Node. js.

## <a name="prerequisites"></a>Předpoklady

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje Node. js.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2019, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2017, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) .
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úloha Node.js v instalačním programu VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ji nemáte nainstalovanou, doporučujeme nainstalovat verzi LTS z webu [Node. js](https://nodejs.org/en/download/) , aby se dosáhlo nejlepší kompatibility s externími architekturami a knihovnami. Node. js je sestaven pro 32 bitové a 64 architektury. Nástroje Node. js v aplikaci Visual Studio, které jsou součástí úlohy Node. js, podporují obě verze. Je vyžadována pouze jedna a instalační program Node. js podporuje pouze instalaci v jednom okamžiku.
    
    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nezjistí nainstalovaný modul runtime, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný modul runtime na stránce vlastnosti (po vytvoření projektu klikněte pravým tlačítkem myši na uzel projektu, vyberte možnost **vlastnosti**a nastavte **cestu k Node. exe**). Můžete použít globální instalaci Node. js nebo můžete zadat cestu k místní interpretaci v každém z vašich projektů Node. js. 

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Node. js.

1. Pokud ještě nemáte modul runtime Node. js nainstalovaný, nainstalujte verzi LTS z webu [Node. js](https://nodejs.org/en/download/) .

    Další informace najdete v části požadavky.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **Node. js**a pak zvolte **vytvořit nový prázdný projekt webové aplikace Node. js** (JavaScript). V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **JavaScript**a pak zvolte **Node. js**. V prostředním podokně zvolte **prázdná webová aplikace Node. js**a pak zvolte **OK**.
    ::: moniker-end
    Pokud nevidíte prázdnou šablonu projektu **webové aplikace Node. js** , je nutné přidat úlohu **vývoje Node. js** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

    Visual Studio vytvoří a nového řešení a otevře projekt. *Server. js* se otevře v editoru v levém podokně.

## <a name="explore-the-ide"></a>Prozkoumejte rozhraní IDE

1. Podívejte se na **Průzkumník řešení** v pravém podokně.

   ![Průzkumník řešení](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Projekt je zvýrazněný tučným písmem a má název, který jste zadali v dialogovém okně **Nový projekt**. Na disku je tento projekt reprezentován souborem *. njsproj* ve složce projektu.

   - Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako příslušný projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

   - Uzel npm zobrazuje všechny nainstalované balíčky npm. Po kliknutí pravým tlačítkem na uzel npm lze vyhledat a nainstalovat balíčky npm pomocí dialogového okna.

1. Pokud chcete nainstalovat balíčky npm nebo příkazy Node. js z příkazového řádku, klikněte pravým tlačítkem myši na uzel projektu a vyberte **otevřít příkazový řádek zde**.

   ![Příkazový řádek Node. js](../ide/media/quickstart-nodejs-command-prompt.png)

1. V souboru *Server. js* v editoru (levé podokno) zvolte `http.createServer` a potom stiskněte klávesu **F12** nebo zvolte **Přejít k definici** z místní nabídky (kliknutím pravým tlačítkem myši). Tento příkaz vás přesměruje do definice funkce `createServer` v *indexu. d. TS*.

   ![Přejít na kontextovou nabídku definice](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Vraťte se na *Server. js*, umístěte kurzor na konec řetězce v tomto řádku kódu `res.end('Hello World\n');`a upravte jej tak, aby vypadal takto:

    `res.end('Hello World\n' + res.connection.`

    Když zadáte `connection.`, technologie IntelliSense poskytne možnosti automatického dokončování položky kódu.

   ![Automatické dokončování IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Zvolte **localPort**a potom zadejte `);` k dokončení příkazu, aby vypadal takto:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Spuštění aplikace

1. Spusťte aplikaci stisknutím klávesy **Ctrl**+**F5** (nebo **ladění > Spustit bez ladění**). Aplikace se otevře v prohlížeči.

1. V okně prohlížeče se zobrazí zpráva "Hello World" plus číslo místního portu.

1. Zavřete webový prohlížeč.

Blahopřejeme k dokončení tohoto rychlého startu, ve kterém jste začali s IDE sady Visual Studio a Node. js. Pokud se chcete podrobněji dohlížet na jeho funkce, pokračujte v kurzu v části obsah **kurzů** .

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace na Linux App Service](../javascript/publish-nodejs-app-azure.md)

- [Kurz pro Node. js a Express](../javascript/tutorial-nodejs.md)
- [Kurz pro Node. js a reakce](../javascript/tutorial-nodejs-with-react-and-jsx.md)