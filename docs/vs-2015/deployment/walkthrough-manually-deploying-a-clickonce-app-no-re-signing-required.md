---
title: 'Návod: Ruční nasazení aplikace ClickOnce, která nevyžaduje opětovné podepsání a které zachovává údaje o poskytovateli | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2d6531a94a99e2a1c24d80e9f326d23fcc6c4ec3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252990"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Návod: Ruční nasazení aplikace ClickOnce, jež nevyžaduje opětovné podepsání a které zachovává údaje o poskytovateli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když vytvoříte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace a pak mu přidělte zákazníkovi k publikování a nasazení, zákazník tradičně museli aktualizovat manifest nasazení a znovu podepsat. Který je stále upřednostňuje ve většině případů, rozhraní .NET Framework 3.5 vám umožní vytvořit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení, která je možné nasadit pomocí zákazníky bez nutnosti znovu vygenerovat nový manifest nasazení. Další informace najdete v tématu [nasazení ClickOnce aplikace pro testování a produkční servery bez Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Když vytvoříte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace a pak mu přidělte zákazníkovi k publikování a nasazení, aplikace můžete použít značky zákazníka nebo můžete zachovat brandingu. Pokud aplikace je jednou vlastní aplikací, můžete chtít zachovat brandingu. Pokud aplikace je velmi upravili pro každého zákazníka, můžete chtít použít značky zákazníka. Rozhraní .NET Framework 3.5 umožňuje zachovat branding, informace o vydavateli a podpis zabezpečení při nasazení aplikace organizace. Další informace najdete v tématu [vytváření aplikací ClickOnce k jiné nasazení](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  V tomto návodu vytvoříte nasazení ručně pomocí nástroje příkazového řádku Mage.exe nebo grafického nástroje MageUI.exe. Další informace o ruční nasazení najdete v tématu [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Požadavky  
 K provedení kroků v tomto návodu budete potřebovat následující:  
  
-   Aplikace Windows Forms, který jste připraveni k nasazení. Tato aplikace bude uvedené jako WindowsFormsApp1.  
  
-   Visual Studio nebo Windows SDK.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>K nasazení aplikace ClickOnce s více nasazení a přizpůsobení prostředí značce podporu pomocí Mage.exe  
  
1.  Otevřete příkazový řádek sady Visual Studio nebo [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] příkazový řádek a přejděte do adresáře, ve kterém budete ukládat vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] soubory.  
  
2.  Vytvořte adresář po aktuální verzi vašeho nasazení. Pokud je to poprvé, že nasazujete aplikaci, bude pravděpodobně zvolíte **1.0.0.0**.  
  
    > [!NOTE]
    >  Verze vašeho nasazení může být liší od verze souborů aplikace.  
  
3.  Vytvořte podadresář s názvem **bin** a zkopírujte všechny soubory aplikací, včetně spustitelných souborů, sestavení, prostředky a datové soubory.  
  
