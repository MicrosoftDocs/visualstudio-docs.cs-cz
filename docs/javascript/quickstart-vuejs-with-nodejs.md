---
title: 'Úvodní příručka: Vytvořte si první aplikaci Vue.js'
description: V tomto rychlém startu vytvoříte aplikaci Vue.js v sadě Visual Studio pomocí nástrojů Node.js pro visual studio
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235103"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Úvodní příručka: Vytvoření první aplikace Vue.js pomocí Sady Visual Studio

V tomto 5-10 minut úvod do integrovaného vývojového prostředí Visual Studio (IDE), budete vytvářet a spouštět jednoduchou webovou aplikaci Vue.js.

> [!IMPORTANT]
> Tento článek vyžaduje šablonu Vue.js, která je k dispozici od visual studia 2017 verze 15.8.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou visual studio a úlohu vývoje Node.js.

    ::: moniker range=">=vs-2019"
    Pokud jste visual studio 2019 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste visual studio 2017 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...**, který otevře Instalační program sady Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Úloha node.js v Instalačníslužbě VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ji nemáte nainstalovanou, doporučujeme nainstalovat verzi LTS z webu [Node.js](https://nodejs.org/en/download/) pro nejlepší kompatibilitu s externími architekturami a knihovnami. Soubor Node.js je vytvořen pro 32bitové a 64bitové architektury. Nástroje Node.js v sadě Visual Studio, které jsou součástí úlohy Node.js, podporují obě verze. Je vyžadován pouze jeden a instalační program Node.js podporuje pouze jednu, která je nainstalována současně.
    
    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nerozpozná nainstalovaný za běhu, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný běh na stránce vlastností (po vytvoření projektu klepněte pravým tlačítkem myši na uzel projektu, zvolte **Vlastnosti**a nastavte **cestu Node.exe**). Můžete použít globální instalaci souboru Node.js nebo můžete určit cestu k místnímu interpretu v každém z projektů Node.js. 

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Vue.js.

1. Pokud nemáte runtime Node.js již nainstalován, nainstalujte verzi LTS z webu [Node.js.](https://nodejs.org/en/download/)

    Další informace naleznete v požadavcích.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Stisknutím **klávesy Esc** zavřete počáteční okno. Zadejte **Ctrl + Q,** chcete-li otevřít vyhledávací pole, zadejte **Základní vue.js**, pak zvolte **Základní Vue.js webová aplikace** (buď JavaScript nebo TypeScript). Do zobrazeného dialogového okna zadejte název **basic-vuejs**a pak zvolte **Vytvořit**.

    ![Šablona Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** rozbalte **JavaScript** nebo **TypeScript**a pak zvolte **Node.js**. V prostředním podokně zvolte **Základní webová aplikace Vue.js**, zadejte název **basic-vuejs**a pak zvolte **OK**.

    ![Šablona Vue.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Pokud nevidíte šablonu projektu **webové aplikace Vue.js,** je nutné přidat **vývojové úlohy Node.js.** Podrobné pokyny naleznete v tématu [Požadavky](#prerequisites).

    Visual Studio vytvoří nový projekt. Nový projekt se otevře v Průzkumníku řešení (v pravém podokně).

1. Zkontrolujte, zda výstupní okno (dolní podokno) průběh instalace npm balíčky potřebné pro aplikaci.

1. V Průzkumníku řešení otevřete uzel **npm** a ujistěte se, že jsou nainstalovány všechny uvedené balíčky npm.

    Pokud nějaké balíčky chybí (ikona vykřičníku), můžete klepnout pravým tlačítkem myši na uzel **npm** a zvolit **možnost Instalovat chybějící balíčky npm**.

## <a name="explore-the-ide"></a>Prozkoumejte ide

1. Podívejte se na **Průzkumníka řešení** v pravém podokně.

     ![Řešení Vue.js](../javascript/media/vuejs-solution.png)

   - Projekt je zvýrazněný tučným písmem a má název, který jste zadali v dialogovém okně **Nový projekt**. Na disku je tento projekt reprezentován . *njsproj* ve složce projektu.

   - Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako příslušný projekt. Řešení reprezentované . *sln* na disku, je kontejner pro jeden nebo více souvisejících projektů.

   - Uzel **npm** zobrazuje všechny nainstalované balíčky npm. Po kliknutí pravým tlačítkem na uzel npm lze vyhledat a nainstalovat balíčky npm pomocí dialogového okna.

2. Chcete-li nainstalovat balíčky npm nebo spustit příkazy Node.js z příkazového řádku, klepněte pravým tlačítkem myši na uzel projektu a **zvolte Otevřít příkazový řádek zde**.

## <a name="add-a-vue-file-to-the-project"></a>Přidání souboru .vue do projektu

1. V Průzkumníku řešení klepněte pravým tlačítkem myši na libovolnou složku, například do složky *src/components,* a pak zvolte **Přidat** > **novou položku**.

1. Vyberte buď **javascriptová komponenta jednoho souboru,** nebo **komponentu Vue single file a**pak klepněte na **Přidat**.

    Visual Studio přidá nový soubor do projektu.

## <a name="build-the-project"></a>Sestavení projektu

1. (Pouze projekt jazyka TypeScript) V sadě Visual Studio zvolte **Build** > **Clean Solution**.

    ::: moniker range=">=vs-2019"
    V šabloně TypeScript, která je součástí Visual Studia 2019, tento krok přeskočte.
    ::: moniker-end

1. Dále zvolte **sestavení** > **sestavení řešení** k sestavení projektu. Zkontrolujte **okno Výstup,** chcete-li zobrazit výsledky sestavení, a zvolte **Sestavit** ze seznamu Zobrazit **výstup ze** seznamu.

    Šablona projektu JavaScript Vue.js (a starší verze šablony `build` Jazyka) používá skript npm konfigurací události post build. Chcete-li toto nastavení změnit, otevřete soubor projektu*\<(název\>projektu .njsproj*) z Průzkumníka Windows a vyhledejte tento řádek kódu:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím **kláves Ctrl**+**F5** (nebo **Ladění > spustit bez ladění**) spusťte aplikaci.

   V konzole se zobrazí zpráva *Spuštění vývojového serveru*.

   Poté se aplikace otevře v prohlížeči.
   
   Pokud spuštěnou aplikaci nevidíte, aktualizujte stránku.

   ![Aplikace Vue.js spuštěná v prohlížeči](../javascript/media/vuejs-running-app.png)

1. Zavřete webový prohlížeč.

Gratulujeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli něco o použití IDE sady Visual Studio s vue.js. Pokud byste se chtěli ponořit hlouběji do jeho možností, pokračujte kurzem v části **Kurzy** v obsahu.

## <a name="next-steps"></a>Další kroky

- Procházení [kurzu pro Node.js a Express](tutorial-nodejs.md)
- Projděte [si kurz pro Node.js a reagovat](tutorial-nodejs-with-react-and-jsx.md)
- [Nasazení aplikace do linuxové služby App Service](../javascript/publish-nodejs-app-azure.md)