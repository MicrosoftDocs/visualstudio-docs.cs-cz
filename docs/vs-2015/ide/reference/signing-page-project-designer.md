---
title: Stránka podepisování, Návrhář projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5707ef277892c37cab16f78ac11113194a95e190
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663503"
---
# <a name="signing-page-project-designer"></a>Stránka Podepisování, návrhář projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Použijte stránku **podepisování** **Návrháře projektu** k podepsání manifestů aplikace a nasazení a také k podepsání sestavení (podepisování silného názvu).

 Všimněte si, že podepisování manifestů aplikace a nasazení je proces, který se liší od podepsání sestavení, přestože se obě úlohy provádějí na stránce **podepisování** .

 Kromě toho se úložiště informací o klíčovém souboru liší od podepisování manifestu a podepsání sestavení. V případě podepisování manifestu jsou informace o klíči uloženy v databázi kryptografického úložiště v počítači a v úložišti certifikátů systému Windows aktuálního uživatele. V případě podepisování sestavení jsou informace o klíči uloženy pouze v databázi kryptografického úložiště vašeho počítače.

 Pro přístup na stránku **podepisování** vyberte uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** klikněte na **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **podepisování** .

## <a name="application-and-deployment-manifest-signing"></a>Podepisování manifestu aplikace a nasazení
 Zaškrtnutím políčka **podepsat manifesty ClickOnce** zaškrtněte toto políčko pro podepsání manifestů aplikace a nasazení pomocí páru veřejného a privátního klíče. Další informace o tom, jak to provést, naleznete v tématu [How to: Signing Application and Deployment Manifests](../../ide/how-to-sign-application-and-deployment-manifests.md).

 Tlačítko **vybrat z úložiště** umožňuje vybrat existující certifikát z osobního úložiště certifikátů aktuálního uživatele. Můžete vybrat jeden z těchto certifikátů pro podepsání aplikace a manifestů nasazení.

 Když kliknete na **vybrat ze Storu** , otevře se dialogové okno **Vybrat certifikát** , ve kterém najdete seznam certifikátů v osobním úložišti certifikátů, které jsou aktuálně platné (neprošlé), a které mají privátní klíče. Účel certifikátu, který vyberete, by měl zahrnovat podepisování kódu.

 Pokud kliknete na **Zobrazit vlastnosti certifikátu**, zobrazí se dialogové okno **Podrobnosti o certifikátu** . Toto dialogové okno obsahuje podrobné informace o certifikátu a obsahuje další možnosti. Kliknutím na Další informace **o certifikátech** můžete zobrazit další informace o nápovědě.

 Tlačítko **vybrat ze souboru** umožňuje vybrat certifikát z existujícího souboru klíče.

 Kliknutím na **vybrat ze souboru** se otevře dialogové okno **Vybrat soubor** , ve kterém můžete vybrat soubor klíče certifikátu (. pfx). Soubor musí být chráněný heslem a v osobním úložišti certifikátů ho už nejde najít.

 V dialogovém okně **zadat heslo pro otevření souboru** zadejte heslo pro otevření souboru klíče certifikátu (. pfx). Informace o heslech jsou uložené v osobním seznamu kontejnerů klíčů a v úložišti osobních certifikátů.

 Tlačítko **vytvořit testovací certifikát** umožňuje vytvořit certifikát pro testování. Testovací certifikát se používá k podepsání aplikace ClickOnce a manifestů nasazení.

 Kliknutím na **vytvořit testovací certifikát** otevřete dialogové okno **vytvořit testovací certifikát** , ve kterém můžete zadat heslo pro soubor klíče se silným názvem pro testovací certifikát. Soubor má název *ProjectName*_TemporaryKey. pfx. Pokud kliknete na tlačítko **OK** bez zadání hesla, není soubor. pfx zašifrovaný heslem.

 Pole **Adresa URL serveru časového razítka** Určuje adresu serveru, který obsahuje časovou razítko vašeho podpisu. Když zadáte certifikát, tato externí lokalita ověří čas, kdy byla aplikace podepsána.

## <a name="assembly-signing"></a>Podepisování sestavení
 Zaškrtněte políčko pro **podepsání sestavení** zaškrtněte toto políčko pro podepsání sestavení a vytvoření silně pojmenovaného souboru klíče. Další informace o podepsání sestavení pomocí **Návrháře projektu**naleznete v tématu [How to: Sign a Assembly (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564).

 Tato možnost používá k podepsání sestavení nástroj Al. exe, který poskytuje [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]. Další informace o nástroji Al. exe naleznete v tématu [How to: Sign a Assembly se silným názvem](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 **Zvolte seznam souborů klíčů se silným názvem** , který umožňuje zadat nový nebo existující silně pojmenovaný soubor klíče, který se používá k podepsání sestavení. Vybrat **\<Browse... >** pro výběr existujícího souboru klíče.

 Vybrat **\<New... >** vytvořit nový soubor klíče, který má podepsat sestavení. Zobrazí se dialogové okno **vytvořit klíč se silným názvem** , pomocí kterého můžete zadat název souboru klíče a chránit soubor klíče heslem. Heslo musí mít délku alespoň 6 znaků. Pokud zadáte heslo, vytvoří se soubor Personal Information Exchange (. pfx); Pokud nezadáte heslo, vytvoří se silný soubor s názvem klíče (. snk).

 Tlačítko **změnit heslo** změní heslo pro soubor klíče Personal Information Exchange (. pfx), který se používá k podepsání sestavení.

 Kliknutím na **změnit heslo** se otevře dialogové okno **změnit heslo klíče** . V tomto dialogovém okně je **staré** heslo aktuální heslo pro soubor klíče. **Nové heslo** musí mít délku nejméně 6 znaků. Informace o heslech jsou uložené v úložišti certifikátů Windows aktuálního uživatele.

 Zaškrtávací políčko **pouze Zpožděné podepsání** zaškrtnutím tohoto políčka povolíte zpožděné podepisování.

 Všimněte si, že zpožděný podepsaný projekt nebude spuštěn a nebude možné ho ladit. K přeskočení ověřování během vývoje však můžete použít [Nástroj Sn. exe (nástroj Strong Name)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) s možností `-Vr`.

> [!NOTE]
> Když podepisujete sestavení, možná nebudete mít vždycky přístup k privátnímu klíči. Organizace může mít například úzce chráněný pár klíčů, ke kterému nemají vývojáři přístup denně. Veřejný klíč může být dostupný, ale přístup k privátnímu klíči je omezený na pár jednotlivců. V takovém případě můžete použít *Zpožděné* nebo *částečné podepisování* k poskytnutí veřejného klíče a odložit přidání privátního klíče, dokud nebude sestavení předáno.

## <a name="see-also"></a>Viz také
 [Vlastnosti projektu reference](../../ide/reference/project-properties-reference.md) ke [správě sestavení a podepsání](../../ide/managing-assembly-and-manifest-signing.md) podepisování [silného názvu pro spravované aplikace](https://msdn.microsoft.com/5fef3490-c519-4363-94fd-8b1ad260dab5) [Postupy: podepsání manifestů aplikací a nasazení](../../ide/how-to-sign-application-and-deployment-manifests.md) [Postupy: podepsání sestavení (Visual Studio)](https://msdn.microsoft.com/f468a7d3-234c-4353-924d-8e0ae5896564) [Postupy: podepsání sestavení silným názvem sestavení se](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [silným názvem](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)
