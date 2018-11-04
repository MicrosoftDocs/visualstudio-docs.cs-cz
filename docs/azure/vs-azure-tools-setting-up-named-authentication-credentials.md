---
title: Nastavení přihlašovacích údajů pro ověřování s názvem | Dokumentace Microsoftu
description: Zjistěte, jak k zadání přihlašovacích údajů, které Visual Studio můžete použít k ověření požadavků ve službě Azure, takže můžete publikovat aplikaci do Azure ze sady Visual Studio nebo monitorujte existující cloudovou službu.
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: f3d0a3499257a72d500774f00824150f88757823
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673510"
---
# <a name="set-up-named-authentication-credentials"></a>Nastavení přihlašovacích údajů pro ověřování s názvem

K publikování aplikace do Azure nebo k monitorování existující cloudovou službu Visual Studio vyžaduje přihlašovací údaje pro ověření požadavků ve službě Azure, a to ID vašeho předplatného Azure a platný certifikát X.509 v3 s klíčem alespoň 2 048 bitů. Zadáte tyto přihlašovací údaje pomocí kteréhokoliv z následujících metod:

- V sadě Visual Studio vyberte **zobrazení > Průzkumníka serveru**, klikněte pravým tlačítkem myši **Azure** uzlu, vyberte **připojit k předplatnému Microsoft Azure**a přihlaste se.
- Vytvořte soubor předplatného (`.publishsettings`), který obsahuje veřejný klíč pro certifikát. Soubor odběru může obsahovat přihlašovací údaje pro více než jedno předplatné, jak je popsáno v tomto článku.

Poznámka: tyto přihlašovací údaje se liší od přihlašovací údaje použité pro ověřování požadavků na služby Azure storage.

## <a name="create-a-subscription-file"></a>Vytvořte soubor předplatného

V Průzkumníku serveru, klikněte pravým tlačítkem myši **Azure** uzel a vyberte možnost **spravovat a filtrovat předplatná**. Vyberte **certifikáty** kartu a pak udělejte jednu z následujících akcí:

- Vyberte **Import** otevřít **předplatná Microsoft Azure Import** dialogové okno. Vyberte **stáhnout soubor předplatného** propojit a v prohlížeči Uložte stažený soubor do dočasné složky. V dialogovém okně přejděte do umístění, stahování a importovat ho pro použití při ověřování.
- Zvolte předplatné aktivní a vyberte **upravit**, která otevře dialogové okno, ve kterém můžete upravit existujícího předplatného pro použití při ověřování.
- Vyberte **nový** otevřít **nové předplatné** dialogové okno pole a zadejte požadované podrobnosti. K nahrání certifikátu do cloudové služby jsou uvedené v dialogovém okně přihlásit na webu Azure portal, přejděte ke cloudové službě, vyberte **Nastavení > certifikáty pro správu**vyberte **nahrát**, pak Zadejte cestu k `.cer` souboru.

Pokud chcete vytvořit certifikát, můžete použít pokyny v [vytvoření a nahrání certifikátu pro správu pro Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) a ručně nahrát certifikát, který [webu Azure portal](https://portal.azure.com/).

## <a name="next-steps"></a>Další kroky

- [Obecný přehled o Web Apps](https://docs.microsoft.com/azure/app-service/)
- [Nasazení aplikace do služby Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Nasazení WebJobs pomocí sady Visual Studio](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Vytvořit a nasadit cloudovou službu](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)