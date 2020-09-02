---
title: Přidání Azure Storage pomocí připojených služeb | Microsoft Docs
description: Přidání závislosti služby Azure Storage do aplikace pomocí připojených služeb sady Visual Studio
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 08/13/2020
ms.author: ghogen
ms.openlocfilehash: f2f55a149420205435d9f64ea1f66c8c6854ec38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800512"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Přidání služby Azure Storage pomocí připojených služeb sady Visual Studio

Pomocí sady Visual Studio můžete pomocí funkce **připojené služby** připojit kterýkoli z následujících Azure Storage:

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

## <a name="connect-to-azure-storage-using-connected-services"></a>Připojení k Azure Storage pomocí připojených služeb

::: moniker range="vs-2017"

1. Otevřete svůj projekt v sadě Visual Studio.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

    ![Přidat připojenou službu Azure](./media/vs-azure-tools-connected-services-storage/add-connected-service.png)

1. Na stránce **připojené služby** vyberte **cloudové úložiště s Azure Storage**.

    ![Přidání služby Azure Storage](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. V dialogovém okně **Azure Storage** vyberte existující účet úložiště a vyberte **Přidat**.

    Pokud potřebujete vytvořit účet úložiště, pokračujte na další krok. V opačném případě přejděte ke kroku 6.

    ![Přidat existující účet úložiště do projektu](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Vytvoření účtu úložiště:

   1. V dolní části dialogového okna vyberte **vytvořit nový účet úložiště** .

   1. Vyplňte dialogové okno **vytvořit účet úložiště** a vyberte **vytvořit**.

       ![Nový účet úložiště Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Po zobrazení dialogového okna **Azure Storage** se v seznamu zobrazí nový účet úložiště. V seznamu vyberte nový účet úložiště a pak vyberte **Přidat**.

1. Služba připojená k úložišti se zobrazí pod uzlem **odkazy na služby** vašeho projektu.
:::moniker-end

:::moniker range=">=vs-2019"

1. Otevřete svůj projekt v sadě Visual Studio.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

    ![Přidat připojenou službu Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Na kartě **připojené služby** vyberte ikonu + pro **závislosti služby**.

    ![Přidat závislost služby](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stránce **Přidat závislost** vyberte **Azure Storage**.

    ![Přidání služby Azure Storage](./media/vs-azure-tools-connected-services-storage/vs-2019/add-azure-storage.png)

    Pokud ještě nejste přihlášení, přihlaste se k účtu Azure. Pokud účet Azure nemáte, můžete si zaregistrovat [bezplatnou zkušební verzi](https://azure.microsoft.com/account/free).

1. Na obrazovce **konfigurace Azure Storage** vyberte existující účet úložiště a **pak vyberte další**.

    Pokud potřebujete vytvořit účet úložiště, pokračujte na další krok. V opačném případě přejděte ke kroku 6.

    ![Přidat existující účet úložiště do projektu](./media/vs-azure-tools-connected-services-storage/vs-2019/select-azure-storage-account.png)

1. Vytvoření účtu úložiště:

   1. V dolní části dialogového okna vyberte **vytvořit účet úložiště** .

   1. Vyplňte **Azure Storage: vytvořit nový** dialog a vyberte **vytvořit**.

       ![Nový účet úložiště Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/create-storage-account.png)

   1. Po zobrazení dialogového okna **Azure Storage** se v seznamu zobrazí nový účet úložiště. V seznamu vyberte nový účet úložiště a **pak vyberte další**.

1. Zadejte název připojovacího řetězce a vyberte, zda chcete připojovací řetězec Uložit do místního souboru tajných klíčů, nebo v [Azure Key Vault](/azure/key-vault).

   ![Zadat připojovací řetězec](./media/vs-azure-tools-connected-services-storage/vs-2019/connection-string.png)

1. Obrazovka **Souhrn změn** zobrazuje všechny změny, které budou provedeny v projektu, pokud jste dokončili proces. Pokud se změní vzhled tlačítka OK, klikněte na tlačítko **Dokončit**.

   ![Souhrn změn](./media/vs-azure-tools-connected-services-storage/vs-2019/summary-of-changes.png)

1. Služba připojená k úložišti se zobrazí pod uzlem **odkazy na služby** vašeho projektu.
:::moniker-end

## <a name="see-also"></a>Viz také

- [Fórum Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Dokumentace ke službě Azure Storage](/azure/storage/)
- [Připojené služby (Visual Studio pro Mac)](/visualstudio/mac/connected-services)
