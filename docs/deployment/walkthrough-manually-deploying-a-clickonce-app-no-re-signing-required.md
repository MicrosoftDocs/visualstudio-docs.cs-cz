---
title: Ruční nasazení aplikace ClickOnce & zachování brandingu
description: Naučte se vytvářet aplikace ClickOnce, které budou zákazníci nasazovat, aniž byste vygenerovali nový manifest nasazení a mohli používat značky zákazníka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29bdd080e87e8fad44c7b8943d0d017749b8c30b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350306"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Návod: Ruční nasazení aplikace ClickOnce, která nevyžaduje Opětovné podepsání a které zachovává informace o značkách
Když vytvoříte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci a potom ji přidáte zákazníkovi k publikování a nasazení, zákazník tradičně musel aktualizovat manifest nasazení a znovu ho podepsat. I když je ve většině případů stále upřednostňovanou metodou, .NET Framework 3,5 vám umožní vytvářet [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení, která můžou zákazníci nasadit, aniž by museli znovu vygenerovat nový manifest nasazení. Další informace najdete v tématu [nasazení aplikací ClickOnce pro testovací a produkční servery bez opětovného podepsání](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Když vytvoříte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci a potom ji přidáte zákazníkovi k publikování a nasazení, může aplikace použít značku zákazníka nebo může zachovat vaše branding. Pokud je aplikace například jedna proprietární aplikace, může být vhodné zachovat branding. Pokud je aplikace vysoce přizpůsobená pro každého zákazníka, možná budete chtít použít značku zákazníka. .NET Framework 3,5 vám umožní zachovat značky, informace o vydavateli a bezpečnostní podpis, když aplikaci přidělíte do organizace k nasazení. Další informace najdete v tématu [vytváření aplikací ClickOnce pro ostatní k nasazení](../deployment/creating-clickonce-applications-for-others-to-deploy.md).

> [!NOTE]
> V tomto návodu vytvoříte nasazení ručně pomocí nástroje příkazového řádku *Mage.exe* nebo grafického nástroje *MageUI.exe*. Další informace o ručních nasazeních naleznete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Požadavky
 K provedení kroků v tomto návodu potřebujete následující:

- Model Windows Forms aplikace, kterou jste připraveni nasadit. Tato aplikace bude označována jako *WindowsFormsApp1*.

- Visual Studio nebo Windows SDK.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Nasazení aplikace ClickOnce s podporou více nasazení a brandingu pomocí Mage.exe

1. Otevřete příkazový řádek sady Visual Studio nebo příkazový [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] řádek a přejděte do adresáře, do kterého budete ukládat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory.

2. Vytvořte adresář s názvem po aktuální verzi nasazení. Pokud se jedná o první nasazení aplikace, budete pravděpodobně chtít vybrat **1.0.0.0**.

   > [!NOTE]
   > Verze vašeho nasazení může být odlišná od verze vašich souborů aplikace.

3. Vytvořte podadresář s názvem **bin** a zkopírujte sem všechny soubory aplikace, včetně spustitelných souborů, sestavení, prostředků a datových souborů.

4. Vygenerujte manifest aplikace s voláním Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Podepište manifest aplikace pomocí digitálního certifikátu.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Vygenerujte manifest nasazení s voláním *Mage.exe*. Ve výchozím nastavení *Mage.exe* označí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení jako nainstalovanou aplikaci, aby mohla běžet online i offline. Chcete-li aplikaci zpřístupnit pouze v případě, že je uživatel online, použijte `-i` argument s hodnotou `f` . Vzhledem k tomu, že tato aplikace bude využívat funkci vícenásobného nasazení, vylučte `-providerUrl` argument pro *Mage.exe*. (Ve verzích .NET Framework starších než verze 3,5, kromě `-providerUrl` offline aplikace, bude výsledkem chyba.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Nepodepisujte manifest nasazení.

8. Poskytněte všem souborům zákazníka, který nasadí aplikaci v síti.

9. V tomto okamžiku musí zákazník podepsat manifest nasazení pomocí vlastního certifikátu vygenerovaného svým držitelem. Pokud zákazník například funguje pro společnost s názvem Adventure Works, může vygenerovat certifikát podepsaný svým držitelem pomocí nástroje pro *MakeCert.exe* . Dále pomocí nástroje *Pvk2pfx.exe* kombinovat soubory vytvořené *MakeCert.exe* do souboru PFX, který lze předat *Mage.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. Zákazník dále používá tento certifikát k podepsání manifestu nasazení.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. Zákazník nasadí aplikaci pro své uživatele.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Nasazení aplikace ClickOnce s podporou více nasazení a brandingu pomocí MageUI.exe

1. Otevřete příkazový řádek sady Visual Studio nebo příkazový [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] řádek a přejděte do adresáře, do kterého budete ukládat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] soubory.

2. Vytvořte podadresář s názvem **bin** a zkopírujte sem všechny soubory aplikace, včetně spustitelných souborů, sestavení, prostředků a datových souborů.

3. Vytvořte podadresář s názvem po aktuální verzi nasazení. Pokud se jedná o první nasazení aplikace, budete pravděpodobně chtít vybrat **1.0.0.0**.

   > [!NOTE]
   > Verze vašeho nasazení může být odlišná od verze vašich souborů aplikace.

4. Přesuňte adresář \\ **bin** do adresáře, který jste vytvořili v kroku 2.

5. Spusťte grafický nástroj *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Vytvořte nový manifest aplikace výběrem položky **soubor** , **Nový** a **manifest aplikace** z nabídky.

7. Na kartě výchozí **název** zadejte název a číslo verze tohoto nasazení. Také zadejte hodnotu pro **vydavatele** , která bude použita jako název složky pro odkaz na zástupce aplikace v nabídce Start při nasazení.

8. Vyberte kartu **Možnosti aplikace** a klikněte na **použít manifest aplikace pro informace o důvěryhodnosti**. Tím se povolí branding pro tuto aplikaci třetí strany [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

9. Vyberte kartu **soubory** a klikněte na tlačítko **Procházet** vedle textového pole **adresář aplikace** .

10. Vyberte adresář, který obsahuje soubory aplikace, které jste vytvořili v kroku 2, a klikněte na tlačítko **OK** v dialogovém okně Výběr složky.

11. Kliknutím na tlačítko **naplnit** přidáte všechny soubory aplikace do seznamu souborů. Pokud vaše aplikace obsahuje více než jeden spustitelný soubor, označte hlavní spustitelný soubor pro toto nasazení jako spouštěcí aplikaci tak, že vyberete **vstupní bod** v rozevíracím seznamu **typ souboru** . (Pokud vaše aplikace obsahuje jenom jeden spustitelný soubor, *MageUI.exe* bude označovat za vás.)

12. Vyberte kartu **požadovaná oprávnění** a vyberte úroveň důvěryhodnosti, kterou budete potřebovat k vyhodnocení vaší aplikace. Výchozí hodnota je **plná důvěryhodnost** , která bude vhodná pro většinu aplikací.

13. V nabídce vyberte **soubor** , **Uložit** a uložte manifest aplikace. Při ukládání se zobrazí výzva k podepsání manifestu aplikace.

14. Pokud máte certifikát uložený jako soubor v systému souborů, použijte možnost **podepsat soubor certifikátu** a vyberte certifikát ze systému souborů pomocí tlačítka se třemi tečkami ( **...** ).

     -nebo-

     Pokud je certifikát uložený v úložišti certifikátů, ke kterému se dá dostat z počítače, vyberte **možnost podepsat s uloženým certifikátem** a vyberte certifikát ze zadaného seznamu.

15. V nabídce vyberte **soubor** , **Nový** , **manifest nasazení** a pak na kartě **název** zadejte název a číslo verze ( **1.0.0.0** v tomto příkladu).

16. Přepněte na kartu **aktualizace** a určete, jak často chcete, aby se tato aplikace aktualizovala. Pokud vaše aplikace používá [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rozhraní API pro nasazení pro kontrolu samotných aktualizací, zrušte zaškrtnutí políčka s označením, že **by tato aplikace měla vyhledat aktualizace**.

17. Přepněte na kartu **odkaz na aplikaci** . Všechny hodnoty na této kartě můžete předem naplnit kliknutím na tlačítko **Vybrat manifest** a výběrem manifestu aplikace, který jste vytvořili v předchozích krocích.

18. Klikněte na **Uložit** a uložte manifest nasazení na disk. Při ukládání se zobrazí výzva k podepsání manifestu aplikace. Kliknutím na tlačítko **Storno** uložte manifest bez jeho podpisu.

19. Zadejte všechny soubory aplikace pro zákazníka.

20. V tomto okamžiku musí zákazník podepsat manifest nasazení pomocí vlastního certifikátu vygenerovaného svým držitelem. Pokud zákazník například funguje pro společnost s názvem Adventure Works, může vygenerovat certifikát podepsaný svým držitelem pomocí nástroje pro *MakeCert.exe* . Dále pomocí nástroje *Pvk2pfx.exe* kombinovat soubory vytvořené *MakeCert.exe* do souboru PFX, který lze předat *MageUI.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Pomocí vygenerovaného certifikátu teď zákazník podepíše manifest nasazení otevřením manifestu nasazení v *MageUI.exe* a pak ho uloží. Když se zobrazí dialogové okno podepisování, zákazník vybere možnost **podepsat jako soubor certifikátu** a vybere soubor PFX, který byl uložen na disku.

22. Zákazník nasadí aplikaci pro své uživatele.

## <a name="see-also"></a>Viz také
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)
