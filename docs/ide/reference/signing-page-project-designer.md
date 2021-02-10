---
title: Stránka Podepisování, návrhář projektu (C#)
description: Použijte stránku podepisování Návrháře projektu k podepsání manifestů aplikace a nasazení a také k podepsání sestavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52d02407316fbc8f9a7b5e3db1c02a3566cda87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957579"
---
# <a name="signing-page-project-designer"></a>Stránka Podepisování, návrhář projektu (C#)

Použijte stránku **podepisování** **Návrháře projektu** k podepsání manifestů aplikace a nasazení a také k podepsání sestavení (podepisování silného názvu).

Všimněte si, že podepisování manifestů aplikace a nasazení je proces, který se liší od podepsání sestavení, přestože se obě úlohy provádějí na stránce **podepisování** .

Kromě toho se úložiště informací o klíčovém souboru liší od podepisování manifestu a podepsání sestavení. V případě podepisování manifestu jsou informace o klíči uloženy v databázi kryptografického úložiště v počítači a v úložišti certifikátů systému Windows aktuálního uživatele. V případě podepisování sestavení jsou informace o klíči uloženy pouze v databázi kryptografického úložiště vašeho počítače.

Pro přístup na stránku **podepisování** vyberte uzel projektu v **Průzkumník řešení** a potom v nabídce **projekt** klikněte na **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **podepisování** .

## <a name="application-and-deployment-manifest-signing"></a>Podepisování manifestu aplikace a nasazení

Zaškrtávací políčko **podepsat manifesty ClickOnce**

Zaškrtněte toto políčko pro podepsání manifestů aplikace a nasazení pomocí páru veřejného a privátního klíče. Další informace o tom, jak to provést, naleznete v tématu [How to: Signing Application and Deployment Manifests](../../ide/how-to-sign-application-and-deployment-manifests.md).

Tlačítko **vybrat z úložiště**

Umožňuje vybrat existující certifikát z osobního úložiště certifikátů aktuálního uživatele. Můžete vybrat jeden z těchto certifikátů pro podepsání aplikace a manifestů nasazení.

Když kliknete na **vybrat ze Storu** , otevře se dialogové okno **Vybrat certifikát** , ve kterém najdete seznam certifikátů v osobním úložišti certifikátů, které jsou aktuálně platné (neprošlé), a které mají privátní klíče. Účel certifikátu, který vyberete, by měl zahrnovat podepisování kódu.

Pokud kliknete na **Zobrazit vlastnosti certifikátu**, zobrazí se dialogové okno **Podrobnosti o certifikátu** . Toto dialogové okno obsahuje podrobné informace o certifikátu a obsahuje další možnosti. Kliknutím na Další informace **o certifikátech** můžete zobrazit další informace o nápovědě.

**Vybrat ze souboru** – tlačítko

Umožňuje vybrat certifikát z existujícího souboru klíče.

Kliknutím na **vybrat ze souboru** se otevře dialogové okno **Vybrat soubor** , ve kterém můžete vybrat soubor klíče certifikátu (. pfx). Soubor musí být chráněný heslem a v osobním úložišti certifikátů ho už nejde najít.

V dialogovém okně **zadat heslo pro otevření souboru** zadejte heslo pro otevření souboru klíče certifikátu (. pfx). Informace o heslech jsou uložené v osobním seznamu kontejnerů klíčů a v úložišti osobních certifikátů.

Tlačítko **vytvořit testovací certifikát**

Umožňuje vytvořit certifikát pro testování. Testovací certifikát se používá k podepsání aplikace ClickOnce a manifestů nasazení.

Kliknutím na **vytvořit testovací certifikát** otevřete dialogové okno **vytvořit testovací certifikát** , ve kterém můžete zadat heslo pro soubor klíče se silným názvem pro testovací certifikát. Soubor má název *projectname* _TemporaryKey. pfx. Pokud kliknete na tlačítko **OK** bez zadání hesla, není soubor. pfx zašifrovaný heslem.

Pole **adresy URL serveru časového razítka**

Určuje adresu serveru, který má časovou razítko vaší signatury. Když zadáte certifikát, tato externí lokalita ověří čas, kdy byla aplikace podepsána.

## <a name="assembly-signing"></a>Podepisování sestavení

Zaškrtávací políčko **pro podepsání sestavení**

Toto políčko zaškrtněte, pokud chcete podepsat sestavení a vytvořit soubor silně pojmenovaného klíče. Další informace o podepsání sestavení pomocí **Návrháře projektu** naleznete v tématu [How to: Sign a Assembly (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio).

Tato možnost používá k podepsání sestavení nástroj Al.exe poskytovaný sadou Windows Software Development Kit (SDK). Další informace o Al.exe naleznete v tématu [How to: Sign a Assembly se silným názvem](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

**Zvolit seznam souborů klíčů se silným názvem**

Umožňuje zadat nový nebo existující silně pojmenovaný soubor klíče, který se používá k podepsání sestavení. Tuto možnost vyberte **\<Browse...>** , pokud chcete vybrat existující soubor klíče.

Tuto možnost vyberte, pokud chcete **\<New...>** vytvořit nový soubor klíče, se kterým chcete sestavení podepsat. Zobrazí se dialogové okno **vytvořit klíč se silným názvem** , pomocí kterého můžete zadat název souboru klíče a chránit soubor klíče heslem. Heslo musí mít délku alespoň 6 znaků. Pokud zadáte heslo, vytvoří se soubor Personal Information Exchange (. pfx); Pokud nezadáte heslo, vytvoří se silný soubor s názvem klíče (. snk).

Tlačítko pro **změnu hesla**

Změní heslo pro soubor klíče Personal Information Exchange (. pfx), který se používá k podepsání sestavení.

Kliknutím na **změnit heslo** se otevře dialogové okno **změnit heslo klíče** . V tomto dialogovém okně je **staré** heslo aktuální heslo pro soubor klíče. **Nové heslo** musí mít délku nejméně 6 znaků. Informace o heslech jsou uložené v úložišti certifikátů Windows aktuálního uživatele.

Zaškrtávací políčko **pouze Zpožděné podepsání**

Zaškrtnutím tohoto políčka povolíte zpožděné podepisování.

Všimněte si, že zpožděný podepsaný projekt nebude spuštěn a nebude možné ho ladit. Můžete ale použít [Sn.exe (nástroj Strong Name)](/dotnet/framework/tools/sn-exe-strong-name-tool) s `-Vr` možností pro přeskočení ověřování během vývoje.

> [!NOTE]
> Když podepisujete sestavení, možná nebudete mít vždycky přístup k privátnímu klíči. Organizace může mít například úzce chráněný pár klíčů, ke kterému nemají vývojáři přístup denně. Veřejný klíč může být dostupný, ale přístup k privátnímu klíči je omezený na pár jednotlivců. V takovém případě můžete použít *Zpožděné* nebo *částečné podepisování* k poskytnutí veřejného klíče a odložit přidání privátního klíče, dokud nebude sestavení předáno.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Správa sestavení a podepsání manifestu](../../ide/managing-assembly-and-manifest-signing.md)
- [Postupy: Podepsání manifestů aplikace a nasazení](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [Postupy: podepsání sestavení (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [Postupy: Podepsání sestavení silným názvem](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies)
