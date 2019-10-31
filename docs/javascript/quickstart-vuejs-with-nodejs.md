---
title: 'Rychlý Start: Vytvoření první aplikace v Vue. js'
description: V tomto rychlém startu vytvoříte aplikaci Vue. js v aplikaci Visual Studio pomocí Node.js Tools for Visual Studio
ms.custom: seodec18
ms.date: 09/24/2018
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
ms.openlocfilehash: ba1f403cd722b4d3dd1860c4a8b135c87b80bb4d
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189479"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Rychlý Start: použití sady Visual Studio k vytvoření první aplikace Vue. js

V této 5-10 minut Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte a spustíte jednoduchou webovou aplikaci Vue. js.

> [!IMPORTANT]
> Tento článek vyžaduje šablonu Vue. js, která je k dispozici počínaje verzí Visual Studio 2017 verze 15,8.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje Node. js.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali Visual Studio 2019, Stáhněte si ho do sady [Visual Studio downloads](https://visualstudio.microsoft.com/downloads/)  page, abyste ho mohli zdarma nainstalovat.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali Visual Studio 2017, Stáhněte si ho do sady [Visual Studio downloads](https://visualstudio.microsoft.com/downloads/)  page, abyste ho mohli zdarma nainstalovat.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje**  > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úlohy Node. js v instalačním programu VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ho nemáte nainstalovaný, nainstalujte si verzi LTS z webu [Node.js](https://nodejs.org/en/download/). Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud se nainstalovaný modul runtime nerozpozná, můžete projekt nakonfigurovat na stránce vlastností pomocí odkazu na nainstalovaný modul runtime (po vytvoření projektu klikněte pravým tlačítkem na uzel projektu a zvolte **Vlastnosti**).

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Vue. js.

1. Pokud ještě nemáte modul runtime Node. js nainstalovaný, nainstalujte verzi LTS z webu [Node. js](https://nodejs.org/en/download/) .

    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nezjistí nainstalovaný modul runtime, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný modul runtime na stránce vlastnosti (po vytvoření projektu klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**).

1. Otevřete Visual Studio.

1. Vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **základní Vue. js**a pak zvolte **základní webová aplikace Vue. js** (buď JavaScript nebo TypeScript). V dialogovém okně, které se zobrazí, zadejte název **Basic-vuejs**a pak zvolte **vytvořit**.

    ![Šablona Vue. js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte **JavaScript** nebo **TypeScript**a pak zvolte **Node. js**. V prostředním podokně zvolte **základní webová aplikace Vue. js**, zadejte název **Basic-vuejs**a pak zvolte **OK**.

    ![Šablona Vue. js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Pokud nevidíte základní šablonu projektu **webové aplikace Vue. js** , je nutné přidat úlohu **vývoje Node. js** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

    Visual Studio vytvoří nový projekt. Nový projekt se otevře v Průzkumník řešení (pravé podokno).

1. V okně výstup (dolní podokno) se podívejte na průběh instalace balíčků npm vyžadovaných pro aplikaci.

1. V Průzkumník řešení otevřete uzel **npm** a ujistěte se, že jsou nainstalované všechny uvedené balíčky npm.

    Pokud chybí některé balíčky (ikona s vykřičníkem), můžete kliknout pravým tlačítkem na uzel **npm** a zvolit **Instalovat chybějící balíčky npm**.

## <a name="explore-the-ide"></a>Prozkoumejte rozhraní IDE

1. Podívejte se na **Průzkumník řešení** v pravém podokně.

     ![Řešení Vue. js](../javascript/media/vuejs-solution.png)

   - Projekt je zvýrazněný tučným písmem a má název, který jste zadali v dialogovém okně **Nový projekt**. Na disku je tento projekt reprezentován. soubor *njsproj* ve složce projektu.

   - Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako příslušný projekt. Řešení reprezentované. soubor *sln* na disku je kontejner pro jeden nebo více souvisejících projektů.

   - Uzel **npm** zobrazuje všechny nainstalované balíčky npm. Po kliknutí pravým tlačítkem na uzel npm lze vyhledat a nainstalovat balíčky npm pomocí dialogového okna.

2. Pokud chcete nainstalovat balíčky npm nebo spustit příkazy Node. js z příkazového řádku, klikněte pravým tlačítkem myši na uzel projektu a vyberte **otevřít příkazový řádek zde**.

## <a name="add-a-vue-file-to-the-project"></a>Přidat do projektu soubor. Vue

1. V Průzkumník řešení klikněte pravým tlačítkem myši na libovolnou složku, jako je například složka *Src/Components* , a poté zvolte možnost **Přidat** > **novou položku**.

1. Vyberte buď součást **Vue s jedním souborem** , nebo **součást TypeScript Vue Single File**a pak klikněte na tlačítko **Přidat**.

    Visual Studio přidá nový soubor do projektu.

## <a name="build-the-project"></a>Sestavení projektu

1. (Jenom projekt TypeScript) V aplikaci Visual Studio vyberte možnost **sestavit** > **Vyčistit řešení**.

1. V dalším kroku vyberte **sestavit** > **řešení sestavení** a sestavte projekt. V okně **výstup** Zkontrolujte výsledky sestavení a v seznamu **Zobrazit výstup ze** vyberte **sestavení** .

    Šablona projektu Vue. js používá skript `build` npm konfigurací události po sestavení. Chcete-li toto nastavení změnit, otevřete soubor projektu ( *\<projectname\>. njsproj*) z Průzkumníka Windows a vyhledejte tento řádek kódu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Spuštění aplikace

1. Spusťte aplikaci stisknutím klávesy **Ctrl**+**F5** (nebo **ladění > Spustit bez ladění**).

   V konzole se zobrazí zpráva s *počátkem vývojového serveru*.

   Pak se aplikace otevře v prohlížeči.

   ![Aplikace Vue. js spuštěná v prohlížeči](../javascript/media/vuejs-running-app.png)

1. Zavřete webový prohlížeč.

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se seznámili s používáním integrovaného vývojového prostředí (IDE) sady Visual Studio s Vue. js. Pokud se chcete podrobněji dohlížet na jeho funkce, pokračujte v kurzu v části obsah **kurzů** .

## <a name="next-steps"></a>Další kroky

- Projděte si [kurz pro Node. js a Express](tutorial-nodejs.md)
- Projděte si [kurz pro Node. js a reagují na ně.](tutorial-nodejs-with-react-and-jsx.md)
- [Nasazení aplikace na Linux App Service](../javascript/publish-nodejs-app-azure.md)