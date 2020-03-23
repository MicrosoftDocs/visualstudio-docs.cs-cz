---
title: Publikování cloudové služby pomocí nástrojů Azure | Dokumenty společnosti Microsoft
description: Přečtěte si, jak publikovat projekty cloudových služeb Azure pomocí Visual Studia.
author: ghogen
manager: jillfra
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: d8257e0833da470554ce331c30cd0edf74122093
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301739"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Publikování cloudové služby pomocí sady Visual Studio

Visual Studio můžete publikovat aplikaci přímo do Azure, s podporou pro pracovní a produkční prostředí cloudové služby. Při publikování vyberete prostředí nasazení a účet úložiště, který se dočasně používá pro balíček nasazení.

Když vyvíjíte a testujete aplikaci Azure, můžete pomocí nasazení webu publikovat změny postupně pro vaše webové role. Po publikování aplikace do prostředí nasazení, nasazení webu umožňuje nasadit změny přímo do virtuálního počítače, ve který běží webová role. Není nutné balit a publikovat celou aplikaci Azure pokaždé, když chcete aktualizovat svou webovou roli vyzkoušet změny. S tímto přístupem můžete mít změny webové role k dispozici v cloudu pro testování bez čekání na publikování vaší aplikace do prostředí nasazení.

Pomocí následujících postupů publikujte svou aplikaci Azure a aktualizujte webovou roli pomocí nasazení webu:

- Publikování nebo balíček aplikace Azure z Visual Studia
- Aktualizace webové role v rámci vývojového a testovacího cyklu

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Publikování nebo balíček aplikace Azure z Visual Studia

Když publikujete aplikaci Azure, můžete provést jeden z následujících úkolů:

