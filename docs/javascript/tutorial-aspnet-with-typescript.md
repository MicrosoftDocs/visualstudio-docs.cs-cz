---
title: Vytvoření aplikace ASP.NET Core pomocí TypeScriptu
description: V tomto kurzu vytvoříte aplikaci pomocí ASP.NET Core a TypeScriptu.
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8d733c41e2833eeca2a8bf8c68f5e329f0af723c
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/06/2020
ms.locfileid: "75685305"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Kurz: Vytvoření aplikace ASP.NET Core pomocí TypeScriptu v aplikaci Visual Studio

V tomto kurzu pro vývojové ASP.NET Core a TypeScript sady Visual Studio vytvoříte jednoduchou webovou aplikaci, přidáte nějaký kód TypeScriptu a pak aplikaci spustíte. 

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a nainstalovat zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali aplikaci Visual Studio, přejděte [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a nainstalovat zdarma.

::: moniker-end

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvoření projektu ASP.NET Core
> * Přidejte balíček NuGet pro podporu TypeScript.
> * Přidat nějaký kód TypeScriptu
> * Spuštění aplikace

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje webu ASP.NET.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2019, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali aplikaci Visual Studio 2017, můžete ji nainstalovat zdarma na stránce  [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/) .
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít na **nástroje** > **získat nástroje a funkce...** , které otevře instalační program pro Visual Studio. Zvolte úlohu **vývoje ASP.NET a webu a** pak zvolte **Upravit**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Vytvoření nového projektu ASP.NET Core MVC

Visual Studio spravuje soubory pro jednu aplikaci v *projektu*. Projekt obsahuje zdrojový kód, prostředky a konfigurační soubory.

V tomto kurzu začnete s jednoduchým projektem obsahujícím kód pro ASP.NET Core aplikaci MVC.

1. Otevřít Visual Studio.

1. Vytvořte nový projekt.

    ::: moniker range=">=vs-2019"
    Stisknutím klávesy **ESC** zavřete okno Start. Zadáním **CTRL + Q** otevřete vyhledávací pole, zadejte **ASP.NET**a pak zvolte **ASP.NET Core webová aplikace – C#** . V dialogovém okně, které se zobrazí, vyberte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **JavaScript**a pak zvolte **Node. js**. V prostředním podokně zvolte **ASP.NET Core webová aplikace – C#** a pak zvolte **OK**.
    ::: moniker-end
    Pokud nevidíte šablonu projektu **ASP.NET Core webové aplikace** , je nutné přidat úlohu **vývoje webu ASP.NET a web** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

1. Po zvolení možnosti **vytvořit**vyberte možnost **Webová aplikace (model-zobrazení-kontroler)** v dialogovém okně a pak zvolte možnost **vytvořit**.

   ![Zvolit šablonu MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio vytvoří nové řešení a otevře projekt v pravém podokně.

## <a name="add-some-code"></a>Přidat kód

1. V Průzkumník řešení (pravé podokno). Klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Spravovat balíčky NuGet**. Na kartě **Procházet** vyhledejte **Microsoft. TypeScript. MSBuild**a kliknutím na **nainstalovat** napravo nainstalujte balíček.

   ![Přidat balíček NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Sada Visual Studio přidá balíček NuGet pod uzel **závislosti** v Průzkumník řešení.

   > [!NOTE]
   > Tento kurz vyžaduje balíček NuGet. Případně můžete ve svých vlastních aplikacích chtít použít [balíček TypeScript npm](https://www.npmjs.com/package/typescript).

1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat > nová složka**. Použijte názvy *skriptů* pro novou složku.

1. Klikněte pravým tlačítkem myši na složku *skripty* a vyberte možnost **Přidat > novou položku**. Zvolte **konfigurační soubor JSON pro TypeScript**a pak klikněte na **Přidat**.

   Visual Studio přidá soubor *tsconfig. JSON* do složky *Scripts* . Tento soubor můžete použít ke [konfiguraci možností](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) pro kompilátor TypeScript.

1. Otevřete *tsconfig. JSON* a nahraďte výchozí kód následujícím kódem:

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   Možnost *outDir* určuje výstupní složku pro soubory jazyka JavaScript s plánem, které jsou přepsány kompilátorem TypeScript.

   Tato konfigurace poskytuje základní Úvod k použití TypeScriptu. V jiných scénářích, například při použití [Gulp nebo webpacku](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), můžete chtít použít jiné mezilehlé umístění souborů JavaScriptu v závislosti na vašich nástrojích a preferencích konfigurace místo *... /wwwroot/js*.

1. Klikněte pravým tlačítkem myši na složku *skripty* a vyberte možnost **Přidat > novou položku**. Zvolte **soubor TypeScript**, pro název souboru zadejte název *App. TS* a pak klikněte na **Přidat**.

   Visual Studio přidá *App. TS* do složky *Scripts* .

1. Otevřete *App. TS* a přidejte následující kód TypeScript.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Visual Studio poskytuje podporu technologie IntelliSense pro váš kód TypeScriptu.

    Pokud to chcete otestovat, odeberte `.lastName` z funkce `greeter` a pak znovu zadejte "." a uvidíte IntelliSense.

    ![Zobrazit IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Vyberte `lastName` pro přidání posledního názvu zpět do kódu.

1. Otevřete okno *zobrazení/Domovská* složka a pak otevřete *index. html*.

1. Na konec souboru přidejte následující kód HTML.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Otevřete *zobrazení/sdílená* složka a pak otevřete *_Layout. cshtml*.

1. Před voláním `@RenderSection("Scripts", required: false)`přidejte následující odkaz na skript:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Sestavení aplikace

1. Vyberte **sestavení řešení sestavení >** .

   I když se aplikace při spuštění automaticky vytvoří, chceme se podívat na něco, co se děje během procesu sestavení.

1. Otevřete složku *wwwroot/js* a najdete dva nové soubory, *App. js* a zdrojový soubor mapování, *App. js. map*. Tyto soubory jsou generovány kompilátorem TypeScript.

   Zdrojové soubory mapování jsou vyžadovány pro ladění.

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím klávesy **F5** (**ladění** > **Spustit ladění**) spusťte aplikaci.

    Aplikace se otevře v prohlížeči.

    V okně prohlížeče se zobrazí **úvodní** nadpis a tlačítko **kliknout** .

    ![ASP.NET Core s TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Kliknutím na toto tlačítko zobrazíte zprávu, kterou jsme určili v souboru TypeScript.

## <a name="debug-the-application"></a>Ladění aplikace

1. Nastavte zarážku ve funkci `greeter` v `app.ts` kliknutím na levý okraj v editoru kódu.

    ![Nastavení zarážky](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Stisknutím klávesy **F5** spusťte aplikaci.

   Možná budete muset reagovat na zprávu a povolit tak ladění skriptů.

   Aplikace se pozastaví na zarážce. Nyní můžete kontrolovat proměnné a používat funkce ladicího programu.

## <a name="next-steps"></a>Další kroky

Další informace o použití TypeScriptu s ASP.NET Core můžete chtít získat v podrobnostech.

> [!div class="nextstepaction"]
> [ASP.NET Core a TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
