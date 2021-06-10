---
title: Vytvoření lokalizovaného balíčku bootstrapperu | Microsoft Docs
description: Naučte se vytvářet lokalizované verze balíčku bootstrapperu v ClickOnce vytvořením dalších dvou souborů pro každé národní prostředí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a9d1fc91dcb385a9250dde3adb47c0d9553147f
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877712"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Postupy: Vytvoření lokalizovaného balíčku bootstrapperu
Po vytvoření balíčku bootstrapperu můžete vytvořit lokalizované verze balíčku bootstrapperu tak, že pro každé národní prostředí vytvoříte další dva soubory: soubor softwarových licenčních podmínek (například *eula.rtf)* a manifest balíčku (*package.xml*).

 Ve výchozím nastavení obsahuje Visual Studio 2010 lokalizované balíčky zaváděcího nástroje pouze pro .NET Framework 4, profil klienta .NET Framework 4, F# Runtime 2.0 a F# Runtime 4.0. Můžete vytvořit lokalizované balíčky pro jiné bootstrappers provedením tří kroků.

1. Vytvořte složku pojmenovanou podle názvu národního prostředí v *adresáři \Program Files (x86)\Microsoft \\ \<BootstrapperPackageName> SDKs\ClickOnce Bootstrapper\Packages*.

2. Vytvořte soubor, který obsahuje licenční podmínky pro software balíčku bootstrapperu, a dejte ho do nové složky.

3. Vytvořte manifest balíčku *s názvempackage.xml*, aktualizujte řetězce a jazykovou verzi a dejte soubor do nové složky. Pokud jste už vytvořili bootstrapper Visual Studio cílovém jazyce, můžete zkopírovat soubor Visual Studio *package.xml* a upravit ho v tomto kroku.

> [!NOTE]
> Pokud k nasazení aplikací používáte projekt instalace, můžete aplikaci lokalizovat změnou **vlastnosti Localization.**

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Vytvoření lokalizovaného balíčku bootstrapperu

1. Vytvořte složku s názvem podle názvu národního prostředí.

     Na 32bitových počítačích vytvořte složku ve složce *\Program Files\Microsoft SDKs\ClickOnce Bootstrapper\Packages. \\ \<BootstrapperPackageName> \\*

     Na 64bitových počítačích vytvořte složku ve složce *\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages. \\ \<BootstrapperPackageName> \\*

     Následující tabulka uvádí názvy složek, které můžete použít ke spárování národního prostředí.

    |Národní prostředí|Název složky|
    |------------|-----------------|
    |Čínština (zjednodušená)|zh-Hans|
    |Čínština (tradiční)|zh-Hant|
    |Čeština|Cs|
    |Němčina|De|
    |angličtina|en|
    |španělština|es|
    |Francouzština|Fr|
    |Italština|It|
    |Korejština|Ko|
    |Japonština|ja|
    |Polština|Pl|
    |Portugalština (Brazílie)|pt-BR|
    |Ruština|Ru|
    |Turečtina|Tr|

2. Vytvořte soubor, který obsahuje licenční podmínky pro software balíčku bootstrapperu, a dejte ho do nové složky.

3. Vytvořte manifest balíčku s *názvempackage.xml* a dejte ho do nové složky. Další informace najdete v tématu [Postupy: Vytvoření manifestu balíčku.](../deployment/how-to-create-a-package-manifest.md)

4. Aktualizujte `<Strings>` část manifestu balíčku tak, aby řetězce ve správném jazyce pro národní prostředí.

5. Změňte `<String Name="Culture">` hodnotu tak, aby odpovídala názvu složky.

6. Uložte *souborpackage.xml.*

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Vytvoření balíčku bootstrapperu pro .NET Framework 3.5 Service Pack 1 lokalizované ve francouzštině

1. Vytvořte složku s názvem *fr.* Název složky se musí shodovat s názvem národního prostředí.

     Na 32bitových počítačích vytvořte složku ve složce *\Program Files\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1. \\*

     Na 64bitových počítačích vytvořte složku ve složce *\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1. \\*

2. Lokalizovaná verze licenčních podmínek pro software dejte do *složky fr.*

3. Zkopírujte *soubor \Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* do složky *fr* a otevřete soubor v Návrháři XML.

4. Aktualizujte `<Strings>` část manifestu balíčku tak, aby chybové řetězce ve francouzštině.

5. Změňte `<String Name="Culture">` hodnotu na *fr*.

6. Uložte *souborpackage.xml.*

>[!NOTE]
> Počínaje verzí Visual Studio 2019 s aktualizací Update 7 budou zjištěny také balíčky bootstrapperu v cestě *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages*.

## <a name="see-also"></a>Viz také
- [Vytváření balíčků bootstrapperu](../deployment/creating-bootstrapper-packages.md)
- [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)
- [Postupy: Vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md)