- Vytvoření balíčku služeb: Tento balíček a konfigurační soubor služby můžete použít k publikování aplikace do prostředí nasazení z [portálu Azure](https://portal.azure.com).

- Publikování projektu Azure z Visual Studia: Chcete-li publikovat aplikaci přímo do Azure, použijte Průvodce publikováním. Další informace naleznete [v tématu Publish Azure Application Wizard](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Vytvoření balíčku služeb z aplikace Visual Studio

1. Až budete připraveni publikovat aplikaci, otevřete Průzkumníka řešení, otevřete místní nabídku pro projekt Azure, který obsahuje vaše role, a zvolte Publikovat.

1. Chcete-li vytvořit pouze balíček služeb, postupujte takto:

   a. V místní nabídce pro projekt Azure zvolte **Balíček**.

   b. V dialogovém okně **Balíček aplikace Azure** zvolte konfiguraci služby, pro kterou chcete vytvořit balíček, a pak zvolte konfiguraci sestavení.

   c. (Nepovinné) Pokud chcete po publikování zapnout vzdálenou plochu pro cloudovou službu, vyberte **Povolit vzdálenou plochu pro všechny role**a pak vyberte **Nastavení** pro konfiguraci přihlašovacích údajů ke vzdálené ploše. Další informace najdete [v tématu Povolení připojení ke vzdálené ploše pro roli v Cloudových službách Azure pomocí sady Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Pokud chcete ladit cloudovou službu po publikování, zapněte vzdálené ladění výběrem **možnosti Povolit vzdálený debugger pro všechny role**.

   d. Chcete-li vytvořit balíček, zvolte odkaz **Balíček.**

      Průzkumník souborů zobrazuje umístění souboru nově vytvořeného balíčku. Toto umístění můžete zkopírovat, abyste ho mohli použít z webu Azure Portal.

   e. Chcete-li publikovat tento balíček do prostředí nasazení, musíte použít toto umístění jako umístění balíček při vytváření cloudové služby a nasazení tohoto balíčku do prostředí s portálem Azure.

1. (Nepovinné) Chcete-li proces nasazení zrušit, zvolte v místní nabídce řádkové položky v protokolu aktivit **možnost Storno a odebrat**. Tento příkaz zastaví proces nasazení a odstraní prostředí nasazení z Azure. Pokud chcete po nasazení odebrat prostředí, použijte portál Azure.

1. (Nepovinné) Po spuštění instancí rolí Visual Studio automaticky zobrazí prostředí nasazení v uzlu **Cloudservices** v Průzkumníkovi serveru. Zde můžete zobrazit stav jednotlivých instancí rolí. Viz [Správa prostředků Azure pomocí Cloud Exploreru](vs-azure-tools-resources-managing-with-cloud-explorer.md). Následující obrázek znázorňuje instance rolí, když jsou stále ve stavu Inicializace:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Aktualizace webové role v rámci vývojového a testovacího cyklu

Pokud je back-endová infrastruktura vaší aplikace stabilní, ale webové role potřebují častější aktualizace, můžete pomocí nasazení webu aktualizovat jenom webovou roli v projektu. Nasazení webu je užitečné, pokud nechcete znovu sestavit a znovu nasadit role back-endového pracovního procesu, nebo pokud máte více webových rolí a chcete aktualizovat pouze jednu z webových rolí.

### <a name="requirements-for-using-web-deploy"></a>Požadavky na použití nasazení webu

- **Pouze pro účely vývoje a testování**: Změny jsou provedeny přímo do virtuálního počítače, kde je spuštěna webová role. Pokud tento virtuální počítač má být recyklovány, změny jsou ztraceny, protože původní balíček, který jste publikovali se používá k opětovnému vytvoření virtuálního počítače pro roli. Znovu publikujte aplikaci, abyste získali nejnovější změny pro webovou roli.

- **Aktualizovat lze pouze webové role**: Role pracovního procesu nelze aktualizovat. Kromě toho nelze aktualizovat `RoleEntryPoint` v `web role.cs`.

- **Může podporovat pouze jednu instanci webové role**: Ve vašem prostředí nasazení nelze mít více instancí libovolné webové role. Je však podporováno více webových rolí, z nichž každá má pouze jednu instanci.

- **Povolit připojení ke vzdálené ploše**: Tento požadavek umožňuje nasazení webu používat uživatele a heslo k připojení k virtuálnímu počítači k nasazení změn na server se spuštěnou Internetovou informační službou (IIS). Kromě toho může být nutné připojit k virtuálnímu počítači přidat důvěryhodný certifikát do služby IIS v tomto virtuálním počítači. (Tento certifikát zajišťuje, že vzdálené připojení služby IIS používané nasazením webu je zabezpečené.)

Následující postup předpokládá, že používáte Průvodce **publikováním aplikace Azure.**

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Povolení nasazení webu při publikování aplikace

1. Chcete-li povolit možnost **Povolit nasazení webu pro všechny webové role,** musíte nejprve nakonfigurovat připojení ke vzdálené ploše. Vyberte **Povolit vzdálenou plochu** pro všechny role a pak zadejte pověření, která se používají ke vzdálenému připojení v poli **Konfigurace vzdálené plochy,** které se zobrazí. Viz [Povolení připojení ke vzdálené ploše pro roli v CloudOvých službách Azure pomocí Sady Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Pokud chcete povolit nasazení webu pro všechny webové role v aplikaci, vyberte **Povolit nasazení webu pro všechny webové role**.

    Zobrazí se žlutý výstražný trojúhelník. Nasazení webu používá ve výchozím nastavení nedůvěryhodný certifikát podepsaný svým držitelem, který se nedoporučuje pro odesílání citlivých dat. Pokud potřebujete zabezpečit tento proces pro citlivá data, můžete přidat certifikát SSL, který se použije pro připojení nasazení webu. Tento certifikát musí být důvěryhodný certifikát. Další informace naleznete v [tématu Zabezpečení nasazení webu](#make-web-deploy-secure).

1. Zvolte **Další,** chcete-li zobrazit obrazovku **Souhrn,** a pak zvolte **Publikovat,** chcete-li nasadit cloudovou službu.

    Cloudová služba je publikována. Vytvořený virtuální počítač má pro službu IIS povolena vzdálená připojení, takže nasazení webu lze použít k aktualizaci webových rolí bez jejich opětovného publikování.

   > [!NOTE]
   > Pokud máte více než jednu instanci nakonfigurovanou pro webovou roli, zobrazí se varovná zpráva, která uvádí, že každá webová role je omezena na jednu instanci pouze v balíčku, který je vytvořen pro publikování vaší aplikace. Pokračujte výběrem tlačítka **OK**. Jak je uvedeno v části Požadavky, můžete mít více než jednu webovou roli, ale pouze jednu instanci každé role.

### <a name="update-your-web-role-by-using-web-deploy"></a>Aktualizace webové role pomocí nasazení webu

1. Chcete-li použít nasazení webu, proveďte změny kódu projektu pro všechny webové role v sadě Visual Studio, kterou chcete publikovat, a potom klepněte pravým tlačítkem myši na tento uzel projektu ve vašem řešení a přejděte na **Publish**. Zobrazí se dialogové okno **Publikovat web.**

1. (Nepovinné) Pokud jste přidali důvěryhodný certifikát SSL, který chcete použít pro vzdálená připojení pro službu IIS, můžete zrušit zaškrtnutí políčka **Povolit nedůvěryhodný certifikát.** Informace o tom, jak přidat certifikát, aby bylo nasazení webu zabezpečené, naleznete v části **Zabezpečení nasazení webu** dále v tomto článku.

1. Chcete-li použít nasazení na webu, mechanismus publikování potřebuje uživatelské jméno a heslo, které jste nastavili pro připojení ke vzdálené ploše při prvním publikování balíčku.

   a. Do **pole Uživatelské jméno**zadejte uživatelské jméno.

   b. Do **pole Heslo**zadejte heslo.

   c. (Nepovinné) Pokud chcete toto heslo uložit do tohoto profilu, zvolte **Uložit heslo**.

1. Chcete-li publikovat změny webové role, zvolte **Publikovat**.

    Na stavovém řádku se zobrazí **spuštění publikování**. Po dokončení publikování se zobrazí **úspěšné publikování.** Změny byly nyní nasazeny do webové role ve vašem virtuálním počítači. Teď můžete spustit aplikaci Azure v prostředí Azure a otestovat změny.

### <a name="make-web-deploy-secure"></a>Zabezpečte nasazení webu

1. Nasazení webu používá ve výchozím nastavení nedůvěryhodný certifikát podepsaný svým držitelem, který se nedoporučuje pro odesílání citlivých dat. Pokud potřebujete zabezpečit tento proces pro citlivá data, můžete přidat certifikát SSL, který se použije pro připojení nasazení webu. Tento certifikát musí být důvěryhodný certifikát, který získáte od certifikační autority (CA).

    Chcete-li, aby bylo nasazení webu zabezpečené pro každý virtuální počítač pro každou z vašich webových rolí, musíte na web nahrát důvěryhodný certifikát, který chcete použít pro nasazení webu. Tento certifikát zajišťuje, že certifikát je přidán do virtuálního počítače, který je vytvořen pro webovou roli při publikování aplikace.

1. Chcete-li do služby IIS přidat důvěryhodný certifikát SSL pro vzdálená připojení, postupujte takto:

   a. Chcete-li se připojit k virtuálnímu počítači, ve který běží webová role, vyberte instanci webové role v **Průzkumníku cloudu** nebo **Průzkumníku serveru**a pak zvolte příkaz **Připojit pomocí vzdálené plochy.** Podrobné kroky týkající se připojení k virtuálnímu počítači najdete v [tématu Povolení připojení ke vzdálené ploše pro roli v Cloudových službách Azure pomocí sady Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Prohlížeč vás vyzve ke `.rdp` stažení souboru.

   b. Chcete-li přidat certifikát SSL, otevřete službu správy ve Správci služby IIS. Ve Správci služby IIS povolte protokol SSL otevřením odkazu **Vazby** v podokně **akcí.** Zobrazí se dialogové okno **Přidat vazbu sítě.** Zvolte **Přidat**a pak v rozevíracím seznamu **Typ** zvolte HTTPS. V seznamu **certifikátů SSL** zvolte certifikát SSL, který jste podepsali certifikační autoritou a který jste nahráli na portál Azure. Další informace naleznete v [tématu Konfigurace nastavení připojení pro službu Správa .](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10))

      > [!NOTE]
      > Pokud přidáte důvěryhodný certifikát SSL, žlutý výstražný trojúhelník se již nezobrazí v **Průvodci publikováním**.

## <a name="include-files-in-the-service-package"></a>Zahrnout soubory do balíčku služeb

Možná budete muset zahrnout konkrétní soubory do balíčku služeb tak, aby byly k dispozici na virtuálním počítači, který je vytvořen pro roli. Můžete například přidat `.exe` soubor nebo `.msi` soubor, který používá spouštěcí skript do balíčku služby. Nebo budete muset přidat sestavení, které vyžaduje webová role nebo projekt role pracovníka. Chcete-li zahrnout soubory, musí být přidány do řešení pro vaši aplikaci Azure.

1. Chcete-li přidat sestavení do balíčku služeb, postupujte takto:

   a. V **Průzkumníku řešení**otevřete uzel projektu pro projekt, který chybí odkazované sestavení.
   b. Chcete-li přidat sestavení do projektu, otevřete místní nabídku pro složku **Odkazy** a pak zvolte **Přidat odkaz**. Zobrazí se dialogové okno Přidat odkaz.
   c. Zvolte odkaz, který chcete přidat, a pak zvolte **OK**. Odkaz je přidán do seznamu ve složce **References.**
   d. Otevřete místní nabídku pro sestavení, které jste přidali, a zvolte **Vlastnosti**. Zobrazí se okno **Vlastnosti.**

      Chcete-li toto sestavení zahrnout do balíčku služeb, v **seznamu Kopírovat místní** zvolte **True**.
1. V **Průzkumníku řešení** otevřete uzel projektu pro projekt, který chybí odkazované sestavení.

1. Chcete-li přidat sestavení do projektu, otevřete místní nabídku pro složku **Odkazy** a pak zvolte **Přidat odkaz**. Zobrazí se dialogové okno **Přidat odkaz.**

1. Zvolte odkaz, který chcete přidat, a pak zvolte tlačítko **OK.**

    Odkaz je přidán do seznamu ve složce **References.**

1. Otevřete místní nabídku pro sestavení, které jste přidali, a zvolte **Vlastnosti**. Zobrazí se okno Vlastnosti.

1. Chcete-li toto sestavení zahrnout do balíčku služeb, zvolte v seznamu **Kopírovat místní** možnost **True**.

1. Chcete-li zahrnout soubory do balíčku služeb, které byly přidány do projektu webových rolí, otevřete místní nabídku souboru a zvolte **Vlastnosti**. V okně **Vlastnosti** zvolte **Obsah** ze seznamu **Akce sestavení.**

1. Chcete-li zahrnout soubory do balíčku služeb, které byly přidány do projektu role pracovníka, otevřete místní nabídku souboru a zvolte **Vlastnosti**. V okně **Vlastnosti** zvolte **Kopírovat, pokud je novější** ze seznamu **Kopírovat do výstupního adresáře.**

## <a name="next-steps"></a>Další kroky

Další informace o publikování do Azure z Visual Studia najdete [v tématu Publish Azure Application Wizard](vs-azure-tools-publish-azure-application-wizard.md).
