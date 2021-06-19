---
title: Vytvoření první aplikace Node.js
ms.custom:
- vs-acquisition
- SEO-VS-2020
description: V tomto rychlém startu vytvoříte aplikaci Node.js v aplikaci Visual Studio.
ms.date: 03/25/2021
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0c44bfcfe1e7f07f83ca2b7dbb8b0604f5efe5f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386160"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Rychlý Start: Vytvoření první aplikace Node.js pomocí sady Visual Studio

V tomto 5 až deseti minutách Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte jednoduchou webovou aplikaci Node.js.

## <a name="prerequisites"></a>Požadavky

Než začnete, nainstalujte sadu Visual Studio a nastavte prostředí Node.js.

### <a name="install-visual-studio"></a>Instalace sady Visual Studio

::: moniker range=">=vs-2019"
Pokud jste ještě nenainstalovali Visual Studio 2019, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) .
::: moniker-end
::: moniker range="vs-2017"
Pokud jste ještě nenainstalovali Visual Studio 2017, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) .
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Nastavení Node.jsho prostředí

Sada Visual Studio vám může pomáhat nastavit vaše prostředí, včetně instalace nástrojů, které jsou společné pro Node.js vývoj.

1. V aplikaci Visual Studio přejdete na **nástroje**  >  **získat nástroje a funkce**.

1. V Instalační program pro Visual Studio zvolte úlohu **vývojeNode.js** a vyberte **Upravit** ke stažení a instalaci úlohy.

    ![Node.js úlohy v Instalační program pro Visual Studio](../ide/media/quickstart-nodejs-workload.png)

1. Nainstalujte verzi LTS [ modulu runtimeNode.js](https://nodejs.org/en/download/). Pro zajištění nejlepší kompatibility s externími architekturami a knihovnami doporučujeme verzi LTS.

    I když je Node.js sestavena pro 32 bitové a 64 architektury, instalační program Node.js podporuje pouze jednu verzi nainstalovanou v jednom okamžiku.

1. Pokud Visual Studio nerozpozná nainstalovaný modul runtime (obvykle to znamená), nakonfigurujte projekt tak, aby odkazoval na instalovaný modul runtime:

   1. Po [Vytvoření projektu](#create-your-app-project)klikněte pravým tlačítkem myši na uzel projektu.

   1. Vyberte **vlastnosti** a nastavte **cestuNode.exe**. Můžete použít globální instalaci Node.js nebo zadat cestu k místnímu interpretu v každém z vašich Node.jsch projektů.

## <a name="create-your-app-project"></a>Vytvoření projektu aplikace

1. Pokud jste to ještě neudělali, nainstalujte verzi LTS [ modulu runtimeNode.js](https://nodejs.org/en/download/). Další informace najdete v části [požadavky](#prerequisites).

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"

    1. Stisknutím klávesy **ESC** zavřete okno Start.

    1. Stisknutím **kombinace kláves CTRL + Q** otevřete vyhledávací pole a pak zadejte **Node.js**.

    1. Vyberte **prázdnou Node.js webovou aplikaci (JavaScript)**. V dialogovém okně vyberte **vytvořit**.

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. V horním řádku nabídek vyberte **soubor** > **Nový** > **projekt**.

    1. V levém podokně dialogového okna **Nový projekt** rozbalte položku **JavaScript** a vyberte možnost **Node.js**.

    1. V prostředním podokně zvolte **prázdné Node.js webová aplikace** a vyberte **OK**.

    ::: moniker-end
    
    Pokud nevidíte šablonu projektu **prázdná Node.js webové aplikace** , je nutné přidat úlohu **vývojeNode.js** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

    Visual Studio vytvoří a otevře projekt. Soubor *server.js* projektu se otevře v editoru na levé straně.

## <a name="explore-the-ide"></a>Prozkoumejte rozhraní IDE

1. V pravém podokně se podívejte na **Průzkumník řešení**.

   ![Průzkumník řešení](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Zvýrazněná tučně je váš projekt pomocí názvu, který jste zadali při nastavování projektu. Na disku je tento projekt reprezentován souborem *. njsproj* ve složce projektu.

   - Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako příslušný projekt. Řešení, reprezentované na disku souborem *.sln*, je kontejner pro jeden nebo více souvisejících projektů.

   - Uzel **npm** zobrazuje nainstalované balíčky npm. Můžete kliknout pravým tlačítkem na uzel npm a vyhledat a nainstalovat balíčky npm pomocí dialogového okna.

1. Pokud chcete nainstalovat balíčky npm nebo příkazy Node.js z příkazového řádku, klikněte pravým tlačítkem myši na uzel projektu a vyberte **otevřít příkazový řádek zde**.

   ![Uzel tečka j s – příkazový řádek](../ide/media/quickstart-nodejs-command-prompt.png)

1. Chcete-li otestovat navigaci na zdrojový kód, v souboru Open *server.js* vyberte možnost **http. createServer** a stiskněte klávesu **F12** nebo zvolte možnost **Přejít k definici** z kontextové nabídky (kliknutím pravým tlačítkem myši). Tento příkaz vás provede definicí `createServer` funkce v *http. d. TS*.

   ![Přejít na kontextovou nabídku definice](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Vraťte se na *server.js* a vyhledejte tento řádek kódu: `res.end('Hello World\n');` . Upravte kód takto:

    `res.end('Hello World\n' + res.connection.`

    Při psaní **připojení** technologie IntelliSense poskytuje možnosti automatického dokončování položky kódu.

   ![Automatické dokončování IntelliSense](../ide/media/quickstart-nodejs-intellisense.png)

1. Vyberte **localPort** a typ **);** dokončení příkazu:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>Spuštění aplikace

1. Spusťte aplikaci stisknutím **kombinace kláves CTRL + F5** (nebo **ladění**  >  **Spusťte bez ladění**). 
 
   Aplikace se otevře v prohlížeči.

1. V prohlížeči ověřte, že se zobrazí zpráva "Hello World" a číslo místního portu.

Gratulujeme! Pomocí sady Visual Studio jste vytvořili jednoduchou aplikaci Node.js. Pokud chcete pokračovat hlouběji, pokračujte v části s **kurzy** v obsahu.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Nasazení aplikace na Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Kurz pro Node.js a Express](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Kurz pro Node.js a reakce](../javascript/tutorial-nodejs-with-react-and-jsx.md)
