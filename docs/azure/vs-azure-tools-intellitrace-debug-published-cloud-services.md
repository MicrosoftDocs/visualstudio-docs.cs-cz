---
title: Ladění publikované cloudové služby Azure pomocí IntelliTrace
ms.custom: SEO-VS-2020
description: Naučte se ladit cloudovou službu pomocí sady Visual Studio a IntelliTrace
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.openlocfilehash: d419f80dc0319fbcebe053cd063cf668fc278a38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844200"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Ladění publikované cloudové služby Azure pomocí sady Visual Studio a nástroje IntelliTrace
Pomocí IntelliTrace můžete protokolovat rozsáhlé ladicí informace pro instanci role, když běží v Azure. Pokud potřebujete najít příčinu problému, můžete pomocí protokolů IntelliTrace Procházet kód ze sady Visual Studio, jako kdyby běžel v Azure. V důsledku toho IntelliTrace zaznamenává provádění kódu klíče a data prostředí, když je vaše aplikace Azure spuštěná jako cloudová služba v Azure a umožňuje přehrajte zaznamenaná data ze sady Visual Studio.

IntelliTrace můžete použít, pokud máte nainstalovaný Visual Studio Enterprise a vaše aplikace Azure cílí .NET Framework 4 nebo novější verze. IntelliTrace shromažďuje informace pro vaše role Azure. Virtuální počítače pro tyto role vždycky spouštějí 64 operační systémy.

Alternativně můžete [vzdálené ladění](vs-azure-tools-debugging-cloud-services-overview.md) použít k přímému připojení ke cloudové službě běžící v Azure.

> [!IMPORTANT]
> IntelliTrace je určený jenom pro scénáře ladění a neměl by se používat pro produkční nasazení.
>

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurace aplikace Azure pro IntelliTrace
Pokud chcete povolit IntelliTrace pro aplikaci Azure, musíte vytvořit a publikovat aplikaci z projektu Visual Studio Azure. Musíte nakonfigurovat IntelliTrace pro aplikaci Azure ještě před tím, než ji publikujete do Azure. Pokud publikujete aplikaci bez konfigurace IntelliTrace, je nutné projekt znovu publikovat. Další informace najdete v tématu [publikování projektů cloudových služeb Azure pomocí sady Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

1. Až budete připraveni k nasazení aplikace Azure, ověřte, že cíle sestavení projektu jsou nastavené na **ladění**.

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt a v místní nabídce vyberte **publikovat**.

1. V dialogovém okně **publikovat aplikaci Azure** vyberte předplatné Azure a **pak vyberte další**.

1. Na stránce **Nastavení** vyberte kartu **Rozšířená nastavení** .

1. Zapněte možnost **Povolit IntelliTrace** pro shromažďování protokolů IntelliTrace pro vaši aplikaci, když je publikovaná v cloudu.

1. Pokud chcete přizpůsobit základní konfiguraci IntelliTrace, vyberte **Nastavení** vedle možnosti **Povolit IntelliTrace**.

    ![Odkaz na nastavení IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)

1. V dialogovém okně **Nastavení IntelliTrace** můžete určit, které události se mají protokolovat, jestli se mají shromažďovat informace o voláních, které moduly a procesy mají shromažďovat protokoly, a kolik místa k záznamu se má přidělit. Další informace o IntelliTrace naleznete v tématu [ladění pomocí IntelliTrace](../debugger/intellitrace.md).

    ![Nastavení IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Protokol IntelliTrace je Cyklický soubor protokolu s maximální velikostí zadanou v nastavení IntelliTrace (výchozí velikost je 250 MB). Protokoly IntelliTrace jsou shromažďovány do souboru v systému souborů virtuálního počítače. Když vyžádáte protokoly, v tomto okamžiku se vytvoří snímek a stáhne se do místního počítače.

Po publikování cloudové služby Azure do Azure můžete zjistit, jestli je IntelliTrace povolený z uzlu Azure v **Průzkumník serveru**, jak je znázorněno na následujícím obrázku:

![Průzkumník serveru – IntelliTrace povolen](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Stažení protokolů IntelliTrace pro instanci role
Pomocí sady Visual Studio můžete stáhnout protokoly IntelliTrace pro instanci role pomocí následujících kroků:

1. V **Průzkumník serveru** rozbalte uzel **Cloud Services** a najděte instanci role, jejíž protokoly chcete stáhnout.

1. Klikněte pravým tlačítkem myši na instanci role a v kontextové nabídce s vyberte **Zobrazit protokoly IntelliTrace**.

    ![Zobrazit možnost nabídky protokolů IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Protokoly IntelliTrace se stáhnou do souboru v adresáři na místním počítači. Pokaždé, když požádáte o protokoly IntelliTrace, vytvoří se nový snímek. Během stahování protokolů Visual Studio zobrazí průběh operace v okně **protokolu aktivit Azure** . Jak je znázorněno na následujícím obrázku, můžete rozbalit položku řádku pro operaci a zobrazit tak další podrobnosti.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Během stahování protokolů IntelliTrace můžete pokračovat v práci v aplikaci Visual Studio. Až se stahování protokolu dokončí, otevře se v aplikaci Visual Studio.

> [!NOTE]
> Protokoly IntelliTrace mohou obsahovat výjimky, které rozhraní generuje a následně zpracuje. Kód interního rozhraní generuje tyto výjimky jako normální součást spuštění role, takže je můžete bezpečně ignorovat.
>
>

## <a name="next-steps"></a>Další kroky
- [Možnosti ladění cloudových služeb Azure](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publikování cloudové služby Azure pomocí sady Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)