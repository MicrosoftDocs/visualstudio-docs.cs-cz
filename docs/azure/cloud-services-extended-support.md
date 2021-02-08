---
title: Použít Cloud Services (Rozšířená podpora) (Preview)
description: Naučte se vytvářet a nasazovat Cloud Services (Rozšířená podpora) pomocí Azure Resource Manager se sadou Visual Studio.
author: ghogen
manager: jmartens
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: 39a76f4c76afb2ed0c738adfc477807eebfdbc61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841130"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio-preview"></a>Vytvoření a nasazení do Cloud Services (Rozšířená podpora) v aplikaci Visual Studio (Preview)

Počínaje [verzí Visual Studio 2019 verze 16,9](https://visualstudio.microsoft.com/vs/preview) (aktuálně ve verzi Preview) můžete pracovat s cloud services pomocí Azure Resource Manager, což výrazně zjednodušuje a modernizes údržbu a správu prostředků Azure. Tato možnost je povolená novou službou Azure, která se označuje jako *Cloud Services (Rozšířená podpora)*. Existující cloudovou službu můžete publikovat na Cloud Services (Rozšířená podpora). Informace o této službě Azure najdete v [dokumentaci Cloud Services (Rozšířená podpora)](/azure/cloud-services-extended-support/overview).

## <a name="publish-to-cloud-services-extended-support"></a>Publikování na Cloud Services (Rozšířená podpora)

Když publikujete stávající projekt cloudové služby Azure do Cloud Services (Rozšířená podpora), pořád si zachováte možnost publikovat do klasické cloudové služby Azure. V aplikaci Visual Studio 2019 verze 16,9 Preview 3 a novější má klasický projekt cloudové služby speciální verzi příkazu **publikovat** , **publikovat (Rozšířená podpora)**. Tento příkaz se zobrazí v místní nabídce v **Průzkumník řešení**.

Když publikujete do Cloud Services (Rozšířená podpora), dojde k nějakým rozdílům. Nebudete například dotazováni, pokud publikujete do **přípravy** nebo **výroby**, protože tyto sloty nasazení nejsou součástí modelu publikování rozšířené podpory. Místo toho můžete pomocí Cloud Services (rozšířenou podporu) nastavit více nasazení a prohodit nasazení v Azure Portal. I když nástroje sady Visual Studio umožňují tuto funkci nastavit v 16,9 Preview 3, funkce swap nebude povolena až do pozdější verze Cloud Services (Rozšířená podpora) a může způsobit selhání při nasazení během období Preview.

Před publikováním klasické cloudové služby Azure do Cloud Services (Rozšířená podpora) Zkontrolujte účty úložiště, které váš projekt používá, a ujistěte se, že jsou účty úložiště v1 nebo úložiště v2. Klasické typy účtů úložiště selžou s chybovou zprávou v době nasazení. Nezapomeňte zkontrolovat účet úložiště používaný diagnostikou. Informace o kontrole účtu úložiště diagnostiky najdete v tématu [nastavení diagnostiky pro Azure Cloud Services a virtuální počítače](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Pokud vaše služba používá klasický účet úložiště, můžete ji upgradovat. viz [upgrade na účet úložiště pro obecné účely v2](/azure/storage/common/storage-account-upgrade?tabs=azure-portal).  Obecné informace o typech účtů úložiště najdete v tématu [Přehled účtu úložiště](/azure/storage/common/storage-account-overview).

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Publikování klasického projektu cloudové služby Azure pro Cloud Services (Rozšířená podpora)

1. Cloud Services (Rozšířená podpora) je aktuálně ve verzi Preview. Zaregistrujte funkci pro vaše předplatné následujícím způsobem:

   ```azurepowershell-interactive
   Register-AzProviderFeature -FeatureName CloudServices -ProviderNamespace Microsoft.Compute
   ```

1. Klikněte pravým tlačítkem myši na uzel projektu v projektu cloudové služby Azure (Classic) a vyberte **publikovat (Rozšířená podpora)...** Na první obrazovce se otevře **Průvodce publikováním** .

   ![V nabídce vyberte publikovat (Rozšířená podpora).](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   Zobrazí se průvodce **publikováním** .

   ![Přihlašovací stránka](./media/cloud-services-extended-support/publish-step1.png)

1. **Účet** – vyberte účet nebo v rozevíracím seznamu účet vyberte **Přidat účet** .

1. **Vyberte své předplatné** – vyberte předplatné, které chcete použít pro vaše nasazení.

1. Kliknutím na tlačítko **Další** přejděte na stránku **Nastavení** .

   ![Společná nastavení](./media/cloud-services-extended-support/publish-settings.png)

1. **Cloudová služba (Rozšířená podpora)** – pomocí rozevíracího seznamu vyberte existující cloudovou službu (rozšířenou podporu) nebo vyberte **vytvořit novou** a vytvořte ji. Datové centrum se zobrazí v závorkách pro každou cloudovou službu (Rozšířená podpora). Doporučuje se, aby umístění datového centra pro cloudovou službu (rozšířené podpoře) bylo stejné jako umístění datového centra pro účet úložiště.

   Pokud se rozhodnete vytvořit novou službu, zobrazí se dialogové okno **vytvořit cloudovou službu (Rozšířená podpora)** . Zadejte umístění a skupinu prostředků, které chcete použít pro cloudovou službu (Rozšířená podpora).

   ![Vytvoření cloudové služby (Rozšířená podpora)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Konfigurace sestavení** – vyberte buď **ladění** , nebo **vydání**.

1. **Konfigurace služby** – vyberte buď **Cloud** , nebo **místní**.

1. **Účet úložiště** – vyberte účet úložiště, který se má použít pro toto nasazení, nebo **vytvořte nový** pro vytvoření účtu úložiště. Oblast se zobrazí v závorkách pro každý účet úložiště. Doporučuje se, aby bylo umístění datového centra pro účet úložiště stejné jako umístění datového centra pro cloudovou službu (společné nastavení).

   Účet úložiště Azure ukládá balíček pro nasazení aplikace.

1. **Trezor klíčů** – zadejte Trezor klíčů, který obsahuje tajné klíče pro tuto cloudovou službu (Rozšířená podpora). Tato možnost je povolená, pokud je povolená Vzdálená plocha, nebo pokud se do konfigurace přidávají certifikáty.

1. **Povolit vzdálenou plochu pro všechny role** – tuto možnost vyberte, pokud chcete být schopni se vzdáleně připojit ke službě. Zobrazí se výzva k zadání přihlašovacích údajů.

   ![Nastavení vzdálené plochy](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. Kliknutím na tlačítko **Další** přejdete na stránku **nastavení diagnostiky** .

   ![Nastavení diagnostiky](./media/cloud-services-extended-support/diagnostics-settings.png)

   Diagnostika umožňuje řešit potíže s cloudovou službou Azure (Rozšířená podpora). Informace o diagnostice najdete v tématu [Konfigurace diagnostiky pro Azure Cloud Services a Virtual Machines](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Informace o Application Insights najdete v tématu [co je Application Insights?](/azure/application-insights/app-insights-overview).

1. Kliknutím na tlačítko **Další** přejděte na stránku **Souhrn** .

   ![Souhrn](./media/cloud-services-extended-support/publish-summary.png)

1. **Cílový profil** – můžete zvolit vytvoření profilu publikování z nastavení, které jste si zvolili. Můžete například vytvořit jeden profil pro testovací prostředí a jiný pro produkční prostředí. Chcete-li uložit tento profil, klikněte na ikonu **Uložit** . Průvodce vytvoří profil a uloží jej do projektu aplikace Visual Studio. Chcete-li změnit název profilu, otevřete seznam **cílový profil** a pak zvolte možnost **Spravovat...**.

   > [!Note]
   > Profil publikování se zobrazí v Průzkumník řešení v aplikaci Visual Studio a nastavení profilu se zapisuje do souboru s příponou *. azurePubxml* . Nastavení jsou uložena jako atributy značek XML.

1. Jakmile nakonfigurujete všechna nastavení pro nasazení projektu, v dolní části dialogového okna vyberte **publikovat** . Stav procesu můžete sledovat v okně výstup **protokolu aktivit Azure** v aplikaci Visual Studio. Klikněte na odkaz **otevřít v portálu** na 

Gratulujeme! Publikovali jste projekt cloudové služby (Rozšířená podpora) do Azure. Chcete-li znovu publikovat se stejným nastavením, můžete znovu použít profil publikování, nebo opakováním těchto kroků vytvořit nové. Šablona Azure Resource Manager (ARM) a parametry, které se používají pro nasazení, se ukládají do složky *bin/ \<configuration\> /Publish* .

## <a name="clean-up-azure-resources"></a>Vyčištění prostředků Azure

Pokud chcete vyčistit prostředky Azure, které jste vytvořili pomocí tohoto kurzu, klikněte na [Azure Portal](https://portal.azure.com), vyberte **skupiny prostředků**, najděte a otevřete skupinu prostředků, kterou jste použili k vytvoření cloudové služby (Rozšířená podpora), a vyberte **Odstranit skupinu prostředků**.

## <a name="next-steps"></a>Další kroky

Pomocí tlačítka **Konfigurovat** na obrazovce **publikování** nastavte průběžnou integraci (CI). Další informace najdete v [dokumentaci Azure Pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).
