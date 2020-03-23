---
title: Vytvoření aplikace ASP.NET Core pomocí TypeScriptu
description: V tomto kurzu vytvoříte aplikaci pomocí ASP.NET Core a TypeScript
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
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988548"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Kurz: Vytvoření aplikace ASP.NET Core s TypeScriptem ve Visual Studiu

V tomto kurzu pro vývoj sady Visual Studio ASP.NET Core a TypeScript vytvoříte jednoduchou webovou aplikaci, přidáte nějaký kód Typu Script a pak aplikaci spusťte. 

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

V tomto kurzu se naučíte:
> [!div class="checklist"]
> * Vytvoření projektu ASP.NET Core
> * Přidání balíčku NuGet pro podporu jazyka TypeScript
> * Přidání nějakého kódu jazyka TypeScript
> * Spuštění aplikace
> * Přidání knihovny třetí strany pomocí npm

## <a name="prerequisites"></a>Požadavky

* Musíte mít nainstalovanou visual studio a ASP.NET zatížení vývoje webu.

    ::: moniker range=">=vs-2019"
    Pokud jste visual studio 2019 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pokud jste visual studio 2017 ještě nenainstalovali, přejděte na stránku ke stažení ve Visual [Studiu](https://visualstudio.microsoft.com/downloads/)a nainstalujte ho zdarma.
    ::: moniker-end

    Pokud potřebujete nainstalovat úlohy, ale už máte Visual Studio, přejděte na **nástroje** > **získat nástroje a funkce...**, který otevře Instalační program sady Visual Studio. Zvolte **úlohu ASP.NET a vývoje webu a** pak zvolte **Změnit**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Vytvoření nového projektu ASP.NET Core MVC

Visual Studio spravuje soubory pro jednu aplikaci v *projektu*. Projekt obsahuje zdrojový kód, prostředky a konfigurační soubory.

>[!NOTE]
> Chcete-li začít s prázdným projektem ASP.NET Core a přidat front-end jazyka TypeScript, přečtěte si místo toho [ASP.NET jádro s TypeScriptem.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

V tomto kurzu začnete s jednoduchým projektem obsahujícím kód pro aplikaci Core MVC ASP.NET.

1. Otevřete sadu Visual Studio.

1. Vytvoření nového projektu

    ::: moniker range=">=vs-2019"
    Pokud úvodní okno není otevřené, zvolte Počáteční okno **souboru** > **Start Window**. V počátečním okně zvolte **Vytvořit nový projekt**. V rozevíracím seznamu jazyka zvolte **C#**. Do vyhledávacího pole zadejte **ASP.NET**a pak zvolte **ASP.NET Základní webová aplikace**. Zvolte **Další**.

    Zadejte název projektu a zvolte **Vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V horním řádku nabídek zvolte **Soubor** > **nového** > **projektu**. V levém podokně dialogového okna **Nový projekt** rozbalte **položku Visual C#** a pak zvolte **.NET Core**. V prostředním podokně zvolte **ASP.NET Základní webová aplikace – C#** a pak zvolte **OK**.
    ::: moniker-end
    Pokud nevidíte šablonu projektu **ASP.NET core webová aplikace,** musíte přidat **ASP.NET a zatížení vývoje webu.** Podrobné pokyny naleznete v tématu [Požadavky](#prerequisites).

1. V zobrazeném dialogovém okně vyberte v dialogovém okně **možnost Webová aplikace (Model-View-Controller)** a pak zvolte **Vytvořit** (nebo **OK).**

   ![Výběr šablony MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio vytvoří nové řešení a otevře projekt v pravém podokně.

## <a name="add-some-code"></a>Přidání nějakého kódu

1. V Průzkumníku řešení (pravé podokno). Klepněte pravým tlačítkem myši na uzel projektu a zvolte **Spravovat balíčky NuGet**. Na kartě **Procházet** vyhledejte **microsoft.TypeScript.MSBuild**a potom klikněte na **Nainstalovat** vpravo a nainstalujte balíček.

   ![Přidat balíček NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio přidá balíček NuGet pod uzel **Závislosti** v Průzkumníku řešení.

   > [!NOTE]
   > Tento kurz vyžaduje balíček NuGet. Případně můžete ve vlastních aplikacích použít [balíček TypeScript npm](https://www.npmjs.com/package/typescript).

1. V Průzkumníku řešení klepněte pravým tlačítkem myši na uzel projektu a zvolte **Přidat > novou složku**. Použijte *názvové skripty* pro novou složku.

1. Klepněte pravým tlačítkem myši na složku *Skripty* a zvolte **Přidat > novou položku**. Zvolte **konfigurační soubor Jazyka JSON a**klepněte na **tlačítko Přidat**.

   Visual Studio přidá soubor *tsconfig.json* do složky *skriptů.* Tento soubor můžete použít ke [konfiguraci možností](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) pro kompilátor TypeScript.

1. Otevřete *soubor tsconfig.json* a nahraďte výchozí kód následujícím kódem:

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

   Volba *outDir* určuje výstupní složku pro soubory jazyka JavaScript plánu, které jsou transponovány kompilátorem TypeScript.

   Tato konfigurace poskytuje základní úvod k použití jazyka TypeScript. V jiných scénářích, například při použití [doušku nebo webpacku](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), můžete chtít jiné mezilehlé umístění pro transpované soubory JavaScript, v závislosti na vašich nástrojích a předvolbách konfigurace, namísto *.. /wwwroot/js*.

1. Klepněte pravým tlačítkem myši na složku *Skripty* a zvolte **Přidat > novou položku**. Zvolte **Soubor TypeScript**, zadejte *název app.ts* pro název souboru a klikněte na **Přidat**.

   Visual Studio přidá *app.ts* do složky *skripty.*

1. Otevřete *soubor app.ts* a přidejte následující kód jazyka TypeScript.

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

    Visual Studio poskytuje podporu technologie IntelliSense pro váš kód Typu Script.

    Chcete-li to `.lastName` otestovat, odeberte z `greeter` funkce, pak znovu zadejte ".", a uvidíte IntelliSense.

    ![Zobrazit inteligentní technologie IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Výběrem `lastName` vyberte, chcete-li do kódu přidat příjmení.

1. Otevřete složku *Zobrazení / Domov* a potom otevřete soubor *index.html*.

1. Na konec souboru přidejte následující kód HTML.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Otevřete složku *Zobrazení / Sdílená* a potom *otevřete soubor _Layout.cshtml*.

1. Před voláním na `@RenderSection("Scripts", required: false)`::

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Sestavení aplikace

1. Zvolte **sestavit > sestavení řešení**.

   I když se aplikace automaticky vytvoří při spuštění, chceme se podívat na něco, co se stane během procesu sestavení.

1. Otevřete složku *wwwroot / js* a najdete dva nové soubory, *app.js* a zdrojový mapový soubor *app.js.map*. Tyto soubory jsou generovány kompilátorem TypeScript.

   Zdrojové mapové soubory jsou vyžadovány pro ladění.

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím **klávesy F5** (**Ladění** > **počátečního ladění**) spusťte aplikaci.

    Aplikace se otevře v prohlížeči.

    V okně prohlížeče se zobrazí nadpis **Uvítání** a tlačítko **Kliknout na mě.**

    ![ASP.NET jádro pomocí Jazyka TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Klepnutím na tlačítko zobrazíte zprávu, kterou jsme zadali v souboru TypeScript.

## <a name="debug-the-application"></a>Ladění aplikace

1. Nastavte zarážku `greeter` ve `app.ts` funkci v kliknutím na levý okraj v editoru kódu.

    ![Nastavení zarážky](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Stisknutím **klávesy F5** spusťte aplikaci.

   Možná budete muset odpovědět na zprávu povolit ladění skriptů.

   Aplikace se pozastaví na zarážky. Nyní můžete zkontrolovat proměnné a používat funkce ladicího programu.

## <a name="add-typescript-support-for-a-third-party-library"></a>Přidání podpory jazyka TypeScript pro knihovnu jiného výrobce

1. Postupujte podle pokynů ve [správě balíčků npm](../javascript/npm-package-management.md#aspnet-core-projects) a přidejte `package.json` soubor do projektu. Tím přidáte podporu npm do vašeho projektu.

   >[!NOTE]
   > Pro ASP.NET core projekty můžete také použít [Správce knihovny](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) nebo přízi namísto npm k instalaci souborů JavaScript a CSS na straně klienta.

1. V tomto příkladu přidejte do projektu definiční soubor TypeScript pro jQuery. Do souboru *package.json* zahrňte následující.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Tím přidáte podporu jazyka TypeScript pro jQuery. Samotná knihovna jQuery je již zahrnuta v šabloně projektu MVC (podívejte se pod wwwroot/lib v Průzkumníku řešení). Pokud používáte jinou šablonu, možná budete muset zahrnout balíček jquery npm.

1. Pokud balíček v Průzkumníku řešení není nainstalován, klepněte pravým tlačítkem myši na uzel npm a zvolte **obnovit balíčky**.

   >[!NOTE]
   > V některých případech může Průzkumník řešení znamenat, že balíček npm není synchronizován s *souborem package.json* z důvodu známého problému [popsaného zde](https://github.com/aspnet/Tooling/issues/479). Balíček se může například při instalaci zobrazit jako nenainstalovaný. Ve většině případů můžete aktualizovat Průzkumníka řešení odstraněním *package.json*, restartováním sady Visual Studio a opětovným přidáním souboru *package.json,* jak je popsáno výše v tomto článku.

1. V Průzkumníku řešení klepněte pravým tlačítkem myši na složku Skripty a zvolte **Přidat** > **novou položku**.

1. Zvolte **Soubor typu TypeScript**, zadejte *soubor library.ts*a zvolte **Přidat**.

1. Do *souboru library.ts*přidejte následující kód.

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

   Pro jednoduchost tento kód zobrazí zprávu pomocí jQuery a výstrahy.

   S typescript definice typů pro jQuery přidán, dostanete IntelliSense podporu na jQuery objekty, když zadáte "." po jQuery objektu, jak je znázorněno zde.

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. V _Layout.cshtml aktualizujte odkazy na `library.js`skripty tak, aby zahrnovaly .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. V souboru Index.cshtml přidejte na konec souboru následující kód HTML.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Stisknutím **klávesy F5** (**Ladění** > **počátečního ladění**) spusťte aplikaci.

    Aplikace se otevře v prohlížeči.

    Klikněte na **TLAČÍTKO OK** ve výstraze zobrazíte stránku aktualizovanou na **jQuery verze je: 3.3.1!**.

    ![příklad jquery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Další kroky

Můžete se dozvědět více podrobností o používání jazyka TypeScript s ASP.NET jádrem.

> [!div class="nextstepaction"]
> [ASP.NET jádro a textový skript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
