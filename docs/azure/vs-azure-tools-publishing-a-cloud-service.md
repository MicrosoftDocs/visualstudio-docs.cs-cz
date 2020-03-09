---
title: Publikování cloudové služby pomocí nástrojů Azure | Microsoft Docs
description: Přečtěte si, jak publikovat projekty cloudových služeb Azure pomocí sady Visual Studio.
author: ghogen
manager: jillfra
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: d8257e0833da470554ce331c30cd0edf74122093
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408681"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Publikování cloudové služby pomocí sady Visual Studio

Visual Studio může publikovat aplikaci přímo do Azure s podporou pro pracovní i produkční prostředí cloudové služby. Při publikování můžete vybrat prostředí nasazení a účet úložiště, který se pro balíček pro nasazení dočasně používá.

Při vývoji a testování aplikace Azure můžete pomocí Nasazení webu publikovat změny přírůstkově pro webové role. Po publikování aplikace do prostředí nasazení vám Nasazení webu umožní nasadit změny přímo do virtuálního počítače, na kterém je spuštěná webová role. Pokaždé, když chcete aktualizovat webovou roli a otestovat změny, nemusíte zabalit a publikovat celou aplikaci Azure. S tímto přístupem můžete mít změny vaší webové role dostupné v cloudu pro účely testování, aniž byste čekali na jejich publikování do prostředí nasazení.

K publikování aplikace Azure a aktualizaci webové role pomocí Nasazení webu použijte následující postupy:

- Publikování nebo zabalení aplikace Azure ze sady Visual Studio
- Aktualizace webové role v rámci cyklu vývoje a testování

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Publikování nebo zabalení aplikace Azure ze sady Visual Studio

Při publikování aplikace Azure můžete provést jednu z následujících úloh:

