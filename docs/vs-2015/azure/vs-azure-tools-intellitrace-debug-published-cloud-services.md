---
title: Ladění publikované cloudové služby Azure pomocí sady Visual Studio a IntelliTrace | Microsoft Docs
description: Zjistěte, jak ladění cloudové služby pomocí IntelliTrace a sady Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 5e6662fc-b917-43ea-bf2b-4f2fc3d213dc
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 03/21/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 00e13c6f217c54b99dfe103b86f1e775e36fd62a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74293539"
---
# <a name="debugging-a-published-azure-cloud-service-with-visual-studio-and-intellitrace"></a>Ladění publikované cloudové služby Azure pomocí sady Visual Studio a nástroje IntelliTrace
Pomocí nástroje IntelliTrace můžete protokolovat podrobné ladicí informace pro instanci role při spuštění v Azure. Pokud je potřeba najít příčinu problému, můžete protokoly IntelliTrace ke krokování kódu ze sady Visual Studio, jako kdyby byly spuštěné v Azure. Nástroj IntelliTrace zaznamenává v důsledku toho klíčů provádění kódu a dat prostředí, když vaše aplikace Azure běží jako cloudová služba v Azure a umožňuje přehrát zaznamenaná data ze sady Visual Studio. 

Můžete použít nástroj IntelliTrace, pokud máte nainstalované Visual Studio Enterprise a vaše aplikace Azure cílí rozhraní .NET Framework 4 nebo novější. Nástroj IntelliTrace shromažďuje informace o Azure role. Virtuální počítače pro tyto role ke spuštění vždy 64bitové operační systémy.

Alternativně můžete [vzdálené ladění](https://go.microsoft.com/fwlink/p/?LinkId=623041) použít k přímému připojení ke cloudové službě běžící v Azure.

> [!IMPORTANT]
> Nástroj IntelliTrace je určená pro účely ladění pouze a neměl by se používat pro produkční nasazení.
> 

## <a name="configure-an-azure-application-for-intellitrace"></a>Konfigurace aplikace Azure pro technologii IntelliTrace
K povolení technologie IntelliTrace pro aplikaci Azure, musíte vytvořit a publikovat aplikace z projektu sady Visual Studio v Azure. Před publikováním na Azure, je nutné nakonfigurovat nástroj IntelliTrace pro vaše aplikace Azure. Pokud publikujete aplikaci bez nástroje IntelliTrace, budete muset znovu publikujte projekt. Další informace najdete v tématu [publikování projektů cloudových služeb Azure pomocí sady Visual Studio](https://go.microsoft.com/fwlink/p/?LinkId=623012).

1. Až budete připraveni k nasazení aplikace Azure, ověřte, že cíle sestavení projektu jsou nastavené na **ladění**.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a v místní nabídce vyberte **publikovat**.
   
1. V dialogovém okně **publikovat aplikaci Azure** vyberte předplatné Azure a **pak vyberte další**.

1. Na stránce **Nastavení** vyberte kartu **Rozšířená nastavení** .

1. Zapněte možnost **Povolit IntelliTrace** pro shromažďování protokolů IntelliTrace pro vaši aplikaci, když je publikovaná v cloudu.
   
1. Pokud chcete přizpůsobit základní konfiguraci IntelliTrace, vyberte **Nastavení** vedle možnosti **Povolit IntelliTrace**.

    ![Odkaz nastavení IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/intellitrace-settings-link.png)
   
1. V dialogovém okně **Nastavení IntelliTrace** můžete určit, které události se mají protokolovat, jestli se mají shromažďovat informace o voláních, které moduly a procesy mají shromažďovat protokoly, a kolik místa k záznamu se má přidělit. Další informace o IntelliTrace naleznete v tématu [ladění pomocí IntelliTrace](https://go.microsoft.com/fwlink/?LinkId=214468).
   
    ![Nastavení technologie IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC519063.png)

Protokol nástroje IntelliTrace je cyklická soubor protokolu o maximální velikosti zadaného v nastavení nástroje IntelliTrace (výchozí velikost je 250 MB). Do souboru v systému souborů virtuálního počítače jsou shromážděné protokoly IntelliTrace. Pokud si vyžádáte protokoly, snímku je přijata od tohoto okamžiku v čase a stáhnou do místního počítače.

Po publikování cloudové služby Azure do Azure můžete zjistit, jestli je IntelliTrace povolený z uzlu Azure v **Průzkumník serveru**, jak je znázorněno na následujícím obrázku:

![Průzkumník serveru – IntelliTrace povoleno](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC744134.png)

## <a name="download-intellitrace-logs-for-a-role-instance"></a>Stáhnout protokoly IntelliTrace pro instanci role
Pomocí sady Visual Studio, si můžete stáhnout protokoly IntelliTrace pro instanci role pomocí následujících kroků:

1. V **Průzkumník serveru**rozbalte uzel **Cloud Services** a najděte instanci role, jejíž protokoly chcete stáhnout. 

1. Klikněte pravým tlačítkem myši na instanci role a v kontextové nabídce s vyberte **Zobrazit protokoly IntelliTrace**. 

    ![Zobrazit možnost nabídky protokoly IntelliTrace](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/view-intellitrace-logs.png)

1. Protokoly IntelliTrace se stáhnou do souboru v adresáři v místním počítači. Protokoluje pokaždé, když, abyste si vyžádali nástroje IntelliTrace, je vytvořen nový snímek. Během stahování protokolů Visual Studio zobrazí průběh operace v okně **protokolu aktivit Azure** . Jak je znázorněno na následujícím obrázku, můžete rozbalit položku řádku pro operace, která se zobrazí podrobnější údaje.

![VST_IntelliTraceDownloadProgress](./media/vs-azure-tools-intellitrace-debug-published-cloud-services/IC745551.png)

Můžete pokračovat v práci v sadě Visual Studio při stahování protokolu IntelliTrace. Po dokončení stahování protokolu se otevře v sadě Visual Studio.

> [!NOTE]
> Protokoly nástroje IntelliTrace může obsahovat výjimky, které rozhraní framework generuje a zpracovává později. Interní rámec kód generuje tyto výjimky v rámci normálního spouštění role, takže může bezpečně ignorovat.
> 
> 

## <a name="next-steps"></a>Další kroky
- [Možnosti ladění cloudových služeb Azure](vs-azure-tools-debugging-cloud-services-overview.md)
- [Publikování cloudové služby Azure pomocí sady Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)