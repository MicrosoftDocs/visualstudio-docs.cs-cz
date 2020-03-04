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
ms.openlocfilehash: a1995353d00f9e48811f388e1d853c93850b85f4
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235103"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Rychlý start: Použití sady Visual Studio k vytvoření první aplikace pro Vue.js

V tomto úvodu 5 až 10 minut do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte a spustí jednoduchou webovou aplikaci Vue.js.

> [!IMPORTANT]
> Tento článek vyžaduje Vue.js šablonu, která je k dispozici od verze Visual Studio 2017 verze 15.8.

## <a name="prerequisites"></a>Předpoklady

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

    Pokud ji nemáte nainstalovanou, doporučujeme nainstalovat verzi LTS z webu [Node. js](https://nodejs.org/en/download/) , aby se dosáhlo nejlepší kompatibility s externími architekturami a knihovnami. Node. js je sestaven pro 32 bitové a 64 architektury. Nástroje Node. js v aplikaci Visual Studio, které jsou součástí úlohy Node. js, podporují obě verze. Je vyžadována pouze jedna a instalační program Node. js podporuje pouze instalaci v jednom okamžiku.
    
    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nezjistí nainstalovaný modul runtime, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný modul runtime na stránce vlastnosti (po vytvoření projektu klikněte pravým tlačítkem myši na uzel projektu, vyberte možnost **vlastnosti**a nastavte **cestu k Node. exe**). Můžete použít globální instalaci Node. js nebo můžete zadat cestu k místní interpretaci v každém z vašich projektů Node. js. 

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt Vue.js webové aplikace.

1. Pokud ještě nemáte modul runtime Node. js nainstalovaný, nainstalujte verzi LTS z webu [Node. js](https://nodejs.org/en/download/) .

    Další informace najdete v části požadavky.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

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

1. V Průzkumník řešení otevřete uzel **npm** a ujistěte se, že jsou nainstalované všechny uvedené balíčky npm.

    Pokud chybí některé balíčky (ikona s vykřičníkem), můžete kliknout pravým tlačítkem na uzel **npm** a zvolit **Instalovat chybějící balíčky npm**.

## <a name="explore-the-ide"></a>Prozkoumejte rozhraní IDE

1. Podívejte se na **Průzkumník řešení** v pravém podokně.

     ![VUE.js řešení](../javascript/media/vuejs-solution.png)

   - Projekt je zvýrazněný tučným písmem a má název, který jste zadali v dialogovém okně **Nový projekt**. Na disku je tento projekt reprezentován. soubor *njsproj* ve složce projektu.

   - Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako příslušný projekt. Řešení reprezentované. soubor *sln* na disku je kontejner pro jeden nebo více souvisejících projektů.

   - Uzel **npm** zobrazuje všechny nainstalované balíčky npm. Po kliknutí pravým tlačítkem na uzel npm lze vyhledat a nainstalovat balíčky npm pomocí dialogového okna.

2. Pokud chcete nainstalovat balíčky npm nebo spustit příkazy Node. js z příkazového řádku, klikněte pravým tlačítkem myši na uzel projektu a vyberte **otevřít příkazový řádek zde**.

## <a name="add-a-vue-file-to-the-project"></a>Přidejte do projektu soubor .vue

1. V Průzkumník řešení klikněte pravým tlačítkem myši na libovolnou složku, jako je například složka *Src/Components* , a poté zvolte možnost **Přidat** > **novou položku**.

1. Vyberte buď součást **Vue s jedním souborem** , nebo **součást TypeScript Vue Single File**a pak klikněte na tlačítko **Přidat**.

    Visual Studio přidá nový soubor do projektu.

## <a name="build-the-project"></a>Sestavení projektu

1. (Jenom projekt TypeScript) V aplikaci Visual Studio vyberte možnost **sestavit** > **Vyčistit řešení**.

    ::: moniker range=">=vs-2019"
    V šabloně TypeScript, která je součástí sady Visual Studio 2019, tento krok přeskočte.
    ::: moniker-end

1. V dalším kroku vyberte **sestavit** > **řešení sestavení** a sestavte projekt. V okně **výstup** Zkontrolujte výsledky sestavení a v seznamu **Zobrazit výstup ze** vyberte **sestavení** .

    Šablona projektu Vue. js JavaScriptu (a starší verze šablony TypeScript) používá skript `build` npm konfigurací události po sestavení. Chcete-li toto nastavení změnit, otevřete soubor projektu ( *\<projectname\>. njsproj*) z Průzkumníka Windows a vyhledejte tento řádek kódu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Spuštění aplikace

1. Spusťte aplikaci stisknutím klávesy **Ctrl**+**F5** (nebo **ladění > Spustit bez ladění**).

   V konzole se zobrazí zpráva s *počátkem vývojového serveru*.

   Potom aplikace se otevře v prohlížeči.
   
   Pokud nevidíte spuštěnou aplikaci, aktualizujte stránku.

   ![VUE.js aplikace spuštěná v prohlížeči](../javascript/media/vuejs-running-app.png)

1. Zavřete webový prohlížeč.

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli ještě něco o integrovaném vývojovém prostředí sady Visual Studio pomocí Vue.js. Pokud se chcete podrobněji dohlížet na jeho funkce, pokračujte v kurzu v části obsah **kurzů** .

## <a name="next-steps"></a>Další kroky

- Projděte si [kurz pro Node. js a Express](tutorial-nodejs.md)
- Projděte si [kurz pro Node. js a reagují na ně.](tutorial-nodejs-with-react-and-jsx.md)
- [Nasazení aplikace na Linux App Service](../javascript/publish-nodejs-app-azure.md)