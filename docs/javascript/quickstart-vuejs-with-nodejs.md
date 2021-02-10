---
title: 'Rychlý Start: Vytvoření první aplikace Vue.js'
description: V tomto rychlém startu vytvoříte aplikaci Vue.js v aplikaci Visual Studio pomocí nástrojů Node.js Tools for Visual Studio.
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: ee855700502469783a8eab60bb24a28c2e30a9c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950637"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Rychlý Start: použití sady Visual Studio k vytvoření první aplikace Vue.js

V této 5-10 minut Úvod do integrovaného vývojového prostředí (IDE) sady Visual Studio vytvoříte a spustíte jednoduchou Vue.js webovou aplikaci.

> [!IMPORTANT]
> Tento článek vyžaduje šablonu Vue.js, která je k dispozici počínaje verzí Visual Studio 2017 verze 15,8.

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje Node.js.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali Visual Studio 2019, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali Visual Studio 2017, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte úlohu **Vývoj aplikací Node.js** a pak zvolte **Změnit**.

    ![Node.js úlohy v instalačním programu VS](../ide/media/quickstart-nodejs-workload.png)

* Je nutné mít nainstalovaný modul runtime Node.js.

    Pokud ho nemáte nainstalovaný, doporučujeme, abyste si nainstalovali verzi LTS z webu [Node.js](https://nodejs.org/en/download/) , abyste dosáhli nejlepší kompatibility s externími architekturami a knihovnami. Node.js je sestavená pro 32 bitové a 64 architektury. Nástroje Node.js v aplikaci Visual Studio, které jsou součástí úlohy Node.js, podporují obě verze. Je vyžadována pouze jedna a instalační služba Node.js podporuje pouze instalaci v jednom okamžiku.
    
    Obecně platí, že Visual Studio automaticky rozpozná nainstalovaný modul runtime Node.js. Pokud nezjistí nainstalovaný modul runtime, můžete nakonfigurovat projekt tak, aby odkazoval na nainstalovaný modul runtime na stránce vlastnosti (po vytvoření projektu klikněte pravým tlačítkem myši na uzel projektu, vyberte možnost **vlastnosti** a nastavte **cestuNode.exe**). Můžete použít globální instalaci Node.js nebo můžete zadat cestu k místnímu interpretu v každém z vašich Node.jsch projektů. 

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webové aplikace Vue.js.

1. Pokud modul runtime Node.js již není nainstalován, nainstalujte z webu [Node.js](https://nodejs.org/en/download/) verzi LTS.

    Další informace najdete v části požadavky.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **základní Vue.js** a pak zvolte **základní Vue.js webová aplikace** (JavaScript nebo TypeScript). V dialogovém okně, které se zobrazí, zadejte název **Basic-vuejs** a pak zvolte **vytvořit**.

    ![Šablona Vue.js](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **JavaScript** nebo **TypeScript** a zvolte možnost **Node.js**. V prostředním podokně zvolte **základní Vue.js webová aplikace**, zadejte název **Basic-vuejs** a pak zvolte **OK**.

    ![Šablona Vue.js](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Pokud nevidíte šablonu projektu **základní Vue.js webové aplikace** , je nutné přidat úlohu **vývojeNode.js** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

    Visual Studio vytvoří nový projekt. Nový projekt se otevře v Průzkumník řešení (pravé podokno).

1. V okně výstup (dolní podokno) se podívejte na průběh instalace balíčků npm vyžadovaných pro aplikaci.

1. V Průzkumník řešení otevřete uzel **npm** a ujistěte se, že jsou nainstalované všechny uvedené balíčky npm.

    Pokud chybí některé balíčky (ikona s vykřičníkem), můžete kliknout pravým tlačítkem na uzel **npm** a zvolit **Instalovat chybějící balíčky npm**.

## <a name="explore-the-ide"></a>Prozkoumejte rozhraní IDE

1. Podívejte se na **Průzkumník řešení** v pravém podokně.

     ![Řešení Vue.js](../javascript/media/vuejs-solution.png)

   - Projekt je zvýrazněný tučným písmem a má název, který jste zadali v dialogovém okně **Nový projekt**. Na disku je tento projekt reprezentován. soubor *njsproj* ve složce projektu.

   - Na nejvyšší úrovni je řešení, které má ve výchozím nastavení stejný název jako příslušný projekt. Řešení reprezentované. soubor *sln* na disku je kontejner pro jeden nebo více souvisejících projektů.

   - Uzel **npm** zobrazuje všechny nainstalované balíčky npm. Po kliknutí pravým tlačítkem na uzel npm lze vyhledat a nainstalovat balíčky npm pomocí dialogového okna.

2. Pokud chcete nainstalovat balíčky npm nebo spustit Node.js příkazy z příkazového řádku, klikněte pravým tlačítkem myši na uzel projektu a vyberte **otevřít příkazový řádek zde**.

## <a name="add-a-vue-file-to-the-project"></a>Přidat do projektu soubor. Vue

1. V Průzkumník řešení klikněte pravým tlačítkem myši na libovolnou složku, jako je například složka *Src/Components* , a pak zvolte možnost **Přidat**  >  **novou položku**.

1. Vyberte buď součást **Vue s jedním souborem** , nebo **součást TypeScript Vue Single File** a pak klikněte na tlačítko **Přidat**.

    Visual Studio přidá nový soubor do projektu.

## <a name="build-the-project"></a>Sestavení projektu

::: moniker range=">=vs-2019"
1. Potom pro sestavení projektu vyberte **sestavení** sestavení > **řešení** .

1. V okně **výstup** Zkontrolujte výsledky sestavení a v seznamu **Zobrazit výstup ze** vyberte **sestavení** .
::: moniker-end
::: moniker range="vs-2017"
1. (Jenom projekt TypeScript) V aplikaci Visual Studio vyberte **sestavit** > **Vyčištění řešení**.

1. Potom pro sestavení projektu vyberte **sestavení** sestavení > **řešení** .

1. V okně **výstup** Zkontrolujte výsledky sestavení a v seznamu **Zobrazit výstup ze** vyberte **sestavení** .
::: moniker-end

Šablona projektu Vue.js JavaScriptu (a starší verze šablony TypeScript) používá `build` skript npm konfigurací události po sestavení. Chcete-li toto nastavení změnit, otevřete soubor projektu (*\<projectname\> . njsproj*) z Průzkumníka Windows a vyhledejte tento řádek kódu:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Spuštění aplikace

1. Spusťte aplikaci stisknutím klávesy **CTRL** + **F5** (nebo **ladění > spustit bez ladění**).

   V konzole se zobrazí zpráva s *počátkem vývojového serveru*.

   Pak se aplikace otevře v prohlížeči.
   
   Pokud nevidíte spuštěnou aplikaci, aktualizujte stránku.

   ![Aplikace Vue.js spuštěná v prohlížeči](../javascript/media/vuejs-running-app.png)

1. Zavřete webový prohlížeč.

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli o používání integrovaného vývojového prostředí (IDE) sady Visual Studio s Vue.js. Pokud se chcete podrobněji dohlížet na jeho funkce, pokračujte v kurzu v části obsah **kurzů** .

## <a name="next-steps"></a>Další kroky

- Projděte si článek pro [Vue.js](create-application-with-vuejs.md)
- Projděte si [kurz Node.js a Express](tutorial-nodejs.md)
- [Nasazení aplikace na Linux App Service](../javascript/publish-nodejs-app-azure.md)