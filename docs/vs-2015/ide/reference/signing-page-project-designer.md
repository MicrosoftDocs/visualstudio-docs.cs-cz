---
title: Stránka podepisování, Návrhář projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4aa8ee86032c4cadf9cbfa59d3db840102be669
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263937"
---
# <a name="signing-page-project-designer"></a>Stránka Podepisování, návrhář projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Použití **podepisování** stránku **Návrháře projektu** k podepsání manifestů aplikace a nasazení a také k podepsání sestavení (podepisování silným názvem).  
  
 Všimněte si, že podepisování manifestů aplikace a nasazení je proces liší od podepsání sestavení, i když obě úlohy se provádějí na **podepisování** stránky.  
  
 Navíc ukládání informací o souboru klíče se liší pro podepsání manifestu a podepsání sestavení. Pro podepsání manifestu, se informace o klíči uložených v databázi kryptografického úložiště počítače a úložiště certifikátů Windows aktuálního uživatele. Pro podepsání sestavení informace o klíči uložený jenom v kryptografických úložiště databáze.  
  
 Pro přístup **podepisování** stránky, vyberte uzel projektu v **Průzkumníku řešení**a pak klikněte na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **Návrháře projektu** se zobrazí, klikněte na tlačítko **podepisování** kartu.  
  
## <a name="application-and-deployment-manifest-signing"></a>Podepisování manifestů aplikace a nasazení  
 **Podepsání manifestů ClickOnce** zaškrtávací políčko  
 Vyberte toto zaškrtávací políčko k podepsání manifestů aplikace a nasazení pomocí dvojice veřejného/soukromého klíče. Další informace o tom, jak to provést, najdete v části [postupy: přihlášení aplikace a manifesty nasazení](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 **Vybrat Store** tlačítko  
 Můžete vybrat existující certifikát z úložiště osobních certifikátů aktuálního uživatele. Můžete vybrat jednu z těchto certifikátů k podepsání manifestů vaší aplikace a nasazení.  
  
 Kliknutím na **vybírat Store** otevře **vyberte certifikát, který** dialogové okno, který zobrazí certifikáty v úložišti osobních certifikátů, které jsou aktuálně platná (prošlou platností) a které mají privátní klíče. Účel certifikátu, který jste vybrali by měl zahrnovat podepisování kódu.  
  
 Vyberete-li **zobrazit vlastnosti certifikátu**, **podrobnosti o certifikátu** zobrazí se dialogové okno. Toto dialogové okno obsahuje podrobné informace o certifikátu a obsahuje další možnosti. Můžete kliknout na **Další informace o certifikátech** chcete zobrazit další informace.  
  
 **Vyberte ze souboru** tlačítko  
 Umožňuje vybrat certifikát z existujícího souboru s klíčem.  
  
 Kliknutím na **vybrat ze souboru** otevře **vybrat soubor** dialogové okno, které vám umožní vybrat soubor klíče (.pfx) certifikátu. Soubor musí být chráněn heslem a již nemůže být umístěn v osobním úložišti certifikátů.  
  
 V **zadejte heslo pro otevření souboru** dialogového okna zadejte heslo pro otevření souboru klíče (.pfx) certifikátu. Informace o hesle uložený v seznamu osobní kontejner klíčů a vašem osobním úložišti certifikátů.  
  
 **Vytvořit testovací certifikát** tlačítko  
 Umožňuje vytvořit certifikát pro účely testování. Testovací certifikát se používá k podepisování manifestů aplikace a nasazení vaší ClickOnce.  
  
 Kliknutím na **vytvořit testovací certifikát** otevře **vytvořit testovací certifikát** dialogové, ve kterém můžete zadat heslo pro soubor klíče se silným názvem pro testovací certifikát. Soubor *projectname*_TemporaryKey.pfx. Vyberete-li **OK** bez zadávání hesla se soubor PFX není zašifrované heslo.  
  
 **Adresa URL serveru časového razítka** pole  
 Určuje adresu serveru tento časová razítka podpisu. Když zadáte certifikát, ověří tato externí web čas, který aplikace byla podepsána.  
  
## <a name="assembly-signing"></a>Podepisování sestavení  
 **Podepsat sestavení** zaškrtávací políčko  
 Vyberte toto zaškrtávací políčko k podepsání sestavení a vytvoření silným názvem souboru klíče. Další informace o podepisování sestavení s použitím **Návrháře projektu**, naleznete v tématu [postupy: podepsání sestavení (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 Tato volba používá nástroj Al.exe poskytované [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] k podepsání sestavení. Další informace o Al.exe najdete v tématu [postupy: podepsání sestavení silným názvem](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 **Vyberte soubor klíče se silným názvem** seznamu  
 Umožňuje zadat nový nebo existující silným názvem soubor s klíčem, který se používá k podepsání sestavení. Vyberte  **\<Procházet... >** a vyberte existující soubor klíče.  
  
 Vyberte  **\<nový … >** vytvořte nový soubor klíče, pomocí kterého se má sestavení podepsat. **Vytvořit klíč se silným názvem** se zobrazí dialogové okno, které můžete použít k zadání názvu souboru klíče a chránit soubor klíče s heslem. Heslo musí být dlouhý aspoň 6 znaků. Pokud určíte heslo, vytvoří se soubor Personal Information Exchange (.pfx); Pokud heslo nezadáte, vytvoří soubor silným názvem klíče (.snk).  
  
 **Změna hesla** tlačítko  
 Změní heslo pro soubor klíče Personal Information Exchange (.pfx), který se používá k podepsání sestavení.  
  
 Kliknutím na **změnit heslo** otevře **změnit heslo klíče** dialogové okno. V tomto dialogovém okně **staré heslo** je aktuální heslo pro soubor klíče. **Nové heslo** musí mít alespoň 6 znaků. Informace o hesle je uložen v úložišti certifikátů Windows aktuálního uživatele.  
  
 **Zpoždění podepsání** zaškrtávací políčko  
 Zaškrtněte toto políčko, pokud chcete povolit podepisování zpoždění.  
  
 Mějte na paměti, že zpoždění podepsané se nespustí a není možné ladit. Můžete však použít [Sn.exe (nástroj Strong Name)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) s `-Vr` možnost pro přeskočení ověření během vývoje.  
  
> [!NOTE]
>  Při podpisu sestavení, nemusí mít vždy přístup k privátnímu klíči. Organizace může například mít úzce strážených pár klíčů, aby vývojáři nemuseli přístup k každý den. Veřejný klíč může být k dispozici, ale přístup k privátnímu klíči omezen na několika jednotlivcům. V takovém případě můžete použít *zpožděné* nebo *částečné podepsání* poskytnout veřejný klíč, přidání soukromého klíče odložit, dokud je předáno sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)   
 [Správa sestavení a podepsání manifestu](../../ide/managing-assembly-and-manifest-signing.md)   
 [Podepisování pro spravované aplikace silným názvem](http://msdn.microsoft.com/en-us/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Postupy: podepsání manifestů aplikace a nasazení](../../ide/how-to-sign-application-and-deployment-manifests.md)   
 [Postupy: podepsání sestavení (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Postupy: podepsání sestavení silným názvem](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)   
 [Sestavení se silným názvem](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)



