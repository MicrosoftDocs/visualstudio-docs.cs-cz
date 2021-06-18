---
title: Vytvoření aplikace ASP.NET Core pomocí TypeScriptu
description: V tomto kurzu vytvoříte aplikaci pomocí jazyka ASP.NET Core a TypeScript.
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0728011c05d47996a313c11a18f31a196ec08e10
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306496"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Kurz: Vytvoření aplikace ASP.NET Core s TypeScriptem v Visual Studio

V tomto kurzu Visual Studio vývoje ASP.NET Core a TypeScript vytvoříte jednoduchou webovou aplikaci, přidáte kód TypeScriptu a pak aplikaci spustíte.

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste si ještě nenainstalujete Visual Studio 2022 Preview, přejděte na stránku [stahování Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) a nainstalujte si ji zdarma.

::: moniker-end

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvoření projektu ASP.NET Core
> * Přidání balíčku NuGet pro podporu TypeScriptu
> * Přidání kódu TypeScriptu
> * Spuštění aplikace
> * Přidání knihovny třetí strany pomocí npm

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou Visual Studio a ASP.NET webového vývoje.

    ::: moniker range=">=vs-2019"
    Pokud jste si ještě nenainstalujete Visual Studio 2019, přejděte na stránku [Visual Studio ke](https://visualstudio.microsoft.com/downloads/) stažení a nainstalujte si ji zdarma.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste si ještě nenainstalujete Visual Studio 2017, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads/) a nainstalujte si ji zdarma.
    ::: moniker-end

    Pokud potřebujete tuto úlohu nainstalovat, ale Visual Studio, přejděte na **Nástroje** Získat nástroje a funkce. Otevře se  >  Instalační program pro Visual Studio. Zvolte **úlohu ASP.NET a vývoj pro web** a pak zvolte **Upravit.**

## <a name="create-a-new-aspnet-core-mvc-project"></a>Vytvoření nového projektu ASP.NET Core MVC

Visual Studio spravuje soubory pro jednu aplikaci v *projektu*. Projekt obsahuje zdrojový kód, prostředky a konfigurační soubory.

>[!NOTE]
> Pokud chcete začít s prázdným ASP.NET Core a přidat front-end TypeScriptu, podívejte se na ASP.NET [Core s TypeScriptem.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

V tomto kurzu začnete s jednoduchým projektem obsahujícím kód pro aplikaci ASP.NET Core MVC.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    V Visual Studio 2019 zvolte **v** úvodním okně Vytvořit nový projekt. Pokud úvodní okno není otevřené, zvolte **Úvodní**  >  **okno souboru**. Zadejte **webovou aplikaci,** jako jazyk zvolte **C#,** pak **zvolte ASP.NET Core Web Application (Model-View-Controller)** a pak zvolte **Další.** Na další obrazovce zadejte název projektu a pak zvolte **Další.**

    Zvolte doporučené cílové rozhraní (.NET Core 3.1) nebo .NET 5 a pak zvolte **Vytvořit.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **File** New Project  >  **(Soubor nového**  >  **projektu).** V levém podokně dialogového okna **Nový** projekt rozbalte **Visual C#** a pak zvolte **.NET Core**. V prostředním podokně zvolte **ASP.NET Core Web Application – C#** a pak zvolte **OK.**

    V dialogovém okně, které se zobrazí, vyberte v dialogovém okně Webová aplikace **(Model-View-Controller)** a pak zvolte **Vytvořit** (nebo **OK).**

    ![Volba šablony MVC](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    Pokud nevidíte šablonu projektu webové aplikace **ASP.NET Core,** musíte přidat úlohu vývoje ASP.NET **a** webu. Podrobné pokyny najdete v tématu [Požadavky.](#prerequisites)

    Visual Studio vytvoří nové řešení a otevře projekt v pravém podokně.

## <a name="add-some-code"></a>Přidání kódu

1. V Průzkumník řešení (pravé podokno). klikněte pravým tlačítkem na uzel projektu a zvolte **Spravovat balíčky NuGet.** Na kartě **Procházet** vyhledejte **Soubor Microsoft.TypeScript.MSBuild** a pak kliknutím na Nainstalovat vpravo nainstalujte balíček. 

   ![Přidání balíčku NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio přidá balíček NuGet do **uzlu Závislosti** v Průzkumník řešení.

1. Klikněte pravým tlačítkem na uzel projektu a zvolte **Add > New Item (Přidat novou položku).** Zvolte konfigurační **soubor JSON typescriptu a** pak klikněte na **Přidat.**

   Visual Studio přidátsconfig.js *on* do kořenového adresáře projektu. Tento soubor můžete použít ke [konfiguraci možností](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) pro kompilátor TypeScript.

1. Otevřete *tsconfig.json a* nahraďte výchozí kód následujícím kódem:

   ```json
   {
     "compileOnSave": true,
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

   Možnost *outDir* určuje výstupní složku pro prosté javascriptové soubory, které jsou transpilovány kompilátorem TypeScriptu.

   Tato konfigurace poskytuje základní úvod do používání TypeScriptu. V jiných scénářích, například při použití nástroje gulp nebo [webpack,](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)můžete chtít jiné přechodné umístění pro transpilované soubory JavaScriptu v závislosti na vašich nástrojích a předvolbách konfigurace místo *wwwroot/js.*

1. V Průzkumník řešení klikněte pravým tlačítkem na uzel projektu a zvolte Add > New Folder (Přidat novou **složku).** Použijte *skripty názvů* pro novou složku.

1. Klikněte pravým tlačítkem *na složku scripts* a zvolte **Add > New Item (Přidat novou položku).** Zvolte **TypeScript File (Soubor TypeScript),** jako *název souboru zadejte app.ts* a pak klikněte na **Add (Přidat).**

   Visual Studio do *složky scripts přidá app.ts.* 

1. Otevřete *soubor app.ts* a přidejte následující kód TypeScriptu.

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

    Visual Studio poskytuje podporu Technologie IntelliSense pro váš kód TypeScript.

    Otestujte to tak, že odeberete funkci , pak znovu napíšete "." a zobrazí `.lastName` `greeter` se IntelliSense.

    ![Zobrazení IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Výběrem `lastName` možnosti přidejte příjmení zpět do kódu.

1. Otevřete složku *Views/Home* a pak otevřete *soubor Index.cshtml.*

1. Na konec souboru přidejte následující kód HTML.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Otevřete složku *Views/Shared* a pak otevřete soubor *_Layout.cshtml.*

1. Před volání přidejte následující odkaz na skript `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Sestavení aplikace

1. Zvolte **Build > Build Solution (Sestavit a sestavit řešení).**

   I když se aplikace při spuštění automaticky sestaví, chceme se podívat na něco, co se stane během procesu sestavení.

1. Otevřete složku *wwwroot/js* a vyhledejte dva nové soubory, *app.js* a zdrojový soubor mapy, *app.js.map*. Tyto soubory jsou generovány kompilátorem TypeScriptu.

   Soubory zdrojové mapy jsou vyžadovány pro ladění.

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím **klávesy F5** (  >  **Ladění spustit ladění**) spusťte aplikaci.

    Aplikace se otevře v prohlížeči.

    V okně prohlížeče se zobrazí nadpis **Vítejte** a tlačítko **Klikněte** na mě.

    ![ASP.NET Core s TypeScriptem](../javascript/media/aspnet-core-ts-running-app.png)

1. Kliknutím na tlačítko zobrazíte zprávu, kterou jsme zadali v souboru TypeScript.

## <a name="debug-the-application"></a>Ladění aplikace

1. Zarážku ve funkci ve funkci v nastavte kliknutím `greeter` na levý okraj v editoru `app.ts` kódu.

    ![Nastavení zarážky](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Stisknutím **klávesy F5** spusťte aplikaci.

   Možná budete muset reagovat na zprávu, abyste umožnili ladění skriptů.

   Aplikace se pozastaví na zarážce. Teď můžete kontrolovat proměnné a používat funkce ladicího programu.

## <a name="add-typescript-support-for-a-third-party-library"></a>Přidání podpory TypeScriptu pro knihovnu třetí strany

1. Podle pokynů ve [správě balíčků npm](../javascript/npm-package-management.md#aspnet-core-projects) přidejte `package.json` soubor do projektu. Tím se do projektu přidá podpora npm.

   >[!NOTE]
   > Pro ASP.NET Core můžete k instalaci [](/aspnet/core/client-side/libman/) javascriptových souborů a souborů CSS na straně klienta použít také Správce knihoven nebo yarn místo npm.

1. V tomto příkladu přidejte do projektu definiční soubor TypeScriptu pro jQuery. Do souboru souborupackage.js *následující* informace.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Tím se přidá podpora TypeScriptu pro jQuery. Samotná knihovna jQuery už je součástí šablony projektu MVC (podívejte se do části wwwroot/lib v Průzkumník řešení). Pokud používáte jinou šablonu, možná budete muset zahrnout také balíček jquery npm.

1. Pokud balíček v Průzkumník řešení nainstalovaný, klikněte pravým tlačítkem na uzel npm a zvolte **Obnovit balíčky**.

   >[!NOTE]
   > V některých scénářích Průzkumník řešení, že je balíček npm *nesynchronní* spackage.json kvůli známému problému popsanému [tady.](https://github.com/aspnet/Tooling/issues/479) Balíček se například může při instalaci zobrazit jako nenainstalovaný. Ve většině případů můžete aktualizovat Průzkumník řešení odstraněnímpackage.jsna *,* restartováním služby Visual Studio a opakovaným přidáním souboru *package.js,* jak je popsáno výše v tomto článku.

1. V Průzkumník řešení klikněte pravým tlačítkem na složku scripts a zvolte **Přidat**  >  **novou položku.**

1. Vyberte **soubor TypeScript**, zadejte *Library. TS* a klikněte na **Přidat**.

1. V *knihovně. TS* přidejte následující kód.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString() + " " + v + "!!");
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

Další informace o použití TypeScriptu s ASP.NET Core můžete chtít získat v podrobnostech. Pokud vás zajímá programování AngularJS v aplikaci Visual Studio, můžete použít [rozšíření služby AngularJS Language](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) pro Visual Studio.

> [!div class="nextstepaction"]
> [ASP.NET Core a TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

> [!div class="nextstepaction"]
> [Rozšíření služby pro jazyk AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
