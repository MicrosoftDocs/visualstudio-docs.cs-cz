---
title: 'Krok 5: Nasazení aplikace ASP.NET Core do Azure'
description: Pomocí tohoto výukového programu na video a podrobných pokynů nasaďte ASP.NET Core Web App do Azure.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580027"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Krok 5: Nasazení aplikace ASP.NET Core do Azure

Podle těchto kroků nasadíte ASP.NET aplikaci Core a její databázi do Azure.

_Podívejte se na toto video a postupujte podle pokynů k nasazení první aplikace ASP.NET Core do Azure._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Otevření projektu

Otevřete aplikaci ASP.NET Core ve Visual Studiu 2019. Aplikace by již měla používat nastavení s EF Core a pracovní webové rozhraní API, jak je nakonfigurováno v [kroku 4 této série kurzů](tutorial-aspnet-core-ef-step-04.md).

## <a name="publish-to-azure-app-service"></a>Publikování do Azure App Service

Klikněte pravým tlačítkem myši na projekt v průzkumníku řešení a zvolte **Publikovat**. Ponechte výchozí nastavení **služby App Service** a **Vytvořit nový** a klikněte na tlačítko **Publikovat.** Pokud ještě nemáte účet Azure, klikněte na **vytvořit bezplatný účet Azure** a dokončete krátký proces registrace.

Přidejte SQL Server. Zadejte uživatelské jméno a heslo správce.

![Visual Studio 2019 Vytvoření Azure SQL Serveru](media/vs-2019/vs2019-azure-sql-server.png)

Přidejte přehledy aplikací.

Pokračujte klepnutím na tlačítko **Vytvořit.**

![Visual Studio 2019 Vytvořit novou službu Azure App Service](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Prozkoumání portálu Azure a hostované aplikace

Po vytvoření služby aplikace se váš web spustí v prohlížeči. Při načítání můžete taky najít službu App Service na webu Azure Portal. Při procházení dostupných možností služby aplikace najdete část **Přehled,** kde můžete aplikaci spustit a zastavit.

![Možnosti služby Azure App Service](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Škálovatelnost

Můžete prozkoumat možnosti škálování aplikace, stejně jako ven. Škálování znamená zvýšení prostředků přidělených každé instanci hostující vaši aplikaci. Horizontální navýšení kapacity odkazuje na zvýšení počtu instancí hostujících vaši aplikaci. Můžete nakonfigurovat automatické škálování pro vaši aplikaci, která automaticky zvýší počet instancí používaných k hostování vaší aplikace v reakci na načtení a pak je sníží, jakmile se sníží zatížení.

### <a name="security-and-compliance"></a>Zabezpečení a dodržování předpisů

Další výhodou hostování naší aplikace pomocí Azure je zabezpečení a dodržování předpisů. Služba Azure App Service poskytuje dodržování předpisů ISO, SOC a PCI. Můžeme se rozhodnout ověřit uživatele pomocí Azure Active Directory nebo sociálních přihlášení, jako je Twitter, Facebook, Google nebo Microsoft. Můžeme vytvářet omezení IP adres, spravovat identity služeb, přidávat vlastní domény a podporovat protokol SSL pro aplikaci a také konfigurovat zálohy s obnovovatelnými archivními kopiemi obsahu, konfigurace a databáze aplikace. Tyto funkce jsou přístupné v možnostech nabídky Ověřování / Autorizace, Identita, zálohy a Nastavení Protokolu SSL.

### <a name="deployment-slots"></a>Nasazovací sloty

Často při nasazování aplikace, je malá doba prostojů, zatímco aplikace restartuje. Nasazení Sloty vyhnout se tomuto problému tím, že vám umožní nasadit na samostatnou pracovní instanci nebo sadu instancí a zahřát tyto před jejich přepnutí do produkčního prostředí. Výměna je jen okamžité a bezproblémové přesměrování provozu. Pokud existují nějaké problémy v produkčním prostředí po prohození, můžete vždy vyměnit zpět do posledního známého dobrého stavu výroby.

## <a name="update-connection-string"></a>Aktualizovat připojovací řetězec

Ve výchozím nastavení Azure očekává, že připojení nové aplikace k nové `DefaultConnection`databázi SERVERU SQL Server bude používat připojovací řetězec s názvem . V současné době aplikace, kterou jsme vytvořili `AppDbContext`dříve v této sérii kurzů, používá připojovací řetězec s názvem . Musíme to změnit v *appsettings.json* a *Startup.cs* a potom znovu nasadit aplikaci.

## <a name="test-the-app-running-in-azure"></a>Testování aplikace spuštěné v Azure

Přejděte na cestu */Games* a měli byste být schopni přidat novou hru a vidět ji uvedenou. Dále přejděte na */swagger* cestu a měli byste být schopni použít koncové body webového rozhraní API odtud potvrdit, že rozhraní API aplikace funguje také.

Blahopřejeme! Dokončili jste toto video tutorial série!

## <a name="next-steps"></a>Další kroky

Další informace o tom, jak navrhovat ASP.NET základní aplikace pomocí těchto volných prostředků.

[ASP.NET základní aplikační architektura](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Viz také

- [Publikování aplikace ASP.NET Core do Azure pomocí Visual Studia](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)