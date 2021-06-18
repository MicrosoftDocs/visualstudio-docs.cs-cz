---
title: 'Rychlý start: Vytvoření webové služby ASP.NET Core v F #'
description: Podrobné informace o vytvoření webové ASP.NET Core Visual Studio v jazyce F#
ms.date: 08/24/2018
ms.topic: quickstart
ms.custom: acquisition
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 5048a92f2a8029a4d4fc1c4c44d14f1630116e83
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307931"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Rychlý start: Použití Visual Studio k vytvoření první webové služby ASP.NET Core v F\#

V tomto 5 až 10minutových úvodu do jazyka F# Visual Studio vytvoříte webovou aplikaci F# ASP.NET Core.

::: moniker range="vs-2017"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste si ještě nenainstalujete Visual Studio, přejděte na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a nainstalujte si ho zdarma.

::: moniker-end

::: moniker range="vs-2022"

Pokud jste si ještě nenainstalujete Visual Studio 2022 Preview, přejděte na stránku [stahování Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte projekt webového rozhraní API ASP.NET Core. Typ projektu se dodává se soubory šablon, které tvoří funkční webovou službu, ještě než cokoli přidáváte.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

2. V horním řádku nabídek zvolte **File** New Project > **(Soubor nového** > **projektu).**

3. V dialogovém **okně Nový** projekt v levém podokně rozbalte Visual F# **a** pak zvolte **Web.** V prostředním podokně zvolte **ASP.NET Core Web Application** a pak zvolte **OK.**

     Pokud nevidíte kategorii šablony projektu **.NET Core,** zvolte v levém **podokně Instalační program pro Visual Studio** otevřít nový odkaz. Spustí se instalační program pro Visual Studio. Zvolte **úlohu ASP.NET a vývoj pro web** a pak zvolte **Upravit.**

     ![ASP.NET úlohy v instalačním programu sady Visual Studio](../ide/media/quickstart-aspnet-workload.png)

4.In dialogovém **okně New ASP.NET Core Web Application** (Nová webová aplikace ASP.NET Core 2.1) vyberte v rozevírací nabídce ASP.NET **Core 2.1.** (Pokud v seznamu nevidíte **ASP.NET Core 2.1,** nainstalujte ho  pomocí odkazu Stáhnout, který by se měl zobrazit ve žlutém panelu v horní části dialogového okna.) Zvolte **OK.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V úvodním okně zvolte **Vytvořit nový projekt.**

3. Na **stránce Vytvořit nový projekt** zadejte do vyhledávacího pole **f# web** a pak zvolte šablonu projektu ASP.NET Core Web **Application.** Zvolte **Další**.

4. Na **stránce Configure your new project** (Konfigurace nového projektu) zadejte název a pak zvolte **Create (Vytvořit).**

5. Na **stránce Create a new ASP.NET Core Web Application** (Vytvořit novou webovou aplikaci ASP.NET Core **2.1)** v horní rozevírací nabídce vyberte a pak zvolte **Create (Vytvořit).**

::: moniker-end

## <a name="explore-the-ide"></a>Prozkoumání integrovaného vývojového prostředí (IDE)

1. Na panelu **Průzkumník řešení** rozbalte složku **Kontrolery** a pak zvolte **ValuesController.fs** a otevřete ji v editoru.

   ![Průzkumník řešení s rozbalenou složku Controllers v projektu webového rozhraní API F#](../ide/media/hello-world-fs-sln-explorer.png)

2. Dále upravte `Get()` člen takto:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kód je jednoduchý. Pole hodnot F# je svázáno s názvem a poté předáno rozhraní `values` ASP.NET Core MVC jako `ActionResult` . ASP.NET Core se o zbytek postará za vás.

V editoru by to mělo vypadat takhle:

![Úprava získání člena](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím **kláves Ctrl** + **F5** spusťte aplikaci a otevřete ji ve webovém prohlížeči.

2. Stránka by měla přejít na trasu, ale pokud ne, zadejte `/api/values` `https://localhost:44396/api/values` ji do prohlížeče.

Ve webovém prohlížeči se teď zobrazí JSON odpovídající dříve zadaným informacím.

## <a name="next-steps"></a>Další kroky

Blahopřejeme k dokončení tohoto rychlého startu! Doufáme, že jste se trochu dozvěděli o F#, ASP.NET Core a Visual Studio IDE. Pokud chcete zobrazit aplikaci spuštěnou na veřejném serveru, vyberte následující tlačítko.

> [!div class="nextstepaction"]
> [Nasazení aplikace do Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Další informace o F# najdete v oficiální příručce [jazyka F#.](/dotnet/fsharp/index)
