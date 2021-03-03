---
ms.openlocfilehash: a33871a9a80dfcb6260f57e504c72ae2f72077bd
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750667"
---
## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) nainstalované s odpovídajícími úlohami pro svůj jazyk, který si vyberete:
  * ASP.NET: **vývoj pro ASP.NET a web**
  * Python: **vývoj v Pythonu**
  * Node.js: **vývojNode.js**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) nainstalované s odpovídajícími úlohami pro svůj jazyk, který si vyberete:
  * ASP.NET: **vývoj pro ASP.NET a web**
  * Python: **vývoj v Pythonu**
  * Node.js: **vývojNode.js**
::: moniker-end

* Projekt ASP.NET, ASP.NET Core, Python nebo Node.js. Pokud projekt ještě nemáte, vyberte některou z níže uvedených možností:
  * ASP.NET Core: Sledujte [rychlý Start: pomocí sady Visual Studio vytvořte svou první webovou aplikaci ASP.NET Core](../../ide/quickstart-aspnet-core.md)nebo použijte následující postup:
    ::: moniker range=">=vs-2019"
    V aplikaci Visual Studio 2019 v okně Start vyberte možnost **vytvořit nový projekt** . Pokud okno Start není otevřeno, klikněte **na tlačítko**  >  **Start okna**. Do vyhledávacího pole zadejte **Web App** , jako jazyk vyberte **C#** a pak zvolte **ASP.NET Core webová aplikace (model-zobrazení-kontroler)** a pak zvolte **Další**. Na další obrazovce pojmenujte projekt **MyASPApp** a klikněte na tlačítko **Další**.

    Zvolte buď Doporučené cílové rozhraní (.NET Core 3,1), nebo .NET 5 a pak zvolte **vytvořit**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    V aplikaci Visual Studio 2017 zvolte **soubor**  >  **Nový projekt**, vyberte **Visual C#**  >  **.NET Core** a pak vyberte **ASP.NET Core webová aplikace**. Po zobrazení výzvy vyberte šablonu **Webová aplikace (model-zobrazení-kontroler)** , ujistěte se, že není vybráno **žádné ověřování** , a pak vyberte **OK**.
    ::: moniker-end
  * Python: postup: [Vytvoření první webové aplikace v Pythonu pomocí sady Visual Studio](../../ide/quickstart-python.md)nebo použití **souboru**  >  **Nový projekt**, vyberte **Python** a pak vyberte **webový projekt na baňce**.
  * Node.js: Sledujte [rychlý Start: pomocí sady Visual Studio vytvořte svou první aplikaci Node.js](../../ide/quickstart-nodejs.md)nebo použijte **soubor**  >  **Nový projekt**, vyberte **JavaScript** a pak vyberte **prázdná Node.js webová aplikace**.

* Před provedením kroků nasazení se ujistěte, že jste sestavili projekt pomocí příkazu nabídky **build > Build Solution** .