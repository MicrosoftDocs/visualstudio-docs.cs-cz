---
title: Přidat službu Azure Signal pomocí připojených služeb | Microsoft Docs
description: Přidání služby Azure Signal do aplikace pomocí sady Visual Studio pro přidání připojené služby
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4576c2eb15097860870b78fbca0faf727c3eae74
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902880"
---
# <a name="add-azure-signalr-by-using-visual-studio-connected-services"></a>Přidání služby Azure Signal pomocí připojených služeb sady Visual Studio

Pomocí sady Visual Studio můžete ke službě Azure Signal Service připojit kteroukoli z následujících funkcí pomocí funkce **připojené služby** :

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

## <a name="connect-to-azure-signalr-using-connected-services"></a>Připojení ke službě Azure Signal pomocí připojených služeb

1. Otevřete svůj projekt v sadě Visual Studio.

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

1. Na kartě **připojené služby** vyberte ikonu + pro **závislosti služby**.

    ![Přidat závislost služby](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stránce **Přidat závislost** vyberte **Služba signalizace Azure**.

    ![Přidat službu Azure Signal](./media/azure-signalr-add-connected-service/add-signalr-service.png)

    Pokud ještě nejste přihlášení, přihlaste se k účtu Azure. Pokud účet Azure nemáte, můžete si zaregistrovat [bezplatnou zkušební verzi](https://azure.microsoft.com/account/free).

1. Na obrazovce **Konfigurace služby Azure Signal** vyberte existující součást služby Azure Signal a vyberte **Další**.

    Pokud potřebujete vytvořit novou součást, pokračujte k dalšímu kroku. Jinak přejděte ke kroku 7.

    ![Připojit ke stávající komponentě služby Azure Signal](./media/azure-signalr-add-connected-service/created-signalr.png)

1. Vytvoření instance služby signalizace Azure:

   1. V dolní části obrazovky vyberte **vytvořit novou instanci služby signalizace Azure** .

   1. Vyplňte **službu Azure Signal Service: vytvořit novou** obrazovku a vyberte **vytvořit**.

       ![Nová instance služby signalizace Azure](./media/azure-signalr-add-connected-service/create-new-signalr.png)

   1. Po zobrazení obrazovky **Konfigurovat službu signalizace Azure** se v seznamu zobrazí nová instance. V seznamu vyberte novou instanci a vyberte **Další**.

1. Zadejte název připojovacího řetězce nebo vyberte výchozí a vyberte, zda chcete připojovací řetězec Uložit do místního souboru tajných klíčů nebo v [Azure Key Vault](/azure/key-vault).

   ![Zadat připojovací řetězec](./media/azure-signalr-add-connected-service/connection-string.png)

1. Obrazovka **Souhrn změn** zobrazuje všechny změny, které budou provedeny v projektu, pokud jste dokončili proces. Pokud se změní vzhled tlačítka OK, klikněte na tlačítko **Dokončit**.

   ![Souhrn změn](./media/azure-signalr-add-connected-service/summary-of-changes.png)

1. Připojení se zobrazí v části **závislosti služby** na kartě **připojené služby** .

   ![Závislosti služeb](./media/azure-signalr-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Viz také

- [Stránka produktového signálu Azure](https://azure.microsoft.com/services/signalr-service/)
- [Dokumentace ke službě Azure SignalR](/azure/azure-signalr)
- [Připojené služby (Visual Studio pro Mac)](/visualstudio/mac/connected-services)
