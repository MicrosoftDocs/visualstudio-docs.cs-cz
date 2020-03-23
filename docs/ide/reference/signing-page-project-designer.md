---
title: Stránka Podepisování, návrhář projektu (C#)
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 516e2aaf4a55ad6422200f9fef1cbbf2d435af7b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597331"
---
# <a name="signing-page-project-designer"></a>Stránka Podepisování, návrhář projektu (C#)

Pomocí stránky **Podepisování** **Návrháře projektu** podepište manifesty aplikace a nasazení a také k podepsání sestavení (podepisování silného názvu).

Všimněte si, že podepisování manifestů aplikace a nasazení je proces odlišný od podepisování sestavení, i když oba úkoly jsou prováděny na stránce **podepisování.**

Také ukládání informací o souboru klíčů se liší pro podepisování manifestu a podepisování sestavení. Pro podepisování manifestu jsou informace o klíči uloženy v databázi kryptografického úložiště počítače a v úložišti certifikátů systému Windows aktuálního uživatele. Pro podepisování sestavení jsou informace o klíči uloženy pouze v databázi kryptografického úložiště počítače.

Chcete-li získat přístup ke stránce **Podepisování,** vyberte uzel projektu v **Průzkumníku řešení**a v nabídce **Project** klepněte na příkaz **Vlastnosti**. Po zobrazení **Návrháře projektů** klikněte na kartu **Podpis.**

## <a name="application-and-deployment-manifest-signing"></a>Podepisování manifestu aplikací a nasazení

**Zaškrtávací** políčko Podepsat manifesty ClickOnce

Toto políčko zaškrtněte, chcete-li podepsat manifesty aplikace a nasazení pomocí dvojice veřejných a soukromých klíčů. Další informace o tom, jak to provést, naleznete v [tématu How to: Sign Application and Deployment Manifests](../../ide/how-to-sign-application-and-deployment-manifests.md).

**Vybrat z** tlačítka Store

Umožňuje vybrat existující certifikát z úložiště osobních certifikátů aktuálního uživatele. Můžete vybrat jeden z těchto certifikátů k podepsání manifestů aplikace a nasazení.

Kliknutím na **Vybrat ze storu** se otevře dialogové okno **Vybrat certifikát,** ve kterém jsou certifikáty v úložišti osobních certifikátů, které jsou aktuálně platné (jejichž platnost nevypršela) a které mají soukromé klíče. Účel certifikátu, který vyberete, by měl zahrnovat podepisování kódu.

Klepnete-li na **tlačítko Zobrazit vlastnosti certifikátu**, zobrazí se dialogové okno **Podrobnosti o certifikátu.** Toto dialogové okno obsahuje podrobné informace o certifikátu a další možnosti. Kliknutím na Další informace o certifikátech zobrazíte další informace **nápovědy.**

**Vybrat z** tlačítka Soubor

Umožňuje vybrat certifikát z existujícího souboru klíče.

Klepnutím na **tlačítko Vybrat ze souboru** se otevře dialogové okno **Vybrat soubor,** které umožňuje vybrat soubor klíče certifikátu (.pfx). Soubor musí být chráněn heslem a již nemůže být umístěn v úložišti osobních certifikátů.

V dialogovém **okně Zadat heslo k otevření souboru** zadejte heslo pro otevření souboru klíče certifikátu (.pfx). Informace o hesle jsou uloženy v seznamu osobních kontejnerů klíčů a v úložišti osobních certifikátů.

**Tlačítko Vytvořit testovací certifikát**

Umožňuje vytvořit certifikát pro testování. Testovací certifikát se používá k podepisování manifestů aplikace ClickOnce a nasazení.

Klepnutím na **tlačítko Vytvořit testovací certifikát** se otevře dialogové okno Vytvořit testovací **certifikát,** ve kterém můžete zadat heslo pro soubor klíče silného názvu pro testovací certifikát. Soubor se nazývá *název projektu*_TemporaryKey.pfx. Pokud klepnete na **tlačítko OK** bez zadání hesla, soubor PFx není šifrován heslem.

Pole **URL serveru časového razítka**

Určuje adresu serveru, který časově oznamuje váš podpis. Pokud zadáte certifikát, tento externí web ověří čas, kdy byla aplikace podepsána.

## <a name="assembly-signing"></a>Podepisování sestavení

**Zaškrtávací** políčko Podepsat sestavení

Zaškrtnutím tohoto políčka podepíšete sestavení a vytvoříte silně pojmenovaný soubor klíče. Další informace o podepisování sestavení pomocí **Návrháře projektu**naleznete v [tématu How to: Sign a Assembly (Visual Studio).](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)

Tato možnost používá nástroj Al.exe poskytovovaný sadou Windows Software Development Kit (SDK) k podepsání sestavení. Další informace o souboru Al.exe naleznete v [tématu How to: Sign a Assembly with a Strong Name](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).

Výběr seznamu **souborů klíčů silného názvu**

Umožňuje zadat nový nebo existující silně pojmenovaný soubor klíče, který se používá k podepsání sestavení. Vyberte ** \<Procházet...>** a vyberte existující soubor klíče.

Vyberte ** \<Nový...>** a vytvořte nový soubor klíče, se kterým chcete podepsat sestavení. Zobrazí se dialogové okno **Vytvořit silný klíč názvu,** pomocí kterého můžete zadat název souboru klíče a chránit soubor klíče heslem. Heslo musí mít alespoň 6 znaků. Pokud zadáte heslo, vytvoří se soubor Výměny osobních informací (.pfx); Pokud heslo nezadáte, vytvoří se soubor s výrazným názvem klíče (.snk).

**Tlačítko Změnit heslo**

Změní heslo pro soubor klíče výměny osobních informací (.pfx), který se používá k podepsání sestavení.

Kliknutím na **Změnit heslo** se otevře dialogové okno Změnit **heslo klíče.** V tomto dialogovém okně je **staré heslo** aktuálním heslem pro soubor klíče. **Nové heslo** musí mít trvat nejméně 6 znaků. Informace o hesle jsou uloženy v úložišti certifikátů systému Windows aktuálního uživatele.

Zaškrtávací políčko **Pouze znaménko zpoždění**

Zaškrtnutím tohoto políčka povolíte zpoždění podepisování.

Všimněte si, že zpožděné podepsané projektu nebude spuštěna a nelze ladit. Můžete však použít [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool) s `-Vr` možností přeskočit ověření během vývoje.

> [!NOTE]
> Při podepisování sestavení nemusí mít vždy přístup k soukromému klíči. Organizace může mít například pečlivě střežený pár klíčů, ke kterému vývojáři nemají přístup každý den. Veřejný klíč může být k dispozici, ale přístup k soukromému klíči je omezen na několik osob. V takovém případě můžete použít *zpožděné* nebo *částečné podepisování* poskytnout veřejný klíč, odložení přidání soukromého klíče, dokud je předán sestavení.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)
- [Správa sestavení a podepsání manifestu](../../ide/managing-assembly-and-manifest-signing.md)
- [Postupy: Podepsání manifestů aplikace a nasazení](../../ide/how-to-sign-application-and-deployment-manifests.md)
- [Postup: Podepsání sestavení (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)
- [Postupy: Podepsání sestavení silným názvem](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies)
