---
title: Přidání Application Insights Azure pomocí připojených služeb | Microsoft Docs
description: Přidání služby Azure Application Insights do vaší aplikace pomocí sady Visual Studio pro přidání připojené služby
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: c15e7a14052efdab82388a950865557cb4425771
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643434"
---
# <a name="add-azure-application-insights-by-using-visual-studio-connected-services"></a>Přidání Application Insights Azure pomocí připojených služeb sady Visual Studio

Pomocí sady Visual Studio můžete k Azure Application Insights připojit kterýkoli z následujících funkcí s **připojenými službami** :

- .NET Framework Konzolová aplikace
- ASP.NET MVC (.NET Framework) 
- Jádro ASP.NET
- .NET Core (včetně konzolové aplikace, WPF, model Windows Forms, knihovny tříd)
- Role pracovního procesu .NET Core
- Azure Functions
- Aplikace Univerzální platforma Windows
- Xamarin
- Cordova

Funkce připojené služby přidá všechny potřebné odkazy a kód připojení k vašemu projektu a patřičně upraví konfigurační soubory.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [připojené služby v Visual Studio pro Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Předpoklady

- Visual Studio s nainstalovanou úlohou Azure
- Projekt jednoho z podporovaných typů

## <a name="connect-to-azure-application-insights-using-connected-services"></a>Připojení k Azure Application Insights pomocí připojených služeb

1. Otevřete svůj projekt v sadě Visual Studio.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

1. Na kartě **připojené služby** vyberte ikonu + pro **závislosti služby**.

    ![Přidat závislost služby](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stránce **Přidat závislost** vyberte **Azure Application Insights**.

    ![Přidat Application Insights Azure](./media/azure-app-insights-add-connected-service/azure-app-insights.png)

    Pokud ještě nejste přihlášení, přihlaste se k účtu Azure. Pokud účet Azure nemáte, můžete si zaregistrovat [bezplatnou zkušební verzi](https://azure.microsoft.com/account/free).

1. Na obrazovce **konfigurace Application Insights pro Azure** vyberte existující součást Azure Application Insights a vyberte **Další**.

    Pokud potřebujete vytvořit novou součást, pokračujte k dalšímu kroku. Jinak přejděte ke kroku 7.

    ![Připojit k existující součásti Application Insights](./media/azure-app-insights-add-connected-service/created-app-insights.png)

1. Vytvoření součásti Application Insights:

   1. V dolní části obrazovky vyberte **vytvořit novou součást Application Insights** .

   1. Vyplňte **Application Insights: vytvořit novou** obrazovku a vyberte **vytvořit**.

       ![Nová součást Azure App Insights](./media/azure-app-insights-add-connected-service/create-new-app-insights.png)

   1. Když se zobrazí obrazovka **Konfigurace služby Azure Application Insights** , v seznamu se zobrazí nová komponenta. V seznamu vyberte novou součást a vyberte **Další**.

1. Zadejte název klíče instrumentace, nebo vyberte výchozí a vyberte, zda chcete připojovací řetězec Uložit do místního souboru tajných klíčů nebo v [Azure Key Vault](/azure/key-vault).

   ![Zadat připojovací řetězec](./media/azure-app-insights-add-connected-service/connection-string.png)

1. Obrazovka **Souhrn změn** zobrazuje všechny změny, které budou provedeny v projektu, pokud jste dokončili proces. Pokud se změní vzhled tlačítka OK, klikněte na tlačítko **Dokončit**.

   ![Souhrn změn](./media/azure-app-insights-add-connected-service/summary-of-changes.png)

1. Připojení se zobrazí v části **závislosti služby** na kartě **připojené služby** .

   ![Závislosti služeb](./media/azure-app-insights-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Viz také

- [Stránka Azure Monitor produktu](https://azure.microsoft.com/services/monitor/)
- [Dokumentace ke službě Azure App Insights](/azure/azure-monitor/app/app-insights-overview/)
- [Připojené služby (Visual Studio pro Mac)](/visualstudio/mac/connected-services)
