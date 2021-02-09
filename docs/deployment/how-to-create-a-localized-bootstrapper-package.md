---
title: Vytvoření lokalizovaného balíčku zaváděcího nástroje | Microsoft Docs
description: Naučte se vytvářet lokalizované verze balíčku zaváděcího nástroje v ClickOnce vytvořením dalších dalších souborů pro každé národní prostředí.
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
ms.openlocfilehash: 9eb06c54caceb2e9329347fb1dd0114749975e7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927584"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Postupy: Vytvoření lokalizovaného balíčku bootstrapperu
Po vytvoření balíčku zaváděcího nástroje můžete vytvořit lokalizované verze balíčku zaváděcího nástroje, a to vytvořením dalších dalších souborů pro každé národní prostředí: souboru licenčních podmínek softwaru (například *EULA. RTF*) a manifestu balíčku (*package.xml*).

 Ve výchozím nastavení Visual Studio 2010 obsahuje lokalizované balíčky zaváděcího nástroje jenom pro .NET Framework 4, .NET Framework 4 Client Profiles, F # runtime 2,0 a F # runtime 4,0. Pomocí tří kroků můžete vytvořit lokalizované balíčky pro další zaváděcí nástroje.

1. Vytvořte složku s názvem za názvem národního prostředí v *adresáři \Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName>*.

2. Vytvořte soubor, který obsahuje licenční smlouvy k softwaru pro balíček zaváděcího nástroje, a vložte ho do nové složky.

3. Vytvořte manifest balíčku s názvem *package.xml*, aktualizujte řetězce a jazykovou verzi a vložte soubor do nové složky. Pokud jste již vytvořili zaváděcí nástroj sady Visual Studio v cílovém jazyce, můžete zkopírovat soubor *package.xml* sady Visual Studio a upravit ho v tomto kroku.

> [!NOTE]
> Pokud k nasazení aplikací používáte projekt instalace, můžete aplikaci lokalizovat změnou vlastnosti **Localization** .

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Vytvoření lokalizovaného balíčku zaváděcího nástroje

1. Vytvořte složku s názvem za názvem národního prostředí.

     Na 32 počítačů Vytvořte složku ve složce *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> \\* .

     Na 64 počítačů Vytvořte složku ve složce *\Program Files (86 \\ \<BootstrapperPackageName> \\ ) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* .

     V následující tabulce jsou uvedeny názvy složek, které lze použít pro shodu národního prostředí.

    |Národní prostředí|Název složky|
    |------------|-----------------|
    |Čínština (zjednodušená)|zh – Hans|
    |Čínština (tradiční)|zh – Hant|
    |Čeština|cs|
    |Němčina|&|
    |angličtina|en|
    |španělština|es|
    |Francouzština|FR|
    |Italština|její|
    |Korejština|Ko|
    |Japonština|dža|
    |Polština|pl|
    |Portugalština (Brazílie)|pt-BR|
    |Ruština|ru|
    |Turečtina|recenzent|

2. Vytvořte soubor, který obsahuje licenční smlouvy k softwaru pro balíček zaváděcího nástroje, a vložte ho do nové složky.

3. Vytvořte manifest balíčku s názvem *package.xml* a vložte ho do nové složky. Další informace naleznete v tématu [How to: Create a manifest balíčku](../deployment/how-to-create-a-package-manifest.md).

4. Aktualizujte `<Strings>` oddíl manifestu balíčku tak, aby byly řetězce ve správném jazyce pro národní prostředí.

5. Změňte `<String Name="Culture">` hodnotu tak, aby odpovídala názvu složky.

6. Uložte soubor *package.xml* .

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Vytvoření balíčku zaváděcího nástroje pro aktualizaci Service Pack 1 .NET Framework 3,5 lokalizované ve francouzštině

1. Vytvořte složku s názvem *fr*. Název složky se musí shodovat s názvem národního prostředí.

     Na 32 počítačů Vytvořte složku ve složce *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\* .

     Na 64 počítačů Vytvořte složku ve složce *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\* .

2. Do složky *fr* umístěte lokalizovanou verzi licenčních podmínek pro software.

3. Zkopírujte soubor *\Program Files (x86) \microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* do složky *fr* a otevřete soubor v Návrháři XML.

4. Aktualizujte `<Strings>` oddíl manifestu balíčku tak, aby byly chybové řetězce ve francouzštině.

5. Změňte `<String Name="Culture">` hodnotu na *fr*.

6. Uložte soubor *package.xml* .

## <a name="see-also"></a>Viz také
- [Vytváření balíčků bootstrapperu](../deployment/creating-bootstrapper-packages.md)
- [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)
- [Postupy: Vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md)