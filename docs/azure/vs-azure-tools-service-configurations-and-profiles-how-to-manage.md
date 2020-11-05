---
title: Správa konfigurací a profilů služby | Microsoft Docs
description: Naučte se pracovat s konfiguračními soubory profilů a konfigurací služby | nastavení úložišť pro prostředí pro nasazení a nastavení publikování pro cloudové služby.
author: ghogen
manager: jillfra
assetId: 7da8c551-fb06-4057-b5c7-c77f4b39d803
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/11/2017
ms.author: ghogen
ms.openlocfilehash: 42c4668b2bf9925fe92db51b6a4275c535960a61
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398875"
---
# <a name="how-to-manage-service-configurations-and-profiles"></a>Postup správy konfigurací a profilů služby
## <a name="overview"></a>Přehled
Když publikujete cloudovou službu, Visual Studio ukládá informace o konfiguraci do dvou typů konfiguračních souborů: konfigurace a profily služby. Konfigurace služby (soubory. cscfg): nastavení ukládání pro prostředí nasazení pro cloudovou službu Azure. Azure tyto konfigurační soubory používá při správě cloudových služeb. Na druhé straně profily (soubory. azurePubxml) ukládají nastavení publikování pro cloudové služby. Tato nastavení jsou záznamem o tom, co zvolíte při použití Průvodce publikováním a které jsou používány místně v aplikaci Visual Studio. Toto téma vysvětluje, jak pracovat s oběma typy konfiguračních souborů.

## <a name="service-configurations"></a>Konfigurace služby
Můžete vytvořit více konfigurací služby pro použití pro každé prostředí nasazení. Můžete například vytvořit konfiguraci služby pro místní prostředí, které používáte ke spouštění a testování aplikace Azure a další konfiguraci služby pro produkční prostředí.

Podle vašich požadavků můžete tyto konfigurace služby přidat, odstranit, přejmenovat a změnit. Tyto konfigurace služby můžete spravovat ze sady Visual Studio, jak je znázorněno na následujícím obrázku.

![Správa konfigurací služby](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-service-config.png)

Můžete také otevřít dialogové okno **Správa konfigurací** ze stránek vlastností role. Chcete-li otevřít vlastnosti pro roli v projektu Azure, otevřete místní nabídku pro danou roli a pak zvolte možnost **vlastnosti**. Na kartě **Nastavení** rozbalte seznam **Konfigurace služby** a pak výběrem **možnosti spravovat** otevřete dialogové okno **Správa konfigurací** .

### <a name="to-add-a-service-configuration"></a>Přidání konfigurace služby
1. V Průzkumník řešení otevřete místní nabídku pro projekt Azure a pak vyberte **spravovat konfigurace**.

    Zobrazí se dialogové okno **Správa konfigurací služby** .
2. Chcete-li přidat konfiguraci služby, je nutné vytvořit kopii existující konfigurace. Provedete to tak, že v seznamu název zvolíte konfiguraci, kterou chcete zkopírovat, a pak vyberete **vytvořit kopii**.
3. Volitelné Pokud chcete pro konfiguraci služby zadat jiný název, zvolte novou konfiguraci služby ze seznamu název a pak vyberte **Přejmenovat**. Do textového pole **název** zadejte název, který chcete použít pro tuto konfiguraci služby, a pak vyberte **OK**.

    Nový konfigurační soubor služby s názvem ServiceConfiguration. [Nový název]. cscfg se přidá do projektu Azure v Průzkumník řešení.

### <a name="to-delete-a-service-configuration"></a>Odstranění konfigurace služby
1. V Průzkumník řešení otevřete místní nabídku pro projekt Azure a pak vyberte **spravovat konfigurace**.

    Zobrazí se dialogové okno **Správa konfigurací služby** .
2. Pokud chcete odstranit konfiguraci služby, zvolte v seznamu **název** konfiguraci, kterou chcete odstranit, a pak vyberte **Odebrat**. Zobrazí se dialogové okno pro ověření, zda chcete odstranit tuto konfiguraci.
3. Vyberte **Odstranit**.

     Konfigurační soubor služby se odebere z projektu Azure v Průzkumník řešení.

### <a name="to-rename-a-service-configuration"></a>Přejmenování konfigurace služby
1. V Průzkumník řešení otevřete místní nabídku pro projekt Azure a pak vyberte **spravovat konfigurace**.

    Zobrazí se dialogové okno **Správa konfigurací služby** .
2. Pokud chcete přejmenovat konfiguraci služby, zvolte novou konfiguraci služby ze seznamu **název** a pak vyberte **Přejmenovat**. Do textového pole **název** zadejte název, který chcete použít pro tuto konfiguraci služby, a pak vyberte **OK**.

    Název konfiguračního souboru služby se v projektu Azure v Průzkumník řešení změnil.

