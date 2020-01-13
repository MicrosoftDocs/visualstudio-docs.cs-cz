---
title: Nastavení přihlašovacích údajů s názvem ověřování | Microsoft Docs
description: Naučte se, jak zadat přihlašovací údaje, které může Visual Studio použít k ověřování požadavků do Azure, takže můžete publikovat aplikaci do Azure ze sady Visual Studio nebo monitorovat stávající cloudovou službu.
author: ghogen
manager: jillfra
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 27837390306ad29da55c7c5262ecd8fa6bcf75b3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917370"
---
# <a name="set-up-named-authentication-credentials"></a>Nastavení pojmenovaných přihlašovacích údajů pro ověřování

Pokud chcete publikovat aplikaci do Azure nebo monitorovat stávající cloudovou službu, Visual Studio vyžaduje přihlašovací údaje pro ověřování požadavků do Azure, konkrétně pro ID předplatného Azure a platný certifikát X. 509 v3 s klíčem minimálně 2048 bitů. Tyto přihlašovací údaje zadáte jednou z následujících metod:

- V aplikaci Visual Studio vyberte **zobrazení > Průzkumník serveru**, klikněte pravým tlačítkem myši na uzel **Azure** , vyberte možnost **připojit k Microsoft Azure předplatného**a přihlaste se.
- Vytvořte soubor předplatného (`.publishsettings`), který obsahuje veřejný klíč pro certifikát. Soubor předplatného může obsahovat přihlašovací údaje pro více než jedno předplatné, jak je popsáno v tomto článku.

Poznámka: tyto přihlašovací údaje se liší od přihlašovacích údajů používaných k ověřování žádostí do služeb Azure Storage.

## <a name="create-a-subscription-file"></a>Vytvořit soubor předplatného

V Průzkumník serveru klikněte pravým tlačítkem myši na uzel **Azure** a vyberte **Spravovat a filtrovat předplatná**. Pak vyberte kartu **certifikáty** a pak proveďte jednu z následujících akcí:

- Výběrem **importovat** otevřete dialogové okno **importovat předplatná Microsoft Azure** . Vyberte odkaz **Stáhnout soubor předplatného** a v prohlížeči uložte stažený soubor do dočasného umístění. Zpátky v dialogovém okně přejděte do umístění pro stahování a pak ho importujte pro použití v ověřování.
- Zvolte aktivní předplatné a klikněte na **Upravit**. otevře se dialogové okno, ve kterém můžete upravit existující předplatné pro použití v ověřování.
- Výběrem **nové** otevřete dialogové okno **Nový odběr** a zadejte požadované podrobnosti. Pokud chcete nahrát certifikát do vaší cloudové služby, přihlaste se do Azure Portal, přejděte do cloudové služby, vyberte **nastavení > certifikáty pro správu**, vyberte **nahrát**a pak zadejte cestu k souboru `.cer`.

Pokud chcete vytvořit certifikát sami, můžete postupovat podle pokynů v tématu [Vytvoření a nahrání certifikátu pro správu pro Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) a ručního nahrání certifikátu do [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Další kroky

- [Obecný přehled Web Apps](/azure/app-service/)
- [Nasazení aplikace pro Azure App Service](/azure/app-service/app-service-deploy-local-git) 
- [Nasazení WebJobs pomocí sady Visual Studio](/azure/app-service/websites-dotnet-deploy-webjobs)
- [Vytvoření a nasazení cloudové služby](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)