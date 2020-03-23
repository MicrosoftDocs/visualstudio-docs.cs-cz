---
title: 'Postup: Podepsání manifestů aplikací a nasazení'
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbf25301095ac5ff438514c37f61337e46342860
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596161"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Postup: Podepsání manifestů aplikací a nasazení

Pokud chcete publikovat aplikaci pomocí nasazení ClickOnce, manifesty aplikace a nasazení musí být podepsány dvojicí veřejného a soukromého klíče a podepsány pomocí technologie Authenticode. Manifesty můžete podepsat pomocí certifikátu z úložiště certifikátů systému Windows nebo souboru klíčů.

Další informace o nasazení clickonce naleznete v [tématu ClickOnce security and deployment](../deployment/clickonce-security-and-deployment.md).

Podepisování manifestů ClickOnce je volitelné pro aplikace založené na *exe.* Další informace naleznete v části Generovat nepodepsané manifesty v tomto dokumentu.

Informace o vytváření klíčových souborů naleznete v [tématu Postup: Vytvoření páru klíčů veřejného a soukromého sektoru](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> Visual Studio podporuje pouze klíčové soubory Výměny osobních informací (PFX), které mají příponu *.pfx.* Můžete však vybrat jiné typy certifikátů z úložiště certifikátů systému Windows aktuálního uživatele klepnutím na tlačítko **Vybrat ze storu** na stránce **Podepisování** vlastností projektu.

## <a name="sign-using-a-certificate"></a>Podepisování pomocí certifikátu

1. Přejděte do okna vlastností projektu (klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a vyberte **vlastnosti).** Na kartě **Podpis** zaškrtněte políčko **Podepsat manifesty ClickOnce.**

2. Klikněte na tlačítko **Vybrat ze obchodu.**

     Zobrazí se dialogové okno **Vybrat certifikát,** které zobrazí obsah úložiště certifikátů systému Windows.

    > [!TIP]
    > Pokud klepnutím na tlačítko **Klepnutím sem zobrazíte vlastnosti certifikátu**, zobrazí se dialogové okno **Podrobnosti o certifikátu.** Toto dialogové okno obsahuje podrobné informace o certifikátu a další možnosti. Chcete-li zobrazit další informace nápovědy, klepněte na **položku Certifikáty.**

3. Vyberte certifikát, který chcete použít k podepsání manifestů.

4. Kromě toho můžete zadat adresu serveru časových razítek v textovém poli **adresy URL serveru časového razítka.** Jedná se o server, který poskytuje časové razítko určující, kdy byl manifest podepsán.

## <a name="sign-using-an-existing-key-file"></a>Podepisování pomocí existujícího souboru klíče

1. Na stránce **Podepisování** zaškrtněte políčko **Podepsat manifesty ClickOnce.**

2. Klepněte na tlačítko **Vybrat ze souboru.**

     Zobrazí se dialogové okno **Vybrat soubor.**

3. V dialogovém okně **Vybrat soubor** vyhledejte umístění souboru klíče (*.pfx),* který chcete použít, a klepněte na tlačítko **Otevřít**.

    > [!NOTE]
    > Tato možnost podporuje pouze soubory, které mají příponu *.pfx.* Pokud máte soubor klíče nebo certifikát v jiném formátu, uložte jej do úložiště certifikátů systému Windows a vyberte certifikát je popsán v předchozím postupu. Účel vybraného certifikátu by měl zahrnovat podepisování kódu.

     Zobrazí se dialogové okno **Zadat heslo k otevření souboru.** (Pokud je soubor *.pfx* již uložen v úložišti certifikátů systému Windows nebo není chráněn heslem, nebudete vyzváni k zadání hesla.)

4. Zadejte heslo pro přístup k souboru klíče a pak vyberte **Enter**.

> [!NOTE]
> Soubor *.pfx* nemůže obsahovat informace o řetězení certifikátů. Pokud ano, dojde k následující chybě importu: **Nelze najít certifikát a soukromý klíč pro dešifrování**. Chcete-li odebrat informace o řetězení certifikátů, můžete použít *certmgr.msc* a [zakázat možnost](/previous-versions/aa730868(v=vs.80)) **Zahrnout všechny certifikáty** při exportu souboru *.pfx.

## <a name="sign-using-a-test-certificate"></a>Podepisování pomocí testovacího certifikátu

1. Na stránce **Podepisování** zaškrtněte políčko **Podepsat manifesty ClickOnce.**

2. Chcete-li vytvořit nový certifikát pro testování, klepněte na tlačítko **Vytvořit testovací certifikát.**

3. V dialogovém okně **Vytvořit testovací certifikát** zadejte heslo, které vám pomůže zabezpečit testovací certifikát.

## <a name="generate-unsigned-manifests"></a>Generovat nepodepsané manifesty

Podepisování manifestů ClickOnce je volitelné pro aplikace založené na *exe.* Následující postupy ukazují, jak generovat nepodepsané manifesty ClickOnce.

> [!IMPORTANT]
> Nepodepsané manifesty mohou zjednodušit vývoj a testování vaší aplikace. Nepodepsané manifesty však představují podstatná bezpečnostní rizika v produkčním prostředí. Nepodepsané manifesty zvažte pouze v případě, že aplikace ClickOnce běží v počítačích v rámci sítě intranet, která je zcela izolována od Internetu nebo jiných zdrojů škodlivého kódu.

Ve výchozím nastavení ClickOnce automaticky generuje podepsané manifesty, pokud jeden nebo více souborů jsou výslovně vyloučeny z generované hodnoty hash. Jinými slovy publikování aplikace výsledky podepsané manifesty, pokud jsou všechny soubory zahrnuty do hash, i když je zaškrtnuto políčko **Podepsat ClickOnce manifestů** zaškrtnutí políčka.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Generování nepodepsaných manifestů a zahrnutí všech souborů do generované hodu hash

1. Chcete-li generovat nepodepsané manifesty, které obsahují všechny soubory v hash, musíte nejprve publikovat aplikaci spolu s podepsanými manifesty. Proto nejprve podepsat ClickOnce manifesty podle následující chod jeden z předchozích postupů a potom publikovat aplikaci.

2. Na stránce **Podpiszrušte** zaškrtnutí **políčka Podepsat manifesty ClickOnce.**

3. Obnovte verzi publikování tak, aby byla k dispozici pouze jedna verze aplikace. Ve výchozím nastavení Visual Studio automaticky inkumuje číslo revize verze publikování při každém publikování aplikace. Další informace naleznete v [tématu How to: Set the ClickOnce publish version](../deployment/how-to-set-the-clickonce-publish-version.md).

4. Publikujte aplikaci.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Generování nepodepsaných manifestů a vyloučení jednoho nebo více souborů z generované houštiny hash

1. Na stránce **Podpiszrušte** zaškrtnutí **políčka Podepsat manifesty ClickOnce.**

2. Otevřete dialogové okno **Soubory aplikace** a nastavte **nastavení Hash** to **Exclude** pro soubory, které chcete vyloučit z generované hodu hash.

    > [!NOTE]
    > Vyloučení souboru z hash konfiguruje ClickOnce zakázat automatické podepisování manifestů, takže není nutné nejprve publikovat s podepsanými manifesty, jak je znázorněno v předchozím postupu.

3. Publikujte aplikaci.

## <a name="see-also"></a>Viz také

- [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies)
- [Postup: Vytvoření páru klíčů veřejného a soukromého sektoru](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Podepisovací stránka, Návrhář projektu](../ide/reference/signing-page-project-designer.md)
- [Zabezpečení a nasazení ClickOnce](../deployment/clickonce-security-and-deployment.md)
