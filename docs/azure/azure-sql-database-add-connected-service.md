---
title: Přidat připojení k Azure SQL Database | Microsoft Docs
description: Přidání připojení Azure SQL Database k aplikaci pomocí připojených služeb sady Visual Studio
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: e1594ea4239b4200bf72ec4a2ef2c558839ef95c
ms.sourcegitcommit: 3ef987e99616c3eecf4731bf5ac89e16238e68aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88643416"
---
# <a name="add-a-connection-to-azure-sql-database"></a>Přidání připojení k Azure SQL Database

Pomocí sady Visual Studio můžete ke službě Azure SQL Database připojit kteroukoli z následujících funkcí pomocí funkce **připojené služby** :

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

## <a name="connect-to-azure-sql-database-using-connected-services"></a>Připojení k Azure SQL Database pomocí připojených služeb

1. Otevřete svůj projekt v sadě Visual Studio.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

1. Na kartě **připojené služby** vyberte ikonu + pro **závislosti služby**.

    ![Přidat závislost služby](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stránce **Přidat závislost** vyberte **Azure SQL Database**.

    ![Přidat Azure SQL Database službu](./media/azure-sql-database-add-connected-service/azure-sql-database.png)

    Pokud ještě nejste přihlášení, přihlaste se k účtu Azure. Pokud účet Azure nemáte, můžete si zaregistrovat [bezplatnou zkušební verzi](https://azure.microsoft.com/account/free).

1. Na obrazovce **Azure SQL Database konfigurace** vyberte existující Azure SQL Database a vyberte **Další**.

    Pokud potřebujete vytvořit novou součást, pokračujte k dalšímu kroku. Jinak přejděte ke kroku 7.

    ![Připojit k existující součásti Azure SQL Database](./media/azure-sql-database-add-connected-service/created-azure-sql-database.png)

1. Vytvoření Azure SQL Database:

   1. V dolní části obrazovky vyberte **vytvořit SQL Database** .

   1. Vyplňte **Azure SQL Database: vytvořit novou** obrazovku a vyberte **vytvořit**.

       ![Nový Azure SQL Database](./media/azure-sql-database-add-connected-service/create-new-azure-sql-database.png)

   1. Když se zobrazí obrazovka **konfigurace Azure SQL Database** , v seznamu se zobrazí nová databáze. V seznamu vyberte novou databázi a vyberte **Další**.

1. Zadejte název připojovacího řetězce nebo vyberte výchozí a vyberte, zda chcete připojovací řetězec Uložit do místního souboru tajných klíčů nebo v [Azure Key Vault](/azure/key-vault).

   ![Zadat připojovací řetězec](./media/azure-sql-database-add-connected-service/connection-string.png)

1. Obrazovka **Souhrn změn** zobrazuje všechny změny, které budou provedeny v projektu, pokud jste dokončili proces. Pokud se změní vzhled tlačítka OK, klikněte na tlačítko **Dokončit**.

   ![Souhrn změn](./media/azure-sql-database-add-connected-service/summary-of-changes.png)

   Pokud se zobrazí výzva k nastavení pravidel brány firewall, vyberte **Ano**.

   ![Pravidla brány firewall](./media/azure-sql-database-add-connected-service/firewall-rules.png)

1. Připojení se zobrazí v části **závislosti služby** na kartě **připojené služby** .

   ![Závislosti služeb](./media/azure-sql-database-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Viz také

- [Stránka Azure SQL Database produktu](https://azure.microsoft.com/services/sql-database/)
- [Dokumentace ke službě Azure SQL Database](/azure/azure-sql/database/)
- [Připojené služby (Visual Studio pro Mac)](/visualstudio/mac/connected-services)
