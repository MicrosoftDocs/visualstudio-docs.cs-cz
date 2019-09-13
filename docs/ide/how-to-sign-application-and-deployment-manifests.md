---
title: 'Postupy: Podepsání manifestů aplikace a nasazení'
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3f9c0f4913c80e1cf2f2fee24dbed5ad910ca75
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887792"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Postupy: Podepsání manifestů aplikace a nasazení

Pokud chcete publikovat aplikaci pomocí nasazení ClickOnce, manifesty aplikace a nasazení musí být podepsány pomocí páru veřejného a privátního klíče a podepsány pomocí technologie Authenticode. Manifesty můžete podepsat pomocí certifikátu z úložiště certifikátů Windows nebo souboru klíče.

Další informace o nasazení ClickOnce naleznete v tématu [Security and Deployment ClickOnce](../deployment/clickonce-security-and-deployment.md).

Podepisování manifestů ClickOnce je volitelné pro aplikace založené na *. exe*. Další informace naleznete v části "generování nepodepsaných manifestů" v tomto dokumentu.

Informace o vytváření souborů klíčů naleznete v tématu [How to: Vytvoří pár](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)veřejného a privátního klíče.

> [!NOTE]
> Visual Studio podporuje pouze soubory klíčů PFX (Personal Information Exchange), které mají příponu *. pfx* . Můžete ale vybrat jiné typy certifikátů z úložiště certifikátů Windows aktuálního uživatele tak, že kliknete na **vybrat ze Storu** na stránce **podepisování** vlastností projektu.

## <a name="sign-using-a-certificate"></a>Podepsat pomocí certifikátu

1. Přejděte do okna Vlastnosti projektu (klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte **vlastnosti**). Na kartě **podepisování** zaškrtněte políčko **podepsat manifesty ClickOnce** .

2. Klikněte na tlačítko **vybrat z úložiště** .

     Zobrazí se dialogové okno **Vybrat certifikát** , ve kterém se zobrazí obsah úložiště certifikátů Windows.

    > [!TIP]
    > Pokud kliknete na **možnost kliknutím sem zobrazíte vlastnosti certifikátu**, zobrazí se dialogové okno **Podrobnosti o certifikátu** . Toto dialogové okno obsahuje podrobné informace o certifikátu a dalších možnostech. Kliknutím na **certifikáty** zobrazíte další informace o nápovědě.

3. Vyberte certifikát, který chcete použít k podepsání manifestů.

4. Navíc můžete zadat adresu serveru časového razítka v textovém poli **Adresa URL serveru časového razítka** . Toto je server, který poskytuje časové razítko, které určuje, kdy byl manifest podepsán.

## <a name="sign-using-an-existing-key-file"></a>Podepsat pomocí existujícího souboru klíče

1. Na stránce **podepisování** zaškrtněte políčko **podepsat manifesty ClickOnce** .

2. Klikněte na tlačítko **vybrat ze souboru** .

     Zobrazí se dialogové okno **Vybrat soubor** .

3. V dialogovém okně **Vybrat soubor** přejděte do umístění souboru klíče ( *. pfx*), který chcete použít, a potom klikněte na tlačítko **otevřít**.

    > [!NOTE]
    > Tato možnost podporuje pouze soubory, které mají příponu *. pfx* . Pokud máte soubor klíče nebo certifikát v jiném formátu, uložte ho do úložiště certifikátů Windows a vyberte certifikát, který je popsaný v předchozím postupu. Vybraný účel certifikátu by měl zahrnovat podepisování kódu.

     Zobrazí se dialogové okno **zadat heslo pro otevření souboru** . (Pokud soubor *. pfx* už je uložený v úložišti certifikátů Windows nebo není chráněný heslem, nezobrazí se výzva k zadání hesla.)

4. Zadejte heslo pro přístup k souboru klíče a pak vyberte **ENTER**.

