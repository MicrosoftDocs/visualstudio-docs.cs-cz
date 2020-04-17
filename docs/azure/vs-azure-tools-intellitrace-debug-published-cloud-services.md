---
title: Ladění publikované cloudové služby Azure pomocí Služby IntelliTrace
description: Zjistěte, jak ladit cloudovou službu pomocí Visual Studia a IntelliTrace
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: c61af4a08c61cbfd16d33e2b5cf7402960163f12
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489711"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Ladění publikované cloudové služby Azure pomocí sady Visual Studio a nástroje IntelliTrace
S IntelliTrace můžete protokolovat rozsáhlé informace o ladění pro instanci role při spuštění v Azure. Pokud potřebujete najít příčinu problému, můžete použít protokoly IntelliTrace krokovat kód z Visual Studia, jako kdyby byly spuštěny v Azure. IntelliTrace ve skutečnosti zaznamenává spuštění kódu klíče a data prostředí, když vaše aplikace Azure běží jako cloudová služba v Azure, a umožňuje přehrát nahraná data z Visual Studia.

IntelliTrace můžete použít, pokud máte nainstalovanou Visual Studio Enterprise a vaše aplikační cíle Azure .NET Framework 4 nebo novější verzi. IntelliTrace shromažďuje informace pro vaše role Azure. Virtuální počítače pro tyto role vždy spustit 64bitové operační systémy.

Jako alternativu můžete použít [vzdálené ladění](vs-azure-tools-debugging-cloud-services-overview.md) připojit přímo ke cloudové službě, která běží v Azure.

> [!IMPORTANT]
> IntelliTrace je určen pouze pro scénáře ladění a neměl by být používán pro produkční nasazení.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurace aplikace Azure pro IntelliTrace
Chcete-li povolit IntelliTrace pro aplikaci Azure, musíte vytvořit a publikovat aplikaci z projektu Visual Studio Azure. Před publikováním do Azure je nutné nakonfigurovat IntelliTrace pro vaši aplikaci Azure. Pokud publikujete aplikaci bez konfigurace IntelliTrace, je třeba znovu publikovat projekt. Další informace najdete [v tématu Publikování projektů cloudových služeb Azure pomocí Visual Studia](vs-azure-tools-publishing-a-cloud-service.md).

1. Až budete připraveni k nasazení aplikace Azure, ověřte, že cíle sestavení projektu jsou nastaveny na **ladění**.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt a v místní nabídce vyberte **Publikovat**.

1. V dialogovém okně **Publikovat aplikaci Azure** vyberte předplatné Azure a vyberte **Další**.

1. Na stránce **Nastavení** vyberte kartu **Upřesnit nastavení.**

1. Zapněte **možnost Povolit IntelliTrace** pro shromažďování protokolů IntelliTrace pro vaši aplikaci při publikování v cloudu.

1. Chcete-li přizpůsobit základní konfiguraci Technologie IntelliTrace, vyberte **možnost Nastavení** vedle **položky Povolit intelliTrace**.

    ![Odkaz nastavení IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. V dialogovém okně **Nastavení IntelliTrace** můžete určit, které události se mají protokolovat, zda shromažďovat informace o volání, které moduly a procesy pro shromažďování protokolů a kolik místa přidělit záznamu. Další informace o IntelliTrace naleznete v tématu [ladění pomocí technologie IntelliTrace](../debugger/intellitrace.md).

    ![Nastavení IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Protokol IntelliTrace je cyklický soubor protokolu o maximální velikosti zadané v nastavení IntelliTrace (výchozí velikost je 250 MB). Protokoly IntelliTrace jsou shromažďovány do souboru v systému souborů virtuálního počítače. Pokud požadujete protokoly, snímek je pořízena v tomto okamžiku a stáhnout do místního počítače.

Po publikování cloudové služby Azure do Azure můžete určit, jestli byl IntelliTrace povolen z uzlu Azure v **Průzkumníkovi serveru**, jak je znázorněno na následujícím obrázku:

![Průzkumník serveru – technologie IntelliTrace povolena](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Stáhnout protokoly IntelliTrace pro instanci role
Pomocí sady Visual Studio můžete stáhnout protokoly IntelliTrace pro instanci role pomocí následujících kroků:

1. V **Průzkumníkovi serveru**rozbalte uzel **Cloudservices** a vyhledejte instanci role, jejíž protokoly chcete stáhnout.

1. Klepněte pravým tlačítkem myši na instanci role a v kontextové nabídce s vyberte **zobrazit protokoly IntelliTrace**.

    ![Možnost nabídky Zobrazit protokoly IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Protokoly IntelliTrace jsou staženy do souboru v adresáři v místním počítači. Pokaždé, když požadujete protokoly IntelliTrace, je vytvořen nový snímek. Při stahování protokolů Visual Studio zobrazí průběh operace v okně **protokolu aktivit Azure.** Jak je znázorněno na následujícím obrázku, můžete rozbalit řádkovou položku pro operaci a zobrazit tak více podrobností.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Můžete pokračovat v práci v sadě Visual Studio při stahování protokolů IntelliTrace. Po dokončení stahování protokolu se otevře v sadě Visual Studio.

> [!NOTE]
> IntelliTrace protokoly může obsahovat výjimky, které rozhraní generuje a zpracovává později. Kód vnitřní hospo- architektury generuje tyto výjimky jako normální součást spuštění role, takže je můžete bezpečně ignorovat.
>
>

## <a name="next-steps"></a>Další kroky
- [Možnosti ladění cloudových služeb Azure](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publikování cloudové služby Azure pomocí Visual Studia](vs-azure-tools-publishing-a-cloud-service.md)