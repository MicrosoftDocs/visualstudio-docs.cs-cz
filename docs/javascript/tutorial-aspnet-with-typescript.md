---
title: Vytvoření aplikace ASP.NET Core pomocí TypeScriptu
description: V tomto kurzu vytvoříte aplikaci pomocí ASP.NET Core a TypeScriptu.
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e8a12c16c4c53ab2d0850bf5b768488160fa729a
ms.sourcegitcommit: b8ec700fc4c14c68c6ce280f29c19870261990d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2020
ms.locfileid: "87453697"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Kurz: Vytvoření aplikace ASP.NET Core pomocí TypeScriptu v aplikaci Visual Studio

V tomto kurzu pro vývojové ASP.NET Core a TypeScript sady Visual Studio vytvoříte jednoduchou webovou aplikaci, přidáte nějaký kód TypeScriptu a pak aplikaci spustíte. 

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvoření projektu ASP.NET Core
> * Přidejte balíček NuGet pro podporu TypeScript.
> * Přidat nějaký kód TypeScriptu
> * Spuštění aplikace
> * Přidání knihovny třetí strany pomocí npm

## <a name="prerequisites"></a>Předpoklady

* Musíte mít nainstalovanou aplikaci Visual Studio a úlohu vývoje webu ASP.NET.

    ::: moniker range=">=vs-2019"
    Pokud jste ještě nenainstalovali Visual Studio 2019, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/)   .
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste ještě nenainstalovali Visual Studio 2017, můžete si ho nainstalovat zdarma na stránku se [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads/)   .
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohu, ale už máte Visual Studio, můžete přejít do části **nástroje**  >  **získat nástroje a funkce...**, které otevře instalační program pro Visual Studio. Zvolte úlohu **vývoje ASP.NET a webu a** pak zvolte **Upravit**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Vytvoření nového projektu ASP.NET Core MVC

Visual Studio spravuje soubory pro jednu aplikaci v *projektu*. Projekt obsahuje zdrojový kód, prostředky a konfigurační soubory.

>[!NOTE]
> Pokud chcete začít s prázdným ASP.NET Core projektem a přidat front-endu TypeScript, přečtěte si místo toho [ASP.NET Core pomocí TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) .

