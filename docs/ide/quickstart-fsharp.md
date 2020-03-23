---
title: 'Úvodní příručka: Vytvořte ASP.NET základní webové služby v F #'
description: Zjistěte, jak vytvořit ASP.NET základní webové služby v sadě Visual Studio s F#, krok za krokem.
ms.date: 08/24/2018
ms.topic: quickstart
author: cartermp
ms.author: phcart
manager: andrehal
dev_langs:
- FSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 990106f7f3ca97ae38a20170ca6ed2e1d699d4e4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "70180326"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-service-in-f"></a>Úvodní příručka: Pomocí sady Visual Studio můžete vytvořit první ASP.NET webovou službu Core ve F.\#

V tomto 5-10 minut úvod do F# v sadě Visual Studio , vytvoříte F# ASP.NET základní webové aplikace.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range="vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

## <a name="create-a-project"></a>Vytvoření projektu

Nejprve vytvoříte ASP.NET projektu základního webového rozhraní API. Typ projektu je dodáván se soubory šablon, které tvoří funkční webovou službu, ještě předtím, než jste něco přidali!

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

2. V horním řádku nabídek zvolte **Soubor** > **Nový** > **Projekt**.

3. V dialogovém okně **Nový projekt** rozbalte v levém podokně **položku Visual F#** a pak zvolte **Web**. V prostředním podokně zvolte **ASP.NET Základní webová aplikace**a pak zvolte **OK**.

     Pokud kategorii šablony projektu **.NET Core** nevidíte, zvolte v levém podokně odkaz Otevřít instalační program **sady Visual Studio.** Spustí se instalační program pro Visual Studio. Zvolte **úlohu ASP.NET a vývoje webu a** pak zvolte **Změnit**.

     ![ASP.NET zatížení v Instalačníslužbě VS](../ide/media/quickstart-aspnet-workload.png)

4.In dialogovéokno **Nová ASP.NET jádrová webová aplikace** vyberte v horní rozevírací nabídce ASP.NET **Jádrem 2.1.** (Pokud v seznamu ASP.NET **jádra 2.1** nevidíte, nainstalujte ho podle odkazu **Stáhnout,** který by se měl zobrazit ve žlutém pruhu v horní části dialogového okna.) Zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

2. V počátečním okně zvolte **Vytvořit nový projekt**.

3. Na stránce **Vytvořit nový projekt** zadejte do vyhledávacího pole web **f#** a pak zvolte šablonu projektu **ASP.NET Základní webová aplikace.** Zvolte **Další**.

4. Na stránce **Konfigurovat nový projekt** zadejte název a pak zvolte **Vytvořit**.

5. Na stránce **Vytvořit novou ASP.NET základní webovou aplikaci** vyberte v horní rozevírací nabídce ASP.NET Jádro **2.1** a pak zvolte **Vytvořit**.

::: moniker-end

## <a name="explore-the-ide"></a>Prozkoumejte ide

1. Na panelu nástrojů **Průzkumník a hřešení** rozbalte složku **Řadiče** a pak ji v editoru otevřete zvolte **ValuesController.fs.**

   ![Průzkumník řešení se složkou Řadiče rozbalenou v projektu f# webového rozhraní API](../ide/media/hello-world-fs-sln-explorer.png)

2. Dále upravte `Get()` člen takto:

   ```fsharp
   [<HttpGet>]
   member this.Get() =
       let values = [|"Hello"; "World"; "First F#/ASP.NET Core web API!"|]
       ActionResult<string[]>(values)
   ```

Kód je jednoduchý. Pole F# hodnot je vázánna `values` na název a pak předány ASP.NET `ActionResult`core MVC framework jako . ASP.NET Core se postará o zbytek za vás.

Mělo by to vypadat takto v editoru:

![Upravený člen get](../ide/media/hello-world-fs-get-member.png)

## <a name="run-the-application"></a>Spuštění aplikace

1. Stisknutím **klávesy Ctrl**+**F5** spusťte aplikaci a otevřete ji ve webovém prohlížeči.

2. Stránka by měla `/api/values` přejít na trasu, `https://localhost:44396/api/values` ale pokud tomu tak není, zadejte do prohlížeče.

Webový prohlížeč nyní zobrazí JSON odpovídající tomu, co jste zadali dříve.

## <a name="next-steps"></a>Další kroky

Gratulujeme k dokončení tohoto rychlého startu! Doufáme, že jste se dozvěděli něco o F#, ASP.NET Core a IDE sady Visual Studio. Chcete-li zobrazit aplikaci spuštěnou na veřejném serveru, vyberte následující tlačítko.

> [!div class="nextstepaction"]
> [Nasazení aplikace do služby Azure App Service](../deployment/quickstart-deploy-to-azure.md)

Chcete-li se dozvědět více o F#, podívejte se na oficiální [F# Guide](/dotnet/fsharp/index).