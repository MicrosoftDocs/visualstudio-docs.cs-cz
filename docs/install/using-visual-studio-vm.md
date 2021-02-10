---
title: Používání sady Visual Studio na virtuálním počítači Azure
titleSuffix: ''
description: Naučte se používat Visual Studio na virtuálním počítači Azure
ms.date: 11/17/2020
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine
- installation
- visual studio
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7111c53a498fe10710ec2b328600052a7d4de0cd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935635"
---
# <a name="visual-studio-images-on-azure"></a><a id="top"></a> Image sady Visual Studio v Azure

Použití sady Visual Studio v předkonfigurovaném virtuálním počítači Azure je rychlý a snadný způsob, jak přejít z žádného nečinnosti do provozního vývojového prostředí. Systémové image s různými konfiguracemi sady Visual Studio jsou k dispozici v [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps/category/compute?filters=virtual-machine-images%3Bmicrosoft%3Bwindows&page=1&subcategories=application-infrastructure).

Jste nováčky v prostředí Azure? [Vytvořte si bezplatný účet Azure](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Jaké konfigurace a verze jsou k dispozici?

Obrázky pro nejaktuálnější hlavní verze, Visual Studio 2019, Visual Studio 2017 a Visual Studio 2015, najdete v Azure Marketplace.  U každé vydané hlavní verze se zobrazí původní verze "vydáno do webu" (RTW) a nejnovější aktualizované verze.  Každá z těchto verzí nabízí Visual Studio Enterprise a edici Visual Studio Community.  Tyto image se aktualizují aspoň každý měsíc, aby zahrnovaly nejnovější aktualizace sady Visual Studio a Windows.  I když názvy imagí zůstanou stejné, popis každého obrázku zahrnuje nainstalovanou verzi produktu a datum "od".

| Verze vydaných verzí                                                                                                                                          | Edice              |    Verze produktu    |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:---------------------:|:-----------------------:|
| [Visual Studio 2019: nejnovější (verze 16,8)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019latest?tab=Overview) | Enterprise, Community | 16.8.0 verze    |
| [Visual Studio 2019: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio2019?tab=Overview)                         | Enterprise            | 16.0.20 verze    |
| [Visual Studio 2017: nejnovější (verze 15,9)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)           | Enterprise, Community | 15.9.29 verze   |
| [Visual Studio 2017: RTW](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)                             | Enterprise, Community | 15.0.28 verze   |
| [Visual Studio 2015: nejnovější (aktualizace 3)](https://azuremarketplace.microsoft.com/marketplace/apps/microsoftvisualstudio.visualstudio?tab=Overview)               | Enterprise, Community | 14.0.25431.01 verze |

> [!NOTE]
> V souladu se zásadami poskytování služeb Microsoftu vypršela platnost původní vydané verze sady Visual Studio 2015 pro účely údržby. Pro produktovou řadu Visual Studio 2015 je k dispozici pouze ta zbývající verze sady Visual Studio 2015 Update 3.

Další informace najdete v tématu [zásady údržby sady Visual Studio](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Jaké funkce jsou nainstalovány?

Každý obrázek obsahuje doporučenou sadu funkcí pro tuto edici sady Visual Studio. Obecně platí, že instalace zahrnuje:

* Všechny dostupné úlohy, včetně doporučených volitelných součástí jednotlivých úloh
* .NET 4.6.2 a .NET 4,7 SDK, cílení na sady a Vývojářské nástroje
* Visual F#
* GitHub Extension for Visual Studio
* Nástroje LINQ to SQL

K instalaci sady Visual Studio při sestavování imagí používáme následující příkazový řádek:

```shell
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       --add Microsoft.Net.Component.4.7.SDK ^
       --add Microsoft.Net.Component.4.7.TargetingPack ^
       --add Microsoft.Net.Component.4.6.2.SDK ^
       --add Microsoft.Net.Component.4.6.2.TargetingPack ^
       --add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       --add Microsoft.VisualStudio.Component.FSharp ^
       --add Component.GitHub.VisualStudio ^
       --add Microsoft.VisualStudio.Component.LinqToSql
```

Pokud image neobsahují funkci sady Visual Studio, kterou požadujete, poskytněte zpětnou vazbu prostřednictvím nástroje pro zpětnou vazbu v pravém horním rohu stránky.

## <a name="what-size-vm-should-i-choose"></a>Jakou velikost virtuálního počítače mám zvolit?

Azure nabízí celou škálu velikostí virtuálních počítačů. Vzhledem k tomu, že je Visual Studio výkonná aplikace s více vlákny, chcete mít velikost virtuálního počítače, která zahrnuje aspoň dva procesory a 7 GB paměti. Pro Image sady Visual Studio doporučujeme použít následující velikosti virtuálních počítačů:

* Standard_D2_v3
* Standard_D2s_v3
* Standard_D4_v3
* Standard_D4s_v3
* Standard_D2_v2
* Standard_D2S_v2
* Standard_D3_v2

Další informace o nejnovějších velikostech počítačů najdete v tématu [velikosti virtuálních počítačů s Windows v Azure](/azure/virtual-machines/windows/sizes).

S Azure můžete svoji počáteční volbu znovu vyvážit změnou velikosti virtuálního počítače. Můžete buď zřídit nový virtuální počítač s vhodnější velikostí, nebo změnit velikost stávajícího virtuálního počítače na jiný základní hardware. Další informace najdete v tématu [Změna velikosti virtuálního počítače s Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Když je virtuální počítač spuštěný, co dál?

Visual Studio se řídí modelem "Přineste si vlastní licenci" v Azure. Jedním z prvních kroků je jako instalace na proprietární hardware licencování pro instalaci sady Visual Studio. Chcete-li odemknout aplikaci Visual Studio, buď:
- Přihlaste se pomocí účet Microsoft, která je přidružená k předplatnému sady Visual Studio.
- Odemkněte Visual Studio pomocí kódu Product Key, který jste obdrželi s vaším počátečním nákupem.

Další informace najdete v tématu [přihlášení do sady Visual Studio](../ide/signing-in-to-visual-studio.md) a [o tom, jak odemknout Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Návody uložit virtuální počítač pro vývoj pro budoucí nebo týmovou práci?

Spektrum vývojových prostředí je velmi náročné a k vytváření složitějších prostředí se účtují reálné náklady. Bez ohledu na konfiguraci vašeho prostředí můžete nakonfigurovaný virtuální počítač uložit nebo zachytit jako základní image pro budoucí použití nebo pro ostatní členy týmu. Při spuštění nového virtuálního počítače pak místo Azure Marketplace image zřídíte základní image.

Rychlý přehled: použijte nástroj pro přípravu systému (Sysprep) a vypněte běžící virtuální počítač a potom Zachyťte *(obrázek 1)* virtuální počítač jako Image prostřednictvím uživatelského rozhraní v Azure Portal. Azure uloží `.vhd` soubor, který obsahuje obrázek v účtu úložiště, který zvolíte. Nový obrázek se pak v seznamu prostředků vašeho předplatného zobrazí jako prostředek obrázku.

![Zachycení image prostřednictvím uživatelského rozhraní Azure Portal](media/capture-vm.png)

*(Obrázek 1) Zachytit image prostřednictvím uživatelského rozhraní Azure Portal.*

Další informace najdete v tématu [Vytvoření spravované image zobecněného virtuálního počítače v Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Nezapomeňte použít nástroj Sysprep k přípravě virtuálního počítače. Pokud jste tento krok nezrušili, Azure nemůže z image zřídit virtuální počítač.

> [!NOTE]
> Pořád se vám účtují poplatky za ukládání imagí, ale tyto přírůstkové náklady můžou být v porovnání s režijními náklady na opětovné sestavení virtuálního počítače od začátku pro každého člena týmu, který ho potřebují. Například má za měsíc vytvoření a uložení image 127-GB na měsíc, který je možné využít celý tým, náklady na několik dolarů. Tyto náklady jsou ale ve srovnání s hodinami nevýznamné, protože každý zaměstnanec investoval do sestavení a ověří správně nakonfigurované vývojové pole pro jejich individuální použití.

Kromě toho můžou vaše vývojářské úlohy nebo technologie potřebovat větší měřítko, jako jsou odrůdy konfigurací vývoje a více konfigurací počítačů. Azure DevTest Labs můžete použít k vytvoření _recepty_ , které automatizují konstrukci "zlatých imagí". DevTest Labs můžete použít také ke správě zásad pro běžící virtuální počítače vašeho týmu. Pro další informace o DevTest Labs je nejvhodnějším zdrojem [použití Azure DevTest Labs pro vývojáře](/azure/devtest-lab/devtest-lab-developer-lab) .

## <a name="next-steps"></a>Další kroky

Teď, když víte o předkonfigurovaných bitových kopiích sady Visual Studio, je dalším krokem vytvoření nového virtuálního počítače:

* [Vytvoření virtuálního počítače pomocí Azure Portal](/azure/virtual-machines/windows/quick-create-portal)
* [Přehled Windows Virtual Machines](/azure/virtual-machines/windows/overview)
