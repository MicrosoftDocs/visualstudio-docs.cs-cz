---
title: 'Krok 5: nasazení aplikace ASP.NET Core do Azure'
description: Pomocí tohoto výukového kurzu a podrobných pokynů nasaďte svou ASP.NET Core webovou aplikaci do Azure.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: dc13dbdadb0c9bca25a816b15c5a99039bff454c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77580027"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Krok 5: nasazení aplikace ASP.NET Core do Azure

Pomocí těchto kroků nasadíte aplikaci ASP.NET Core a její databázi do Azure.

_Podívejte se na toto video a sledujte, jak nasadit první aplikaci ASP.NET Core do Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Otevřete projekt

Otevřete aplikaci ASP.NET Core v aplikaci Visual Studio 2019. Aplikace by už měla používat nastavení s EF Core a funkční webové rozhraní API, jak je nakonfigurované v [kroku 4 této série kurzů](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

V Průzkumníku řešení klikněte pravým tlačítkem myši na projekt a vyberte **publikovat**. Ponechte výchozí nastavení **App Service** a **vytvořte nové** a klikněte na tlačítko **publikovat** . Pokud ještě nemáte účet Azure, klikněte na **vytvořit bezplatný účet Azure** a dokončete proces krátké registrace.

Přidejte SQL Server. Zadejte uživatelské jméno a heslo správce.

![Visual Studio 2019 vytvoření Azure SQL Server](media/vs-2019/vs2019-azure-sql-server.png)

Přidejte Application Insights.

Pokračujte kliknutím na tlačítko **vytvořit** .

![Visual Studio 2019 vytvořit nové Azure App Service](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Prozkoumání Azure Portal a hostované aplikace

Po vytvoření služby App Service se vaše lokalita spustí v prohlížeči. I když se načítá, můžete App Service také najít v Azure Portal. Prozkoumejte dostupné možnosti pro službu App Service najdete část s **přehledem** , kde můžete spustit a zastavit aplikaci.

![Možnosti Azure App Service](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Škálovatelnost

Můžete si prohlédnout možnosti pro horizontální navýšení kapacity aplikace i. Horizontální navýšení kapacity znamená zvýšení prostředků uvedených v každé instanci hostující vaši aplikaci. Horizontální navýšení kapacity znamená zvýšení počtu instancí, které hostují vaši aplikaci. Pro svou aplikaci můžete nakonfigurovat automatické škálování, které automaticky zvýší počet instancí používaných k hostování vaší aplikace v reakci na načtení a pak je po snížení zatížení sníží.

### <a name="security-and-compliance"></a>Zabezpečení a dodržování předpisů

Další výhodou pro hostování naší aplikace pomocí Azure je zabezpečení a dodržování předpisů. Azure App Service poskytuje kompatibilitu s normou ISO, SOC a PCI. Můžeme se rozhodnout pro ověřování uživatelů pomocí Azure Active Directory nebo sociálních přihlášení, jako je Twitter, Facebook, Google nebo Microsoft. Můžeme vytvořit omezení IP adres, spravovat identity služeb, přidávat vlastní domény a podporovat protokol SSL pro aplikaci a také konfigurovat zálohy s obnovitelné archivními kopiemi obsahu, konfigurace a databáze aplikace. Tyto funkce jsou k dispozici v možnostech nabídky pro ověřování, autorizaci, identitu, zálohování a nastavení SSL.

### <a name="deployment-slots"></a>Nasazovací sloty

Při nasazení aplikace se často během restartování aplikace vyskytnou krátké výpadky. Sloty nasazení Vyhněte tomuto problému tím, že vám umožní nasadit na samostatnou pracovní instanci nebo sadu instancí a začlenit je před jejich odchodem do produkčního prostředí. Swap je jenom okamžité a bezproblémové přesměrování provozu. Pokud po prohození dojde k nějakým potížím v produkčním prostředí, můžete se kdykoli vrátit zpátky k poslednímu známému funkčnímu stavu výroby.

## <a name="update-connection-string"></a>Aktualizovat připojovací řetězec

Ve výchozím nastavení očekává Azure nové připojení aplikace k nové SQL Server databázi, aby používala připojovací řetězec s názvem `DefaultConnection`. Aktuálně vytvořená aplikace, kterou jsme vytvořili dříve v této sérii kurzů, používá připojovací řetězec s názvem `AppDbContext`. Musíme to změnit v souboru *appSettings. JSON* a v *Startup.cs* a pak aplikaci znovu nasadit.

## <a name="test-the-app-running-in-azure"></a>Testování aplikace běžící v Azure

Přejděte na cestu */Games* a měli byste být schopni přidat novou hru a zobrazit ji v seznamu. Potom přejděte na cestu k */Swagger* a měli byste být schopni použít koncové body webového rozhraní API z této služby, aby bylo možné také ověřit, zda rozhraní API aplikace funguje.

Blahopřejeme! Dokončili jste tuto řadu kurzů videí!

## <a name="next-steps"></a>Další kroky

Přečtěte si další informace o tom, jak architektem ASP.NET Core aplikací pomocí těchto bezplatných prostředků.

[ASP.NET Core aplikační architektura](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Viz také

- [Publikování aplikace ASP.NET Core do Azure pomocí sady Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)