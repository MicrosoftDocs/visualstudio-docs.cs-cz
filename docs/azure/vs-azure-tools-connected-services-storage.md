---
title: Přidání Azure Storage pomocí připojených služeb | Microsoft Docs
description: Přidání Azure Storage do aplikace pomocí dialogového okna Přidat připojené služby v aplikaci Visual Studio
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: ca65086ce7ce09a1ca288c2f5cd04c31e00f8e95
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911899"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Přidání služby Azure Storage pomocí připojených služeb sady Visual Studio

Pomocí sady Visual Studio můžete pomocí dialogového okna **Přidat připojené služby** připojit kterýkoli z následujících Azure Storage:

- C#Cloudová služba
- Mobilní služba back-endu .NET
- Web nebo služba ASP.NET
- Služba ASP.NET Core
- Služba Azure WebJob

Funkce připojené služby přidá všechny potřebné odkazy a kód připojení k vašemu projektu a patřičně upraví konfigurační soubory.

Po dokončení se v dialogovém okně **Přidat připojené služby** automaticky zobrazí dokumentace s podrobnostmi o krocích potřebných pro zahájení práce s úložištěm objektů blob, frontami a tabulkami.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [připojené služby v Visual Studio pro Mac](/visualstudio/mac/connected-services).

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Připojení k Azure Storage pomocí dialogového okna připojené služby

1. Otevřete projekt v aplikaci Visual Studio

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

    ![Přidat připojenou službu Azure](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. Na stránce **připojené služby** vyberte **cloudové úložiště s Azure Storage**.

    ![Přidat Azure Storage](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. V dialogovém okně **Azure Storage** vyberte existující účet úložiště a vyberte **Přidat**.

    Pokud potřebujete vytvořit účet úložiště, pokračujte na další krok. V opačném případě přejděte ke kroku 6.

    ![Přidat existující účet úložiště do projektu](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Vytvoření účtu úložiště:

   1. V dolní části dialogového okna vyberte **vytvořit nový účet úložiště** .

   1. Vyplňte dialogové okno **vytvořit účet úložiště** a vyberte **vytvořit**.

       ![Nový účet úložiště Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Po zobrazení dialogového okna **Azure Storage** se v seznamu zobrazí nový účet úložiště. V seznamu vyberte nový účet úložiště a pak vyberte **Přidat**.

1. Služba připojená k úložišti se zobrazí pod uzlem **odkazy na služby** vašeho projektu.

## <a name="how-your-project-is-modified"></a>Způsob úpravy projektu

Po dokončení dialogu Visual Studio přidá odkazy a upraví určité konfigurační soubory. Konkrétní změny závisí na typu projektu:

- ASP.NET projekt – [co se stalo – projekty ASP.NET](/azure/visual-studio/vs-storage-aspnet-getting-started-blobs)
- ASP.NET Core projekt – [co se stalo – projekty ASP.NET 5](/azure/visual-studio/vs-storage-aspnet5-getting-started-blobs)
- Projekt cloudové služby (webové role a role pracovního procesu) – [co se stalo – projekty cloudových služeb](/azure/visual-studio/vs-storage-cloud-services-getting-started-blobs)
- Projekt webové úlohy – [co se stalo – projekty WebJob](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="see-also"></a>Viz také:

- [Fórum MSDN: Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog týmu Microsoft Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Dokumentace k Azure Storage](/azure/storage/)
- [Připojené služby (Visual Studio pro Mac)](/visualstudio/mac/connected-services)