> [!NOTE]
> Soubor *. pfx* nemůže obsahovat informace o řetězení certifikátů. V takovém případě dojde k následující chybě importu: **Nejde najít certifikát a privátní klíč pro dešifrování**. Chcete-li odebrat informace o řetězení certifikátů, můžete použít program *certmgr. msc* a [zakázat možnost](/previous-versions/aa730868(v=vs.80)?redirectedfrom=MSDN#rsvssign_topic3) **zahrnutí všech certifikátů** při exportování souboru *. pfx.

## <a name="sign-using-a-test-certificate"></a>Podepsat pomocí testovacího certifikátu

1. Na stránce **podepisování** zaškrtněte políčko **podepsat manifesty ClickOnce** .

2. Chcete-li vytvořit nový certifikát pro testování, klikněte na tlačítko **vytvořit testovací certifikát** .

3. V dialogovém okně **vytvořit testovací certifikát** zadejte heslo pro zvýšení zabezpečení testovacího certifikátu.

## <a name="generate-unsigned-manifests"></a>Generovat nepodepsané manifesty

Podepisování manifestů ClickOnce je volitelné pro aplikace založené na *. exe*. Následující postupy ukazují, jak generovat nepodepsané manifesty ClickOnce.

> [!IMPORTANT]
> Nepodepsané manifesty mohou zjednodušit vývoj a testování vaší aplikace. Nepodepsané manifesty však představují podstatná bezpečnostní rizika v produkčním prostředí. Zvažte použití nepodepsaných manifestů, pokud vaše aplikace ClickOnce běží na počítačích v intranetu, který je zcela izolovaný od Internetu nebo jiných zdrojů škodlivého kódu.

Ve výchozím nastavení ClickOnce automaticky generuje podepsané manifesty, pokud jeden nebo více souborů není výslovně vyloučen z generované hodnoty hash. Jinými slovy, publikování aplikace má za následek podepsané manifesty, pokud jsou všechny soubory zahrnuty v hodnotě hash, a to i v případě, že není zaškrtnuto políčko **podepsat manifesty ClickOnce** .

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Generování nepodepsaných manifestů a zahrnutí všech souborů do generované hodnoty hash

1. Chcete-li generovat nepodepsané manifesty, které obsahují všechny soubory v hodnotě hash, je nutné nejprve publikovat aplikaci společně s podepsanými manifesty. Proto nejprve podepište manifesty ClickOnce pomocí jednoho z předchozích postupů a pak aplikaci publikujte.

2. Na stránce **podepisování** zrušte zaškrtnutí políčka **podepsat manifesty ClickOnce** .

3. Obnovte verzi publikování tak, aby byla k dispozici pouze jedna verze aplikace. Ve výchozím nastavení Visual Studio automaticky zvyšuje číslo revize verze publikování pokaždé, když publikujete aplikaci. Další informace najdete v tématu [jak: Nastavte publikační verzi](../deployment/how-to-set-the-clickonce-publish-version.md)ClickOnce.

4. Publikujte aplikaci.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Generování nepodepsaných manifestů a vyloučení jednoho nebo více souborů z generované hodnoty hash

1. Na stránce **podepisování** zrušte zaškrtnutí políčka **podepsat manifesty ClickOnce** .

2. Otevřete dialogové okno **soubory aplikace** a nastavte **hodnotu hash** na **vyloučené** pro soubory, které chcete vyloučit z vygenerované hodnoty hash.

    > [!NOTE]
    > Vyloučení souboru z hodnoty hash konfiguruje ClickOnce pro zákaz automatického podepisování manifestů, takže není nutné nejprve publikovat s podepsanými manifesty, jak je znázorněno v předchozím postupu.

3. Publikujte aplikaci.

## <a name="see-also"></a>Viz také:

- [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies)
- [Postupy: Vytvoření páru klíčů veřejného a soukromého](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Stránka podepisování, Návrhář projektu](../ide/reference/signing-page-project-designer.md)
- [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)
