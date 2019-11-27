---
title: Přidání služby Azure Storage pomocí připojených služeb
description: Přidání služby Azure Storage do vaší aplikace pomocí dialogu Visual Studio přidání připojené služby
author: ghogen
manager: jillfra
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 6d7bf7901ab33dc6dba50013ebdfa05c3188cd6c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300176"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Přidání služby Azure storage pomocí připojených služeb sady Visual Studio
Pomocí sady Visual Studio můžete pomocí dialogového okna **Přidat připojené služby** připojit kterýkoli z následujících Azure Storage:

- Cloudovou službu C#
- Mobilní služby back-end .NET
- Webové stránky ASP.NET nebo služby
- Služba ASP.NET Core
- Služba Azure WebJob

Funkce připojené služby do vašeho projektu přidá potřebné odkazy a připojovací kód a odpovídajícím způsobem upraví konfigurační soubory.

Po dokončení se v dialogovém okně **Přidat připojené služby** automaticky zobrazí dokumentace s podrobnostmi o krocích potřebných pro zahájení práce s úložištěm objektů blob, frontami a tabulkami.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Připojení k Azure Storage pomocí dialogového okna připojené služby
1. Otevřete projekt v sadě Visual Studio

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel **připojené služby** a v místní nabídce vyberte **Přidat připojenou službu**.

    ![Přidat Azure připojené služby](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. Na stránce **připojené služby** vyberte **cloudové úložiště s Azure Storage**.

    ![Přidání služby Azure Storage](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. V dialogovém okně **Azure Storage** vyberte existující účet úložiště a vyberte **Přidat**.

    Pokud potřebujete vytvořit účet úložiště, přejděte k dalšímu kroku. V opačném případě přejděte ke kroku 6.

    ![Přidat existující účet úložiště do projektu](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Chcete-li vytvořit účet úložiště:

   1. V dolní části dialogového okna vyberte **vytvořit nový účet úložiště** .

   1. Vyplňte dialogové okno **vytvořit účet úložiště** a vyberte **vytvořit**.

       ![Nový účet úložiště Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)

   1. Po zobrazení dialogového okna **Azure Storage** se v seznamu zobrazí nový účet úložiště. V seznamu vyberte nový účet úložiště a pak vyberte **Přidat**.

1. Služba připojená k úložišti se zobrazí pod uzlem **odkazy na služby** vašeho projektu.

## <a name="how-your-project-is-modified"></a>Jak se váš projekt změnil
Po dokončení dialogové okno sady Visual Studio přidá odkazy a změní některé konfigurační soubory. Konkrétní změny závisí na typu projektu:

- ASP.NET projekt – [co se stalo – projekty ASP.NET](https://go.microsoft.com/fwlink/p/?LinkId=513126)
- ASP.NET Core projekt – [co se stalo – projekty ASP.NET 5](https://go.microsoft.com/fwlink/p/?LinkId=513124)
- Projekt cloudové služby (webové role a role pracovního procesu) – [co se stalo – projekty cloudových služeb](https://go.microsoft.com/fwlink/p/?LinkId=516965)
- Projekt webové úlohy – [co se stalo – projekty WebJob](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Další kroky
- [Fórum MSDN: Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog týmu Microsoft Azure Storage](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Dokumentace k Azure Storage](https://docs.microsoft.com/azure/storage/)
