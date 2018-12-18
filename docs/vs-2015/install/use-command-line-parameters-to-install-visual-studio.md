---
title: Použití parametrů příkazového řádku pro instalaci sady Visual Studio 2015 | Dokumentace Microsoftu
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: e84d9d7bde30ab781da2f135c94baf74b697e567
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059136"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Použití parametrů příkazového řádku instalace sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci pro sadu Visual Studio 2017 najdete v tématu [použitím parametrů příkazového řádku instalace sady Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Když nainstalujete sadu Visual Studio 2015 z příkazového řádku, můžete použít následující parametry příkazového řádku (také se označují jako přepínače).

> [!NOTE]
>  Ujistěte se, že používáte skutečné instalační program a ne soubor zaváděcího nástroje. Například, ujistěte se, že používáte **`vs_enterprise.exe`** místo vs_enterprise_*GUID*.exe. Můžete stáhnout instalační program z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Seznam parametrů příkazového řádku
 Parametry příkazového řádku aplikace Visual Studio nerozlišují malá a velká písmena.

|Parametr|Popis|
|---------------|-----------------|
|**/?**<br /><br /> **/ Help**<br /><br /> **/h**|Zobrazí parametry příkazového řádku.|
|**/ AddRemoveFeatures**|Určuje, které funkce se mají přidat nebo odebrat u nainstalovaného produktu.|
|**/ Admin** *AdminDeployment.xml*|Nainstaluje aplikaci Visual Studio pomocí datového souboru, který jste zadali pro instalaci pro správu.|
|**/ ChainingPackage** *BundleName*|Určuje, který svazek řetězí tento svazek. Také můžete použít k určení kohorty prostředí pro zlepšování zákazníky.|
|**/ CreateAdminFile \<název souboru >**|Určuje umístění pro vytvoření řídicí soubor, který lze použít pomocí parametru/adminfile.|
|**/ CustomInstallPath** *Adresář_instalace*|Nainstaluje všechny balíčky s opětovným cílem do adresáře, který určíte.|
|**/ ForceRestart**|Po instalaci vždy restartuje počítač.|
|**/ úplné**|Nainstaluje všechny funkce produktu.|
|**/ InstallSelectableItems \<název položky 1 > [;\< Název položky 2 >]**|Seznam položky stromu výběru, můžete zkontrolovat na obrazovce pro výběr v Průvodci instalačním programem.|
|**/l**<br /><br /> **/ Protokolu** *název souboru*|Určí umístění souboru protokolu.|
|**/ Layout** *adresáře*|Zkopíruje soubory z instalačního média do zadaného adresáře.|
|**/ NoCacheOnlyMode**|Zabrání předběžnému naplnění mezipaměti balíčku.|
|**/ NoRefresh**|Zabrání kontrole požadovaných nebo doporučených aktualizovaných verzí pro novější verze tohoto produktu.|
|**/ norestart /**|Zabrání restartování počítače během instalace aplikace i po jejím dokončení. Najdete v části návratové kódy [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md) najdete návratové kódy, které chcete vyhledat.|
|**noweb**|Zabrání instalaci z internetu.|
|**/ OverrideFeedUri \<cesta_k_souboru_informačního_kanálu >**|Cesta k místnímu nebo externímu informačnímu kanálu s popisem softwarových položek.|
|**/ ProductKey**<br /><br /> *ProductKey*|Nastaví vlastní kód produkt key, který neobsahuje pomlčky a má maximálně 25 znaků.|
|**/ PromptRestart**|Vyzve uživatele před restartováním počítače.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/ silent**|Potlačí zobrazení uživatelského rozhraní (UI) pro instalaci aplikace. Pokud nezadáte žádné parametry s výjimkou tohoto a sada Visual Studio je již nainstalována, instalace aplikace bude spuštěna v režimu údržby.|
|**/qb**<br /><br /> **/passive**|Zobrazí průběh, ale nečeká na vstup uživatele.|
|**/ repair**|Opraví aplikaci Visual Studio.|
|**/ SuppressRefreshPrompt**|Zabrání zobrazení dialogového okna k dispozici aktualizacemi v Průvodci instalací, proto Průvodce instalací se automaticky přijme všechny požadované nebo doporučené aktualizované verze.|
|**/u**<br /><br /> **/ Uninstall**|Odinstaluje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|**/ Uninstall/Force**<br /><br /> **/ Force /u**|Odinstaluje Visual Studio a všechny funkce, které jsou sdíleny s jinými produkty. **Upozornění:** používáte-li tento parametr, jiné produkty, které jsou nainstalované na stejném počítači můžou přestat správně fungovat.|

## <a name="see-also"></a>Viz také
 [Příručka správce sady Visual Studio](../install/visual-studio-administrator-guide.md)