### <a name="to-change-a-service-configuration"></a>Změna konfigurace služby
* Pokud chcete změnit konfiguraci služby, otevřete místní nabídku pro konkrétní roli, kterou chcete změnit v projektu Azure, a pak vyberte **vlastnosti**. Další informace najdete v tématu [How to: Configure a role pro cloudovou službu Azure pomocí sady Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md) .

## <a name="make-different-setting-combinations-by-using-profiles"></a>Vytváření různých kombinací nastavení pomocí profilů
Pomocí profilu můžete automaticky vyplnit **Průvodce publikováním** s různými kombinacemi nastavení pro různé účely. Můžete mít například jeden profil pro ladění a další pro sestavení vydaných verzí. V takovém případě váš **ladicí** profil by měl povolený **IntelliTrace** a vybraná konfigurace **ladění** a váš profil **verze** by **IntelliTrace** byl zakázán a byla vybrána konfigurace **vydané verze** . K nasazení služby pomocí jiného účtu úložiště můžete použít také jiné profily.

Při prvním spuštění Průvodce se vytvoří výchozí profil. Visual Studio uloží profil do souboru, který má příponu. azurePubXml, která se přidá do vašeho projektu Azure ve složce **Profiles** . Pokud ručně zadáte různé volby při spuštění Průvodce později, soubor se automaticky aktualizuje. Než spustíte následující postup, měli byste už mít cloudovou službu aspoň jednou.

### <a name="to-add-a-profile"></a>Přidání profilu
1. Otevřete místní nabídku pro projekt Azure a pak vyberte **publikovat**.
2. Vedle seznamu **cílový profil** vyberte tlačítko **Uložit profil** , jak je znázorněno na následujícím obrázku. Tím se vytvoří profil.

    ![Vytvořit nový profil](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/create-new-profile.png)
3. Po vytvoření profilu vyberte **<spravovat... >** v seznamu **cílový profil** .

    Zobrazí se dialogové okno **Spravovat profily** , jak ukazuje následující obrázek.

    ![Dialogové okno Správa profilů](./media/vs-azure-tools-service-configurations-and-profiles-how-to-manage/manage-profiles.png)
4. V seznamu **název** vyberte profil a pak vyberte **vytvořit kopii**.
5. Klikněte na tlačítko **Zavřít** .

    Nový profil se zobrazí v seznamu cílový profil.
6. V seznamu **cílový profil** vyberte profil, který jste právě vytvořili. Nastavení Průvodce publikováním se vyplní možnostmi z profilu, který jste vybrali.
7. Výběrem tlačítek **předchozí** a **Další** Zobrazte jednotlivé stránky průvodce publikováním a potom Přizpůsobte nastavení pro tento profil. Informace najdete v tématu [Průvodce publikováním aplikace Azure](vs-azure-tools-publish-azure-application-wizard.md) .
8. Po dokončení přizpůsobení nastavení vyberte **Další** a vraťte se na stránku nastavení. Profil se uloží při publikování služby pomocí těchto nastavení nebo v případě, že vyberete možnost **Uložit** vedle seznamu profilů.

### <a name="to-rename-or-delete-a-profile"></a>Přejmenování nebo odstranění profilu
1. Otevřete místní nabídku pro projekt Azure a pak vyberte **publikovat**.
2. V seznamu **cílový profil** vyberte **Spravovat**.
3. V dialogovém okně **Spravovat profily** vyberte profil, který chcete odstranit, a pak vyberte **Odebrat**.
4. V potvrzovacím dialogovém okně, které se zobrazí, vyberte **OK**.
5. Vyberte **Zavřít**.

### <a name="to-change-a-profile"></a>Změna profilu
1. Otevřete místní nabídku pro projekt Azure a pak vyberte **publikovat**.
2. V seznamu **cílový profil** vyberte profil, který chcete změnit.
3. Výběrem tlačítek **předchozí** a **Další** Zobrazte jednotlivé stránky průvodce publikováním a pak změňte požadovaná nastavení. Informace najdete v tématu [Průvodce publikováním aplikace Azure](vs-azure-tools-publish-azure-application-wizard.md) .
4. Po dokončení změny nastavení vyberte **Další** a vraťte se na stránku **Nastavení** .
5. (Volitelné) vyberte **publikovat** a publikujte cloudovou službu pomocí nového nastavení. Pokud nechcete momentálně publikovat cloudovou službu a zavřete Průvodce publikováním, zobrazí se v aplikaci Visual Studio, jestli chcete změny profilu Uložit.

## <a name="next-steps"></a>Další kroky
Další informace o konfiguraci dalších částí projektu Azure ze sady Visual Studio najdete v tématu [konfigurace projektu Azure](vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address.md).
