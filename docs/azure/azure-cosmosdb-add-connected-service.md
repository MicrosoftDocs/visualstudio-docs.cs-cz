---
title: Přidání Azure CosmosDB pomocí připojených služeb | Microsoft Docs
description: Přidejte do své aplikace podporu Azure CosmosDB pomocí sady Visual Studio, abyste mohli přidat připojenou službu.
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4a2789246a75fe7d2331156eecb106f31f21cbf5
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902919"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Přidání Azure Cosmos DB do aplikace pomocí připojených služeb sady Visual Studio

Pomocí sady Visual Studio můžete pomocí funkce **připojené služby** připojit kterýkoli z následujících Azure Cosmos DB:

- .NET Framework Konzolová aplikace
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
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

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Připojení k Azure Cosmos DB pomocí připojených služeb

1. Otevřete svůj projekt v sadě Visual Studio.

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

1. Na kartě **připojené služby** vyberte ikonu + pro **závislosti služby**.

    ![Přidat závislost služby](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stránce **Přidat závislost** vyberte **Azure Cosmos DB**.

    ![Přidat Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Pokud ještě nejste přihlášení, přihlaste se k účtu Azure. Pokud účet Azure nemáte, můžete si zaregistrovat [bezplatnou zkušební verzi](https://azure.microsoft.com/account/free).

1. Na obrazovce **Azure Cosmos DB** vyberte existující Azure Cosmos DB a vyberte **Další**.

    Pokud potřebujete vytvořit databázi, pokračujte na další krok. Jinak přejděte ke kroku 7.

    ![Přidat existující Cosmos DB do projektu](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Vytvoření Azure Cosmos DB:

   1. V dolní části obrazovky vyberte **vytvořit novou Azure Cosmos DB** .

   1. Vyplňte **Azure Cosmos DB: vytvořit novou** obrazovku a vyberte **vytvořit**.

       ![Nový Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Po zobrazení dialogového okna **konfigurovat Azure Cosmos DB** se v seznamu zobrazí nová databáze. V seznamu vyberte novou databázi a vyberte **Další**.

1. Zadejte název připojovacího řetězce a vyberte, zda chcete připojovací řetězec Uložit do místního souboru tajných klíčů, nebo v [Azure Key Vault](/azure/key-vault).

   ![Zadat připojovací řetězec](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. Obrazovka **Souhrn změn** zobrazuje všechny změny, které budou provedeny v projektu, pokud jste dokončili proces. Pokud se změní vzhled tlačítka OK, klikněte na tlačítko **Dokončit**.

   ![Souhrn změn](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. Připojení se zobrazí v části **závislosti služby** na kartě **připojené služby** .

   ![Závislosti služeb](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Viz také

- [Stránka Azure Cosmos DB produktu](https://azure.microsoft.com/services/cosmos-db/)
- [Dokumentace ke službě Azure Cosmos DB](/azure/cosmos-db/)
- [Připojené služby (Visual Studio pro Mac)](/visualstudio/mac/connected-services)
