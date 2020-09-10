---
title: Zachovat stálou virtuální IP adresu pro cloudovou službu Azure
description: Naučte se, jak zajistit, aby se virtuální IP adresa (VIP) cloudové služby Azure nezměnila.
author: ghogen
manager: jillfra
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: dcc39c4321a6f9a081d2a0479ee60d3e56b8eb04
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2020
ms.locfileid: "89740121"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Zachování konstantní virtuální IP adresy cloudové služby Azure
Když aktualizujete cloudovou službu, která je hostovaná v Azure, možná budete muset zajistit, aby se virtuální IP adresa (VIP) služby nezměnila. Mnoho služeb správy domény používá k registraci názvů domén systém DNS (Domain Name System). Služba DNS funguje jenom v případě, že VIP zůstane stejná. Pomocí **Průvodce publikováním** v nástrojích Azure můžete zajistit, aby se virtuální IP adresa vaší cloudové služby při aktualizaci nezměnila. Další informace o tom, jak používat službu Správa domén DNS pro cloudové služby, najdete v tématu [Konfigurace vlastního názvu domény pro cloudovou službu Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Publikování cloudové služby beze změny její virtuální IP adresy
Virtuální IP adresa cloudové služby se přidělí při prvním nasazení do Azure v konkrétním prostředí, například v produkčním prostředí. VIP se mění jenom v případě, že nasazení odstraníte explicitně nebo se nasazení implicitně odstraní procesem aktualizace nasazení. Chcete-li zachovat virtuální IP adresy, nesmíte odstranit nasazení a je nutné zajistit, aby aplikace Visual Studio automaticky neodstranila nasazení.

Nastavení nasazení můžete zadat v **Průvodci publikováním**, který podporuje několik možností nasazení. Můžete zadat nové nasazení nebo nasazení aktualizace, které může být přírůstkové nebo souběžné. V obou druzích nasazení aktualizace se virtuální IP adresa uchovává. Definice těchto různých typů nasazení najdete v tématu [Průvodce publikováním aplikace Azure](vs-azure-tools-publish-azure-application-wizard.md). Kromě toho můžete řídit, jestli se při výskytu chyby odstraní předchozí nasazení cloudové služby. Pokud tuto možnost nenastavíte správně, může se stát, že se virtuální IP adresa neočekávaně změní.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Aktualizace cloudové služby beze změny její virtuální IP adresy
1. Vytvořte nebo otevřete projekt cloudové služby Azure v aplikaci Visual Studio.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt. V místní nabídce vyberte **publikovat**.

    ![Publikování nabídky](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. V dialogovém okně **publikovat aplikaci Azure** vyberte předplatné Azure, které chcete nasadit. V případě potřeby se přihlaste a vyberte **Další**.

    ![Publikovat přihlašovací stránku aplikace Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Na kartě **běžné nastavení** ověřte správnost názvu cloudové služby, do které nasazujete, **prostředí**, **konfigurace sestavení**a **Konfigurace služby** .

    ![Karta pro publikování Common Settings aplikace Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Na kartě **Upřesnit nastavení** ověřte správnost **popisku nasazení** a **účtu úložiště** . Ověřte, zda není zaškrtnuto políčko **Odstranit nasazení při selhání** , a ověřte, zda je zaškrtnuto políčko **aktualizace nasazení** . Zrušením zaškrtnutí políčka **Odstranit nasazení při selhání** se ujistěte, že se vaše virtuální IP adresa neztratí, pokud během nasazení dojde k chybě. Zaškrtnutím políčka **aktualizace nasazení** zajistěte, aby se nasazení neodstranilo a vaše VIP při opětovném publikování aplikace nebylo ztraceno.

    ![Karta pro publikování rozšířených nastavení aplikace Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Chcete-li dále určit, jak chcete aktualizovat role, vyberte **nastavení vedle možnosti** **aktualizace nasazení**. Vyberte možnost **přírůstková aktualizace** nebo **Souběžná aktualizace**a vyberte **OK**. Zvolením možnosti **přírůstková aktualizace** aktualizujte jednotlivé instance aplikace, jednu po druhé, aby byla aplikace vždy k dispozici. Chcete-li aktualizovat všechny instance aplikace současně, vyberte možnost **Souběžná aktualizace** . Současná aktualizace je rychlejší, ale služba nemusí být během procesu aktualizace dostupná. Po dokončení vyberte **Další**.

    ![Stránka pro publikování nastavení nasazení aplikace Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. V dialogovém okně **publikovat aplikaci Azure** vyberte **Další** , dokud se nezobrazí stránka **Souhrn** . Ověřte nastavení a pak vyberte **publikovat**.

    ![Stránka pro publikování souhrnu aplikací Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Další kroky
- [Použití průvodce publikováním aplikace Azure v sadě Visual Studio](vs-azure-tools-publish-azure-application-wizard.md)
