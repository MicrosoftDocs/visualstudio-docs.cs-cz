---
title: Přidání mezipaměti Azure pro Redis pomocí připojených služeb | Microsoft Docs
description: Přidejte do své aplikace podporu Azure cache pro Redis, která umožňuje přidat připojenou službu pomocí sady Visual Studio.
author: AngelosP
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: ad233d51e271dfbacb80b7f5f2792d546a8a3e0a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903055"
---
# <a name="add-azure-cache-for-redis-by-using-visual-studio-connected-services"></a>Přidání mezipaměti Azure pro Redis pomocí připojených služeb sady Visual Studio

Pomocí sady Visual Studio můžete ke službě Azure cache for Redis připojit libovolný z následujících funkcí pomocí funkce **připojených služeb** :

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

## <a name="connect-to-azure-cache-for-redis-using-connected-services"></a>Připojení k Azure cache pro Redis pomocí připojených služeb

1. Otevřete svůj projekt v sadě Visual Studio.

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

1. Na kartě **připojené služby** vyberte ikonu + pro **závislosti služby**.

    ![Přidat závislost služby](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stránce **Přidat závislost** vyberte **mezipaměť Azure pro Redis**.

    ![Přidání služby Azure Cache for Redis](./media/azure-redis-cache-add-connected-service/azure-redis-cache.png)

    Pokud ještě nejste přihlášení, přihlaste se k účtu Azure. Pokud účet Azure nemáte, můžete si zaregistrovat [bezplatnou zkušební verzi](https://azure.microsoft.com/account/free).

1. Na obrazovce **Konfigurace mezipaměti Azure pro Redis** vyberte existující mezipaměť Azure pro Redis a vyberte **Další**.

    Pokud potřebujete vytvořit novou součást, pokračujte k dalšímu kroku. Jinak přejděte ke kroku 7.

    ![Připojení k existující mezipaměti Azure pro Redis](./media/azure-redis-cache-add-connected-service/created-azure-redis-cache.png)

1. Vytvoření Azure Redis Cache:

   1. V dolní části obrazovky vyberte **vytvořit novou Azure Redis Cache** .

   1. Vyplňte **mezipaměť Azure pro Redis: vytvořit novou** obrazovku a vyberte **vytvořit**.

       ![Nová mezipaměť Azure pro Redis](./media/azure-redis-cache-add-connected-service/create-new-azure-redis-cache.png)

   1. Když se zobrazí obrazovka **Konfigurace mezipaměti Azure pro Redis** , zobrazí se v seznamu nová mezipaměť. V seznamu vyberte novou databázi a vyberte **Další**.

1. Zadejte název připojovacího řetězce nebo vyberte výchozí a vyberte, zda chcete připojovací řetězec Uložit do místního souboru tajných klíčů nebo v [Azure Key Vault](/azure/key-vault).

   ![Zadat připojovací řetězec](./media/azure-redis-cache-add-connected-service/connection-string.png)

1. Obrazovka **Souhrn změn** zobrazuje všechny změny, které budou provedeny v projektu, pokud jste dokončili proces. Pokud se změní vzhled tlačítka OK, klikněte na tlačítko **Dokončit**.

   ![Souhrn změn](./media/azure-redis-cache-add-connected-service/summary-of-changes.png)

1. Připojení se zobrazí v části **závislosti služby** na kartě **připojené služby** .

   ![Závislosti služeb](./media/azure-redis-cache-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>Viz také

- [Stránka produktu Azure cache pro Redis](https://azure.microsoft.com/services/cache)
- [Dokumentace k Azure cache pro Redis](/azure/azure-cache-for-redis/)
- [Připojené služby (Visual Studio pro Mac)](/visualstudio/mac/connected-services)