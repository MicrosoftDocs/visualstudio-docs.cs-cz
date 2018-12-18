---
title: 'Postupy: podepsání manifestů aplikace a nasazení'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 903bc0df9b24cd6f944e9e92c6dc5283cd1d25ea
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381944"
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Postupy: podepsání manifestů aplikace a nasazení

Pokud chcete publikovat aplikaci pomocí nasazení ClickOnce, manifesty aplikace a nasazení musí být podepsány párem veřejného a privátního klíče a pomocí technologie Authenticode. Manifesty můžete podepsat pomocí certifikátu z úložiště certifikátů Windows nebo soubor klíče.

 Další informace o nasazení ClickOnce naleznete v tématu [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md).

 Podepisování manifestů ClickOnce je nepovinné pro *.exe*– na základě aplikací. Další informace najdete v části "Generování nepodepsaných manifestů" tohoto dokumentu.

 Informace o vytváření souborů klíčů naleznete v tématu [postupy: vytvoření páru veřejného a privátního klíče](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podporuje pouze soubory klíčů Personal Information Exchange (PFX), které mají *.pfx* rozšíření. Ale můžete vybrat jiné typy certifikátů z úložiště certifikátů Windows aktuálního uživatele klepnutím **vybírat Store** na **podepisování** stránky vlastností projektu.

## <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>K podepsání aplikace a nasazení manifesty pomocí certifikátu

1.  Přejděte na okno s vlastnostmi projektu (klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a vyberte **vlastnosti**, nebo typ **vlastnosti projektu** v **Snadné spuštění** okna, nebo stisknutím klávesy **Alt**+**Enter** uvnitř **Průzkumníka řešení**). Na **podepisování** kartu, vyberte **podepsat manifesty ClickOnce** zaškrtávací políčko.

2.  Klikněte na tlačítko **vybírat Store** tlačítko.

     **Vyberte certifikát, který** dialogové okno se zobrazí a zobrazí se obsah z úložiště certifikátů Windows.

    > [!TIP]
    > Vyberete-li **kliknutím sem můžete zobrazit vlastnosti certifikátu**, **podrobnosti o certifikátu** zobrazí se dialogové okno. Toto dialogové okno obsahuje podrobné informace o certifikátu a obsahuje další možnosti. Můžete kliknout na **certifikáty** zobrazíte další informace nápovědy.

3.  Vyberte certifikát, který chcete použít k podepsání manifestů.

4.  Kromě toho můžete zadat adresu serveru časového razítka v **adresa URL serveru časového razítka** textového pole. To je server, který obsahuje časové razítko určující, když byl manifest podepsán.

## <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>Podepsání aplikace a nasazení manifestů pomocí existujícího souboru s klíčem

1.  Na **podepisování** stránky, vyberte **podepsat manifesty ClickOnce** zaškrtávací políčko.

2.  Klikněte na tlačítko **vybrat ze souboru** tlačítko.

     **Vybrat soubor** zobrazí se dialogové okno.

3.  V **vybrat soubor** dialogové okno, přejděte do umístění souboru s klíčem (*.pfx*), který chcete použít a potom klikněte na tlačítko **otevřít**.

    > [!NOTE]
    > Tato možnost podporuje pouze soubory, které mají *.pfx* rozšíření. Pokud máte soubor s klíčem nebo certifikátem v jiném formátu, uložte ho do úložiště certifikátů Windows a vyberte certifikát, který je popsaný v předchozím postupu. Vybraný účel certifikátu by měl zahrnovat podepisování kódu.

     **Zadejte heslo pro otevření souboru** zobrazí se dialogové okno. (Pokud *.pfx* soubor je již uložen v úložišti certifikátů Windows nebo není chráněn heslem, nezobrazí se výzva k zadání hesla.)

4.  Zadejte heslo pro přístup k souboru s klíčem a stiskněte klávesu **Enter**.

## <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>Podepsání aplikace a nasazení manifestů pomocí testovacího certifikátu

1.  Na **podepisování** stránky, vyberte **podepsat manifesty ClickOnce** zaškrtávací políčko.

2.  Chcete-li vytvořit nový certifikát pro účely testování, klikněte na tlačítko **vytvořit testovací certifikát** tlačítko.

3.  V **vytvořit testovací certifikát** dialogového okna zadejte heslo k zabezpečení vašeho testovacího certifikátu.

## <a name="generate-unsigned-manifests"></a>Generování nepodepsaných manifestů

Podepisování manifestů ClickOnce je nepovinné pro *.exe*– na základě aplikací. Následující postupy ukazují, jak vygenerovat nepodepsané manifesty ClickOnce.

> [!IMPORTANT]
> Nepodepsané manifesty mohou zjednodušit vývoj a testování vaší aplikace. Nepodepsané manifesty však představují podstatná bezpečnostní rizika v produkčním prostředí. Pouze zvažte použití nepodepsaných manifestů, pokud vaše aplikace ClickOnce funguje na počítačích v rámci sítě intranet, který je zcela izolována od Internetu nebo jiných zdrojů škodlivého kódu.

 Ve výchozím nastavení ClickOnce automaticky generuje podepsané manifesty, pokud jeden nebo více souborů výslovně vyloučeno z generované hodnoty hash. Jinými slovy, publikování výsledků aplikace podepsané manifesty, pokud jsou všechny soubory zahrnuty v algoritmu hodnoty hash, i když **podepsat manifesty ClickOnce** zrušení zaškrtnutí políčka.

### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Chcete-li generovat nepodepsané manifesty a zahrnout všechny soubory v generované hodnoty hash

1.  Chcete-li generovat nepodepsané manifesty, které zahrnují všechny soubory v algoritmu hodnoty hash, musíte nejprve publikovat aplikace spolu s podepsanými manifesty. Proto nejprve podepište manifesty ClickOnce podle jednoho z předchozích kroků a potom aplikaci publikujte.

2.  Na **podepisování** zrušte **podepsat manifesty ClickOnce** zaškrtávací políčko.

3.  Resetujte verzi publikování, takže je k dispozici pouze jedna verze vaší aplikace. Ve výchozím nastavení Visual Studio automaticky zvýší číslo revize verze publikování pokaždé, když se publikování aplikace. Další informace najdete v tématu [postupy: nastavení publikování ClickOnce verze](../deployment/how-to-set-the-clickonce-publish-version.md).

4.  Publikování aplikace.

### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Generování nepodepsaných manifestů a vyloučení jednoho nebo více souborů z generované hodnoty hash

1.  Na **podepisování** zrušte **podepsat manifesty ClickOnce** zaškrtávací políčko.

2.  Otevřít **soubory aplikace** dialogové okno a nastavte **Hash** k **vyloučit** pro soubory, které chcete vyloučit z generované hodnoty hash.

    > [!NOTE]
    > Vyloučení souboru z hodnoty hash konfiguruje ClickOnce k zakázání automatického podepisování manifestů, takže není nutné nejprve publikovat s podepsanými manifesty, jak je znázorněno v předchozím postupu.

3.  Publikování aplikace.

## <a name="see-also"></a>Viz také:

- [Sestavení se silným názvem](/dotnet/framework/app-domains/strong-named-assemblies)
- [Postupy: vytvoření páru veřejného a privátního klíče](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)
- [Stránka podepisování, Návrhář projektu](../ide/reference/signing-page-project-designer.md)
- [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)