---
ms.openlocfilehash: b2f9327da5e195c50bd074a468e1f9e57ece94ea
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750332"
---
## <a name="prerequisites"></a>Požadavky

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) nainstalované s odpovídajícími úlohami pro svůj jazyk, který si vyberete:
  * ASP.NET: **vývoj pro ASP.NET a web**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) nainstalované s odpovídajícími úlohami pro svůj jazyk, který si vyberete:
  * ASP.NET: **vývoj pro ASP.NET a web**
::: moniker-end

* Předplatné Azure. Pokud ještě předplatné nemáte, [Zaregistrujte se zdarma](https://azure.microsoft.com/free/dotnet/), včetně $200 na kreditu po dobu 30 dnů a 12 měsíců oblíbených bezplatných služeb.

* ASP.NET Core: Sledujte [rychlý Start: pomocí sady Visual Studio vytvořte svou první webovou aplikaci ASP.NET Core](../../ide/quickstart-aspnet-core.md)nebo použijte následující postup:
  ::: moniker range=">=vs-2019"
  V aplikaci Visual Studio 2019 v okně Start vyberte možnost **vytvořit nový projekt** . Pokud okno Start není otevřeno, klikněte **na tlačítko**  >  **Start okna**. Do vyhledávacího pole zadejte **Web App** , jako jazyk vyberte **C#** a pak zvolte **ASP.NET Core webová aplikace (model-zobrazení-kontroler)** a pak zvolte **Další**. Na další obrazovce pojmenujte projekt **MyASPApp** a klikněte na tlačítko **Další**.

  Zvolte buď Doporučené cílové rozhraní (.NET Core 3,1), nebo .NET 5 a pak zvolte **vytvořit**.
  ::: moniker-end
  ::: moniker range="vs-2017"
  V aplikaci Visual Studio 2017 zvolte **soubor**  >  **Nový projekt**, vyberte **Visual C#**  >  **.NET Core** a pak vyberte **ASP.NET Core webová aplikace**. Po zobrazení výzvy vyberte šablonu **Webová aplikace (model-zobrazení-kontroler)** , ujistěte se, že není vybráno **žádné ověřování** , a pak vyberte **OK**.
  ::: moniker-end

* Před provedením kroků nasazení se ujistěte, že jste sestavili projekt pomocí příkazu nabídky **build > Build Solution** .