V tomto kurzu začnete s jednoduchým projektem obsahujícím kód pro ASP.NET Core aplikaci MVC.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Pokud okno Start není otevřeno, klikněte **na tlačítko**  >  **Start okna**. V okně Start vyberte možnost **vytvořit nový projekt**. V rozevíracím seznamu jazyk vyberte **C#**. Do vyhledávacího pole zadejte **ASP.NET**a pak zvolte **ASP.NET Core webová aplikace**. Zvolte **Další**.

    Zadejte název projektu a klikněte na **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek vyberte **soubor**  >  **Nový**  >  **projekt**. V levém podokně dialogového okna **Nový projekt** rozbalte položku **Visual C#** a pak zvolte možnost **.NET Core**. V prostředním podokně zvolte **ASP.NET Core webová aplikace – C#** a pak zvolte **OK**.
    ::: moniker-end
    Pokud nevidíte šablonu projektu **ASP.NET Core webové aplikace** , je nutné přidat úlohu **vývoje webu ASP.NET a web** . Podrobné pokyny najdete v části [požadavky](#prerequisites).

1. V dialogovém okně, které se zobrazí, vyberte možnost **Webová aplikace (model-zobrazení-kontroler)** v dialogovém okně a pak zvolte možnost **vytvořit** (nebo **OK**).

   ![Zvolit šablonu MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio vytvoří nové řešení a otevře projekt v pravém podokně.

## <a name="add-some-code"></a>Přidat kód

1. V Průzkumník řešení (pravé podokno). Klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Spravovat balíčky NuGet**. Na kartě **Procházet** vyhledejte **Microsoft. TypeScript. MSBuild**a kliknutím na **nainstalovat** napravo nainstalujte balíček.

   ![Přidat balíček NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Sada Visual Studio přidá balíček NuGet pod uzel **závislosti** v Průzkumník řešení.

1. Klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **přidat > novou položku**. Zvolte **konfigurační soubor JSON pro TypeScript**a pak klikněte na **Přidat**.

   Visual Studio přidá *tsconfig.js* do souboru do kořenového adresáře projektu. Tento soubor můžete použít ke [konfiguraci možností](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) pro kompilátor TypeScript.

1. Otevřete *tsconfig.js* a nahraďte výchozí kód následujícím kódem:

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Možnost *outDir* určuje výstupní složku pro soubory prostého JavaScriptu, které jsou přepsány kompilátorem TypeScript.

   Tato konfigurace poskytuje základní Úvod k použití TypeScriptu. V jiných scénářích, například při použití [Gulp nebo webpacku](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), můžete chtít použít jiné mezilehlé umístění pro soubory JavaScriptu v závislosti na vašich nástrojích a preferencích konfigurace namísto *wwwroot/js*.

1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a vyberte **přidat > nová složka**. Použijte názvy *skriptů* pro novou složku.

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

    Pokud to chcete otestovat, odeberte `.lastName` z `greeter` funkce a pak znovu zadejte "." a uvidíte IntelliSense.

    ![Zobrazit IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Tuto možnost vyberte, pokud chcete `lastName` Poslední název přidat zpátky do kódu.

1. Otevřete okno *zobrazení/Domovská* složka a pak otevřete *index. cshtml*.

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

1. Přidejte následující odkaz skriptu před voláním `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Sestavení aplikace

1. Vyberte **sestavení řešení sestavení >**.

   I když se aplikace při spuštění automaticky vytvoří, chceme se podívat na něco, co se děje během procesu sestavení.

1. Otevřete složku *wwwroot/js* a najdete dva nové soubory, *app.js* a zdrojový soubor mapování *app.js. map*. Tyto soubory jsou generovány kompilátorem TypeScript.

   Zdrojové soubory mapování jsou vyžadovány pro ladění.

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím klávesy **F5** (**ladění**  >  **Spusťte ladění**) spusťte aplikaci.

    Aplikace se otevře v prohlížeči.

    V okně prohlížeče se zobrazí **úvodní** nadpis a tlačítko **kliknout** .

    ![ASP.NET Core s TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Kliknutím na toto tlačítko zobrazíte zprávu, kterou jsme určili v souboru TypeScript.

## <a name="debug-the-application"></a>Ladění aplikace

1. Nastavte zarážku ve `greeter` funkci kliknutím na `app.ts` levý okraj v editoru kódu.

    ![Nastavení zarážky](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Stisknutím klávesy **F5** spusťte aplikaci.

   Možná budete muset reagovat na zprávu a povolit tak ladění skriptů.

   Aplikace se pozastaví na zarážce. Nyní můžete kontrolovat proměnné a používat funkce ladicího programu.

## <a name="add-typescript-support-for-a-third-party-library"></a>Přidání podpory TypeScriptu pro knihovnu třetích stran

1. Podle pokynů v tématu [Správa balíčků npm](../javascript/npm-package-management.md#aspnet-core-projects) přidejte `package.json` soubor do projektu. Tím se do projektu přidá podpora npm.

   >[!NOTE]
   > Pro ASP.NET Core projekty můžete použít také [Správce knihovny](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) nebo přízi namísto npm k instalaci souborů JavaScript a CSS na straně klienta.

1. V tomto příkladu přidejte soubor definice TypeScript pro jQuery do projektu. Do *package.js* souboru zadejte následující.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Tím se přidá podpora TypeScript pro jQuery. Samotná knihovna jQuery je již obsažena v šabloně projektu MVC (podívejte se do části wwwroot/lib v Průzkumník řešení). Pokud používáte jinou šablonu, bude pravděpodobně nutné zahrnout také balíček jQuery npm.

1. Pokud balíček v Průzkumník řešení není nainstalován, klikněte pravým tlačítkem myši na uzel npm a vyberte možnost **obnovit balíčky**.

   >[!NOTE]
   > V některých scénářích Průzkumník řešení může znamenat, že balíček npm není synchronizovaný s *package.jsna základě* známého problému, který je [zde](https://github.com/aspnet/Tooling/issues/479)popsán. Balíček se například může zobrazit jako nenainstalovaný při instalaci. Ve většině případů můžete aktualizovat Průzkumník řešení odstraněním *package.jsna*, restartováním sady Visual Studio a opětovným přidáním *package.jsdo* souboru, jak je popsáno výše v tomto článku.

1. V Průzkumník řešení klikněte pravým tlačítkem myši na složku skripty a vyberte možnost **Přidat**  >  **novou položku**.

1. Vyberte **soubor TypeScript**, zadejte *Library. TS*a klikněte na **Přidat**.

1. V *knihovně. TS*přidejte následující kód.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Pro zjednodušení tento kód zobrazí zprávu pomocí jQuery a výstrahy.

   S definicemi typu TypeScript pro objekt jQuery získáte podporu technologie IntelliSense pro objekty jQuery, když zadáte "." za objektem jQuery, jak je znázorněno zde.

   ![jQuery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. V _Layout. cshtml aktualizujte odkazy na skripty, které se mají zahrnout `library.js` .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. V indexu. cshtml přidejte následující kód HTML na konec souboru.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Stisknutím klávesy **F5** (**ladění**  >  **Spusťte ladění**) spusťte aplikaci.

    Aplikace se otevře v prohlížeči.

    Kliknutím na **OK** v upozornění zobrazíte stránku, která je aktualizovaná na **verzi jQuery: 3.3.1!!**.

    ![Příklad jQuery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Další kroky

Další informace o použití TypeScriptu s ASP.NET Core můžete chtít získat v podrobnostech.

> [!div class="nextstepaction"]
> [ASP.NET Core a TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