- Vytvoření balíčku služby: pomocí tohoto balíčku a konfiguračního souboru služby můžete aplikaci publikovat do prostředí nasazení z [Azure Portal](https://portal.azure.com).

- Publikování projektu Azure ze sady Visual Studio: Pokud chcete publikovat aplikaci přímo do Azure, použijte Průvodce publikováním. Informace najdete v tématu [Průvodce publikováním aplikace Azure](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Vytvoření balíčku služby ze sady Visual Studio

1. Až budete připraveni k publikování aplikace, otevřete Průzkumník řešení, otevřete místní nabídku pro projekt Azure, který obsahuje vaše role, a klikněte na publikovat.

1. Chcete-li vytvořit pouze balíček služby, postupujte podle těchto kroků:

   a. V místní nabídce projektu Azure vyberte možnost **balíček**.

   b. V dialogovém okně **balíček aplikace Azure** zvolte konfiguraci služby, pro kterou chcete vytvořit balíček, a pak zvolte konfiguraci sestavení.

   c. Volitelné Pokud chcete zapnout službu Vzdálená plocha pro cloudovou službu po jejím publikování, vyberte **Povolit vzdálenou plochu pro všechny role**a pak vyberte **Nastavení** a nakonfigurujte přihlašovací údaje vzdálené plochy. Další informace najdete v tématu [povolení připojení ke vzdálené ploše pro roli v Azure Cloud Services pomocí sady Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Pokud chcete po publikování cloudové služby ladit, zapněte vzdálené ladění tak, že vyberete **Povolit vzdálený ladicí program pro všechny role**.

   d. Chcete-li vytvořit balíček, klikněte na odkaz **balíček** .

      Průzkumník souborů zobrazuje umístění souboru nově vytvořeného balíčku. Toto umístění můžete zkopírovat, abyste ho mohli použít Azure Portal.

   e. Chcete-li tento balíček publikovat do prostředí nasazení, je nutné použít toto umístění jako umístění balíčku při vytváření cloudové služby a nasazení tohoto balíčku do prostředí s Azure Portal.

1. Volitelné Proces nasazení zrušíte tak, že v místní nabídce pro položku řádku v protokolu aktivit kliknete na **zrušit a odebrat**. Tento příkaz celý proces nasazení zastaví a odstraní prostředí nasazení z Azure. Pokud chcete prostředí po nasazení odebrat, použijte Azure Portal.

1. Volitelné Po spuštění instancí rolí Visual Studio automaticky zobrazí prostředí nasazení v uzlu **Cloud Services** v Průzkumník serveru. Tady můžete zobrazit stav jednotlivých instancí rolí. Viz [Správa prostředků Azure pomocí Průzkumníka cloudu](vs-azure-tools-resources-managing-with-cloud-explorer.md). Následující ilustrace znázorňuje instance rolí, když jsou stále ve stavu inicializace:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Aktualizace webové role v rámci cyklu vývoje a testování

Pokud je infrastruktura back-end vaší aplikace stabilní, ale webové role potřebují častější aktualizace, můžete použít Nasazení webu k aktualizaci pouze webové role v projektu. Nasazení webu je užitečné, pokud nechcete znovu sestavovat a znovu nasazovat role pracovních procesů back-endu, nebo pokud máte více webových rolí a chcete aktualizovat jenom jednu z webových rolí.

### <a name="requirements-for-using-web-deploy"></a>Požadavky na použití Nasazení webu

- **Pouze pro účely vývoje a testování**: změny jsou provedeny přímo na virtuálním počítači, kde je webová role spuštěna. Pokud je nutné tento virtuální počítač recyklovat, změny se ztratí, protože původní balíček, který jste publikovali, slouží k opětovnému vytvoření virtuálního počítače pro danou roli. Znovu publikujte aplikaci, abyste získali nejnovější změny webové role.

- **Aktualizovat lze pouze webové role**: role pracovního procesu nelze aktualizovat. Kromě toho nelze aktualizovat `RoleEntryPoint` v `web role.cs`.

- **Může podporovat jenom jednu instanci webové role**: v prostředí nasazení nemůžete mít více instancí žádné webové role. Podporuje se ale víc webových rolí s jenom jednou instancí.

- **Povolit připojení ke vzdálené ploše**: Tento požadavek umožňuje nasazení webu použít uživatele a heslo pro připojení k virtuálnímu počítači, aby se nasadily změny na server, na kterém běží Internetová informační služba (IIS). Kromě toho může být nutné připojit se k virtuálnímu počítači a Přidat důvěryhodný certifikát do služby IIS na tomto virtuálním počítači. (Tento certifikát zajišťuje zabezpečení vzdáleného připojení pro službu IIS používaného Nasazení webu.)

Následující postup předpokládá, že používáte Průvodce **publikováním aplikace Azure** .

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Povolit Nasazení webu při publikování aplikace

1. Pokud chcete povolit možnost **povolit nasazení webu pro všechny webové role** , musíte nejdřív nakonfigurovat připojení ke vzdálené ploše. Vyberte **Povolit vzdálenou plochu** pro všechny role a potom zadejte přihlašovací údaje, které se používají pro vzdálené připojení, v zobrazeném poli **Konfigurace vzdálené plochy** . Další informace najdete v tématu [povolení připojení ke vzdálené ploše pro roli v Azure Cloud Services pomocí sady Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Chcete-li povolit Nasazení webu pro všechny webové role v aplikaci, vyberte možnost **povolit nasazení webu pro všechny webové role**.

    Zobrazí se žlutý výstražný trojúhelník. Ve výchozím nastavení používá Nasazení webu nedůvěryhodný certifikát podepsaný svým držitelem, který se nedoporučuje pro nahrávání citlivých dat. Pokud potřebujete zabezpečit tento proces pro citlivá data, můžete přidat certifikát SSL, který se bude používat pro Nasazení webu připojení. Tento certifikát musí být důvěryhodný certifikát. Další informace najdete v tématu [nastavení zabezpečení webu v zabezpečeném nasazení](#make-web-deploy-secure).

1. Kliknutím na tlačítko **Další** zobrazíte obrazovku **souhrnu** a potom kliknutím na tlačítko **publikovat** nasaďte cloudovou službu.

    Cloudová služba je publikovaná. Virtuální počítač, který je vytvořen, má vzdálená připojení povolená pro službu IIS, aby se Nasazení webu mohl použít k aktualizaci webových rolí bez nutnosti jejich opětovného publikování.

   > [!NOTE]
   > Pokud máte pro webovou roli nakonfigurovanou víc než jednu instanci, zobrazí se varovná zpráva s oznámením, že každá webová role je omezená na jednu instanci jenom v balíčku, který se vytvořil pro publikování vaší aplikace. Pokračujte výběrem tlačítka **OK**. Jak je uvedeno v části požadavky, můžete mít více než jednu webovou roli, ale pouze jednu instanci každé role.

### <a name="update-your-web-role-by-using-web-deploy"></a>Aktualizace webové role pomocí Nasazení webu

1. Chcete-li použít Nasazení webu, proveďte v projektu změny kódu pro jakékoli webové role v aplikaci Visual Studio, které chcete publikovat, a poté klikněte pravým tlačítkem myši na tento uzel projektu v řešení a přejděte na příkaz **publikovat**. Zobrazí se dialogové okno **Publikovat web** .

1. Volitelné Pokud jste přidali důvěryhodný certifikát SSL pro použití pro vzdálená připojení služby IIS, můžete zrušit zaškrtnutí políčka **povolí nedůvěryhodný certifikát** . Informace o tom, jak přidat certifikát pro zajištění Nasazení webu zabezpečení, najdete v části **nasazení webu zabezpečení** dále v tomto článku.

1. Pokud chcete použít Nasazení webu, mechanismus publikování potřebuje uživatelské jméno a heslo, které jste nastavili pro připojení ke vzdálené ploše při prvním publikování balíčku.

   a. Do pole **uživatelské jméno**zadejte uživatelské jméno.

   b. Do pole **heslo**zadejte heslo.

   c. Volitelné Pokud chcete toto heslo uložit v tomto profilu, vyberte **Uložit heslo**.

1. Chcete-li publikovat změny webové role, klikněte na tlačítko **publikovat**.

    Stavový řádek zobrazuje **začátek publikování**. Po dokončení publikování se zobrazí zpráva **publikování se úspěšně** dokončilo. Změny byly nyní nasazeny do webové role na vašem virtuálním počítači. Nyní můžete spustit aplikaci Azure v prostředí Azure a otestovat provedené změny.

### <a name="make-web-deploy-secure"></a>Zabezpečení nasazení webu

1. Ve výchozím nastavení používá Nasazení webu nedůvěryhodný certifikát podepsaný svým držitelem, který se nedoporučuje pro nahrávání citlivých dat. Pokud potřebujete zabezpečit tento proces pro citlivá data, můžete přidat certifikát SSL, který se bude používat pro Nasazení webu připojení. Tento certifikát musí být důvěryhodný certifikát, který obdržíte od certifikační autority (CA).

    Chcete-li zajistit Nasazení webu zabezpečení pro každý virtuální počítač pro každou webovou roli, je nutné odeslat důvěryhodný certifikát, který chcete použít pro nasazení webu, do Azure Portal. Tento certifikát zajistí, že se certifikát přidá do virtuálního počítače, který se vytvoří pro webovou roli při publikování aplikace.

1. Pokud chcete do služby IIS přidat důvěryhodný certifikát SSL pro použití pro vzdálená připojení, postupujte podle těchto kroků:

   a. Pokud se chcete připojit k virtuálnímu počítači, na kterém běží webová role, vyberte instanci webové role v **Průzkumníku cloudu** nebo **Průzkumník serveru**a pak zvolte příkaz **připojit pomocí vzdálené plochy** . Podrobné pokyny, jak se připojit k virtuálnímu počítači, najdete v tématu [povolení připojení ke vzdálené ploše pro roli v Azure Cloud Services pomocí sady Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). V prohlížeči se zobrazí výzva ke stažení souboru `.rdp`.

   b. Chcete-li přidat certifikát protokolu SSL, otevřete službu správy ve Správci služby IIS. V nástroji Správce služby IIS povolte SSL otevřením odkazu **vazby** v podokně **Akce** . Zobrazí se dialogové okno **Přidat vazbu webu** . Zvolte **Přidat**a pak v rozevíracím seznamu **typ** zvolte https. V seznamu **certifikát SSL** vyberte certifikát SSL, který jste podepsali certifikační autoritou a který jste nahráli do Azure Portal. Další informace najdete v tématu [Konfigurace nastavení připojení pro službu správy](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)).

      > [!NOTE]
      > Pokud přidáte důvěryhodný certifikát SSL, žlutý výstražný trojúhelník se už nebude zobrazovat v **Průvodci publikováním**.

## <a name="include-files-in-the-service-package"></a>Zahrnout soubory do balíčku služby

Je možné, že budete muset zahrnout konkrétní soubory do balíčku služby, aby byly k dispozici na virtuálním počítači, který je vytvořen pro roli. Například můžete chtít přidat `.exe` nebo `.msi` soubor, který je používán spouštěcím skriptem pro balíček služby. Nebo může být nutné přidat sestavení, které vyžaduje webová role nebo projekt role pracovního procesu. Chcete-li zahrnout soubory, musí být přidány do řešení pro vaši aplikaci Azure.

1. Chcete-li přidat sestavení do balíčku služby, použijte následující postup:

   a. V **Průzkumník řešení**otevřete uzel projektu pro projekt, ve kterém chybí odkazované sestavení.
   b. Chcete-li přidat sestavení do projektu, otevřete místní nabídku složky **odkazy** a pak zvolte možnost **Přidat odkaz**. Zobrazí se dialogové okno Přidat odkaz.
   c. Zvolte odkaz, který chcete přidat, a klikněte na **tlačítko OK**. Odkaz se přidá do seznamu ve složce **odkazy** .
   d. Otevřete místní nabídku pro sestavení, které jste přidali, a vyberte možnost **vlastnosti**. Zobrazí se okno **vlastnosti** .

      Chcete-li zahrnout toto sestavení do balíčku služby, klikněte v **seznamu Kopírovat místní** na **hodnotu true**.
1. V **Průzkumník řešení** otevřete uzel projektu pro projekt, ve kterém chybí odkazované sestavení.

1. Chcete-li přidat sestavení do projektu, otevřete místní nabídku složky **odkazy** a pak zvolte možnost **Přidat odkaz**. Zobrazí se dialogové okno **Přidat odkaz** .

1. Zvolte odkaz, který chcete přidat, a poté klikněte na tlačítko **OK** .

    Odkaz se přidá do seznamu ve složce **odkazy** .

1. Otevřete místní nabídku pro sestavení, které jste přidali, a vyberte možnost **vlastnosti**. Zobrazí se okno Vlastnosti.

1. Chcete-li zahrnout toto sestavení do balíčku služby, klikněte v seznamu **Kopírovat místní** na **hodnotu true**.

1. Chcete-li zahrnout soubory do balíčku služby, které byly přidány do projektu webové role, otevřete místní nabídku souboru a pak zvolte možnost **vlastnosti**. V okně **vlastnosti** vyberte možnost **obsah** v seznamu **Akce sestavení** .

1. Chcete-li zahrnout soubory do balíčku služby, které byly přidány do projektu role pracovního procesu, otevřete místní nabídku souboru a pak zvolte možnost **vlastnosti**. V okně **vlastnosti** vyberte v seznamu **Kopírovat do výstupního adresáře** možnost **Kopírovat, pokud je novější** .

## <a name="next-steps"></a>Další kroky

Další informace o publikování do Azure ze sady Visual Studio najdete v tématu [Průvodce publikováním aplikací Azure](vs-azure-tools-publish-azure-application-wizard.md).
