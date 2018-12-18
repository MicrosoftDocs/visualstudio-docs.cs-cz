---
title: 'Postupy: vytvoření lokalizovaného balíčku Bootstrapperu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1083633410c42c63f8c3e9a2ff341a2278f0b63a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153212"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Postupy: vytvoření lokalizovaného balíčku bootstrapperu
Po vytvoření balíčku zaváděcího nástroje lokalizované verze balíčku zaváděcího nástroje můžete vytvořit tak, že vytvoříte dva další soubory pro každé národní prostředí: software licenčních podmínek souboru (například *eula.rtf*) a manifest balíčku (*package.xml*).  
  
 Ve výchozím nastavení Visual Studio 2010 obsahuje lokalizované balíčky zaváděcího nástroje pouze pro rozhraní .NET Framework 4, .NET Framework 4 Client Profile, 2.0 modul Runtime F # a F # 4.0 modulu Runtime. Lokalizované balíčky pro jiné bootstrapperů můžete vytvořit pomocí tří kroků.  
  
1.  Vytvořte složku s názvem za název národního prostředí v *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >*.  
  
2.  Vytvořit soubor, který obsahuje licenční podmínky pro software pro balíček zaváděcího nástroje a vložit ho do nové složky.  
  
3.  Vytvoření manifestu balíčku s názvem *package.xml*, aktualizujte řetězce a jazykovou verzi a vložit ho do nové složky. Pokud jste již vytvořili zaváděcí nástroj sady Visual Studio v cílovém jazyce, můžete zkopírovat sady Visual Studio *package.xml* soubor a upravit ho v tomto kroku.  
  
> [!NOTE]
>  Pokud nasazení aplikace pomocí projektu instalace, je možné lokalizovat aplikaci tak, že změníte **lokalizace** vlastnost.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>K vytvoření lokalizovaného balíčku bootstrapperu  
  
1.  Vytvořte složku s názvem za název národního prostředí.  
  
     Na 32bitových počítačích, vytvořte složku v *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  složky.  
  
     Na 64bitových počítačích, vytvořte složku v *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<BootstrapperPackageName >\\*  složky.  
  
     Následující tabulka uvádí názvy složek, které můžete použít tak, aby odpovídaly národní prostředí.  
  
    |Národní prostředí|Název složky|  
    |------------|-----------------|  
    |Čínština (zjednodušená)|zh-Hans|  
    |Čínština (tradiční)|zh-Hant|  
    |Čeština|cs|  
    |Němčina|de|  
    |Angličtina|cs|  
    |Španělština|ES|  
    |Francouzština|FR|  
    |Italština|To|  
    |Korejština|Ko|  
    |Japonština|Japonsko|  
    |Polština|PL|  
    |Portugalština (Brazílie)|pt-BR|  
    |Ruština|RU|  
    |Turečtina|tr|  
  
2.  Vytvořit soubor, který obsahuje licenční podmínky pro software pro balíček zaváděcího nástroje a vložit ho do nové složky.  
  
3.  Vytvoření manifestu balíčku s názvem *package.xml* a vložit ho do nové složky. Další informace najdete v tématu [postupy: vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Aktualizace `<Strings>` část balíček manifestu tak, že jsou řetězce ve správném jazyce pro národní prostředí.  
  
5.  Změnit `<String Name="Culture">` hodnotu tak, aby odpovídaly názvu složky.  
  
6.  Uložit *package.xml* souboru.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Vytvoření balíčku zaváděcího nástroje pro .NET Framework 3.5 Service Pack 1 lokalizované ve francouzštině  
  
1.  Vytvořte složku s názvem *fr*. Název složky musí odpovídat názvu národního prostředí.  
  
     Na 32bitových počítačích, vytvořte složku v *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  složky.  
  
     Na 64bitových počítačích, vytvořte složku v *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  složky.  
  
2.  Lokalizované verzi licenční podmínky pro software do *fr* složky.  
  
3.  Kopírovat *\Program soubory (x86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* do souboru *fr* složky a otevřete soubor v Návrháři XML.  
  
4.  Aktualizace `<Strings>` část balíček manifestu tak, aby chybové řetězce ve francouzštině.  
  
5.  Změnit `<String Name="Culture">` hodnota, která se *fr*.  
  
6.  Uložit *package.xml* souboru.  
  
## <a name="see-also"></a>Viz také:  
 [Vytváření balíčků bootstrapperu](../deployment/creating-bootstrapper-packages.md)   
 [Nezbytné součásti nasazení aplikace](../deployment/application-deployment-prerequisites.md)   
 [Postupy: Vytvoření manifestu balíčku](../deployment/how-to-create-a-package-manifest.md)