4.  Generovat manifest aplikace pomocí volání Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Podepsat manifest aplikace pomocí digitálního certifikátu.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Generovat manifest nasazení pomocí volání Mage.exe. Ve výchozím nastavení, Mage.exe označí vaši [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení jako nainstalovaná aplikace, takže ji můžete spustit online a offline. Aby byla aplikace k dispozici pouze v případě, že uživatel je online, použijte `-i` argument s hodnotou `f`. Protože tato aplikace bude využívat funkci nasazení na více, vyloučit `-providerUrl` argument Mage.exe. (Ve verzích rozhraní .NET Framework verze 3.5, s výjimkou `-providerUrl` pro offline aplikace bude mít za následek chybu.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Uživatel manifest nasazení.  
  
8.  Zadejte všechny soubory s konkrétním zákazníkem, který se nasadit aplikaci ve své síti.  
  
9. V tomto okamžiku zákazník musí podepsat manifest nasazení pomocí vlastní certifikát vygenerovaný sám sebou. Například pokud zákazník pracuje pro společnost s názvem společnosti Adventure Works, může generovat certifikát podepsaný svým držitelem pomocí nástroje MakeCert.exe. Pak pomocí nástroje Pvk2pfx.exe soubory vytvořené MakeCert.exe do souboru PFX, který může být předán Mage.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Zákazník dále používá tento certifikát k podepsání manifestu nasazení.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Zákazník nasazuje aplikace pro své uživatele.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>K nasazení aplikace ClickOnce s více nasazení a přizpůsobení prostředí značce podporu pomocí MageUI.exe  
  
1.  Otevřete příkazový řádek sady Visual Studio nebo [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] příkazový řádek a přejděte do adresáře, ve kterém budete ukládat vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] soubory.  
  
2.  Vytvořte podadresář s názvem **bin** a zkopírujte všechny soubory aplikací, včetně spustitelných souborů, sestavení, prostředky a datové soubory.  
  
3.  Vytvořte podadresář s názvem aktuální verzi vašeho nasazení. Pokud je to poprvé, že nasazujete aplikaci, bude pravděpodobně zvolíte **1.0.0.0**.  
  
    > [!NOTE]
    >  Verze vašeho nasazení může být liší od verze souborů aplikace.  
  
4.  Přesunout \\ **bin** adresář do adresáře, který jste vytvořili v kroku 2.  
  
5.  Spuštění grafického nástroje MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Vytvořit nový manifest aplikace tak, že vyberete **souboru**, **nový**, **Manifest aplikace** z nabídky.  
  
7.  Ve výchozím **název** kartu, zadejte název a verzi číslo tohoto nasazení. Navíc zadat hodnotu **vydavatele**, který se použije jako název složky pro propojení místní aplikace v nabídce Start při nasazení.  
  
8.  Vyberte **možnosti aplikace** kartě a klikněte na tlačítko **použít Manifest aplikace pro informace o vztahu důvěryhodnosti**. Tato možnost vám umožní třetích stran branding pro to [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace.  
  
9. Vyberte **soubory** kartě a klikněte na tlačítko **Procházet** tlačítko vedle textového pole adresáře aplikace.  
  
10. Vyberte adresář, který obsahuje soubory aplikací, které jste vytvořili v kroku 2 a klikněte na tlačítko **OK** na dialogové okno pro výběr složky.  
  
11. Klikněte na tlačítko **naplnit** a přidejte všechny soubory aplikace do seznamu. Pokud vaše aplikace obsahuje více než jeden spustitelný soubor, označte hlavní spustitelný soubor pro toto nasazení jako při spuštění aplikace tak, že vyberete **vstupní bod** z **typ souboru** rozevíracího seznamu. (Pokud vaše aplikace obsahuje jenom jeden spustitelný soubor, MageUI.exe označíte ho za vás.)  
  
12. Vyberte **oprávněních** kartě a vyberte úroveň vztahu důvěryhodnosti, je nutné aplikaci k vyhodnocení. Výchozí hodnota je **plné důvěryhodnosti**, která budou vhodná pro většinu aplikací.  
  
13. Vyberte **souboru**, **Uložit** z nabídky a uložit manifest aplikace. Jste vyzváni k podepsání manifestu aplikace, když jste jej uložili.  
  
14. Pokud máte certifikát uložený jako soubor ve vašem systému souborů, použijte **znaménko jako soubor certifikátu** možnost a vyberte certifikát ze systému souborů pomocí na tři tečky (**...** ) tlačítko.  
  
     -nebo-  
  
     Pokud váš certifikát se ukládají v úložišti certifikátů, který je přístupný z počítače, vyberte **přihlášení pomocí uloženého certifikátu možnost**a vyberte certifikát ze seznamu k dispozici.  
  
15. Vyberte **souboru**, **nový**, **Manifest nasazení** z nabídky pro vytvoření manifestu nasazení a potom na **název** kartu, zadejte název a číslo verze (**1.0.0.0** v tomto příkladu).  
  
16. Přepněte **aktualizovat** kartu a určete, jak často chcete tuto aplikaci aktualizovat. Pokud vaše aplikace používá [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] rozhraní API nasazení kontrolu aktualizací, zrušte zaškrtnutí políčka popisek **tato aplikace by měla vyhledávat aktualizace**.  
  
17. Přepněte **odkaz na aplikaci** kartu. Všechny hodnoty na této kartě předběžnému naplnění kliknutím **manifestu vyberte** tlačítko a vyberete manifest aplikace jste vytvořili v předchozích krocích.  
  
18. Zvolte **Uložit** a uložit manifest nasazení na disk. Jste vyzváni k podepsání manifestu aplikace, když jste jej uložili. Klikněte na tlačítko **zrušit** uložit manifest bez podepsání.  
  
19. Zadejte všechny soubory, aplikace k zákazníkovi.  
  
20. V tomto okamžiku zákazník musí podepsat manifest nasazení pomocí vlastní certifikát vygenerovaný sám sebou. Například pokud zákazník pracuje pro společnost s názvem společnosti Adventure Works, může generovat certifikát podepsaný svým držitelem pomocí nástroje MakeCert.exe. Pak pomocí nástroje Pvk2pfx.exe soubory vytvořené MakeCert.exe do souboru PFX, který může být předán MageUI.exe.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. S certifikátem vygenerovaným zákazník nyní podepíše manifest nasazení tak, že v MageUI.exe otevřou manifest nasazení a pak ji uložit. Pokud se zobrazí dialogové okno podepisování, zákazník vybere **znaménko jako soubor certifikátu** možnost a vybere soubor PFX uložil na disku.  
  
22. Zákazník nasazuje aplikace pro své uživatele.  
  
## <a name="next-steps"></a>Další kroky  
  
## <a name="see-also"></a>Viz také  
 [Mage.exe (generování manifestu a nástroj pro úpravy)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [MakeCert.exe (nástroj pro vytvoření certifikátu)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)



