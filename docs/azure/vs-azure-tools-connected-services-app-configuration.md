---
title: Přidání konfigurace aplikace Azure pomocí připojených služeb | Microsoft Docs
description: Přidání závislosti služby konfigurace Azure do vaší aplikace pomocí připojených služeb sady Visual Studio
author: ghogen
manager: ''
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 12/11/2020
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 250b89c983da039717982b31873a470172bde0f5
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683294"
---
# <a name="adding-azure-app-configuration-by-using-visual-studio-connected-services"></a>Přidání konfigurace aplikace Azure pomocí připojených služeb sady Visual Studio

V tomto kurzu se naučíte, jak snadno přidat všechno, co potřebujete k tomu, abyste mohli začít používat Azure App Configuration ke správě příznaků konfigurace a funkcí pro webové projekty v aplikaci Visual Studio. Pomocí funkce připojené služby v aplikaci Visual Studio může Visual Studio automaticky přidat všechny kódy, balíčky NuGet a nastavení konfigurace, která potřebujete připojit k prostředku konfigurace aplikace v Azure. Chcete-li použít tuto funkci, musíte použít Visual Studio 2019 verze 16,9 nebo novější.

Funkci konfigurace aplikace připojené služby můžete použít v ASP.NET Core, konzole .NET Core a v projektech .NET Framework.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [připojené služby v Visual Studio pro Mac](/visualstudio/mac/connected-services).

## <a name="prerequisites"></a>Požadavky

- Visual Studio s nainstalovanou úlohou Azure
- Projekt jednoho z podporovaných typů

## <a name="connect-to-azure-app-configuration-using-connected-services"></a>Připojení k Azure App Configuration pomocí připojených služeb

1. Otevřete svůj projekt v sadě Visual Studio.

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

    ![Přidat připojenou službu Azure](./media/vs-azure-tools-connected-services-storage/vs-2019/add-connected-service.png)

1. Na kartě **připojené služby** vyberte ikonu + pro **závislosti služby**.

    ![Přidat závislost služby](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. Na stránce **Přidat závislost** vyberte **Konfigurace aplikace Azure**.

    ![Přidat konfiguraci aplikace](./media/vs-azure-tools-connected-services-app-configuration/add-azure-app-configuration.png)

    Pokud ještě nejste přihlášení, přihlaste se k účtu Azure. Pokud účet Azure nemáte, můžete si zaregistrovat [bezplatnou zkušební verzi](https://azure.microsoft.com/free/dotnet).

1. Na obrazovce konfigurace **aplikace Azure** vyberte vaše předplatné a stávající úložiště konfigurace. Pak vyberte **Další**.

    Pokud potřebujete vytvořit úložiště konfigurace aplikace, pokračujte na další krok. V opačném případě přejděte ke kroku 6.

    ![Přidat existující konfigurační účet do projektu](./media/vs-azure-tools-connected-services-app-configuration/select-config-store.png)

1. Vytvoření úložiště konfigurace aplikace:

   1. Vyberte ikonu + napravo od záhlaví **úložiště konfigurace aplikace** . 

   1. Vyplňte **konfiguraci aplikace Azure: vytvořit nový** dialog a vyberte **vytvořit**. Všimněte si, že pole název prostředku musí být jedinečné. 

       ![Nové úložiště konfigurace aplikace Azure](./media/vs-azure-tools-connected-services-app-configuration/create-new-config-store.png)

   1. Po zobrazení dialogového okna **Konfigurace aplikace Azure** se v seznamu zobrazí nové úložiště konfigurace. Vyberte toto nové úložiště a pak vyberte **Další**.

1. Zadejte název připojovacího řetězce a vyberte, zda chcete připojovací řetězec Uložit do místního souboru tajných klíčů, nebo v [Azure Key Vault](/azure/key-vault).

   ![Zadat připojovací řetězec](./media/vs-azure-tools-connected-services-app-configuration/connection-string-app-config.png)

1. Obrazovka **Souhrn změn** zobrazuje všechny změny, které budou provedeny v projektu, pokud jste dokončili proces. Pokud se změní vzhled tlačítka OK, klikněte na tlačítko **Dokončit**.

   ![Souhrn změn](./media/vs-azure-tools-connected-services-app-configuration/summary-of-changes-app-config.png)

1. Po dokončení **procesu konfigurace závislosti** se teď v uzlu **závislosti služby** v projektu zobrazí konfigurace aplikace Azure.

## <a name="next-steps"></a>Další kroky

Přečtěte si o konfiguraci aplikací Azure v [dokumentaci ke konfiguraci aplikací Azure](/azure/azure-app-configuration/overview).

## <a name="see-also"></a>Viz také

- [Kurz pro použití dynamické konfigurace v konfiguraci aplikace připojené ASP.NET Core aplikaci](/azure/azure-app-configuration/enable-dynamic-configuration-aspnet-core)
- [Připojené služby (Visual Studio pro Mac)](/visualstudio/mac/connected-services)