---
title: 'Rychlý start: Vytvoření první aplikace pro Vue.js'
description: V tomto rychlém startu vytvoříte aplikaci Vue.js v sadě Visual Studio pomocí Node.js Tools for Visual Studio
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 5f7b877d825a573b935a9bf0f2c907ec2ce6f808
ms.sourcegitcommit: 2f64b3b231900018fceafb72b5a1c65140213a18
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73428763"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Rychlý start: Použití sady Visual Studio k vytvoření první aplikace pro Vue.js

V tomto úvodu 5 až 10 minut do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte a spustí jednoduchou webovou aplikaci Vue.js.

> [!IMPORTANT]
> Tento článek vyžaduje Vue.js šablonu, která je k dispozici od verze Visual Studio 2017 verze 15.8.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje Node. js.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2019, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2017, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úloha Node.js v instalačním programu VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud se nainstalovaný modul runtime nerozpozná, můžete projekt nakonfigurovat na stránce vlastností pomocí odkazu na nainstalovaný modul runtime (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu a zvolte **Vlastnosti**).

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt Vue.js webové aplikace.

1. Pokud nemáte modul runtime Node.js, který je už nainstalovaný, nainstalujte verzi LTS z [Node.js](https://nodejs.org/en/download/) webu.

    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nezjistí nainstalovaný modul runtime, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný modul runtime na stránce vlastnosti (po vytvoření projektu klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**).

1. Otevřít Visual Studio.

1. Vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **základní Vue. js**a pak zvolte **základní webová aplikace Vue. js** (buď JavaScript nebo TypeScript). V dialogovém okně, které se zobrazí, zadejte název **Basic-vuejs**a pak zvolte **vytvořit**.

    ![VUE.js šablony](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte **JavaScript** nebo **TypeScript**a pak zvolte **Node. js**. V prostředním podokně zvolte **základní webová aplikace Vue. js**, zadejte název **Basic-vuejs**a pak zvolte **OK**.

    ![VUE.js šablony](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Pokud nevidíte základní šablonu projektu **webové aplikace Vue. js** , je nutné přidat úlohu **vývoje Node. js** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

    Visual Studio vytvoří nový projekt. Otevře se nový projekt v Průzkumníku řešení (pravé podokno).

1. Průběh instalace balíčků npm potřebnou pro aplikaci najdete v okně výstup (dolní podokno).

1. V Průzkumníku řešení otevřete **npm** uzlu a ujistěte se, zda jsou nainstalovány všechny balíčky uvedené npm.

    Pokud všechny balíčky, které chybí (ikona vykřičník), kliknete pravým tlačítkem **npm** uzlu a zvolte **instalovat chybějící balíčky npm**.

## <a name="explore-the-ide"></a>Prozkoumejte rozhraní IDE

1. Podívejte se na **Průzkumníka řešení** v pravém podokně.

     ![VUE.js řešení](../javascript/media/vuejs-solution.png)

   - Projekt je zvýrazněný tučným písmem a má název, který jste zadali v dialogovém okně **Nový projekt**. Na disku, je reprezentována tento projekt. *njsproj* souboru ve složce vašeho projektu.

   - Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako příslušný projekt. Řešení, reprezentovaný. *sln* souboru na disku, je kontejner pro jeden nebo více souvisejících projektů.

   - **Npm** uzlu se zobrazuje všechny balíčky npm nainstalované. Po kliknutí pravým tlačítkem na uzel npm lze vyhledat a nainstalovat balíčky npm pomocí dialogového okna.

2. Pokud chcete nainstalovat balíčky npm nebo spustit příkazy Node.js z příkazového řádku, klikněte pravým tlačítkem na uzel projektu a zvolte **tady otevřete příkazový řádek**.

## <a name="add-a-vue-file-to-the-project"></a>Přidejte do projektu soubor .vue

1. V Průzkumník řešení klikněte pravým tlačítkem myši na libovolnou složku, jako je například složka *Src/Components* , a poté zvolte možnost **Přidat** > **novou položku**.

1. Vyberte buď **komponenta jednoho souboru jazyka JavaScript Vue** nebo **TypeScript Vue jeden soubor součásti**a potom klikněte na tlačítko **přidat**.

    Visual Studio přidá nový soubor do projektu.

## <a name="build-the-project"></a>Sestavení projektu

1. (Pouze aplikace project TypeScript) Ze sady Visual Studio, zvolte **sestavení** > **Vyčistit řešení**.

    ::: moniker range=">=vs-2019"
    V šabloně TypeScript, která je součástí sady Visual Studio 2019, tento krok přeskočte.
    ::: moniker-end

1. Dále zvolte **sestavení** > **sestavit řešení** k sestavení projektu. V okně **výstup** Zkontrolujte výsledky sestavení a v seznamu **Zobrazit výstup ze** vyberte **sestavení** .

    Šablona projektu Vue. js JavaScriptu (a starší verze šablony TypeScript) používá skript `build` npm konfigurací události po sestavení. Pokud chcete toto nastavení změnit, otevřete soubor projektu ( *\<projectname\>.njsproj*) z Průzkumníka Windows a vyhledejte tento řádek kódu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím klávesy **Ctrl**+**F5** (nebo **ladit > Spustit bez ladění**) ke spuštění aplikace.

   V konzole, zobrazí se zpráva *spuštění vývojového serveru*.

   Potom aplikace se otevře v prohlížeči.
   
   Pokud nevidíte spuštěnou aplikaci, aktualizujte stránku.

   ![VUE.js aplikace spuštěná v prohlížeči](../javascript/media/vuejs-running-app.png)

1. Zavřete webový prohlížeč.

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli ještě něco o integrovaném vývojovém prostředí sady Visual Studio pomocí Vue.js. Pokud se chcete podrobněji dohlížet na jeho funkce, pokračujte v kurzu v části obsah **kurzů** .

## <a name="next-steps"></a>Další kroky

- Projděte si [kurz Node.js a Express](tutorial-nodejs.md)
- Projděte si [kurz Node.js a React](tutorial-nodejs-with-react-and-jsx.md)
- [Nasazení aplikace do služby App Service pro Linux](../javascript/publish-nodejs-app-azure.md)